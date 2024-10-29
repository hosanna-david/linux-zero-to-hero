Linux commands I used 99% of the time:

𝗕𝗮𝘀𝗶𝗰𝘀:
1. `man` - Skim through manual for better understanding.
2. `nano` / `vim` - Use nano for basic editing, vim for advanced editing.
3. `ls -l` - List files with detailed info.
4. `ssh` - Connect to remote machines securely.
5. `df` / `du -hs *` - Check disk space usage.
6. `chown` / `chmod` - Change ownership and permissions of files.
7. `dig` - DNS lookup to find IPs of hostnames.

𝗘𝘃𝗲𝗿𝘆𝗱𝗮𝘆 𝗨𝘀𝗲:
1. `history` - View command history.
2. `cd -` - Switch to the previous directory.
3. `xargs` - Build and execute commands from input, with parallel execution support.
4. `pstree -p` - Display the process tree with process IDs.
5. `pgrep` / `pkill` - Find and signal processes by name.

𝗣𝗿𝗼𝗰𝗲𝘀𝘀𝗶𝗻𝗴 𝗙𝗶𝗹𝗲𝘀 𝗮𝗻𝗱 𝗗𝗮𝘁𝗮:
1. `find . -iname '*file*'` - Locate files by name.
2. `grep` / `ack` / `ag` - Search within files, with ag being the fastest.
3. `awk` / `sed` - Manipulate and format text.
4. `sort` / `uniq` - Sort and find unique lines.
5. `cut` / `paste` - Extract or combine columns of text.
 
𝗦𝘆𝘀𝘁𝗲𝗺 𝗗𝗲𝗯𝘂𝗴𝗴𝗶𝗻𝗴:
1. `top` / `htop` - View system performance and resource usage.
2. `netstat -lntp` - List all listening ports and associated processes.
3. `dstat` - Combined system stats view.
4. `strace` - Trace system calls and signals.
5. `lsof` - List open files and associated processes.
6. `tail -f /var/log/*.log`  - checking the logs is important 

System Intelligence:
• `htop` - Like top, but actually useful
• `df -h` - Because disk space issues find you
• `netstat -tulpn` - Your network's story
• `lsof` - What's using that port?
• `ps aux | grep` - Finding that runaway process
• `dmesg` - Kernel's gossip channel

File Operations:
• `find . -name` - Your file search superhero
• `tar -xvf` - Unzip like a pro
• `rsync` - scp's smarter cousin
• `sed -i` - Stream editing wizard
• `awk` - Text manipulation magic
• `grep -r` - Find text like a detective

Container Life:
• `docker stats` - Container vital signs
• `docker logs -f` - Live container stories
• `crictl pods` - Kubernetes container whisperer
• `kubectl get pods` - K8s status check

Monitoring Magic:
• `tail -f` - Log watching party
• `watch` - Command on repeat
• `vmstat` - Memory tales
• `iostat` - Disk performance poetry

Network Ninja:
• `curl -v` - HTTP storyteller
• `nc` - Network swiss army knife
• `dig` - DNS detective
• `ss` - Socket statistics

Security Stuff:
• `chmod` - Permission painter
• `chown` - Ownership wizard
• `openssl` - Certificate craftsman
• `ssh-keygen` - Key creator

Process Control:
• `systemctl` - Service sorcery
• `journalctl` - Log time machine
• `kill -9` - Process terminator
• `nice` - Priority painter

Performance Profiling:
• `strace` - System call spy
• `tcpdump` - Network packet poet
• `sar` - System activity reporter
• `perf` - Performance profiler

Text Wrangling:
• `cut -d` - Column collector
• `sort | uniq -c` - Pattern finder
• `tr` - Character changer
• `wc -l` - Line counter

File System:
• `du -sh` - Directory size detective
• `fdisk -l` - Disk detective
• `mount` - filesystem connector
• `ln -s` - Symlink sorcerer

Shell Shortcuts:
• `history` | grep - Command time machine
• `!!` - Last command replay
• `ctrl+r` - Reverse search magic
• `alias` - Command shortcut creator

Miscellaneous Mastery:
• `tee` - Output splitter
• `xargs` - Command multiplier
• `at` - Job scheduler
• `screen/tmux` - Terminal multiplexer
