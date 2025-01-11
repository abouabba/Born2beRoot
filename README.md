
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

          sudo apt install openssh-server

https://mathieu-soysal.gitbook.io/~gitbook/image?url=https%3A%2F%2F3975474142-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252FvxQldFCzdjsw8BkClhdK%252Fuploads%252FhcKqv6JgKgqPu3jZiFGz%252Fimage.png%3Falt%3Dmedia%26token%3De76e8653-fe65-4d53-be48-10782aa15d87&width=768&dpr=4&quality=100&sign=1001f0a5&sv=2

3. Anywan curious that the installation have been realices without problems we can use:

          sudo service ssh status

📶
Configuring SSH

For that we will use Nano or VIM (we will need to install vim since it's not preinstalled using sudo apt install vim) or any other text editor.
First file that we will edit will be /etc/ssh/sshd_config. If you are not on root you will not be able to edit the file; as you know, for switching to root we use su

          su
          
          nano /etc/ssh/sshd_config
The # means that line it is commented; the lines that we will be edit have to be uncommented. Once we are editing the file we need to update the following lines:

          #Port 22 -> Port 4242
