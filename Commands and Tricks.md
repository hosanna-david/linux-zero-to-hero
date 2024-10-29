1. SSH Key Authentication: ssh-keygen -t rsa ssh-copy-id user@hostname
2. File Transfer: scp localfile.txt user@remote:/path
3. Text Search: grep -r "pattern" /path/to/search
4. Process Management: ps aux | grep process_name kill -9 process_id
5. System Information: uname -a cat /etc/os-release
6. Disk Usage: apt-get update apt-get install package_name
7. Package Management: ifconfig netstat -tulpn
8. Network Information: useradd username passwd username
9. User Management: chmod +x filename chown user:group filename
10. File Permissions: chmod +x filename chown user:group filename
11. Cron Jobs: crontab -e
12. System Logs: tail -f /var/log/syslog
13. SSH Tunneling: ssh -L local_port:remote_host:remote_port user@hostname
14. Firewall Configuration: ufw allow 80
15. Check Service Status: systemctl status service_name
16. Create a RAM Disk: mount -t tmpfs -o size=512M tmpfs /mnt/ramdisk
17. Environment Variables: export VARIABLE=value
18. Disk Encryption: cryptsetup luksFormat /dev/sdX
19. Docker Commands: docker ps docker exec -it container_id /bin/bash
20. Check System Load: Top
21. System Upgrades: apt-get upgrade
22. Run a Command in the Background: command &
23. List Open Ports: lsof -i
24. Find and Replace in Files: sed -i 's/old_text/new_text/g' filename
25. Check Available Memory: free -m
26. Monitor Network Traffic: tcpdump -i eth0
27. Install Nginx: apt-get install nginx
28. SSH Configurations: nano ~/.ssh/config
29. Generate Random Password: openssl rand -base64 12
30. Archive and Compress: tar -czvf archive.tar.gz /path/to/directory
31. Check System Uptime: Uptime
32. Run a Command on Multiple Servers: parallel-ssh -h hosts.txt -l username -i "command"
33. Monitor Disk I/O: iostat -d 5
34. Check Kernel Version: uname -r
35. Find Large Files: find / -type f -size +100M
36. Install Node.js: curl -sL https://deb.nodesource.com/setup_14.x | bash - apt-get install -y nodejs
37. Check File System Type: df -Th
38. Run a Command at Regular Intervals: watch -n 1 command
39. Limit CPU Usage: cpulimit -e process_name -l 50
40. Install Git: apt-get install git
41. Check System Architecture: Arch
42. List Installed Packages: dpkg –list
43. Create Symbolic Link: ln -s /path/to/source /path/to/link
44. List USB Devices: Lsusb
45. List Open Files by User: lsof -u username
46. Check SELinux Status: Sestatus
47. Install Python Pip: apt-get install python3-pip
48. Check RAID Status: cat /proc/mdstat
49. Check OpenVPN Status: systemctl status openvpn
50. Check Failed Login Attempts: cat /var/log/auth.log | grep "Failed password"
