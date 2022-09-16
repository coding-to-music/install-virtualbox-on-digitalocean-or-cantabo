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

# Install gh GitHub CLI

https://cli.github.com

https://github.com/cli/cli

https://github.com/cli/cli/blob/trunk/docs/install_linux.md

```
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y
```

### login to GitHub:

```
gh auth login

# verify

gh auth status
```

### verify can connect to GitHub:

chmod 600 both public and private keys in .ssh

```
ssh -vT git@github.com
```

## Install Chrome Remote Desktop (Ubuntu 20.04) on Google Cloud 2022

https://www.youtube.com/watch?v=2n4kwxUlX48&ab_channel=ChrisCheng

### install Chrome Remote Desktop

https://remotedesktop.google.com/headless

Use console to connect via ssh to the droplet

```
wget https://dl.google.com/linux/direct/chrome-remote-desktop_current_amd64.deb
```

```
sudo apt install ./chrome-remote-desktop_current_amd64.deb
```


### Set up another computer

https://remotedesktop.google.com/headless

You're nearly finished! Run the following command on the remote computer to complete the setup process. Please note that this command can only be used to set up one computer; click Start over if you have more computers to set up.

```
DISPLAY= /opt/google/chrome-remote-desktop/start-host --code="4/big-long-string" --redirect-url="https://remotedesktop.google.com/_/oauthredirect" --name=$(hostname)
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

# How to create an Ubuntu 20.04 VPS with GUI on Contabo using RDP - Tutorial - by Cloud Tech

https://www.youtube.com/watch?v=OEK86061KEU&ab_channel=CloudTech

# How to Create an Ubuntu 20.04 VPS with GUI Desktop on Contabo using RDP - Step-by-Step Tutorial

https://www.youtube.com/watch?v=_NnxgAQsJkE&ab_channel=CloudTech

Cloud Tech
2.54K subscribers

I show you step-by-step how you can create a very secure Ubuntu 20.04 VPS with Desktop , from scratch. We are then going to access it by the windows 10 remote desktop connection via RDP by installing XRDP . And finally, how to link it to Google Drive Online Account

Contabo Link : https://cloudtechlinks.com/V30-Contab...

## My Other Videos mentioned in this Video

FREE Server 2019 : https://www.youtube.com/watch?v=so72p...
FREE Server 2022 : https://www.youtube.com/watch?v=o4vwU...

0.00 The Video Purpose
2.52 The Ubuntu 20.04 VPS purchase Process
8.15 Build Ubuntu 20.04 with GUI Desktop via Putty SSH Client
13.30 Run Remote Desktop Connection and Basic Configuration
16.20 Enable all Online Accounts including Google Drive on Ubuntu 20.04
22.10 YouTube End Cards

## Build Ubuntu 20.04 with Desktop via Putty SSH Client Commands

Follow these steps

1.  adduser xrdpuser (password : e.g paste se7ye8pc5hs0 )
2.  usermod -aG sudo,adm xrdpuser && su xrdpuser
3.  sudo apt-get update && sudo apt-get upgrade -y
4.  sudo apt-get install ubuntu-desktop mmv htop stacer gnome-software xrdp -y
5.  sudo rm /usr/share/polkit-1/actions/org.freedesktop.color.policy

sudo ufw reset

Omit this 6. sudo sed -i 's/3389/53579/g' /etc/xrdp/xrdp.ini
Omit this 8. sudo ufw allow 53572 && sudo ufw allow 53579 && sudo ufw enable && sudo ufw status numbered
Omit Original - 11. sudo ufw allow 53572 && sudo ufw allow 3389 && sudo ufw enable && sudo ufw status numbered

7.  sudo sed -i 's/#Port 22/Port 53572/g' /etc/ssh/sshd_config
8.  sudo ufw allow 53572 && sudo ufw allow 3389 && sudo ufw enable && sudo ufw status numbered
9.  sudo reboot

reconnect via SSH port 53572 using xrdpuser

      10) sudo passwd --delete --lock root
      11) sudo reboot

Connect via The Remote Dektop Connection (RDP) port 53579

Configuration 1) ASAP - On desktop, disable all lock screen settings - on privacy options

How to link Google Drive 1) On the Desktop, In the Terminal Application :
a) cd /etc/netplan && sudo mmv '\*.yaml' '#1.moved-for-youtube' && ls -la
b) sudo wget ht tp://files.cloudtech.video/V30-cloudtech.yaml --output-document=v30-cloudtech.yaml && ls -la && cat v30-cloudtech.yaml
(please remove the spaces in https)
c) sudo reboot

i) Show how to get a free Google Account
ii) Connect to Google Drive Online account :ycloudtech@gmail.com
cloudtech11Q

d) cd /etc/netplan && sudo rm v30-cloudtech.yaml && sudo mmv '\*.moved-for-youtube' '#1.yaml' && ls -la
e) sudo reboot

- Connecting via RDP from MacOS : https://www.youtube.com/watch?v=x7TCvLuWlF0&ab_channel=Parried
- Connecting via RDP from Chromebook : https://www.youtube.com/watch?v=4PUraznLMMs&ab_channel=CloudSolvedIT.com
- Connecting via RDP from Linux : https://opensource.com/article/18/6/linux-remote-desktop

how to create a google account (also knon as a gmail account) :
https://www.youtube.com/watch?v=lcvWhAgS028&t=0s&ab_channel=PinoyTechTips

Video describing how to create a brand new Google Drive Account (if needed) :
https://www.youtube.com/watch?v=1uJ1TxklS2Y&t=0s&ab_channel=HowtoGoogle

# View running processes and thier memory usage

```
echo "USER                 RSS      PROCS" ; echo "-------------------- -------- -----" ; ps hax -o rss,user | awk '{rss[$2]+=$1;procs[$2]+=1;}END{for(user in rss) printf "%-20s %8.0f %5.0f\n", user, rss[user]/1024, procs[user];}' | sort -rnk2
```

Contabo

```
USER                 RSS      PROCS
-------------------- -------- -----
xrdpuser                 2034    80
root                      222   112
colord                     14     1
systemd-resolve            13     1
whoopsie                   12     1
systemd-network             7     1
systemd-timesync            6     1
messagebus                  6     1
syslog                      4     1
avahi                       4     2
rtkit                       3     1
xrdp                        2     1
kernoops                    1     2
```

DigitalOcean

```
USER                 RSS      PROCS
-------------------- -------- -----
tmc                      1920    75
gdm                       745    46
root                      661   145
telegraf                   98     1
influxdb                   96     1
nobody                     91     2
472                        86     1
do-agent                   17     1
whoopsie                   15     1
colord                     14     1
systemd-resolve            12     1
systemd-network             8     1
systemd-timesync            6     1
messagebus                  6     1
syslog                      5     1
avahi                       4     2
rtkit                       3     1
daemon                      2     1
xrdp                        1     1
kernoops                    1     2
```

## Set GNOME desktop appearance theme to Dark

https://www.reddit.com/r/Ubuntu/comments/ued44y/2204_vanilla_gnome_no_appearance_setting_tab/

Try running this in a terminal:

```
XDG_CURRENT_DESKTOP=ubuntu:GNOME gnome-control-center
```
