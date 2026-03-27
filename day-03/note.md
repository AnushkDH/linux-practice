# Day 3 — TAR, Shell Scripting, Permissions & User Management

**Topic:** File Compression, Shell Scripting, File Permissions & User/Group Management

---

## 📚 Key Concepts Learned

### 1. GCP IAM — Granting Project Access
- **IAM = Identity and Access Management** — controls who can access what in GCP
- Process: Grant Access → New Principal → Add email → Assign Role (e.g. Owner)
- SSH keys transfer automatically when project access is granted

---

### 2. Process Monitoring
```bash
top                        # live process viewer (press q to quit)
htop                       # improved visual version of top
uptime                     # how long machine has been running
ps -ef                     # list all running processes
ps -ef | grep java         # filter processes by name (java/python/oom)
ps -aef | grep oom         # filter for Out of Memory processes
du -h                      # folder/directory size in human-readable format
ping www.google.com        # check network connectivity
ping 34.59.109.131         # ping a specific IP address
last                       # show last logged-in users
```

---

### 3. File Compression (TAR)

TAR = **Tape Archive** — Linux equivalent of zip/unzip

```bash
# Create a directory with sample files
mkdir myfiles
touch myfiles/{a.txt,b.txt,c.txt}

# Compress (c=create, v=verbose, f=file)
tar cvf allfiles.tar myfiles/

# Extract (x=extract, v=verbose, f=file)
tar xvf allfiles.tar

# List contents without extracting
tar tvf allfiles.tar
```

| Flag | Meaning |
|------|---------|
| `c` | Create archive |
| `x` | Extract archive |
| `v` | Verbose (show progress) |
| `f` | Specify filename |

---

### 4. Shell Scripting — First Script

A shell script = a file containing multiple commands that run together.

```bash
#!/bin/bash
# ↑ shebang line — always required, tells Linux to use bash

uname -a       # system info
free -h        # memory usage
df -h          # disk usage
who            # logged in users
du -h          # directory sizes
```

**Making a script executable and running it:**
```bash
ls -l shellfile.sh          # check permissions (shows rw-r--r--)
chmod +x shellfile.sh       # add execute permission (shows rwxr-xr-x)
./shellfile.sh              # execute the script
```

---

### 5. File Permissions

Every file has 3 permission sets: **Owner | Group | Others**

```
-rwxr-xr-x
 ↑↑↑ ↑↑↑ ↑↑↑
 │││  │││  └── Others: r-x (read + execute)
 │││  └──────── Group:  r-x (read + execute)
 └──────────── Owner:  rwx (read + write + execute)
```

| Number | Permission | Meaning |
|--------|-----------|---------|
| 7 | rwx | Full access |
| 5 | r-x | Read + Execute |
| 4 | r-- | Read only |

```bash
chmod +x script.sh     # add execute permission
chmod 755 script.sh    # owner=full, group/others=read+execute (standard)
ls -l                  # view permissions of all files
```

> ⚠️ **Never use `chmod 777`** — gives everyone full access, major security risk

---

### 6. User Management

```bash
adduser rk             # create new user 'rk'
passwd rk              # set/change password for rk
su rk                  # switch to user rk
sudo -i                # switch to root from normal user
exit                   # return to previous user
deluser rk             # delete user rk
whoami                 # confirm current user
```

**Key system files:**
| File | Contains |
|------|---------|
| `/etc/passwd` | User account info |
| `/etc/shadow` | Encrypted passwords |
| `/etc/group` | Group memberships |

---

### 7. Group Management

```bash
addgroup linux         # create group 'linux'
addgroup devops        # create group 'devops'
usermod -aG linux rk   # add user rk to group linux
usermod -aG devops rk  # add user rk to group devops
getent group           # list all groups and their members
delgroup devops        # delete group (does NOT delete users)
```

---

### 8. Advanced User Management (chage & sudoers)

```bash
chage rk               # set password expiry/policy for user rk
cat /etc/passwd        # view all user accounts
cat /etc/shadow        # view encrypted passwords (root only)
cat /etc/group         # view all groups
visudo                 # safely edit /etc/sudoers file (grant sudo access)
```

**Real-world use case:** Set account expiry for contract/temporary employees so access auto-revokes on end date.

---

## 💡 What I Observed

- After `chmod +x`, the file name turns **green** in `ls -l` output — confirms it's executable
- `ps -ef | grep <name>` is how DevOps engineers find specific running services in production
- `delgroup` only deletes the group — the users inside it still exist
- `/etc/shadow` is only readable by root — that's by design for security
- My user `rk` was created with sudo privileges via `visudo`

---

## 📝 Real-World Scenarios Discussed

- Filtering processes by OOM (Out of Memory) to debug memory issues on servers
- Replicating a colleague's group permissions for a new team member using `usermod`
- Managing separate groups for `developers` vs `devops` teams with different access levels

---

## 🛠️ Full Commands Reference for Day 3

| Category | Commands |
|----------|---------|
| Monitoring | `top`, `htop`, `uptime`, `free -h`, `df -h`, `ps -ef`, `who`, `w`, `last` |
| Files | `cat`, `vi`, `tar cvf`, `tar xvf`, `du -h`, `ls -l` |
| Users | `adduser`, `deluser`, `su`, `passwd`, `usermod`, `chage` |
| Groups | `addgroup`, `delgroup`, `getent group` |
| Permissions | `chmod`, `ls -l`, `visudo` |
| Network | `ping`, `curl ifconfig.me` |
