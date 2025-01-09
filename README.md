
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
