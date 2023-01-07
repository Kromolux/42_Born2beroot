# 42_Born2beroot

## Description
This project aims to introduce you to the wonderful world of virtualization.

## Skills
* Network & system administration
* Rigor

# Born2beRoot

Summary: This document is a System Administration related exercise.

Version: 1

## Introduction
This project aims to introduce you to the wonderful world of virtualization. You will create your first machine in VirtualBox (or UTM if you can’t use VirtualBox) under specific instructions. Then, at the end of this project, you will be able to set up your own operating system while implementing strict rules.

## General guidelines
* The use of VirtualBox (or UTM if you can’t use VirtualBox) is mandatory.
* You only have to turn in a signature.txt file at the root of your repository. You must paste in it the signature of your machine’s virtual disk. Go to Submission and peer-evaluation for more information.

## Mandatory part
This project consists of having you set up your first server by following specific rules.

> Since it is a matter of setting up a server, you will install the minimum of services. For this reason, a graphical interface is of no use here. It is therefore forbidden to install X.org or any other equivalent graphics server. Otherwise, your grade will be 0.

You must choose as an operating system either the latest stable version of Debian (no testing/unstable), or the latest stable version of CentOS. Debian is highly recommended if you are new to system administration.

> Setting up CentOS is quite complex. Therefore, you don’t have to set up KDump. However, SELinux must be running at startup and its configuration has to be adapted for the project’s needs. AppArmor for Debian must be running at startup too.

You must create at least 2 encrypted partitions using LVM. Below is an example of the expected partitioning:

> During the defense, you will be asked a few questions about the operating system you chose. For instance, you should know the differences between aptitude and apt, or what SELinux or AppArmor is. In short, understand what you use!

A SSH service will be running on port 4242 only. For security reasons, it must not be possible to connect using SSH as root.

> The use of SSH will be tested during the defense by setting up a new account. You must therefore understand how it works.

You have to configure your operating system with the UFW firewall and thus leave only port 4242 open.

> Your firewall must be active when you launch your virtual machine. For CentOS, you have to use UFW instead of the default firewall. To install it, you will probably need DNF.

* The hostname of your virtual machine must be your login ending with 42 (e.g., wil42). You will have to modify this hostname during your evaluation.
* You have to implement a strong password policy.
* You have to install and configure sudo following strict rules.
* In addition to the root user, a user with your login as username has to be present.
* This user has to belong to the user42 and sudo groups.

During the defense, you will have to create a new user and assign it to a group.

To set up a strong password policy, you have to comply with the following requirements:
* Your password has to expire every 30 days.
* The minimum number of days allowed before the modification of a password will be set to 2.
* The user has to receive a warning message 7 days before their password expires.
* Your password must be at least 10 characters long. It must contain an uppercase letter and a number. Also, it must not contain more than 3 consecutive identical characters.
* The password must not include the name of the user.
* The following rule does not apply to the root password: The password must have at least 7 characters that are not part of the former password.
* Of course, your root password has to comply with this policy.

> After setting up your configuration files, you will have to change all the passwords of the accounts present on the virtual machine, including the root account.

To set up a strong configuration for your sudo group, you have to comply with the following requirements:
* Authentication using sudo has to be limited to 3 attempts in the event of an incorrect password.
* A custom message of your choice has to be displayed if an error due to a wrong password occurs when using sudo.
* Each action using sudo has to be archived, both inputs and outputs. The log file has to be saved in the /var/log/sudo/ folder.
* The TTY mode has to be enabled for security reasons.
* For security reasons too, the paths that can be used by sudo must be restricted. Example:`/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin`

Finally, you have to create a simple script called monitoring.sh. It must be developed in bash.
At server startup, the script will display some information (listed below) on all terminals every 10 minutes (take a look at wall). The banner is optional. No error must be visible.

Your script must always be able to display the following information:
* The architecture of your operating system and its kernel version.
* The number of physical processors.
* The number of virtual processors.
* The current available RAM on your server and its utilization rate as a percentage.
* The current available memory on your server and its utilization rate as a percentage.
* The current utilization rate of your processors as a percentage.
* The date and time of the last reboot.
* Whether LVM is active or not.
* The number of active connections.
* The number of users using the server.
* The IPv4 address of your server and its MAC (Media Access Control) address.
* The number of commands executed with the sudo program.

> During the defense, you will be asked to explain how this script works. You will also have to interrupt it without modifying it. Take a look at cron.

This is an example of how the script is expected to work:

