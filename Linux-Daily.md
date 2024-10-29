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
1. `htop` - Like top, but actually useful
2. `df -h` - Because disk space issues find you
3. `netstat -tulpn` - Your network's story
4. `lsof` - What's using that port?
5. `ps aux | grep` - Finding that runaway process
6. `dmesg` - Kernel's gossip channel

File Operations:
1. `find . -name` - Your file search superhero
2. `tar -xvf` - Unzip like a pro
3. `rsync` - scp's smarter cousin
4. `sed -i` - Stream editing wizard
5. `awk` - Text manipulation magic
6. `grep -r` - Find text like a detective

Container Life:
1. `docker stats` - Container vital signs
2. `docker logs -f` - Live container stories
3. `crictl pods` - Kubernetes container whisperer
4. `kubectl get pods` - K8s status check

Monitoring Magic:
1. `tail -f` - Log watching party
2. `watch` - Command on repeat
3. `vmstat` - Memory tales
4. `iostat` - Disk performance poetry

Network Ninja:
1. `curl -v` - HTTP storyteller
2. `nc` - Network swiss army knife
3. `dig` - DNS detective
4. `ss` - Socket statistics

Security Stuff:
1. `chmod` - Permission painter
2. `chown` - Ownership wizard
3. `openssl` - Certificate craftsman
4. `ssh-keygen` - Key creator

Process Control:
1. `systemctl` - Service sorcery
2. `journalctl` - Log time machine
3. `kill -9` - Process terminator
4. `nice` - Priority painter

Performance Profiling:
1. `strace` - System call spy
2. `tcpdump` - Network packet poet
3. `sar` - System activity reporter
4. `perf` - Performance profiler

Text Wrangling:
1. `cut -d` - Column collector
2. `sort | uniq -c` - Pattern finder
3. `tr` - Character changer
4. `wc -l` - Line counter

File System:
1. `du -sh` - Directory size detective
2. `fdisk -l` - Disk detective
3. `mount` - filesystem connector
4. `ln -s` - Symlink sorcerer

Shell Shortcuts:
1. `history` | grep - Command time machine
2. `!!` - Last command replay
3. `ctrl+r` - Reverse search magic
4. `alias` - Command shortcut creator

Miscellaneous Mastery:
1. `tee` - Output splitter
2. `xargs` - Command multiplier
3. `at` - Job scheduler
4. `screen/tmux` - Terminal multiplexer
