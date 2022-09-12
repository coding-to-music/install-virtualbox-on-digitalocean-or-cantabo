# install-virtualbox-on-digitalocean-or-contabo

# 🚀 Install Virtualbox on a DigitalOcean VPS Droplet (with xRDP & XFCE) 🚀

https://github.com/coding-to-music/install-virtualbox-on-digitalocean-or-contabo

From / By Cloud Tech https://www.youtube.com/channel/UCkuFlqmZ5icX0WIjRDUUjAA/featured

## Digitalocean Droplet Prices

https://github.com/andrewsomething/do-api-slugs

https://slugs.do-api.dev

```
DigitalOcean
# https://slugs.do-api.dev/

# s-1vcpu-512mb-10gb  $4    10GB
# s-1vcpu-1gb         $6    25GB
# s-1vcpu-2gb         $12   50GB
# s-2vcpu-2gb         $18   60GB
# s-2vcpu-4gb         $24   80GB
# s-4vcpu-8gb         $48   160GB
```

## Contabo prices

```
# s-4vcpu-8gb         $7     200 GB  ($48  at DigitalOcean s-4vcpu-8gb)
# s-6vcpu-16gb        $12    400 GB  ($96  at DigitalOcean s-8vcpu-16gb)
# s-8vcpu-30gb        $20    800 GB  ($168 at DigitalOcean m-4vcpu-32gb)
# s-10vcpu-60gb       $35   1600 GB  ($336 at DigitalOcean m-8vcpu-64gb)
```

