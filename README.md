
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
2. Following up we will install the main tool for remote access with the SSH protocol, using OpenSSH. The installation requieres the package:

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
Lastly we will add the 4242 port to host and client. The IP's are not required. We will click accept so changes can be saved.
2. The # means that line it is commented; the lines that we will be edit have to be uncommented. Once we are editing the file we need to update the following lines:

          #Port 22 -> Port 4242
   
   ![image](https://github.com/user-attachments/assets/1c92fc1a-4ead-444a-8df0-0ca7f8ffa1d6)

   #PermitRootLogin prohibit-password -> PermitRootLogin no


![image](https://github.com/user-attachments/assets/44e620b2-4bc6-4db0-babb-678017d483e8)

👬
Connecting via SSH

1. Go to device settings and enter settings

   ![image](https://github.com/user-attachments/assets/c1953e1a-e930-48ad-aabc-f92432edd0cd)


2. Once there we will click on Network, click on Advanced so it shows more options, then we click on Port fowarding.

![image](https://github.com/user-attachments/assets/64126c37-0fd4-4a49-ab4b-4de351e10467)

3. Click on the emoji for adding a new rule.

   ![image](https://github.com/user-attachments/assets/83c73a72-1c98-4d44-9f9b-3dc5f4eede80)

4. Lastly we will add the 4242 port to host and client. The IP's are not required. We will click accept so changes can be saved.

   ![image](https://github.com/user-attachments/assets/a8ba7135-531e-4463-b51a-6c0ea47cca24)

🚨 In some devices, the port may be missing, so the connection will not work. It may be useful if you change the port from 4242 to 4241.
