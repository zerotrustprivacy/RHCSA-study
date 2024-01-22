# RHCSA-study
Study notes for the exam.

<h2>Topics covered:</h2>
<p>
  <ul>
    <li>Managing physical storage</li>
  <li>Install and configure software components and services</li>
  <li>Establish network connections</li>
  <li>Monitor and manage running processes</li>
  <li>Manage and secure files and file systems</li>
  <li>Administer users and groups</li>
  <li>Review the system log files and journal for issues</li>
  <li>Remotely manage systems with SSH and the Web Console</li>
    <li>Install Red Hat Enterprise Linux using scalable methods</li>
    <li>Access security files, file systems, and networks</li>
    <li>Execute shell scripting and automation techniques</li>
    <li>Manage storage devices, logical volumes, and file systems</li>
    <li>Manage security and system access</li>
    <li>Control the boot process and system services</li>
  </ul>
</p>
<h2>Resources: </h2>
<p>
  <ul>
    <li>Sander van Vugt RHCSA 9 course</li>
    <li>RHCSA 9 Textbook </li>
    Both can be found on the <a href= "https://learning.oreilly.com"> O'Reilly learning platform.</a>
    <li>Red Hat System Administration I (RH124)</li>
    <li>Red Hat System Administration II (RH134)</li>
  </ul></p>
<h3>Using vim</h3> 
<p>Create file by using the command "vim <file name> "</p>
<p>When in Vim use "i" to get to INSERT mode and begin typing.</p>
 <p>o = new line</p>
    <p>ctrl + c = command mode</p>
  <p>v = visual mode</p>
  <p>dd = delete current line</p>
  <p>gg = top of the document</p>
  <p>^ = start of the line</p>
  <p>:wq = save and exit</p>
<h3>File System</h3>
<p>Files on a Linux system are organized into a single file-system hierarchy</p>
<p>mkdir (make directory), rmdir (remove directory), cp (copy), and mv (move) are commands to manage files.</p>
<p>Hard links</p>
<p>Soft links</p>

<h2>Configuration Files</h2>
<h3>Important File Locations</h3>
<ul>
  <li>Source File: ~/.bashrc</li>
  <li>Password Config: /etc/login.defs/user</li>
  <li>Sudo Config: /etc/sudoers.d/user</li>
  <li>Password info: /etc/passwd</li>
  <li>Group info: /etc/group</li>
  <li>SSH Config & Password Auth: /etc/ssh/sshd_config</li>
  
</ul>

<h3>Configure Users and Permissions</h3>
<ul>
  <li>To change a user's password on log in: chage -d 0 user</li>
  <li>Change expiration date for password: chage -M 30 user</li>
  <li>Check user password expiration: chage -l user</li>
  <li>Add user: useradd</li>
  <li>Modify user: usermod</li>
  <li>Add group: groupadd</li>
  <li>Modify group: groupmod</li>
  <li>Change permission: chmod</li>
  <li>Change ownership: chown</li>
</ul>

<h3>File Access</h3>
<ul>
  <li>Read # Write # Execute</li>
  <li>Owning User # Owning Group # Other</li>
</ul>

<h3>Creating Partitions</h3>
<p><img src="Screenshot 2023-08-27 213830.png"></p>
<h3> Make File System</h3>
<p><img src= "mkfs.png"></p>
<h3> Unmount a mounted filesystem </h3>
<p><img src ="unmount.png"></p> 
<h3> Create a Swap</h3>
<p><img src ="swap.png"></p>

<h3> Resize Logical Volumes and Volume Groups</h3>
<p><img src="lvmgroups.png"</p>
  
<h3>Schedule Jobs </h3> 
<p>Schedule jobs to run  on a repeating schedule with a user's crontab file. </p>
<p> "man at" shows how to execute schedule jobs. These are one time jobs. For example: "at now +3min" runs a job 3 min from now.</p>
<p>"atq" lists scheduled jobs. "atrm" removes the job.</p>
<p>Recurring Jobs: The crond daemon reads multiple config files. Each user has a personal file that they edit with "crontab -e". The fields in the crontab file are in the following order:
<p><ul>
  <li>Minutes</li>
  <li>Hours</li>
  <li>Day of Month</li>
  <li>Month</li>
  <li>Day of Week</li>
  <li>Command</li>
</ul></p></p>

