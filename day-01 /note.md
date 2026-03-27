# Day 1 — Linux Basics & GCP VM Setup

**Topic:** Introduction to Linux, File Structure & Basic Commands

---

## 📚 Key Concepts Learned

### What is Linux?
- An **operating system kernel** (not a complete OS by itself)
- Written in **C language** with 17,000+ open source contributors
- Code is publicly available on GitHub

### Why Linux over Windows for DevOps?
| Feature | Linux |
|--------|-------|
| Cost | Free & open source |
| Security | No .exe/.msi vulnerabilities |
| Performance | Uses less RAM, more lightweight |
| Stability | Fewer updates, rarely crashes |
| Multi-user | Multiple users can work simultaneously |
| Antivirus | Not needed |

### Ways to Run Linux
- ☁️ **Cloud platforms** (GCP, AWS, Azure) ← preferred in DevOps
- 🧪 Playground environments
- 💻 MobaXterm for local terminal access
- 🖥️ Physical installation (not recommended)

---

## 🖥️ Practical: Created GCP VM

- Created **Ubuntu 24.04 LTS** VM on Google Cloud Platform
- Connected via **SSH on port 22**
- Used **MobaXterm** for local terminal access

---

## 📁 Linux File Structure

```
/ (root)
├── bin/      → binary/executable files (no installation needed)
├── etc/      → configuration files (like C:\Windows on Windows)
├── usr/      → user-related files
├── var/
│   └── log/  → system log files (auth.log lives here)
├── tmp/      → temporary files
└── dev/      → device files
```

---

## 🛠️ Commands Practiced

```bash
ls                        # list files in current directory
cd /                      # change to root directory
cd log/                   # change into log folder
pwd                       # show current directory path
sudo -i                   # switch to root user
cat auth.log              # read full file
more auth.log             # read file page by page
tail auth.log             # show last 10 lines
tail -f auth.log          # follow file live (real-time updates)
tail -50 auth.log         # show last 50 lines
tail -f -50 auth.log      # follow + show last 50 lines
grep error auth.log       # search for keyword 'error' in file
cat auth.log | grep error # pipe: filter auth.log for 'error'
cat auth.log | grep anushkd140220  # filter logs by username
history                   # show all previously run commands
```

---

## 💡 What I Observed in auth.log

- Saw my own login session recorded: `session opened for user anushkd140220`
- Saw `sudo` session: `session opened for user root(uid=0)`
- Practiced filtering logs by username using `grep`

---

## 📝 Assignment

Practice all 15 commands independently on personal Linux machine.  
Be ready for **intermediate level topics** in the next session.