# Bonus part
Bonus list:
* Set up partitions correctly so you get a structure similar to the one below:
* Set up a functional WordPress website with the following services: lighttpd, MariaDB, and PHP.
* Set up a service of your choice that you think is useful (NGINX / Apache2 excluded!). During the defense, you will have to justify your choice.

> To complete the bonus part, you have the possibility to set up extra services. In this case, you may open more ports to suit your needs. Of course, the UFW rules has to be adapted accordingly.

> The bonus part will only be assessed if the mandatory part is PERFECT. Perfect means the mandatory part has been integrally done and works without malfunctioning. If you have not passed ALL the mandatory requirements, your bonus part will not be evaluated at all.

# EVALUATION

1. How to check the signature from the virtual machine with the one submitted?
    
    Windows: type`certUtil -hashfile <virtual_machine>.vdi sha1` and compare the result with the one cloned from git.
    
2. What is a Virtual Machine?
    
    A Virtual Machine (VM) is **a computer resource that uses software instead of a physical computer to run programs and deploy apps**. One or more virtual “guest” machines run on a physical “host” machine. ... This means that, for example, a virtual MacOS virtual machine can run on a physical PC.
    
    1. What is it’s purpose?
        
        VMs may be deployed to accommodate different levels of processing power needs, to run software that requires a different
        operating system, or to test applications in a safe, sandboxed environment.
        
    2. How does it works?
        
        VM working through "Virtualization" technology. Virtualization uses software to simulate virtual hardware that allows
        VMs to run on a single host machine.
        
3. What is the difference between CentOS and **Debian**?
    
    CentOS vs Debian are two flavors of Linux operating systems.
    CentOS, as said above, is a Linux distribution.
    It is free and open-source. It is enterprise-class – industries can use meaning for server building; it is supported by a large community and is functionally supported by its upstream source, Red Hat Enterprise Linux.
    Debian is a Unix like computer operating system that is made up of open source components. It is built and supported by a group of individuals who are under the Debian project.
    
    Debian uses Linux as its Kernel. Fedora, CentOS, Oracle Linux are all different distribution from Red Hat Linux and are variant of RedHat Linux. Ubuntu, Kali, etc., are variant of Debian. CentOS vs Debian both are used as internet servers or web servers like web, email, FTP, etc.
    
4. What is the difference between **APT** and **Aptitude?**
    
    Besides the main difference being that Aptitude is a high level package manager while **APT** is a lower level package manager that can be used by other higher level package managers, the other main strengths that separate these two package managers are:
    
    Aptitude is more feature-rich with a GUI than apt-get and incorporates functionality from apt-get and its other variants, including apt-mark and apt-cache. While apt-get handles all package installation, upgrading, system upgrading, package purging, dependency resolution, etc., Aptitude handles a lot more things than apt, including apt-mark and apt-cache functionality, i.e. finding a package in the list of installed packages, marking a package to be installed automatically or manually, containing a package making it unavailable for upgrading, etc.
    
5. **What is SELinux**? Security service for CentOS
    
    SELinux (Security-Enhanced Linux) is a security architecture for Linux® systems that allows administrators to better control access to the system. This architecture was originally designed by the NSA, the national security agency of the United States, as a series of fixes for the Linux kernel based on the LSM (Linux Security Modules) framework.
    
6. What is **AppArmor**? Security service for Debian
    
    AppArmor (Application Armor) is a security software for Linux systems made under GNU General Public License. 
    
    AppArmor ("Application Armor") is a Linux kernel security module that allows the system administrator to restrict programs' capabilities with per-program profiles.
    
7. What is **UFW**? 
    
    **U**ncomplicated **F**ire**W**all
    The default firewall configuration tool for Ubuntu is ufw. Developed to ease iptables firewall configuration, ufw provides a user friendly way to create an IPv4 or IPv6 host-based firewall. By default UFW is disabled.
    
8. What is **SSH**?
    
    **S**ecure **SH**ell or SSH is a network communication protocol that enables two computers to communicate (c.f http or hypertext transfer protocol, which is the protocol used to transfer hypertext such as web pages) and share data.
    
9. How to check if AppArmor is working?
    
    type `sudo aa-status`
    
10. How to check the SSH status?
    
    type `sudo service ssh status`
    type `sudo systemctl status sshd`
    
11. How to connect via SSH?
    
    type `ssh <username>@<ipadress> -p 4242`
    
