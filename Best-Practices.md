
<h2><strong>Linux Security Tips and Best Practices</strong></h2>
<p>As the use of Linux systems continues to grow, it's crucial to implement adequate security measures to protect a system from potential threats. The sections below offer a range of practical tips and best practices for enhancing the security of a Linux system.</p>
<h3>1. Use Strong Passwords</h3>
<p>(Basic security mechanism)</p>
<p>Use strong passwords</a> and change them regularly as a basic step to securing your Linux system. Strong passwords prevent unauthorized access to the system and reduce the risk of identity theft, data loss</a>, and other security incidents.</p>
<p>A strong password is at least 12 characters long and includes a mixture of upper and lowercase letters, numbers, and special characters. That makes brute-force attacks</a> extremely more difficult.</p>
<p>Regularly changing passwords also improves security. The process reduces the risk of password reuse and exposure, giving a potential attacker a limited time frame to exploit the password if it becomes compromised.</p>
<h3>2. Verify All Accounts Have Passwords</h3>
<p>(Basic security mechanism)</p>
<p>Accounts with no passwords allow anyone to log into the system without any authentication, compromising the system's data security and confidentiality. Therefore, make sure to verify that no accounts have empty passwords. </p>
<p>Run the awk command with the following options:</p>
<pre class="wp-block-code"><code>sudo awk -F: &#039;($2 == &quot;&quot;) {print $1}&#039; /etc/shadow </code></pre>
<p>This command searches the <em>/etc/shadow</em> file, which contains information about user account passwords, and prints the names of any accounts with an empty password field. </p>
<p>Since accounts with empty passwords are a serious security risk, consider the following actions:</p>
<ul class="wp-block-list">
<li><strong>Set a password</strong>. For instance, assign a new password to a user with the passwd command:</li>
</ul>
<pre class="wp-block-code"><code>sudo passwd &#091;username]</code></pre>
<ul class="wp-block-list">
<li><strong>Disable the account</strong>. Prevent users from logging into the account by disabling it entirely. To lock a Linux user account, run the&nbsp; usermod command</a> with the <strong><code>-L</code></strong> option (which prints no output): </li>
</ul>
<pre class="wp-block-code"><code>sudo usermod -L &#091;username]</code></pre>
<p>Alternatively, use the <strong><code>passwd</code></strong> command with the <strong><code>-l</code></strong> option:</p>
<pre class="wp-block-code"><code>sudo passwd -l &#091;username]</code></pre>
<p>The user is now unable to log in using their password.</p>
<ul class="wp-block-list">
<li><strong>Delete the account</strong>. Remove unnecessary accounts with:</li>
</ul>
<pre class="wp-block-code"><code>sudo userdel &#091;username]</code></pre>
<p>The command shows no output if executed correctly.</p>
<h3>3. Set Up Password Aging</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Password aging is the practice of requiring users to change passwords regularly. Regular password changes reduce the chance of users reusing previous passwords. The practice also prevents password cracking attacks, which often succeed because of weak passwords that are not changed frequently. </p>
<p>There are several ways to set up password aging for a Linux user:</p>
<ul class="wp-block-list">
<li>Use the <strong><code>chage</code></strong> command. For instance, enable a password aging process that ensures the password expires in 60 days, the system warns the user 10 days before the expiration date, and the user has to change the password within 14 days. To do so, run:</li>
</ul>
<pre class="wp-block-code"><code>sudo chage -M 60 -m 10 -W 14 &#091;username]</code></pre>
<ul class="wp-block-list">
<li>Alternatively, use the <strong><code>passwd</code></strong> command:</li>
</ul>
<pre class="wp-block-code"><code>sudo passwd -x 60 &#091;username]</code></pre>

