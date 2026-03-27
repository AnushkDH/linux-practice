# Day 2 — SSH Keys, File Operations & System Commands

**Topic:** SSH Authentication, Basic File Operations & System Info Commands

---

## 📚 Key Concepts Learned

### SSH Keys — How Access Works in Real Teams
```
Junior (you)                        Team Lead / Manager
─────────────────────────────────────────────────────────
ssh-keygen                    →     receives public key
generates 2 keys:                   adds it to GCP metadata
  private key (NEVER share)   →     VM now trusts your key
  public key (share via email)
                               ←    you SSH in using private key
```

- Keys stored at: `/root/.ssh/`
- Encryption method: **ED25519, 256 bytes**
- Password SSH is possible but **key-based is always preferred** in DevOps

> ⚠️ **Golden Rule:** Never share your private key with anyone, ever.

---

### Git & GitHub Basics
- Installed **Git Bash** on Windows
- Used `git clone <repo-url>` to download Linux source code from GitHub
- GitHub is where Linux source code lives (open source, community developed)

---

### Process States (from Q&A)
| State | Meaning |
|-------|---------|
| Running | Actively using CPU |
| Sleeping | Waiting for something |
| **Zombie** | Half-completed — neither running, sleeping, nor properly killed |

---

## 🛠️ Commands Practiced

### File & Directory Operations
```bash
pwd                  # show current directory
cd ~                 # go to home directory of current user
mkdir devcloudops    # create a new folder
touch newfile        # create an empty file
cp newfile copyfile  # copy a file
mv newfile changefile  # rename or move a file
rm copyfile          # permanently delete a file (NO recycle bin!)
vi changefile        # open file in vi editor
                     # i → insert mode | Esc → exit insert | :wq → save & quit
echo "hello world"   # print text to terminal
ls -l                # list files with details
```

> ⚠️ `rm -rf` deletes folders forcefully and recursively — **never use in production**

### System Information Commands
```bash
hostname             # show machine name
hostname -i          # show private IP address
curl ifconfig.me     # show public IP address
uname -a             # full system details (OS, kernel, architecture)
who                  # who is currently logged in
who -a               # detailed login info
whoami               # show current user
w                    # logged in users + what they're doing
uptime               # how long machine has been running
top                  # live process viewer (like Task Manager)
free -h              # memory usage in human-readable format
df -h                # disk usage in human-readable format
free -h && df -h     # run both commands together
history              # show all previously run commands
```

---

## 💡 What I Observed

- `cd ~` always brings you back to your home directory regardless of where you are
- `rm` in Linux is **permanent** — no recycle bin, no undo
- `free -h` shows RAM (Mem) and swap memory separately
- `df -h` shows disk usage per filesystem/mount point
- `top` shows live CPU and memory usage per process (press `q` to quit)
- Ran `curl ifconfig.me` to find the VM's actual public IP

---

## 📝 Assignment

- Create GCP account → share billing screenshot
- Create first VM → share screenshot
- Practice all commands on personal Linux machine
