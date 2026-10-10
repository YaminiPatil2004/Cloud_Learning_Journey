Linux Notes: Setup and Day 1
Cloud Computing Roadmap, Linux Week 1 (Basics). Written Oct 8, 2026.
1. Why Linux?
• Most cloud servers (including AWS EC2) run Linux.
• Cloud servers usually have no desktop, only a terminal (text interface), so commands are the main way to work.
2. Setup: Ubuntu on Windows (WSL)
WSL = Windows Subsystem for Linux. It runs Ubuntu inside Windows.
1. Open PowerShell as administrator.
2. Run: wsl --install
3. Restart the computer.
4. Open Ubuntu from the Start menu.
5. Create a username and password when asked (mine: dell).
Result: a terminal prompt like this:
dell@DESKTOP-1CH58H5:~$
Reading the prompt
• dell = my username
• DESKTOP-1CH58H5 = computer name
• ~ = current folder (~ means my home folder)
• $ = normal user (# would mean root, the administrator)
3. The Linux filesystem
Linux has no C: or D: drives. Everything is one tree starting at root (/).
Folder
What it holds
/home
personal files (mine: /home/dell)
/etc
configuration files
/var/log
system logs
/usr
installed programs
/bin
essential commands
/tmp
temporary files
Think of folders as rooms in a house. I am always standing in one room, and pwd tells me which.
4. Paths
• Absolute path: starts from /, works from anywhere. Example: /var/log
• Relative path: starts from where I am now. Example: docs/a.txt
• Shortcuts: . = current folder, .. = parent folder (one level up), ~ = home folder
5. Commands learned
Command
Meaning
pwd
print working directory (where am I?)
ls
list files
ls -a
include hidden files (names starting with .)
ls -l
long format (permissions, owner, size, date)
ls -la
long format plus hidden files
cd /path
go to an absolute path
cd ..
go up one level
cd or cd ~
go to home
cd /
go to root
cd -
go back to the previous folder
Mistake I corrected: plain cd goes home, it does not go up a level. To go up one level, use cd ...
6. What I practised
cd /etc          # went to /etc
cd ..            # went up to /
pwd              # showed /
cd ~             # went home
pwd              # showed /home/dell
cd /var/log      # went to the logs folder
ls               # listed log files
cd /var/log      # then:
cd ..            # went up to /var
pwd              # showed /var
7. Reading ls -la output
drwxr-xr-x 2 dell dell 4096 Oct  8 09:11 test
• First character: d = directory, - = regular file
• Next 9 characters: permissions (owner, group, others), explained in Week 3
• dell dell = owner and group
• 4096 = size in bytes
• Oct 8 09:11 = last modified
• test = name
In ls colours, blue = directory, white = regular file.
Hidden files in my home folder
Name
What it is
.bashrc
settings that run each time I open a terminal
.profile
settings that run at login
.bash_logout
runs at logout
.cache, .config
where apps keep cached data and settings
Important logs in /var/log
File
What it records
syslog
general system messages
auth.log
logins and sudo use
dpkg.log, apt/
package installs
kern.log
kernel messages
I will read these with less, tail and journalctl in Week 2.
8. Self-check questions
1. From /var/log, which command goes to /var? cd ..
2. From /var/log, how do I reach /? (two ways: cd ../.. or cd /)
3. What does d at the start of an ls -l line mean? A directory.
4. Absolute or relative: /etc/hosts? docs/a.txt?
