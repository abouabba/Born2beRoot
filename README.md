
It is better to read on Virtualbox because it is very important. Read to benefit from it. And search for hypervisor.

![Screenshot from 2025-01-16 21-16-51](https://github.com/user-attachments/assets/44a8b6c2-a8a8-493f-a5a1-ef7dec6098e7)


# ⚙️Virtual machine setup
👤
Installing sudo & configuration of user and groups
sudo is a program for Unix-like computer operating systems that enables users to run programs with the security privileges of another user, by default the superuser. 
It originally stood for "superuser do", as that was all it did, and it is its most common usage; however, the official Sudo project page lists it as "su 'do' ".

1.    The beginning of the installation starts with changing user to root so we can install sudo, for this purpouse we write:

          su
 
      su in the bash prompt and introduce the root password, in my case Hola42bcn.

2. Once we are done we write down the command

        apt install sudo

3. We must reboot machine so the changes can be applied. For that porpouse we will use the commando:

        sudo reboot

👤
Creating a user

 Now, this step is for the everyone that didn't put his user as the other user asked by the subject during the installation of the system.

Still in the root user we will create an additional user with

          sudo addusr <user>

👥
Creating a group

1. We will create a new group called user42. For that we must use:

             sudo addgroup <group>

🤔 Was the group created without problems? Truth is that there is no sign of one, still we can check it using with:

          getent group <groupname>

📶
Installing & configuring SSH

1. First thing, we should update the system using

          sudo apt update
2. Following up we will install the main tool
First things first, we need to install the packages for UFW, for that we will use: for remote access with the SSH protocol, using OpenSSH. The installation requieres the package:

Lastly we will add the 4242 port to host and client. The IP's are not required. We will click accept so changes can be saved.
          sudo apt install openssh-server

![image](https://github.com/user-attachments/assets/e40f5ec6-85dc-406d-a78a-6de032c5a6aa)


3. Anywan curious that the installation have been realices without problems we can use:

          sudo service ssh status

📶
Configuring SSH

For that we will use Nano or VIM (we will need to install vim since it's not preinstalled using sudo apt install vim) or any other text editor.
First file that we will edit will be /etc/ssh/sshd_config. If you are not on root you will not be able to edit the file; as you know, for switching to root we use su

          su
          
          nano /etc/ssh/sshd_config
Lastly we will add the 4242 port to host an
First things first, we need to install the packages for UFW, for that we will use:d client. The IP's are not required. We will click accept so changes can be saved.
2. The # means that line it is commented; the lines that we will be edit have to be uncommented. Once we are editing the file we need to update the following lines:

          #Port 22 -> Port 4242
   
   ![image](https://github.com/user-attachments/assets/1c92fc1a-4ead-444a-8df0-0ca7f8ffa1d6)

   #PermitRootLogin prohibit-password -> PermitRootLogin no


![image](https://github.com/user-attachments/assets/44e620b2-4bc6-4db0-babb-678017d483e8)

👬
Connecting via SSH

1. Go to device settings and enter settingsIt will ask for the password of the user that we are trying to log in. Once the password is introduced it will show or login in green, that will mean that the connections has been successfully

   ![image](https://github.com/user-attachments/assets/c1953e1a-e930-48ad-aabc-f92432edd0cd)


2. Once there we will click on Network, click on Advanced so it shows more options, then we click on Port fowarding.

![image](https://github.com/user-attachments/assets/64126c37-0fd4-4a49-ab4b-4de351e10467)

3. Click on the emoji for adding a new rule.

   ![image](https://github.com/user-attachments/assets/83c73a72-1c98-4d44-9f9b-3dc5f4eede80)

4. Lastly we will add the 4242 port to host and client. The IP's are not required. We will click accept so changes can be saved.

   ![image](https://github.com/user-attachments/assets/a8ba7135-531e-4463-b51a-6c0ea47cca24)

🚨 In some devices, the port may be missing, so the connection will not work. It may be useful if you change the port from 4242 to 4241.
First things first, we need to install the packages for UFW, for that we will use:

5. To connect via ssh from our machine to the virstual machine using and the use the command

   my username is abouabba.
   So if I want to call you ssh
   type..
   
             ssh abouabba@localhost -p 4241.

It will ask for the password of the user that we are trying to log in. Once the password is introduced it will show or login in green, that will mean that the connections has been successfully

🔥
Installing & configuring UFW 🔥🧱 Firewall

UFW: It is a firewall which use the command line for setting up iptables using a small number of easy commands.

1. 
First things first, we need to install the packages for UFW, for that we will use:

          sudo apt install ufw

then when we are asked for confirmation type y and the installation will proceed.

![image](https://github.com/user-attachments/assets/2236bf49-f8a2-4c2a-91d2-f1aa6abad2f0)

![image](https://github.com/user-attachments/assets/45d20c5a-2752-4890-89ed-ab52d5113c94)

2. When we are done with it, we want to start it using the command:

          sudo ufw enable

   and then it have to show us the the firewall is ative.

🔥
Allow a port to firewall

![image](https://github.com/user-attachments/assets/9c2daa53-f7de-4501-8b25-657e9d9084d6)

1. we must allow our firewall to accept the connections that will happens in the 4242 port. What we will do is use:

          sudo ufw allow 4242
2. Lastly we will check if everything done here is correct checking the actual state of our firewall. For that we will use:

🔐
sudo policies

          sudo ufw status
![image](https://github.com/user-attachments/assets/dab09a07-16e6-4899-8878-8e49b06efaf5)

Begining with this section, we will create a file in /etc/sudoerd.d/. The file will serve the purpouse of storing our sudo policy

          touch /etc/sudoers.d/sudo_config

1. The command that we will use will be 

![image](https://github.com/user-attachments/assets/e965be93-13ef-42df-8dd8-77dc46ae4e75)


2. Then we must create a directory as is asked in the subject in /var/log/ because each commands need to be logged, the input and output. We will use:

          mkdir /var/log/sudo

![image](https://github.com/user-attachments/assets/acceb6dd-afea-4c17-af0f-2729242e8a2f)


3. We must edit the file that we created in the first step of this section. Use any text editor, but for this guide as is in every screenshot we will use nano. Use:

          nano /etc/sudoers.d/sudo_config


Once we are editing the file we must set it up with the following commands:

![image](https://github.com/user-attachments/assets/2a7b5bad-b924-41de-9fc8-8e429b14a819)


Defaults  passwd_tries=3
Defaults  badpass_message="Mensaje de error personalizado"
Defaults  logfile="/var/log/sudo/sudo_config"
Defaults  log_input, log_output
Defaults  iolog_dir="/var/log/sudo"
Defaults  requiretty
Defaults  secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"


As it should be on the file:

![image](https://github.com/user-attachments/assets/f458b97b-4ef5-42a7-81c2-d2e3981f4200)


✅ passwd_tries=3: Total tries for entering the sudo password.

✅ badpass_message="message": The message that will show when the password failed.

✅ logfile="/var/log/sudo/sudo_config": Path where will the sudo logs will be stored.

✅ log_input, log_output: What will be logged.

✅ iolog_dir="/var/log/sudo": What will be logged.

✅ requiretty: TTY become require

✅ secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin": Folders that will be excluded of sudo

🔑
password policy 🔑

1. First step will be editing the login.defs file:

          nano /etc/login.defs

2. Once we are done editing the file, we will set the next parameters:

PASS_MAX_DAYS 99999 -> PASS_MAX_DAYS 30

PASS_MIN_DAYS 0 -> PASS_MIN_DAYS 2

![image](https://github.com/user-attachments/assets/90f826cf-9b28-481c-8b24-3a75f1ba9ee0)

🎃 PASS_MAX_DAYS: It's the max days till password expiration.

🎃 PASS_MIN_DAYS: It's the min days till password change.

🎃 PASS_WARN_AGE: It's the days till password warning.


3. For continuing the installation we must install the next packages to enforce the password quality with the following command:

          sudo apt install libpam-pwquality

![image](https://github.com/user-attachments/assets/c18e268b-88e6-4fe3-86ec-573c11991f0f)


4. Next thing we must do is is edit a file and change itś content. We will use

          nano /etc/pam.d/common-password

6. Below retry=3 we must add the following commands:

          minlen=10 ucredit=-1 dcredit=-1 lcredit=-1 maxrepeat=3 reject_username difok=7 enforce_for_root

![image](https://github.com/user-attachments/assets/d6f92520-6a9a-4d8a-9e14-2d931ba4c160)

🔥 minlen=10 : Specifies the minimum length of the password. In this case, the password must be at least 10 characters long.

🔥 ucredit=-1 : Requires at least 1 uppercase letter in the password. Negative values indicate the minimum required number of characters.

🔥 dcredit=-1 : Requires at least 1 digit in the password.

🔥 lcredit=-1 : Requires at least 1 lowercase letter in the password.

🔥 maxrepeat=3: Restricts repeated characters in the password to a maximum of 3 consecutive occurrences.

🔥 reject_username : Prevents the use of the username (or parts of it) as the password, increasing security.

🔥 difok=7 : Ensures that at least 7 characters in the new password must differ from the old password.

🔥 enforce_for_root : Applies these password rules even for the root user, ensuring consistent enforcement of password policies.

# 🧾Script 🚨

# script:  is a sequence of commands stored in a file that when executed will do the function of each command.

Gathering System Information:

          uname -a
Retrieves the system's architecture and kernel information using the uname command.

          lscpu | grep "^Socket(s):" | awk '{print $2}'
Extracts the number of physical CPUs (sockets) using lscpu.

          grep "^processor" /proc/cpuinfo | wc -l
Counts the number of virtual CPUs (logical processors).

          free -m | awk '/^Mem:/ {printf "%d/%dMB (%.2f%%)\n", $3, $2, ($3/$2)*100}'
Displays the current and total memory usage in MB and as a percentage.

          df -BG --total | awk '/^total/ {printf "%d/%dGb (%s)\n", $3*1024, $2, $5}'
Summarizes the total disk usage in GB and shows the percentage used.

          top -bn1 | grep "Cpu(s)" | awk '{printf "%.1f%%\n", $2 + $4}'
Captures the current CPU load percentage from top.

          who -b | awk '$1 == "system" {print $3 " " $4}'
Gets the last boot time from the who -b command.

          lsblk | grep -q "lvm" && echo "yes" || echo "no"
Checks if Logical Volume Management (LVM) is being used.

          ss -Ht state established | wc -l
Counts the number of established TCP connections using ss.

          users | tr " " "\n" | uniq | wc -l
Counts the number of unique users currently logged in.

          hostname -I
Retrieves the system's IP address.

          ip link show | grep "ether" | awk '{print $2}'
Fetches the MAC address of the system.

          journalctl _COMM=sudo | grep COMMAND | wc -l
Counts the number of sudo commands executed by querying the system logs.

# Total result of the script

          #!/bin/bash
          while true;
          do
          sleep 600
          arc=$(uname -a)
          pcpu=$(lscpu | grep "^Socket(s):" | awk '{print $2}')
          vcpu=$(grep "^processor" /proc/cpuinfo | wc -l)
          ram=$(free -m | awk '/^Mem:/ {printf "%d/%dMB (%.2f%%)\n", $3, $2, ($3/$2)*100}')
          disk=$(df -BG --total | awk '/^total/ {printf "%d/%dGb (%s)\n", $3*1024, $2, $5}')
          cpul=$(top -bn1 | grep "Cpu(s)" | awk '{printf "%.1f%%\n", $2 + $4}')
          lb=$(who -b | awk '$1 == "system" {print $3 " " $4}')
          lvmu=$(lsblk | grep -q "lvm" && echo "yes" || echo "no")
          ctcp=$(ss -Ht state established | wc -l)
          ulog=$(users | tr " " "\n" | uniq | wc -l)
          ip=$(hostname -I)
          mac=$(ip link show | grep "ether" | awk '{print $2}')
          cmds=$(journalctl _COMM=sudo | grep COMMAND | wc -l)
          wall "  #Architecture   : $arc
        #CPU physical   : $pcpu
        #vCPU           : $vcpu
        #Memory Usage   : $ram
        #Disk Usage     : $disk
        #CPU load       : $cpul
        #Last boot      : $lb
        #LVM use        : $lvmu
        #Connections TCP: $ctcp ESTABLISHED
        #User log       : $ulog
        #Network        : IP $ip ($mac)
        #Sudo           : $cmds cmd"
          done

# Result after executing the script ↙️

![image](https://github.com/user-attachments/assets/1aace589-da60-42a2-9e06-d9319bf6f5a8)

# what is crontab

Crontab stands for "cron table", and it’s a tool in Unix-like operating systems (like Linux) used to schedule commands or scripts to run automatically at specific times and intervals.

How does crontab work?

cron: It’s the background service (or daemon) that executes the scheduled tasks.

crontab: It’s the configuration file where you define the tasks and their schedules

Crontab syntax
A crontab entry typically has this structure:

          * * * * * command_to_execute
          - - - - -
          | | | | |
          | | | | +---- Day of the week (0 - 7, Sunday can be 0 or 7)
          | | | +------ Month (1 - 12)
          | | +-------- Day of the month (1 - 31)
          | +---------- Hour (0 - 23)
          +------------ Minute (0 - 59)
1. To properly configure crontab, we must edit the crontab file with the following command:

          sudo crontab -u root -e
2. In the file, we must add the following command for the script to execute every 10 minutes */10 * * * * sh /path_to_file.sh.

![image](https://github.com/user-attachments/assets/31e1a060-0066-4857-ad10-beb584f4c12c)

To well know how crontab works you can go to this site :
https://crontab.guru/

# ✒️Signature.txt

To obtain the signature, the first thing we must do is shut down the virtual machine, since once you turn it on or modify something, the signature will change.

Since once you turn it on or modify something, the signature will change.

1. The next step will be to locate ourselves in the path where we have the .vdi of our virtual machine. From our physical machine.

![image](https://github.com/user-attachments/assets/6a6794ce-fd6c-4620-bc3a-45d27eb3892b)

We had choose the path here

2. Finally, we will run shasum machinename.vdi and this will give us the signature. The result of this signature is what we will need to add to our signature.txt file and subsequently upload the file to the intra repository. It is very important not to reopen the machine since the signature will be modified. For corrections, remember to clone the machine so you can turn it on without fear of changing the signature.

          shasum machinename.vdi

shasum: It is a command that allows you to identify the integrity of a file using the SHA-1 hash check sum of a file.


# ✅ BONUS SERVICES

# 💡Lighttpd

Lighttpd: is a web server designed to be fast, secure, flexible, and standards-compliant. It is optimized for environments where speed is a top priority because it consumes less CPU and RAM than other servers.

1. Installation of Lighttpd packages.

          sudo apt install lighttpd

![image](https://github.com/user-attachments/assets/575e8ceb-9c3d-497c-b0b2-97ae04137b33)

2. We allow connections through port 80 with the command:

          sudo ufw allow 80

3. We check that we have actually allowed it. Port 80 and allow should appear:

          sudo ufw status

4. We add the rule that includes port 80. If you don't remember how to add rules in port forwarding. Machine configuration → Network → Port forwarding → Replicate the capture

![image](https://github.com/user-attachments/assets/ce5ae915-11aa-4c01-8fb9-b8afed7acfe3)

# 📰
WordPress

WordPress is one of the most popular Content Management Systems (CMS) in the world. It allows you to create websites and blogs easily, even if you don’t have advanced programming skills.

1. To install the latest version of WordPress we must first install wget and zip. To do this we will use the following command:

          sudo apt install wget zip

💡 wget: It is a command line tool used to download files from the web.

💡 zip: It is a command line utility for compressing and decompressing files in ZIP format.

2. Once we have installed the packages we must locate ourselves in the folder /var/www/ with the command cd we will access it:

          cd /var/www/
3. Once we are in the path /var/www/ we must download the latest version of WordPress. As my native language is Spanish I will select the latest version in Spanish. We will use the following command:

          sudo wget https://es.wordpress.org/latest-es_ES.zip

💡 I could be https://fr.wordpress.org/latest-fr_FR.zip

4. Unzip the file you just downloaded with the command:

          sudo unzip latest-en_US.zip

5. We will rename the folder html and call it html_old:

          sudo mv html/ html_old/

6. Now we will rename the wordpress folder and call it html:

          sudo mv wordpress/ html

7. Finally we will set these permissions on the html folder. We will use the command sudo chmod -R 755 html. The number 7 indicates that the owner has read, write and execute permissions. The number 5 indicates that the group and others only have read and execute permissions.

          sudo chmod -R 755 html

🐬
Mariadb

MariaDB: It is a database. It is used for various purposes, such as data warehousing, e-commerce, enterprise-level functions, and logging applications.

1. We will install the packages with the command:

          sudo apt install mariadb-server

2. Because the default configuration leaves your MariaDB installation unsecure, we will use a script provided by the mariadb-server package to restrict access to the server and remove unused accounts. We will run the script with the following command:

          sudo mysql_secure_installation