<p>The command sets the password expiration date for <em>NewUser</em> at 60 days.</p>
<h3>4. Restrict the Use of Previous Passwords on Linux</h3>
<p>(Basic security mechanism)</p>
<p>Prevent all users from reusing old passwords. Old passwords might have been compromised and attackers might be actively trying to take advantage of that to hack into the system. </p>
<p>To prevent password reuse attacks:</p>
<ol class="wp-block-list" style="list-style-type:1">
<li>Enforce password history with <strong>PAM</strong>, a unique Linux library with the <strong><code>pam_unix</code></strong> module feature. This feature keeps track of users' passwords and disallows the reuse of any previously used ones.&nbsp;</li>
<li>Enforce rules for password complexity, including minimum length and a mix of characters, with <strong><code>pam_cracklib</code></strong>. Requiring users to create complex passwords makes it more difficult for attackers to guess or crack passwords. </li>
<li>Regularly check system logs for any suspicious activity, such as repeated failed login attempts, to detect potential password-related security threats.</li>
<li>Store hashed passwords using a strong cryptographic hash function such as Message-Digest Algorithm (MDA), Secure Hash Algorithm (SHA), or  NTLM</a>.</li>
<li>Use an&nbsp; enterprise password manager</a>&nbsp;to generate and store unique, secure passwords for each account.</li>
</ol>
<h3>5. Ensure OpenSSH Server Security</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>OpenSSH is a widely used and secure implementation of SSH</a> for Linux systems. It provides encryption for data in transit</a>, robust authentication</a> methods, and a secure way to administer systems and transfer files remotely. To ensure the security of OpenSSH, minimize the tool's vulnerabilities.</p>
<p>Secure the OpenSSH server by following these tips:</p>
<ul class="wp-block-list">
<li>Use non-standard SSH ports</a>.</li>
<li>Limit user access and disable root login.</li>
<li>Use SSH key</a> pairs for authentication.</li>
<li>Disable root login and password-based logins on the server.</li>
<li>Keep OpenSSH updated regularly.</li>
<li>Use strong authentication methods.</li>
<li>Limit the number of authentication attempts.</li>
<li>Disable unused protocols and features.</li>
<li>Implement a firewall.</li>
<li>Monitor logs regularly.</li>
</ul>
<h3>6. Disable Root Login via SSH</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Linux machines have external root access enabled by default. That leaves an open SSH security</a> vulnerability which hackers can exploit with brute-force attacks. Disabling server SSH root login prevents unauthorized individuals from gaining control over the system. An active root account allows attackers to obtain or guess the root password with full administrative privileges.</p>
<p>To disable root login in Linux, change the SSH configuration file:</p>
<p>1. Open the file in a text editor of your choice</a>. To access the config file in Vim, run:</p>
<pre class="wp-block-code"><code>sudo vim /etc/ssh/sshd_config</code></pre>
<p>2. Find the <strong><code>PermitRootLogin</code></strong> line.</p>
<p>3. Change the value from <strong><code>yes</code></strong> to <strong><code>no</code></strong>.</p>
<p>4. <a href="https://phoenixnap.com/kb/how-to-vim-save-quit-exit" target="_blank" rel="noreferrer noopener">Save the changes and exit the file</a>.</p>
<p>5. Restart the SSH service to apply the changes.</p>
<div class="notice-note">
<div></div>
<div class="notice-text"><p><strong>Note</strong>: Disabling root login can prevent legitimate users from performing administrative tasks on the system. Ensure that authorized users have the necessary permissions by creating a regular user account with administrative privileges and add the user to the sudo group</a>.</p>
</div>
</div>
<h3>7. Limit the Use of sudo</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Unrestricted use of <strong><code>sudo</code></strong> leads to privilege escalation and allows attackers to gain control of the system. Limiting <strong><code>sudo</code></strong> permissions reduces the number of potential attack vectors</a>. If an attacker gains access to a user account, they will only be able to run a limited set of Linux commands</a>, making it harder to cause damage. </p>
<p>However, limiting the use of <strong><code>sudo</code></strong> requires modifying the sudoers file</a>. While it's possible to do it correctly, making mistakes could result in security vulnerabilities.</p>
<h3>8. Ensure Only Root Has User ID Set to 0</h3>
<p class="h4">(Basic security mechanism)</p>
<p>The root account controls the system, including installing and removing software, modifying system configuration files, and accessing all user data. Root is also the only account with a User ID (UID) set to 0.</p>
<p>A non-root account with a UID of 0 is effectively equivalent to the root account, creating a significant security risk.</p>
<p>To ensure that no non-root accounts have a UID of 0, run:</p>
<pre class="wp-block-code"><code>sudo awk -F: &#039;($3 == &quot;0&quot;) {print}</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="73" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%2073'%3E%3C/svg%3E" alt="sudo awk -F terminal output" class="wp-image-159156" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output-300x27.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output-768x70.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output.png" /><noscript><img decoding="async" width="800" height="73" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output.png" alt="sudo awk -F terminal output" class="wp-image-159156" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output-300x27.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-awk-f-3-0-print-etc-passwd-terminal-output-768x70.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>The command prints root as the only user with a UID of 0. If the output shows any non-root accounts with a UID of 0, delete them or change the UID to a non-zero value with <strong><code>usermod</code></strong>.&nbsp;</p>
<h3 id="ftoc-heading-11" class="wp-block-heading ftwp-heading">9. Lock User Accounts After Login Failures</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Locking user accounts after several login failures makes it harder for an attacker to guess or brute-force a password.</p>
<p>The system works by setting the maximum number of login attempts per user. Once that number is reached, the account locks for a specified period. Another option is to install a system for unlocking the account, either automatically after a set time has elapsed or manually by an administrator.</p>
<p>To achieve this, use different&nbsp;<a href="https://phoenixnap.com/glossary/identity-and-access-management" target="_blank" rel="noreferrer noopener">Identity Access Management (IAM) systems</a>. These tools block incoming traffic from IP addresses with failed login attempts, helping mitigate brute-force attacks or monitor log files and ban IP addresses with repeated failed login attempts.</p>
<p>Writing custom scripts to parse log files, keep track of failed login attempts, and lock user accounts is also an option.</p>
<h3 id="ftoc-heading-12" class="wp-block-heading ftwp-heading">10. Enable Two-Factor Authentication</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Two-factor authentication (2FA) is a security measure that adds an extra layer of protection. By requiring a secondary verification method, such as a one-time code sent to the user's mobile device, 2FA makes it much more difficult for unauthorized users to access sensitive information or systems.</p>
<p>There are various ways to enable 2FA on Linux systems. Common methods include using <a href="https://phoenixnap.com/glossary/totp-time-based-one-time-password" target="_blank" rel="noreferrer noopener">TOTP (Time-based One-Time Password)</a> apps like <strong>Google Authenticator</strong> or a hardware token like a <strong>Yubikey</strong>. Certain Linux systems have built-in 2FA capabilities, such as <strong>PAM (Pluggable Authentication Modules)</strong>, that work with various authentication methods.</p>
<h3 id="ftoc-heading-13" class="wp-block-heading ftwp-heading">11. Keep Linux Up to Date</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Hackers exploit outdated software. To maintain Linux server security, keep the Linux kernel and software up to date. Different <a href="https://phoenixnap.com/glossary/what-is-a-linux-distribution" target="_blank" rel="noreferrer noopener">Linux distributions</a> offer various&nbsp;package managers&nbsp;to update packages manually, with <a href="https://phoenixnap.com/kb/yum-vs-apt" target="_blank" rel="noreferrer noopener">yum and apt</a> being the most popular.</p>
<p>Another method includes automatic updates. Automatic updates are installed in the background without requiring any action from the user, making updating software easier and more convenient. However, these types of updates are also risky. </p>
<div class="notice-warning">
<div class="warning-icon-wrapper"><i class="fa fa-exclamation-triangle"></i></div>
<div class="notice-text"><p><strong>Important</strong>: Automatic updates cause compatibility issues with other packages or result in unexpected changes to the system. In general, it is not recommended to run automatic updates on production servers.</p>
</div>
</div>
<h3 id="ftoc-heading-14" class="wp-block-heading ftwp-heading">12. Use Linux Security Extensions</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Linux security extensions are tools and features that provide additional security measures to a Linux operating system. These extensions help protect against misconfigured or compromised programs, defend against potential attacks, and enforce limitations on networks and programs.</p>
<p>Popular Linux security extensions are:</p>
<ul class="wp-block-list">
<li><a href="https://phoenixnap.com/kb/selinux" target="_blank" rel="noreferrer noopener">SELinux (Security-Enhanced Linux)</a>&nbsp;is a security feature integrated into the Linux kernel that uses <a href="https://phoenixnap.com/glossary/mandatory-access-control-mac" target="_blank" rel="noreferrer noopener">Mandatory Access Control</a> (MAC) system. It allows administrators to control access to system resources by only allowing authorized users and processes. This ensures that only trusted parties access and modify important system information. SELinux is more common in RHEL and CentOS&nbsp;systems.</li>
<li><a href="https://phoenixnap.com/kb/apparmor-vs-selinux" target="_blank" rel="noreferrer noopener">AppArmor</a>&nbsp;is a mandatory access control system that allows administrators to specify the permissions required by applications to access system resources. It's been a default feature of Ubuntu since version 7.10.&nbsp;</li>
<li>TCP Wrappers are a security tool that provides basic access control for network services by checking the client's IP address against a list of allowed or denied addresses. The request is granted if the client's IP address is found in the <em>allow </em>list, and if it is found in the <em>deny </em>list, the request is rejected.</li>
<li>PAM (Pluggable Authentication Modules) provides a flexible and centralized system for managing authentication on a Linux system. PAM allows administrators to configure the authentication system and choose the best methods for their security needs. Moreover, PAM makes it easier to enforce strong authentication policies and ensures that all applications and services use the same authentication system.</li>
</ul>
<h3 id="ftoc-heading-15" class="wp-block-heading ftwp-heading">13. Configure Linux Firewall&nbsp;</h3>
<p class="h4">(Basic security mechanism)</p>
<p>A&nbsp;<a href="https://phoenixnap.com/glossary/what-is-a-firewall" target="_blank" rel="noreferrer noopener">firewall</a>&nbsp;on a Linux system acts as the first line of defense against malicious network traffic. The firewall&nbsp;defines rules that govern what traffic is allowed and what is blocked. Sysadmins apply those rules to control incoming and outgoing network traffic, blocking unauthorized access and only allowing necessary services.</p>
<p>The default Linux firewall is&nbsp;<a href="https://phoenixnap.com/kb/iptables-tutorial-linux-firewall" target="_blank" rel="noreferrer noopener">iptables</a>, a popular tool that provides packet filtering and manipulation capabilities for IPv4 and IPv6 network traffic. It filters network traffic,&nbsp;<a href="https://phoenixnap.com/kb/iptables-port-forwarding" target="_blank" rel="noreferrer noopener">forwards traffic</a>&nbsp;between network interfaces, and implements&nbsp;<a href="https://phoenixnap.com/glossary/nat-network-address-translation" target="_blank" rel="noreferrer noopener">network address translation (NAT)</a>.</p>
<h3 id="ftoc-heading-16" class="wp-block-heading ftwp-heading">14. Reduce Network Service Vulnerabilities by Isolation</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>To enhance the security of network services, run each service on a separate server or virtual instance. The process limits the number of vulnerable services, making managing <a href="https://phoenixnap.com/glossary/what-is-security-patch" target="_blank" rel="noreferrer noopener">security patches</a>, updates, and configurations easier.</p>
<p>There are several ways to implement this method:</p>
<ul class="wp-block-list">
<li>Use virtualization tools like <a href="https://phoenixnap.com/kb/install-virtualbox-on-ubuntu" target="_blank" rel="noreferrer noopener">VirtualBox</a> to create individual <a href="https://phoenixnap.com/glossary/what-is-a-virtual-machine" target="_blank" rel="noreferrer noopener">virtual machines (VMs)</a> for each network service. Or, create isolated containers with <a href="https://phoenixnap.com/kb/what-is-docker" target="_blank" rel="noreferrer noopener">Docker</a> or <a href="https://phoenixnap.com/kb/what-is-kubernetes" target="_blank" rel="noreferrer noopener">Kubernetes</a> for each network service.</li>
<li>Use firewall rules to control incoming and outgoing network traffic, only allowing the necessary services.</li>
<li><a href="https://phoenixnap.com/blog/network-segmentation-security" target="_blank" rel="noreferrer noopener">Segment the network</a> into separate subnets to isolate different services and minimize the risk of attacks.</li>
<li>Regularly <a href="https://phoenixnap.com/glossary/what-is-network-monitoring" target="_blank" rel="noreferrer noopener">monitor network traffic</a> and logs for suspicious activity and take appropriate action.</li>
</ul>
<h3 id="ftoc-heading-17" class="wp-block-heading ftwp-heading">15. Secure Web Servers</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Web servers like <a href="https://phoenixnap.com/glossary/what-is-apache" target="_blank" rel="noreferrer noopener">Apache</a> and <a href="https://phoenixnap.com/kb/how-to-install-nginx-on-ubuntu-20-04" target="_blank" rel="noreferrer noopener">Nginx</a> are prime cyberattack targets as they often deal with sensitive data. Securing these servers is critical to prevent unauthorized access and <a href="https://phoenixnap.com/blog/what-is-a-data-breach" target="_blank" rel="noreferrer noopener">data breaches</a>.</p>
<p>Top tips for securing Apache and Nginx web servers are:</p>
<ul class="wp-block-list">
<li>Regularly update the software to apply the latest security patches and fixes.</li>
<li>Configure access control to limit access to sensitive information and prevent unauthorized access.</li>
<li>Disable unneeded modules and features to reduce the attack surface and minimize security vulnerabilities.</li>
<li>Use strong passwords to secure the administration interface and prevent unauthorized access.</li>
<li>Use SSL certificates to encrypt data transmitted over the network and secure sensitive information such as passwords and financial data.</li>
<li>Regularly monitor logs for suspicious activity or unauthorized access attempts.</li>
<li>Run web servers as a non-root user with limited privileges to prevent unauthorized access and data breaches.</li>
</ul>
<h3 id="ftoc-heading-18" class="wp-block-heading ftwp-heading">16. Detect Listening Network Ports</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>In a Linux system, <a href="https://phoenixnap.com/glossary/what-is-a-port" target="_blank" rel="noreferrer noopener">ports</a> are used when a program, such as a server or a network service, opens a <a href="https://phoenixnap.com/glossary/what-is-a-socket" target="_blank" rel="noreferrer noopener">network socket</a> to receive incoming client connections. Open ports listen for those incoming connections.</p>
<p>However, listening ports are a weakness attackers exploit. A vulnerable listening port provides access to the system or sensitive information. </p>
<p>By detecting all listening ports, sysadmins identify and secure them by applying updates, limiting access, or disabling unnecessary ones. Furthermore, identifying listening ports helps detect rogue or unauthorized applications that pose a security risk.</p>
<p>Identify listening ports in a Linux system with <a href="https://phoenixnap.com/kb/netstat-command" target="_blank" rel="noreferrer noopener">netstat</a>, <a href="https://phoenixnap.com/kb/ss-command" target="_blank" rel="noreferrer noopener">ss</a>, or <a href="https://phoenixnap.com/kb/lsof-command" target="_blank" rel="noreferrer noopener">lsof</a>.</p>
<h3 id="ftoc-heading-19" class="wp-block-heading ftwp-heading">17. Disable Unwanted Linux Services</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Unneeded services in Linux are a security vulnerability and consume resources like memory and <a href="https://phoenixnap.com/glossary/cpu-definition" target="_blank" rel="noreferrer noopener">CPU</a>. To improve security and performance on a Linux operating system server, keep a minimal installation with only the necessary packages.</p>
<p>To manage system services, Linux uses <a href="https://phoenixnap.com/kb/journalctl-systemd-logs" target="_blank" rel="noreferrer noopener">systemd</a> with the <strong><code>systemctl</code></strong> command.</p>
<p>1. To check if a service is active, run:</p>
<pre class="wp-block-code"><code>sudo systemctl status &#091;service_name]</code></pre>
<p>For instance, check the status for <a href="https://phoenixnap.com/kb/snap-packages" target="_blank" rel="noreferrer noopener">snap</a> with:</p>
<pre class="wp-block-code"><code>sudo systemctl status snapd</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="203" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%20203'%3E%3C/svg%3E" alt="sudo systemctl status snapd terminal output" class="wp-image-159175" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output-300x76.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output-768x195.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output.png" /><noscript><img decoding="async" width="800" height="203" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output.png" alt="sudo systemctl status snapd terminal output" class="wp-image-159175" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output-300x76.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-status-snapd-terminal-output-768x195.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>2. To stop an active service, run:</p>
<pre class="wp-block-code"><code>sudo systemctl stop &#091;service_name]</code></pre>
<p>To stop <strong><code>snap</code></strong>, execute:</p>
<pre class="wp-block-code"><code>sudo systemctl stop snapd</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="79" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%2079'%3E%3C/svg%3E" alt="sudo systemctl stop snapd terminal output" class="wp-image-159176" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output-300x30.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output-768x76.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output.png" /><noscript><img decoding="async" width="800" height="79" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output.png" alt="sudo systemctl stop snapd terminal output" class="wp-image-159176" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output-300x30.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-stop-snapd-terminal-output-768x76.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>3. To prevent the service from starting at boot, use:</p>
<pre class="wp-block-code"><code>sudo systemctl disable &#091;service_name]</code></pre>
<p>For instance, apply this command on <strong><code>snap</code></strong>:</p>
<pre class="wp-block-code"><code>sudo systemctl disable snapd</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="54" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%2054'%3E%3C/svg%3E" alt="sudo systemctl disable snapd terminal output" class="wp-image-159178" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output-300x20.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output-768x52.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output.png" /><noscript><img decoding="async" width="800" height="54" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output.png" alt="sudo systemctl disable snapd terminal output" class="wp-image-159178" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output-300x20.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-systemctl-disable-snapd-terminal-output-768x52.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>When working with older systems that use System V or Upstart, run the <a href="https://phoenixnap.com/kb/chkconfig" target="_blank" rel="noreferrer noopener">chkconfig</a> command to manage services. </p>
<p>It is also important to check dependencies before installing software and inspect auto-started dependencies to ensure they are needed.</p>
<h3 id="ftoc-heading-20" class="wp-block-heading ftwp-heading">18. Use Centralized Authentication Service</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>A Centralized Authentication Service (CAS) is a <a href="https://phoenixnap.com/glossary/single-sign-on-sso" target="_blank" rel="noreferrer noopener">single sign-on</a> protocol that allows web applications that may not be trusted to authenticate users through a centralized, trusted server. The CAS server handles all authentication, so the user's credentials are not revealed to the applications.</p>
<p>A centralized authentication service is crucial for Linux security as it allows sysadmins to enforce password policies and manage user accounts in a secure and scalable way. It makes monitoring and auditing authentication easier, reduces the risk of lost login credentials, and ensures consistent user data.</p>
<p>Common Linux Central Authentication Services are <a href="https://phoenixnap.com/blog/kerberos-authentication" target="_blank" rel="noreferrer noopener">Kerberos</a>, <a href="https://phoenixnap.com/kb/ubuntu-samba" target="_blank" rel="noreferrer noopener">Samba</a>, and Winbind.</p>
<h3 id="ftoc-heading-21" class="wp-block-heading ftwp-heading">19. Set Up an Intrusion Detection System</h3>
<p class="h4">(Advanced security mechanism)</p>
<p>An <a href="https://phoenixnap.com/blog/intrusion-detection-system" target="_blank" rel="noreferrer noopener">intrusion detection system</a> (IDS) monitors processes running on the server. It detects potential threats such as denial-of service attacks, port scans, or attempts to crack into computers by monitoring network traffic.</p>
<p>Popular IDS options include:</p>
<ul class="wp-block-list">
<li><strong>Sophos</strong>. A cloud-based management platform that integrates multiple security products and uses machine learning to trigger automatic threat responses. It also uses advanced techniques like sandboxing and SSL inspection to identify and isolate compromised systems.</li>
<li><strong>SolarWinds - NetFlow Traffic Analyzer</strong>. <a href="https://phoenixnap.com/kb/linux-network-bandwidth-monitor-traffic" target="_blank" rel="noreferrer noopener">A network monitoring utility</a> that inspects network traffic using intrusion detection. It is configured with over 700 event correlation rules, allowing it to automatically detect suspicious activities and implement remediation actions.</li>
<li><a href="https://phoenixnap.com/kb/fail2ban" target="_blank" rel="noreferrer noopener"><strong>Fail2Ban</strong></a>. A lightweight host-based intrusion detection software system designed to protect against brute force attacks. It monitors server logs and detects any suspicious activity, providing an extra layer of security for the server.</li>
</ul>
<h3 id="ftoc-heading-22" class="wp-block-heading ftwp-heading">20. Manage Linux File Permissions</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Managing <a href="https://phoenixnap.com/kb/linux-file-permissions" target="_blank" rel="noreferrer noopener">file permissions in Linux</a> protects sensitive files and directories from unauthorized access. Limiting access to files and directories reduces the risk of data breaches, theft of sensitive information, and unauthorized modifications to the system.</p>
<p>Several tools manage file permissions in Linux, including the <strong><code>chmod</code></strong> command, which allows sysadmins to change <a href="https://phoenixnap.com/kb/chmod-recursive" target="_blank" rel="noreferrer noopener">file permission recursively</a> and configure multiple files and subdirectories using a single command.</p>
<p>The <a href="https://phoenixnap.com/kb/linux-ls-commands" target="_blank" rel="noreferrer noopener">ls command</a> lists file permissions, and the <a href="https://phoenixnap.com/kb/linux-chown-command-with-examples" target="_blank" rel="noreferrer noopener">chown command</a> changes file ownership.</p>
<h3 id="ftoc-heading-23" class="wp-block-heading ftwp-heading">21. Use Access Control Lists (ACLs)</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Compared to traditional file permissions systems, <a href="https://phoenixnap.com/kb/acl-network" target="_blank" rel="noreferrer noopener">ACLs</a> are a more advanced way of controlling access to files and directories in Linux systems. The traditional system only allows three basic permissions (read, write, and execute) to be assigned to three permission classes (file owner, group owner, and others). However, ACLs allow for more fine-grained control.</p>
<p>Sysadmins use ACLs to define different permissions for specific users and groups on a per-file or per-directory basis. This allows for implementing more complex access control policies, like granting certain users read-only access to sensitive files or allowing certain groups write access to specific <a href="https://phoenixnap.com/glossary/what-is-a-directory" target="_blank" rel="noreferrer noopener">directories</a>.</p>
<h3 id="ftoc-heading-24" class="wp-block-heading ftwp-heading">22. Monitor Suspicious Server Logs&nbsp;</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>To improve Linux system security and <a href="https://phoenixnap.com/kb/prevent-brute-force-attacks" target="_blank" rel="noreferrer noopener">prevent brute force attacks</a>, analyze server logs with <a href="https://phoenixnap.com/glossary/log-management" target="_blank" rel="noreferrer noopener">log management</a> applications such as Logwatch or logcheck.&nbsp;</p>
<p>Both tools allow sysadmins to regularly monitor the logs for unusual activity and provide a summarized report.</p>
<p>Logwatch parses log files from services and applications running on the system and generates a daily report of error messages, security alerts, and system warnings. The command has numerous options and settings. For instance, to see a detailed report in the terminal, run:</p>
<pre class="wp-block-code"><code>sudo logwatch --detail high</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="422" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%20422'%3E%3C/svg%3E" alt="sudo logwatch --detail high terminal output" class="wp-image-159184" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output-300x158.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output-768x405.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output.png" /><noscript><img decoding="async" width="800" height="422" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output.png" alt="sudo logwatch --detail high terminal output" class="wp-image-159184" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output-300x158.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-logwatch-detail-high-terminal-output-768x405.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>Logcheck focuses on log files related to system security, such as authentication logs and firewall logs. Logcheck summarizes the events in these logs and sends a daily report via email to the sysadmin.</p>
<p>The <strong><code>logcheck</code></strong> command also has a lot of options. To output everything, run:</p>
<pre class="wp-block-code"><code>sudo -u logcheck logcheck -o -t</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="219" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%20219'%3E%3C/svg%3E" alt="sudo -u logcheck logcheck -o -t terminal output" class="wp-image-159185" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output-300x82.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output-768x210.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output.png" /><noscript><img decoding="async" width="800" height="219" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output.png" alt="sudo -u logcheck logcheck -o -t terminal output" class="wp-image-159185" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output-300x82.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-u-logcheck-logcheck-o-t-terminal-output-768x210.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<div class="notice-note">
<div class="note-icon-wrapper"><i class="fa fa-lightbulb"></i></div>
<div class="notice-text"><p><strong>Note:</strong> Neither Logwatch nor logcheck come preinstalled in Linux. Use the <strong><code>apt</code></strong> command to install them.</p>
</div>
</div>
<h3 id="ftoc-heading-25" class="wp-block-heading ftwp-heading">23. Restrict World-Writable Files</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>World-writable files, directories, and devices on a Linux server pose a significant security risk. Any user is able to modify these files, potentially leading to unauthorized changes, data tampering, or malicious actions.</p>
<p>Locate and remove these files following these steps:</p>
<p>1. Identify world-writable files or directories with the <a href="https://phoenixnap.com/kb/guide-linux-find-command" target="_blank" rel="noreferrer noopener">find command</a>:</p>
<pre class="wp-block-code"><code>sudo find /. -xdev -type d \( -perm -0002 -a ! -perm -1000 \) -print</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="42" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%2042'%3E%3C/svg%3E" alt="Identify world-writable files or directories with the find command" class="wp-image-159187" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output-300x16.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output-768x40.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output.png" /><noscript><img decoding="async" width="800" height="42" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output.png" alt="Identify world-writable files or directories with the find command" class="wp-image-159187" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output-300x16.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-home-xdev-type-d-perm-0002-a-perm-1000-print-terminal-output-768x40.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>2. In this case, the output prints one directory. If there are more, Investigate each one.</p>
<p>3. Use <strong><code>chmod</code></strong> to update the permissions or remove unnecessary files or directories. For instance, set file permissions to 600 to ensure the owner has full read and write access to the directory, while no other user has access.</p>
<pre class="wp-block-code"><code>sudo chmod 600 &#091;directory]</code></pre>
<p>The command has no output.</p>
<h3 id="ftoc-heading-26" class="wp-block-heading ftwp-heading">24. Configure Logging and Auditing Processes</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Logging and auditing provide valuable information about the system and network events, aiding administrators in detecting and addressing malicious threats. To increase security:</p>
<ol class="wp-block-list" style="list-style-type:1">
<li>Centralize log data from different sources to a single <a href="https://phoenixnap.com/glossary/what-is-a-repository" target="_blank" rel="noreferrer noopener">repository</a> making it easier to search, analyze, and store logs.</li>
<li>Rotate logs regularly to keep only a limited number of logs and reduce the storage space.</li>
<li>Enforce a retention policy to save space and prevent log data from becoming too large to handle.</li>
<li>Use SELinux or another auditing framework to track and record specific events, such as access to sensitive files, user logins, and system changes.</li>
<li>Implement real-time <a href="https://phoenixnap.com/kb/syslog-server" target="_blank" rel="noreferrer noopener">syslog server</a> monitoring tools, such as log analyzers or security information and <a href="https://phoenixnap.com/blog/siem-security-information-event-management-tools" target="_blank" rel="noreferrer noopener">event management (SIEM) systems</a>, to get alerts for potential security incidents.</li>
<li>Restrict privileges to log files, allowing access to only necessary users to prevent unauthorized modification or tampering of log data.</li>
<li>Encrypt log data before any network transmission s to maintain data confidentiality.&nbsp;</li>
</ol>
<h3 id="ftoc-heading-27" class="wp-block-heading ftwp-heading">25. Disable Unwanted SUID and SGID Binaries</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>SUID and SGID are file permissions allowing a file to be executed with owner or group privileges. Still, they pose security risks if not adequately secured. The main risk is a privilege escalation attack. Privilege escalation attacks occur when an attacker gains access to a system with limited privileges and then uses a vulnerability to elevate their privileges to the binary owner or group level.</p>
<p>To disable these files:</p>
<p>1. Identify SUID and SGID files with the find command.</p>
<pre class="wp-block-code"><code>sudo find / -perm +u+s -type f</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="109" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%20109'%3E%3C/svg%3E" alt="sudo find / -perm +u+s -type f terminal output" class="wp-image-159193" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output-300x41.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output-768x105.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output.png" /><noscript><img decoding="async" width="800" height="109" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output.png" alt="sudo find / -perm +u+s -type f terminal output" class="wp-image-159193" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output-300x41.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-u-s-type-f-terminal-output-768x105.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<p>2. To locate all SGID files, execute:</p>
<pre class="wp-block-code"><code>sudo find / -perm +g+s -type f</code></pre>
<div class="wp-block-image">
<figure class="aligncenter size-full"><img decoding="async" width="800" height="90" src="data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20800%2090'%3E%3C/svg%3E" alt="sudo find / -perm +g+s -type f terminal output" class="wp-image-159194" data-lazy-srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output-300x34.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output-768x86.png 768w" data-lazy-sizes="(max-width: 800px) 100vw, 800px" data-lazy-src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output.png" /><noscript><img decoding="async" width="800" height="90" src="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output.png" alt="sudo find / -perm +g+s -type f terminal output" class="wp-image-159194" srcset="https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output.png 800w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output-300x34.png 300w, https://phoenixnap.com/kb/wp-content/uploads/2023/02/sudo-find-perm-g-s-type-f-terminal-output-768x86.png 768w" sizes="(max-width: 800px) 100vw, 800px" /></noscript></figure></div>
<div class="notice-note">
<div class="note-icon-wrapper"><i class="fa fa-lightbulb"></i></div>
<div class="notice-text"><p><strong>Note:</strong> An alternative way to locate all SUID and SGID files is the <strong><code>find / -perm +6000 -type f</code></strong> command. However, the command prints an error on some systems that do not support the <strong><code>+6000</code></strong> option, in which case the command returns an error message.</p>
</div>
</div>
<p>3. Evaluate the output and decide what to keep or discard.</p>
<p>4. Use the&nbsp;chmod command to change the permissions or remove unnecessary files.</p>
<p>5. Regularly monitor the SUID and SGID files to ensure the permissions have not changed.</p>
<h3 id="ftoc-heading-28" class="wp-block-heading ftwp-heading">26. Encrypt Data Communication</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Linux provides various methods for encrypting data communication:</p>
<ol class="wp-block-list">
<li><a href="https://phoenixnap.com/kb/what-is-sftp" target="_blank" rel="noreferrer noopener">Secure File Transfer Protocol (SFTP)</a> transfers files between systems securely. With SFTP, users choose the level of authentication for transferring files. To use SFTP, users must install an SFTP server on one system and an SFTP client on the other. However, SFTP only protects files during transfer, and the data is no longer encrypted after reaching the server.</li>
<li><a href="https://phoenixnap.com/kb/tls-vs-ssl" target="_blank" rel="noreferrer noopener">Secure Socket Layer (SSL)</a> guards information passed between two systems via the internet and is used in server-client and server-server communication. SSL encrypts the transmitted data, making it difficult for an attacker to intercept or alter the information. To use SSL, users must obtain an SSL certificate and install it on both the client and the server systems.</li>
<li>Apache SSL (Secure Server Layer) is a component for Apache web server that provides secure communication between a client and a server. It implements the SSL (Secure Socket Layer) or TLS (Transport Layer Security) protocols, which provide encryption and authentication for secure communication.</li>
<li><a href="https://phoenixnap.com/kb/tls-vs-ssl" target="_blank" rel="noreferrer noopener">SSL/TLS:</a>&nbsp;SSL (Secure Sockets Layer) and its successor, TLS (Transport Layer Security), are widely used protocols for encrypting data communication over the internet. TLS (Transport Layer Security) is more secure and provides better encryption.&nbsp;</li>
</ol>
<h3 id="ftoc-heading-29" class="wp-block-heading ftwp-heading">27. Use Encryption Tools to Protect Sensitive Data</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Encryption allows users to protect confidential information from unauthorized access, even during a data breach. Encrypting files before transmitting them with SFTP, for instance, ensures additional protection. The following tools allow users to encrypt files before transmitting:</p>
<ol class="wp-block-list" style="list-style-type:1">
<li><strong>LUKS (Linux Unified Key Setup)</strong>. The most widely used method for encrypting partitions on Linux systems. LUKS allows users to encrypt the entire partition file system, protecting all the data.</li>
<li><strong>Node.js</strong>. An open-source&nbsp;<a href="https://phoenixnap.com/glossary/what-is-javascript" target="_blank" rel="noreferrer noopener">JavaScript (JS)</a> runtime environment that works as an encryption tool. Node.js has an extensive cryptography library, such as crypto, node-forge, or sodium-native, which provide functions for encrypting and decrypting data, generating encryption keys, and managing cryptographic operations.</li>
<li><strong>CryFS</strong>. A cryptographic file system that encrypts users' files and stores the encrypted data on cloud storage services like Dropbox or Google Drive. CryFS works by transparently encrypting a user's files before they are uploaded to the cloud and then decrypting them when accessed. The files remain encrypted and protected from unauthorized access, even when stored in the cloud.</li>
<li><strong>SecureDoc for Linux</strong>. A security solution for Linux endpoints, providing enterprise-class full disk encryption. It separates encryption into two components, encryption, and <a href="https://phoenixnap.com/blog/encryption-key-management-best-practices" target="_blank" rel="noreferrer noopener">key management</a>. SecureDoc for Linux adopts a&nbsp;<a href="https://phoenixnap.com/blog/zero-trust-security" target="_blank" rel="noreferrer noopener">Zero Trust</a>&nbsp;approach to security but allows live disk conversion during encryption.</li>
</ol>
<h3 id="ftoc-heading-30" class="wp-block-heading ftwp-heading">28. Use a VPN</h3>
<p class="h4">(Basic security mechanism)</p>
<p><a href="https://phoenixnap.com/glossary/vpn-definition" target="_blank" rel="noreferrer noopener">Virtual Private Networks</a> (VPNs) are crucial in ensuring communication security over public networks on Linux systems. A VPN uses encryption and authentication to protect sensitive information from interception or tampering during transmission.</p>
<p>Unlike open networks, private and virtual private networks limit access to only authorized users. Private networks use a unique <a href="https://phoenixnap.com/glossary/what-is-an-ip-address" target="_blank" rel="noreferrer noopener">IP address</a> to set up isolated communication channels between servers within the same IP range, allowing data exchange without exposure to a public space.</p>
<p>With a VPN, data is encrypted at the source, transmitted over a public network, and decrypted at the destination. This helps to secure communication between the two points, even over an insecure network. VPNs are useful when connecting to a remote server as if directly connected to a private network.</p>
<p>In Linux, a popular VPN is OpenVPN. This open-source VPN solution provides robust security and high performance. It supports various encryption protocols, including SSL/TLS and PPTP. OpenVPN is known for its ease of use, flexible configuration options, and compatibility with most Linux distributions.</p>
<h3 id="ftoc-heading-31" class="wp-block-heading ftwp-heading">29. Harden the Linux Kernel</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>The Linux kernel plays a crucial role in the overall security of a system. The /etc/sysctl.conf file&nbsp;<a href="https://www.cyberciti.biz/faq/linux-kernel-etcsysctl-conf-security-hardening/" target="_blank" rel="noreferrer noopener nofollow">configures kernel parameters</a>&nbsp;at runtime and hardens the Linux kernel. Hardening the Linux kernel prevents attacks and limits the damage from potential attacks.</p>
<p>To harden the Linux kernel, configure settings in the <em>/etc/sysctl.conf</em> file:</p>
<ul class="wp-block-list">
<li>Disable IP forwarding to reduce the risk of the system being used as a pivot point in an attack.</li>
<li>Enable source address verification to prevent IP spoofing attacks by verifying that incoming packets have a valid source IP address.</li>
<li>Disable ICMP redirect acceptance to stop attackers from altering the system's routing tables through ICMP redirect messages.</li>
<li>Disable IP source routing to prevent IP packet routing manipulation.</li>
<li>Increase the connection tracking table size to limit the memory used by the connection tracking system, reducing the risk of a denial-of-service attack.</li>
</ul>
<h3 id="ftoc-heading-32" class="wp-block-heading ftwp-heading">30. Separate Disk Partitions for Improved Linux Security</h3>
<p class="h4">(Intermediate security mechanism)</p>
<p>Separating disk partitions in a Linux system improves its security by isolating sensitive data and system files from each other. This allows for implementing different security measures for each partition, making it more difficult for an attacker to compromise the entire system.</p>
<p>Critical filesystems to be mounted on separate partitions include:&nbsp;</p>
<ul class="wp-block-list">
<li><em>/usr</em></li>
<li><em>/home</em></li>
<li><em>/tmp&nbsp;</em></li>
<li>/var </li>
<li><em>/var/tmp</em></li>
</ul>
<p><a href="https://phoenixnap.com/kb/linux-create-partition" target="_blank" rel="noreferrer noopener">Creating separate partitions</a> for Apache and FTP server roots is also recommended. Mounting the partitions with different file permissions and mount options, such as the noexec option, prevents the execution of programs in a partition. This helps prevent attackers from exploiting vulnerabilities in the software installed on the system and limits the potential damage.</p>
<p>Having separate partitions also makes it easier to back up, restore, upgrade, or replace individual parts without affecting the rest of the system. In the event of a security breach, this allows for restoring the compromised partition without affecting the entire system.</p>
<h3 id="ftoc-heading-33" class="wp-block-heading ftwp-heading">31. Enable Disk Quotas</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Enabling disk quotas in Linux prevents the system from running out of disk space. Limited disk space makes it easier for attackers to exploit vulnerabilities or cause a denial-of-service (DoS) attack by filling up the disk. Setting disk quotas limits the disk space that each user or group takes, preventing attackers from using up all available disk space.</p>
<h3 id="ftoc-heading-34" class="wp-block-heading ftwp-heading">32. Manage "Noowner" Files</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Managing "noowner" files is essential for Linux security because files not owned by a valid user or group are easily manipulated by an attacker and used to hide malicious files or activities.</p>
<p>To manage "noowner" files:</p>
<ol class="wp-block-list">
<li>Use the <strong><code>find</code></strong> command to locate files that do not belong to a valid user or group.</li>
<li>Investigate each reported file to determine its purpose and usage.</li>
<li>Assign the file to an appropriate user and group, or remove it if unnecessary.</li>
</ol>
<h3 id="ftoc-heading-35" class="wp-block-heading ftwp-heading">33. Backup Linux System</h3>
<p>(Intermediate security mechanism)</p>
<p>Backing up a Linux system is crucial for security, allowing users to recover from a system compromise or data loss. A data backup copy helps restore the system to a secure state in case of a security breach, hardware failure, or another disaster.</p>
<p>To back up a Linux system, use traditional UNIX backup programs such as <strong>dump and restore</strong> or a cloud-based service such as AWS. Ensure the backups' security by encrypting and storing them in a secure location, such as an external storage device or a <a href="https://phoenixnap.com/glossary/nas-network-attached-storage" target="_blank" rel="noreferrer noopener">NAS server</a>.</p>
<p>Most Linux distributions have built-in backup tools. To start with backup on Linux, search for backup tools in the system menu. </p>
<h3 id="ftoc-heading-36" class="wp-block-heading ftwp-heading">34. Install an Antivirus Program</h3>
<p class="h4">(Basic security mechanism)</p>
<p>An antivirus program protects the system from viruses, trojans, and spyware. Antivirus scans the system, detects potential threats, and prevents damage.</p>
<p>Several antivirus options are available for Linux systems, including free and paid options. Popular free antivirus programs are ClamAV and AVG, and paid options include McAfee and Symantec. Also, regularly update and run the antivirus program to ensure that it provides the most up-to-date protection.<a href="https://www.tecmint.com/best-antivirus-programs-for-linux/" target="_blank" rel="noreferrer noopener"></a></p>
<h3 id="ftoc-heading-37" class="wp-block-heading ftwp-heading">35. Prevent Ransomware Attacks</h3>
<p class="h4">(Advanced security mechanism)</p>
<p><a href="https://phoenixnap.com/blog/what-is-ransomware" target="_blank" rel="noreferrer noopener">Ransomware</a> is malware that encrypts user files and demands payment for the decryption key. If a Linux system is infected with ransomware, the loss of important data, files, and sensitive information is possible.</p>
<p><a href="https://phoenixnap.com/blog/how-to-prevent-ransomware" target="_blank" rel="noreferrer noopener">Preventing ransomware</a>&nbsp;attacks requires a combination of security measures, such as:</p>
<ul class="wp-block-list">
<li>Setting up a firewall.</li>
<li>Setting up ad blockers.</li>
<li>Implementing strong passwords.</li>
<li>Keeping software up-to-date.</li>
<li>Using reliable antivirus software.</li>
<li>Running regular security tests.</li>
<li>Whitelisting applications.</li>
<li>Setting up a&nbsp;<a href="https://phoenixnap.com/glossary/what-is-sandbox" target="_blank" rel="noreferrer noopener">sandbox</a>.</li>
<li>Improving&nbsp;<a href="https://phoenixnap.com/blog/email-security-best-practices" target="_blank" rel="noreferrer noopener">email security.</a></li>
<li>Employing the&nbsp;zero-thrust policy.</li>
</ul>
<h3 id="ftoc-heading-38" class="wp-block-heading ftwp-heading">36. Regularly Perform Vulnerability Assessments</h3>
<p class="h4">(Advanced security mechanism)</p>
<p>Performing regular <a href="https://phoenixnap.com/blog/vulnerability-assessment" target="_blank" rel="noreferrer noopener">vulnerability assessments</a> in Linux helps identify any potential security risks and weaknesses in the system.</p>
<p>The process enables sysadmins to proactively mitigate the risks and improve the system's overall security.</p>
<p>Several tools and techniques perform vulnerability assessments in Linux, including:</p>
<ul class="wp-block-list">
<li>Network scanning tools scan the network for open ports and services and identify potential vulnerabilities in the system.</li>
<li><a href="https://phoenixnap.com/blog/penetration-testing" target="_blank" rel="noreferrer noopener">Penetration testing</a> tools simulate an attack on the system to identify weaknesses an attacker could exploit.</li>
<li>Code review tools analyze the source code of applications and system components, looking for potential security vulnerabilities.</li>
<li>Vulnerability databases provide information about known vulnerabilities in specific software and operating systems, including patches and workarounds.</li>
</ul>
<h3 id="ftoc-heading-39" class="wp-block-heading ftwp-heading">37. Invest in Disaster Recovery</h3>
<p class="h4">(Advanced security mechanism)</p>
<p>A disaster recovery plan outlines the steps to be taken in case of a system failure, data loss, or security breach. A well-designed disaster recovery minimizes a disaster's impact, reduces downtime, and increases the Linux system's security.</p>
<p>To create a <a href="https://phoenixnap.com/blog/disaster-recovery-plan-checklist" target="_blank" rel="noreferrer noopener">disaster recovery plan</a>, follow this checklist:</p>
<ul class="wp-block-list">
<li>Identify critical systems and data that must be recovered in a disaster.</li>
<li>Choose a backup and recovery solution that meets your needs and budget.</li>
<li>Test the backup and recovery plan regularly to ensure it works as expected.</li>
<li>Train all personnel on the disaster recovery plan and procedures.</li>
<li>Document the plan and keep it up-to-date.</li>
</ul>
<h3 id="ftoc-heading-40" class="wp-block-heading ftwp-heading">38. Upgrade Security Incident Response Plan (CSIRP)</h3>
<p class="h4">(Advanced security mechanism)</p>
<p>An effective <a href="https:/phoenixnap.com/blog/cyber-security-incident-response-plan" target="_blank" rel="noreferrer noopener">security incident response plan (CSIRP)</a> is critical to a robust security program. It provides a clear and organized plan for responding to various security incidents, such as data breaches, cyber-attacks, and other security-related events. It is essential to periodically update the CSIRP to keep up with new security threats and be able to detect and respond to security incidents to minimize damage and data loss.</p>
<p>When upgrading the CRISP, make sure to:</p>
<ul class="wp-block-list">
<li>Review the current plan and identify areas for improvement.</li>
<li>Evaluate contemporary security threats and assess the impact.</li>
<li>Revise incident response procedures to align with current security best practices.</li>
<li>Update incident categorization and prioritization criteria.</li>
<li>Review and update communication plans for internal and external stakeholders.</li>
<li>Test and refine the updated CSIRP through simulations and tabletop exercises.</li>
</ul>
<h3 id="ftoc-heading-41" class="wp-block-heading ftwp-heading">39. Use a Security-Focused Web Browser</h3>
<p class="h4">(Basic security mechanism)</p>
<p>Using a security-focused web browser and configuring it to block malicious sites on Linux protects against malware attacks by blocking access to known malicious websites and warning users about potentially dangerous sites.</p>
<p>Certain security-focused web browsers like Tor encrypt internet connections to protect against eavesdropping and tampering. The process creates a secure internet connection and reduces the risk of hacking or other cyber attacks.</p>
<p>By blocking malicious sites, security-focused web browsers reduce the risk of data breaches when users inadvertently access sites that contain malware or steal personal information.</p>
<h3 id="ftoc-heading-42" class="wp-block-heading ftwp-heading">40. Ensure Linux Server Physical Security</h3>
<p>(Intermediate/Advanced security mechanism)</p>
<p>To ensure the physical security of Linux servers, organizations must implement several measures to prevent unauthorized access. Here are the key steps to consider:</p>
<ul class="wp-block-list">
<li><strong>Secure physical console access</strong>. Configure the BIOS to disable booting from external devices such as CDs, DVDs, or <a href="https://phoenixnap.com/glossary/what-is-a-usb-port" target="_blank" rel="noreferrer noopener">USB</a> pens. Set BIOS and GRUB boot loader passwords to protect these settings.</li>
<li><strong>Implement multi-layered security</strong>. Use physical locks on server room doors, install security cameras to monitor the area, implement access control systems to restrict access to unauthorized personnel and regularly check the servers for signs of tampering or theft.</li>
<li>I<strong>mplement environmental controls</strong>. Consider installing air conditioning to prevent server damage due to heat or other environmental factors.</li>
<li><strong>Perform regular security audits</strong>. Ensure that the physical security measures are up to date and effective in preventing unauthorized server access.</li>
<li><strong>Lock servers in IDCs</strong>. Make sure to lock all production servers in IDCs (Internet Data Centers) and perform security checks on all personnel accessing the server.</li>
</ul>