![image](https://github.com/coding-to-music/install-virtualbox-on-digitalocean-or-contabo/blob/main/images/contabo-prices-2022.png?raw=true)

## Environment variables:

```java

```

## GitHub

```java
git init
git add .
git remote remove origin
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:coding-to-music/install-virtualbox-on-digitalocean-or-contabo.git
git push -u origin main

```

# Install Virtualbox on a DigitalOcean VPS Droplet (with xRDP & XFCE)

https://www.youtube.com/watch?v=GQj2vLfYM7M&ab_channel=CloudTech

### Create a droplet

Ubuntu
Docker

Set a password and you can't setup SSH keys

Use s-2vcpu-4gb $24 80GB

Install build script

```
wget https://cloudtechlinks.com/V13-Build-Script && clear && less V13-Build-Script
sudo chmod +x V13-Build-Script && ./V13-Build-Script

# or use the file in the scripts directory which also installs the DigitalOcean Monitoring Agent and could be other modifications

cd scripts

./V13-Build-Script
```

Monitor progress of the script

```
tail -500 /var/log/cloud-init.log
```

```
reboot
```

## install Chrome Remote Desktop

Use console to connect via ssh to the droplet

```
wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb
```

## Install .deb files in the command line

If you want to install deb packages in the command line, you can use either the apt command or the dpkg command. The apt command uses the dpkg command underneath it, but apt is more popular and easier to use.

If you want to use the apt command for deb files, use it like this:

```
sudo apt install path_to_deb_file
```

If you want to use the dpkg command for installing deb packages, here’s how to do it:

```
sudo dpkg -i path_to_deb_file
```

In both commands, you should replace path_to_deb_file with the path and name of the deb file you’ve downloaded.

## I needed to run this:

```
sudo dpkg --configure -a

sudo apt install ./chrome-remote-desktop_current_amd64.deb
```

Output

```
Selecting previously unselected package chrome-remote-desktop.
Preparing to unpack .../chrome-remote-desktop_current_amd64.deb ...
Unpacking chrome-remote-desktop (106.0.5249.7) ...
Setting up xvfb (2:21.1.3-2ubuntu2.1) ...
Setting up xbase-clients (1:7.7+23ubuntu2) ...
dpkg: error processing package libxcb-render-util0:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Setting up python3-psutil (5.9.0-1build1) ...
Setting up chrome-remote-desktop (106.0.5249.7) ...
Restarting Chrome Remote Desktop hosts (sessions will be unaffected)...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Errors were encountered while processing:
 libxcb-render-util0:amd64
needrestart is being skipped since dpkg has failed
N: Download is performed unsandboxed as root as file '/root/deb-file/chrome-remote-desktop_current_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Try it again, but without sudo

```
apt install ./chrome-remote-desktop_current_amd64.deb
```

Output

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'chrome-remote-desktop' instead of './chrome-remote-desktop_current_amd64.deb'
chrome-remote-desktop is already the newest version (106.0.5249.7).
The following packages were automatically installed and are no longer required:
  dctrl-tools dkms libdouble-conversion3 libmd4c0 libpcre2-16-0 libqt5core5a libqt5dbus5 libqt5network5
  libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-render-util0
Use 'apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0 B/10.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: error processing package libxcb-render-util0:amd64 (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 libxcb-render-util0:amd64
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

## V13-ubuntu-20.04-build-script-v01

```
#!/bin/bash

#####################################
# V13-ubuntu-20.04-build-script-v01 #
#####################################

function run-cmd ()
{
 echo ""
 echo ""
 echo "================================================================="
 echo " About to run : $1"
 echo "-----------------------------------------------------------------"
 read -t 10 -p ""
 $1
 echo ""

}

# update all repostory indexes so they point to the latest packages #
#-------------------------------------------------------------------#
run-cmd "sudo apt-get update"

# upgrade all installed packages to the version shown in the repository indexes #
#-------------------------------------------------------------------------------#
run-cmd "sudo apt-get upgrade -y"

# install one of the most lightweight desktops #
#----------------------------------------------#
run-cmd "sudo apt-get install xfce4 -y"

# non needed #
#------------#
#run-cmd "sudo apt-get install xfce4-goodies -y"

# install the linux package that provides RDP (for windows remote desktop connection) #
#-------------------------------------------------------------------------------------#
run-cmd "sudo apt-get install xrdp -y"

# put a small file in the RDP users directory, letting XRDP know which desktop to start #
#---------------------------------------------------------------------------------------#
run-cmd "echo 'xfce4-session' > /root/.xsession"
# the above command is for presentation only. the nested quotes i needed were causing
# poblems , so i had to hard code the command and run it on the following line
echo "xfce4-session" > /root/.xsession

# install the version of Virtualbox from the repository #
#-------------------------------------------------------#
run-cmd "sudo apt-get install virtualbox -y"

# install the extenionpack as it contains the Virtualbox RDP Server #
#-------------------------------------------------------------------#
run-cmd "sudo apt install virtualbox-ext-pack -y"

# show the current status of the firewall #
#-----------------------------------------#
run-cmd "sudo ufw status numbered"

# allow the SSH port , number 22 , through the firewall #
#-------------------------------------------------------#
run-cmd "sudo ufw allow 22"

# allow the RDP port, number 3389, for the main ubuntu server #
#-------------------------------------------------------------#
run-cmd "sudo ufw allow 3389"


# allow the RDP random port 50001 onwards for the 1st, 2nd, 3rd, 4th etc VirtualBox VM if needed #
#------------------------------------------------------------------------------------------------#
# run-cmd "sudo ufw allow 50001"
# run-cmd "sudo ufw allow 50002"
# run-cmd "sudo ufw allow 50003"
# run-cmd "sudo ufw allow 50004"

# enable the firewall, dont worry about the warning message, we have already allowed SSH #
#----------------------------------------------------------------------------------------#
run-cmd "sudo ufw enable"

# show the current status of the firewall #
#-----------------------------------------#
run-cmd "sudo ufw status numbered"

# install the firefox web browser. Has proven very useful to download .ISO #
# files for Virtualbox, or to browse Google Drive / Dropbox / Onedrive.    #
#--------------------------------------------------------------------------#
run-cmd "sudo apt-get install firefox -y"

# ========= SCRIPT END ============
```

## use remote Desktop connection to that ip

https://remotedesktop.google.com/home

https://remotedesktop.google.com/access

https://support.google.com/chromebook/answer/1649523?hl=en&co=GENIE.Platform%3DDesktop

https://www.androidcentral.com/how-set-chrome-remote-desktop-chromebook

# How to Create an Ubuntu 20.04 VPS with GUI Desktop on Contabo using RDP - Step-by-Step Tutorial

https://www.youtube.com/watch?v=_NnxgAQsJkE&ab_channel=CloudTech

# How to create an Ubuntu 20.04 VPS with GUI on Contabo using RDP - Tutorial

https://www.youtube.com/watch?v=OEK86061KEU&ab_channel=CloudTech
