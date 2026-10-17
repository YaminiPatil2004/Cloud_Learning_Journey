Linux Notes: Day 5
Cloud Computing Roadmap, Linux Week 2 (Administration). Written Oct 17, 2026.
1. Goal of Day 5
Understand processes: how Linux tracks every running program, how to look at them, and how to stop one safely. This is a core skill for troubleshooting servers.
2. The idea
A process is a program that is running right now. Every process gets a number called a PID (process ID), and Linux uses that number to find and control it. Think of it as a ticket number at a counter.
3. Commands learned
Command
Meaning
ps
snapshot of the processes in my current terminal
ps aux
snapshot of all processes on the system
| (pipe)
send the output of one command into another
ps aux | head -n 8
show only the first 8 lines of the long list
sleep 300
wait 300 seconds and do nothing else (a safe practice process)
command &
run the command in the background and give the prompt back
kill PID
politely ask the process with that PID to stop
top
live dashboard of the system, updates every few seconds
In top, press q to quit (same as less).
4. What I practised
ps                    # showed bash and ps
ps aux | head -n 8    # first lines of all processes
sleep 300 &           # printed [1] 664, so the PID is 664
ps                    # sleep appeared in the list
kill 664              # printed: [1]+ Terminated  sleep 300
ps                    # sleep was gone
top                   # live view, then q to quit
The [1] is only a job number for my terminal. The number Linux uses is the PID (664).
5. Safety rule for kill
• Only kill a PID I am sure about. Always look at the ps output first.
• Killing the wrong process on a server can stop a website or a database.
• Today I only killed my own sleep process.
6. Reading top
Part
What it shows
Top lines
how long the system has been running, and the load
Tasks:
how many processes exist, and how many are running or sleeping
%Cpu(s):
how busy the processor is
MiB Mem:
total, free and used memory (RAM)
The table
each process with PID, user, CPU %, memory % and command name
The table is sorted by CPU use. On a cloud server, top is one of the first things to run when a site feels slow, because it shows whether the CPU or the memory is the problem.
My result: Tasks: 27 total, so my whole Ubuntu runs only 27 processes.
The top row, explained
1  root  20  0  24408  15416  11572  S  0.0  0.4  0:05.25  systemd
Part
Meaning
1
PID 1, the first process
root
runs as the administrator
S
sleeping: idle and waiting for work
0.0 / 0.4
0% CPU and 0.4% memory
0:05.25
5 seconds of CPU time used in total
systemd
the program name
It was at the top only because nothing was busy (every process showed 0.0% CPU), so ties are listed by PID.
systemd is PID 1. It is the first process to start when Linux boots, and it starts and manages all the services (web servers, databases, SSH). Tomorrow's systemctl talks to it.
7. Self-check questions
1. What is a process? A running program, identified by a PID.
2. What is the difference between ps and top? ps is a snapshot, top is a live view.
3. What does & at the end of a command do? Runs it in the background.
4. How do I stop the process with PID 664? kill 664
5. What is systemd? The first process (PID 1), which manages services.
