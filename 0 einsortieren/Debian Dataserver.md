Install sudo Command in Debian

Begin by logging into your Debian system using either the graphical user interface (GUI) or ssh. Then launch a fresh terminal window. You can then use the su command switch to the root account. When prompted, enter your root password. And install the sudo command using the apt package manager as shown:

su
apt-get install sudo

Add User to sudo Group

After installing the sudo command as shown above, add the user you want to use the sudo command to the sudo system group. Remember to change fossman to your username:

adduser fossman  sudo
OR
usermod -aG sudo fossman