12. How to disconnect via SSH?
    
    type `exit`
    
    try as a root user. It should be denied!
    
    type `ssh root@<ipadress> -p 4242`
    
13. How to see the used port for SSH and permission for root user?
    
    type`cat /etc/ssh/sshd_config`
    
14. How to get the ipadress?
    
    type `hostname -I`
    
15. USERGROUP
    1. How to **show** the user groups?
        
        type `groups <username>`
        type `id <username>`
        
    2. How to **create** a new user group?
        
        type `sudo addgroup <usergroup>`
        type `sudo groupadd <usergroup>`
        
    3. How to **delete** a user group?
        
        type `sudo delgroup <usergroup>`
        
    4. How to **check** the user groups?
        
        type `less /etc/group` scroll down, should be the last entry
        press q to leave the less view
        
16. USER
    1. How to **add** a new user?
        
        type `sudo adduser <username>`
        Skip all the value questions
        
    2. How to **delete** a user?
        
        type `sudo userdel -r <username>` -r deletes the created folders
        
    3. How to **check** if a user exists?
        
        type `getent passwd | grep <username>`
        type `getent passwd <username>`
        
    4. How to check password expire for new user?
        
        type `sudo chage -l <username>`
        
    5. How to add a user to a usergroup?
        
        type `sudo adduser <username> <usergroup>`
        type `sudo usermod -aG <usergroup> <username>`
        type 
        
    6. How to delete a user from a usergroup?
        
        type `sudo deluser <username> <usergroup>`
        
17. HOSTNAME
    1. How to change the hostname?
        
        type `sudo nano /etc/hostname` change name save file and reboot
        type `sudo hostnamectl set-hostname <hostname>`
        
    2. How to show the new nostname?
        
        type `hostname`
        
18. DRIVES
    1. What is **LVM**?
        
        **L**ogical **V**olume **M**anager - something like partion magic to create virtual drives on a physical drive.
        
    2. How to check the drive partitions
        
        type `lsblk`
        
19. SUDO
    1. Why there is a root user and the normal user? When do I have sudo rights already?
        
        I never forget that I am doing something as an admin. I am aware what I am doing.
        `sudo` switch user do as ...
        I want to be a normal user and use sudo never be a root user!
        
    2. What is **TTY**?
        
        Type. Command. In computing, tty is a command in Unix and Unix-like operating systems to print the file name of the terminal connected to standard input. tty **stands for TeleTYpewriter**.
        
    3. Why do we have TTY?
        
        It decrypt the data transmitted between two computers. Otherwise it would be in plain text.
        
    4. How to switch to the root user?
        
        type `su -`
        
20. **LOGFILE**
    1. How to see the logfile?
        
        type `sudo ls -la /var/log/sudo`
        
        type `sudo cat /var/log/sudo/<sudo_log.log>`
        
        How to check the input and output?
        
        type `sudo nano /var/log/sudo/00/00/??`
        
    2. Where to find the Logfile, password tries, secure_path, password message settings?
        
        type `sudo nano /etc/sudoers.d/README
        Defaults passwd_tries=3
        Defaults badpass_message="<MESSAGE>"
        Defaults requiretty`- That means I have to run the sudo commands from the terminal
        
        `Defaults logfile="/var/log/sudo/sudo_log.log"
        Defaults iolog_dir="/var/log/sudo"
        Defaults log_input, log_output
        Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"`
        
21. **Password**
    1. Where to find the password rules?
        
        type `sudo nano /etc/pam.d/common-password`
        
        `password requisite pam_pwquality.so
        retry=3` - you can only retrie 3 times
        `minlen=10` - minimum len of the password
        `ucredit=-1` - one uppercase character 
        `decredit=-1` - one decimal character
        `maxrepeat=3` - max 3 times the same character
        `reject_username
        difok=7` - 7 characters different from the previous password
        `enforce_for_root` - the same rules for the root user
        
    2. Where to find the password expire rule?
        
        type `sudo nano /etc/login.defs` - scroll down
        `PASS_MAX_DAYS 30
        PASS_MIN_DAYS 2
        PASS_WARN_AGE 7`
        
        Where to change the password rules for existing users?
        
    3. type `sudo nano /etc/shadow`
    ⚠️**only modify the root and your user!!!**⚠️
    root?????????0:999999:7 ⇒ 2:30:7
    user?????????0:999999:7 ⇒ 2:30:7
