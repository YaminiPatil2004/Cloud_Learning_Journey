Linux Notes: Day 2
Cloud Computing Roadmap, Linux Week 1 (Basics). Written Oct 10, 2026.
1. Goal of Day 2
Create, read, copy, move (rename) and delete files and folders. I practised in a folder called ~/practice (full path /home/dell/practice).
2. Commands learned
Command
Meaning
mkdir name
make a directory (folder)
touch file
create an empty file
echo "text" > file
write text into a file (replaces old contents)
echo "text" >> file
add text to the end of a file
cat file
show what is inside a file
cp src dest
copy a file
mv src dest
move a file, or rename it if the destination is in the same folder
rm file
delete a file
rm -r folder
delete a folder and everything inside it (r = recursive)
rm -i file
ask before deleting
No message after a command usually means it worked. Linux only prints something when there is output or an error.
3. What I practised
cd ~                                  # go home
mkdir practice                        # make a folder
ls                                    # shows: practice  scripts  test
cd practice                           # walk in
pwd                                   # /home/dell/practice
touch notes.txt                       # create an empty file
echo "I am learning Linux" > notes.txt
cat notes.txt                         # I am learning Linux
echo "Day 2 done" >> notes.txt
cat notes.txt                         # both lines shown
cp notes.txt backup.txt               # copy
mv backup.txt old_notes.txt           # rename
cat old_notes.txt                     # same two lines
rm old_notes.txt                      # delete the copy
mkdir trash
rm -r trash                           # delete a folder
4. Safety rules for rm
• Linux has no recycle bin. Deleted means gone.
• Run pwd and ls before every rm to see where I am and what I am deleting.
• Use rm -i if I want Linux to ask first.
• Never run rm -rf on a path I have not double-checked, especially one starting with /.
5. Mistakes I fixed (and what they taught me)
What went wrong
Why
Fix
No such file or directory when running hello.sh
the file did not exist yet in that folder
create it first with nano hello.sh, check with ls
command not found after typing $bash hello.sh
I typed the $, which is part of the prompt
never type the $, only what comes after it
Prompt showed /mnt/c/WINDOWS/system32
I started Linux from a PowerShell window opened in a Windows folder (/mnt/c is the Windows C: drive)
run cd ~ to get home. Do not change anything in that folder.
Habit: every time I open Linux, run pwd first. If it shows /mnt/c/..., type cd ~.
6. Extra things I learned
Using Linux from Windows PowerShell
• wsl in PowerShell enters Ubuntu. exit returns to Windows.
• Prompt PS C:\Users\dell> means Windows PowerShell. Prompt dell@DESKTOP-1CH58H5:~$ means Linux.
• PowerShell does not run bash scripts. Bash scripts run inside Linux (WSL).
My first bash script
File ~/scripts/hello.sh:
#!/bin/bash
echo "Hello from Linux"
Run it with bash hello.sh.
Editing files
• nano file: save with Ctrl+O then Enter, exit with Ctrl+X.
• VS Code with the WSL extension edits files inside Linux. Open a folder with code ..
• Keep Linux scripts in my Linux home (~/scripts), not in /mnt/c.
7. Self-check questions
1. Which command creates an empty file? touch
2. What does echo "Hello" > notes.txt do to a file that already has text? Replaces the old contents.
3. How do I rename a.txt to b.txt? mv a.txt b.txt
4. How do I delete a folder and everything in it? rm -r foldername
5. What should I do before running rm? Run pwd and ls.
