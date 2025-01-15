
⚙️
Virtual machine setup
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