22. PORTS
    1. How to see all ports?
        
        type `sudo ufw status numbered`
        
    2. How to create a new port?
        
        type `sudo ufw allow <portnumber>`
        
    3. How to delete a port?
        
        type `sudo ufw delete <number>` not the port number! the number from the sudo ufw status numbered. Order number change when one is deleted
        type `sudo ufw delete allow <number>`
        
    4. How to check the operating system?
        
        type `hostnamectl`
        type `cat /etc/os-release`
        
23. CRONTAB
    1. What is crontab?
        
        The crontab is **a list of commands that you want to run on a regular schedule**, and also the name of the command used to manage that list. Crontab stands for “cron table, ” because it uses the job scheduler cron to execute tasks; cron itself is named after “chronos, ” the Greek word for time.
        
        type `cat /etc/crontab` - info of crontab
        
    2. How to add/change a crontab job?
        
        type `sudo crontab -u root -e`
        
    3. What is the wall command for?
        
        It will send messages to all users
        
    4. How to change the script?
        
        type `sudo nano /usr/monitoring.sh`
        

What is the `uname -a` command?
Print certain system information. `-a` means all information. See `uname —help`

What is the `nproc` command?
Print the number of processing units available to the current process, which my be less than the number of online processors. See `nproc —help`

What is the `cat /proc/cpuinfo | grep processor | wc -l` command?
The `cat /proc/cpuinfo` command concatenate FILE(s) to the standard output. See `cat —help` The info in the file cpuinfo will read. 
The `|` outputstream will passed to the next command as inputstream. 
The`grep processor` locks for the “processor” in the inputstream and sends lines to the outputstream. See `grep —help` 
The `wc -l` print the newline counts. See `wc —help`

What is the `free —mega | awk ‘NR==2{printf “%s/%sMB (%.2f%%)\n”, $3,$2,$3*100/$2 }’` command?
The `free —mega` shows the output in megabytes.
The `|` outputstream will passed to the next command as inputstream.
The `awk` is a **scripting language used for manipulating data and generating reports**. The awk command programming language requires no compiling and allows the user to use variables, numeric functions, string functions, and logical operators. ... Awk is mostly used for pattern scanning and processing.
The `’Nr==2'` sends the second row to the outputstream.
the `printf` Formats and prints arguments under control of the format.
The `$2` uses the second entry passed to printf as inputstream.

[awk(1p) - Linux manual page](https://man7.org/linux/man-pages/man1/awk.1p.html)

What is the `df -h | awk ‘$NF==”/”{printf “%d/%.1Gb (%s)\n”, $3,$2,$5}’` command?
The `df -h` show information about the file system on which each FILE resides, or all files systems by default, with detailed information about size, avail and so on. See `df —help`
The `‘$NF==”/”’` searches for the `“/”` in the end of a line.

What is the `top -bn1 | grep load | awk ‘{printf “%.2f%%\n”, $(NF-2)}’` command?
The `top` command is used to **show the Linux processes**. It provides a dynamic real-time view of the running system. Usually, this command shows the summary information of the system and the list of processes or threads which are currently managed by the Linux Kernel.

`-b` :Batch-mode operation Starts top in Batch mode, which could be useful for sending output from top to other programs or to a file. In this mode, top will not accept input and runs until the iterations limit you've set with the `-n' command-line option or until killed.

`-n` :Number-of-iterations limit as: -n number Specifies the maximum number of iterations, or frames, top should produce before ending.
See → 

[top(1) - Linux manual page](https://man7.org/linux/man-pages/man1/top.1.html)

What is the `who -b | awk ‘{printf “%s %s\n”, $3,$4}’` command?
The `who` print information about user who are currently logged in. `-b` means time of last system boot. See `who —help`

What is the `if cat /etc/fstab | grep -q “/dev/mapper/”; then echo “yes”; else echo “no”; fi` command?
grep -q suppress all normal output. Nothing will print to the terminal.
An `if then else fi`  statement. `echo` prints `“”` to the terminal.

What is the `cat /proc/net/tcp | wc -l | awk ‘{printf “%d ESTABLISHED\n”, $1-1}’` command?

What is the `w | wc -l | awk ‘{printf “%d\n”, $1-2}’` command?

What is the `ip route list | grep link | awk ‘{printf “%s “, $9}’; ip link show | grep link/ether | awk ‘{printf “(%s)\n”, $2}’` command?
The `ip` - show / manipulate routing, network devices, interfaces and
tunnels. See `ip —help`

What is the `cat /var/log/sudo/sudo_log.log | wc -l | awk ‘{printf “%d cmd\n”, $1/2}’` command?