<h3>Manage Temporary Files</h3>
<p>Red Hat includes the systemd-tmpfiles tool - provides a method to manage temporary directories and files. The systemd-tmpfiles-setup service runs the systemd-tmpfiles command.</p>
<p>systemd-tmpfiles-clean service configuration files exist in three places:
/etc/tmpfiles.d/*.conf
/run/tmpfiles.d/*.conf
/usr/lib/tmpfiles.d/*.conf</p>
<p> In the config file, specify what to do... echo "d/etc/</p>


<h3>Analyze and Store Logs</h3>
<p>The rsyslog service is used to determine for handle log messages. </p>
<p>The logrotate command rotates log files to prevent them from taking too much space in the /var/log directory. When a log is rotated, it is renamed with an extension.</p>
<p>journalctl retrieves all log messages. </p>
<p>-r shows the most recent logs</p>
<p>-p shows the priority level</p>
<p>-b shows the current system boot</p>
<p>The system has its own journal located at system.journal. Indiviual users have their own journals pertaining to their own transacions inside of file called user-userid </p>
<p>Updating Time Zones: Use the command tzselect to view the appropriate time zone. Then use "timedatectl set-timezone" command to set the time zone.</p>

<h3>Manage Compressed tar Archives</h3>
<p>An archive is a file that contains multiple files. "tar" is the command to create manage and extract archives. </p>
<p>Command: dnf list - lists installed and available packages</p>
<p> Use dnf install -y software to install </p>

<h3> Manage Process and jobs</h3>
<p>command & starts a job in the background.</p> 
<p>Jobs- to view all running jobs </p>
<p> A runnable process can be stopped with CTRL+z </p>
<p> The ps command shows current running processes </p>
<p> The "top" command shows the highest running processes </p>
<p> ps -fU user ... for a user's processes </p>
<p> Use "Kill" or "killall dd" to kill processes. To kill a ZOMBIE process </p>
<p> Process Priorities 
<p>
  <ul> 
  <li> Nice and Renice can be used to change priorities of non-realtime processes </li>
  <li> Nice ranges from -20 to 19. Positive values means lower priority.</li>
  <li> Use " Cat /proc/sys/vm/swappiness" to see the value then use "echo _ _ /proc/sys/vm/swappiness" to change it. To make it persistent " cat >> swappiness.conf << EOF" </li>
  <li> loginctl list-user: shows users currently logged in.  loginctl terminate-user: to stop a user session </li> 
  </ul> 
</p>
</p>
<h2>Systemd</h2>
<p>
<ul>
  <li> systemctl edit unit.service : to edit unit files </li>
  <li>systemctl list-dependencies for a complete overview of dependencies</li>
  <li> Mask services : use Systemctl Stop (service) then systemctl mask (service) </li>
  <li>Example: systemctl Status httpd [disabled] ...systemctl enable httpd...</li>
</ul>
</p>

<h2> Configure Logging</h2>
<p>
<ul>
  <li>Preserve the systemd journal: check settings in /etc/systemd/journal.conf. The setting "STORAGE=AUTO" ensures that persistent storage is happening automatically. Make directory /var/log/journal. Restart service: systemctl restart systemd-journald.</li>
  <li>Logrotate is started by a systemd timer to prevent disks from filling up. "systemctl cat logrotate.conf" to view the settings for logrotate.</li>
  <li>Make sure that the /var/log/journal exists</li>
</ul>
</p>
<h2> SELinux </h2>
<p>Security Enhanced Linux (SELinux) provides an additional layer of system security. It should always be enabled. There are two modes: permissive or enforcing. If permissive is enabled, no access is blocked. If enforcing is enabled, all restrictions are applied and SELinux is fully operational. </p> 
<p> 
<ul> 
  <li> getenforce shows the current SELinux state. </li> 
  <li> setenforce toggles between enforcing and permissive and sets them temporarily.</li>
  <p><img src="selinux.png"></p>
  <li>To change the default mode persistently, you need to write it to /etc/sysconfig/selinux, or change GRUB kernel boot arguments.</li>
  
  Context management means applying contexts to files.
  <li> File context labels are applied to every Object: user, rule, type</li>
<li>semanage-fcontext : sets the file context label ( - a to set a new context label) ( -m to modify an existing context label ) </li >
<li> When files are copied, they inherit the context type </li>
</ul> 
</p>
<h2>Example: Setting Context Labels for Apache Document</h2>
<p>Install curl. <p><img src="selinux2.png"></p>
Make a directory called "web" and create an index.html file within the directory.<p><img src="selinux3.png"></p> 
<p>Then edit the httpd conf file by adding "/web" to the DocumentRoot parameter. Be sure that the following is also added to the file:</p>
<p> <img src="selinux4.png"></p> 

Enable the httpd service and then restart. Curl http://localhost to confirm that SELinux has not been set to permissive and you'll see that this is not your webpage. Use "setenforce 0" and repeat the previous step.</p>
<p>Type semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?" to apply to the directory "/web"</p>
<p>Type  restorecon -R -v /web. The restorecon command restores the default SELinux contexts so that changes made by the "semange fcontext" command are persistent.</p>
<h2>SELinux Rules and Policies</h2>
<p>
  <ul>
    <li>SELinux Booleans change the behavior of a rule. To change a Boolean, you can use "setsebool". To list all Booleans - "getsebool -a" or "semanage boolean -l" </li>
    <li>To view logging, you need to access the audit log - "/var/log/audit/audit.log"... SELinux type is AVC so "grep AVC /var/log/audit/audit.log" will show the SELinux logs.</li>
    <li>To understand the logs further, you can use "sealert -l UUID" for more information.</li>
  </ul>
</p>

<h2>Firewalld</h2>
<p>Firewalld is a service that can configure firewall rules by using different interfaces. Administrators can manage rules but rules can also be added or removed without any direct action required of the system administrator.</p>
<p>A zone is a collection of rules applied to incoming packets matching a specific source address or network interface.</p>
<p>A Firewalld service - what should be accepted as incoming and outgoing traffic in the firewall. It typically includes ports to be opened, & kernel modules</p>
<p>firewall-cmd -- is the cmd line tool used for firewall configuration.</p>
<h2>Example: Configuring Automount</h2>
<p>This example will show how to mount NFS server and NFS data automatically</p>
<p>
  <ul>
    <li>dnf install -y autofs</li>
    <li>cd /etc/ </li>
    <li>vim auto.master (add /nfsdata    /etc/auto.nfsdata at the top of the file)</li>
    <li>vim auto.misc </li>
    <li>vim auto.nfsdata (files    -rw    nfsserver:/nfsdata)</li>
    <li>systemctl enable --now autofs</li>
    <li>ls /</li>
    <li>cd /nfsdata</li>
    <li>ls -al</li>
    <li>cd files</li>
    <li>mount | tail -3 (this will show the automount that was created)</li>
  </ul>
</p>
<h3>Example: Automount on Home Directories</h3>
<p>
  <ul>
    <li>showmount -e nfsserver: to check what is currently mounted</li>
    <li>vim /etc/auto.master (/homes    /etc/auto.homes)</li>
    <li>vim /etc/auto.homers (*    -rw    nfsserver:/home/ldap/&)</li>
    <li>systemctl restart autofs</li>
    <li>cd /homes</li>
    <li>ls -a</li>
  </ul>
</p>
<h2>Containers</h2>
<h3>A container has all that is needed to run an application. They are started from container images. Images are provided in image registries.</h3>
<p>Features:</p>
<p>
  <ul>
    <li>Control groups - set limits to the amount of resources that can be used</li>
    <li>Namespaces - provide isolation so that containers only have access to their data and configuration</li>
</ul></p>
<p>Containers need a user ID to be started. Root containers are started by the root users. Rootless containers are started by non-root users.</p>
<p>Normally each container runs one application.</p>
<p>Podman manages containers and container images</p>
<p>Container images are used to package container applications with all of their dependencies.</p>
<p>podman login registry.redhat.io</p>
<p>Configure Registry Access</p>
<p>
  <ul>
    <li>Registry access is configured in /etc/containers/registries.conf</li>
    <li>Container file - text file with instructions to build a custom container image</li>
    <li>dnf install container-tools (view all supporting tools to work with containers)</li>
  </ul>
</p>
<p>git clone repository</p>
<p>Move to the directory with the repo files: cd /rhcsa ... and list the files</p>
<p>cat Containerfile</p>
<p>podman images then podman info to see all of the registries</p>
<p>podman login registry.access.redhat.com</p>

