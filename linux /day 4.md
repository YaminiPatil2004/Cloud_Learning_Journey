Linux Notes: Day 4
Cloud Computing Roadmap, Linux Week 2 (Administration). Written Oct 15, 2026.
1. Goal of Day 4
Understand users and sudo, and install and remove software with apt. This is how I will manage software on AWS servers.
2. Normal user vs administrator
Linux has a powerful administrator account called root. A normal user cannot change system files or install software, which protects the system from mistakes. When I need admin power for one command, I put sudo in front of it ("do this as the administrator").
• whoami shows my username (mine: dell).
• id shows my user number and groups. The group 27(sudo) is why sudo works for me.
• The sudo password is the one I chose when I set up Ubuntu. When I type it, nothing appears on screen, not even dots. That is normal.
3. Commands learned
Command
Meaning
whoami
print my username
id
show my user ID and groups
sudo command
run one command as administrator
sudo apt update
download the latest list of available software (installs nothing)
sudo apt upgrade
install newer versions of installed programs
sudo apt install name
install a program
sudo apt remove name
uninstall a program
which name
show where a command is stored
hash -r
make bash forget remembered program locations
4. What I practised
whoami                    # dell
id                        # groups include 27(sudo)
apt update                # failed: Permission denied
sudo apt update           # worked, listed 13 packages that can be upgraded
sudo apt install tree     # installed the tree program
tree ~/practice           # drew my practice folder as a tree
which tree                # /usr/bin/tree
tail -n 5 /var/log/dpkg.log   # saw my install at the end of the log
sudo apt remove tree      # uninstalled it
which tree                # printed nothing
5. What the outputs taught me
Permission denied without sudo. The error code 13 means a normal user cannot write to system folders such as /var/lib/apt. It is the safety rule at work, not a fault.
apt update only refreshes the list. The Get: lines are downloads of the software list from Ubuntu servers. It did not change any program. The last line (13 packages can be upgraded) means newer versions exist.
Installing follows the same steps as the log. apt showed Selecting, Unpacking, Setting up, matching the install, unpacked, configure steps I read in dpkg.log on Day 3.
Installing one program can trigger another. After tree was installed, man-db (the help-pages system) ran to update itself. That is the Processing triggers for man-db line.
Where programs live. which tree printed /usr/bin/tree. /usr/bin holds commands I can run by name. My own scripts are not there, which is why they need bash or ./.
My install is in the log. The end of /var/log/dpkg.log showed status installed tree:amd64 2.3.1-1 with today's date. The newest events are at the end, so tail is the right tool.
bash remembers locations. After removing tree, running it gave -bash: /usr/bin/tree: No such file or directory, not command not found, because bash remembered the old path. A new terminal, or hash -r, clears it.
6. Self-check questions
1. What does sudo do in front of a command? Runs it with administrator rights.
2. What does sudo apt update do? Downloads the latest list of available software.
3. Why did apt update fail without sudo? A normal user cannot change system files.
4. Which command uninstalls tree? sudo apt remove tree
5. What does which tree tell me? Where the command is stored.
Quiz score: 100%.
