Linux Notes: Day 3
Cloud Computing Roadmap, Linux Week 1 (Basics). Written Oct 15, 2026.
1. Goal of Day 3
Read files properly: see the start of a file, the end of a file, and scroll through a long file. These commands are used constantly to read logs on servers.
2. Why cat is not enough
cat prints the whole file at once. With 50 lines the early ones scroll away, and with a real log of thousands of lines it is useless. head, tail and less solve this.
3. Commands learned
Command
Meaning
seq 1 50
print the numbers 1 to 50, one per line
seq 1 50 > numbers.txt
save those numbers into a file
cat file
print the whole file
head file
show the first 10 lines
tail file
show the last 10 lines
head -n 3 file
show the first 3 lines (-n sets how many)
tail -n 3 file
show the last 3 lines
less file
open a viewer to scroll one screen at a time
Why tail matters: the newest messages in a log are at the end, so tail is the first thing to check when something goes wrong.
4. Keys inside less
Key
What it does
Space
next page
b
back one page
Down / Up arrows
move one line
/25 then Enter
search for "25"
n
jump to the next match
q
quit and return to the prompt
If I feel stuck inside less, press q. It only closes the viewer and does not change the file.
5. What I practised
cd ~/practice                  # start in the right folder
pwd                            # /home/dell/practice
seq 1 50 > numbers.txt         # make a 50-line file
cat numbers.txt                # whole file floods the screen
head numbers.txt               # 1 to 10
tail numbers.txt               # 41 to 50
head -n 3 numbers.txt          # 1 2 3
tail -n 3 numbers.txt          # 48 49 50
less numbers.txt               # scroll, then q to quit
head -n 5 /var/log/dpkg.log    # first 5 lines of the install log
less /var/log/dpkg.log
Good habit: I started in /mnt/c/WINDOWS/System32 (a Windows folder), ran cd ~/practice, and checked with pwd before creating anything.
6. Reading a real log: /var/log/dpkg.log
This file records packages installed on Ubuntu. One line looks like this:
2026-08-27 14:10:47  install  base-passwd:amd64  <none>  3.6.8
 date      time      action    package           old ver  new ver
The first lines of my log tell the story of a package install:
Line
Meaning
startup archives install
the package tool started installing
install base-passwd
began installing. <none> means there was no earlier version.
status half-installed
files are being put in place
status unpacked
files are in place, setup not finished
configure base-passwd
final setup step
A package goes through install, unpacked, configure. If an install fails, the log shows where it stopped. The date 2026-08-27 is when my Ubuntu was first set up.
7. Self-check questions
1. Which command shows the last lines of a log? tail
2. What does head -n 5 numbers.txt do? Shows the first 5 lines.
3. How do I get out of less? Press q.
4. Best command to read a long file page by page and search it? less
5. Which file records installed packages on Ubuntu? /var/log/dpkg.log

Quiz score: 100%.
