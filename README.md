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
# chmod 600 both public and private keys in .ssh

ssh -vT git@github.com
```

## For Remote Desktop, verify that X11Forwarding is set to yes

```java
sudo vi /etc/ssh/ssh_config

# Add/modify following line:

X11Forwarding yes
```

Restart ssh

```java
systemctl restart sshd
```

Likely this is already installed:

To install the full GNOME Desktop, run:

```java
sudo apt install ubuntu-desktop

# start the GNOME desktop

sudo /etc/init.d/gdm3 start
```

Output

```java
Starting gdm3 (via systemctl): gdm3.service.
```

Verify can use GUI

```java
ssh -X username@remotemachine_ip_address

# add debug info
ssh -X -v username@remotemachine_ip_address

xmessage -center hello!

# In case you don't have xmessage, these are alternatives:

# sudo apt install xdg-utils

xdg-open .

xterm

# After logging in, you can try the following commands for opening a X window: xterm, xclock, xcalc, xedit, etc
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

Then go to

https://remotedesktop.google.com/headless

Follow instructions to generate a token that will communicate with Google

Then verify the desktop is visible

https://remotedesktop.google.com/access

## install node, nvm

### Install nvm

```java
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Ensure paths are set up and restart the terminal to cause `source ~/.bashrc`

```java
=> Close and reopen your terminal to start using nvm or run the following to use it now:

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

### Install node 16, 18, 20

```java
nvm install 16
nvm install 18
nvm install 20
nvm use 18
nvm list
```

Output

```java
       v16.20.2
->     v18.19.0
       v20.10.0
default -> 18 (-> v18.19.0)
iojs -> N/A (default)
unstable -> N/A (default)
node -> stable (-> v20.10.0) (default)
stable -> 20.10 (-> v20.10.0) (default)
lts/* -> lts/iron (-> v20.10.0)
lts/argon -> v4.9.1 (-> N/A)
lts/boron -> v6.17.1 (-> N/A)
lts/carbon -> v8.17.0 (-> N/A)
lts/dubnium -> v10.24.1 (-> N/A)
lts/erbium -> v12.22.12 (-> N/A)
lts/fermium -> v14.21.3 (-> N/A)
lts/gallium -> v16.20.2
lts/hydrogen -> v18.19.0
lts/iron -> v20.10.0
```

## Install npm

Should already be installed as part of node

```java
npm --version
```

Output

```java
10.2.5
```

## Install yarn

install globally with `-g`

```java
npm install -g yarn

yarn --version
```

Output

```java
1.22.21
```

## install pyenv and virtualenv

https://github.com/pyenv/pyenv?tab=readme-ov-file#usage

```java
curl https://pyenv.run | bash
```

if needed, run this to make changes to `.bashrc`

```java
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
```

### Install pyenv build dependancies such as C or gcc

https://github.com/pyenv/pyenv/wiki#suggested-build-environment

for Ubuntu / Debian:

```java
sudo apt update; sudo apt install build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev curl \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

### pyenv Usage

### Install additional Python versions

To install additional Python versions, use `pyenv install`

For example, to download and install Python `3.10.4`, run:

```java
pyenv install 3.10.4

# set the global python version to default to

pyenv global 3.10.4
```

Verify it is working by entering the python interactive environment

```java
python
```

Output

```java
Python 3.10.12 (main, Nov 20 2023, 15:14:05) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> quit()
```

## Install virtualenv

```java
pip install pipx

pipx install virtualenv
```

```java
  installed package virtualenv 20.25.0, installed using Python 3.10.4
  These apps are now globally available
    - virtualenv
done! ✨ 🌟 ✨
```

How to use `virtualenv`

```java
virtualenv --help
```

## install java 8

```java
sudo apt update
sudo apt install openjdk-8-jdk
```

Verify installation

```java
java -version
```

Output

```java
openjdk version "1.8.0_392"
OpenJDK Runtime Environment (build 1.8.0_392-8u392-ga-1~22.04-b08)
OpenJDK 64-Bit Server VM (build 25.392-b08, mixed mode)
```

### Set a default Java version (if you have more than one)

https://computingforgeeks.com/how-to-set-default-java-version-on-ubuntu-debian/

```java
sudo update-java-alternatives --list
```

Output

```java
java-1.8.0-openjdk-amd64       1081       /usr/lib/jvm/java-1.8.0-openjdk-amd64
```

If you have multiple Java versions, choose a default via:

```java
sudo update-alternatives --config java
```

### Set JAVA_HOME

in `.bashrc`

```java
export JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::")
```

## rsync hard drive

```java

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

## Change Your SSH Port in Linux

To grand you all the necessary admin rights, always enter the command sudo -i at the beginning of every session:

```
sudo -i
```

This command will grant you the rights of a power user, so you don’t have to write the command sudo at the beginning of every command line. To change your SSH Port, follow the instructions:

Connect to your Contabo server as instructed in chapter 2.2.

Now you have to access and edit sshd_config file. Let’s use the vi text editor in this case:

```
vi /etc/ssh/sshd_config
```

Find the line containing Port 22.

Replace the number with any value from 1024 to 65536 (command “I” in the vi editor). If there is a hashtag symbol next to “Port”, erase it.

Save and exit the sshd_config file (type command “:wq” in the vi editor).

Restart the SSH service using:

```
systemctl restart ssh
```

Don’t forget to adjust your firewall depending on your Linux version. For instance, in case you use Debian or Ubuntu with a default UFW firewall, type:

https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04

```
ufw allow <PORT_NUMBER>/tcp

sudo systemctl ufw status

sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw allow 52222/tcp
sudo ufw deny 22/tcp
sudo ufw enable

sudo ufw status

sudo ufw status verbose

sudo ufw status numbered

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
52222/tcp                  ALLOW IN    Anywhere
22/tcp                     DENY IN     Anywhere
52222/tcp (v6)             ALLOW IN    Anywhere (v6)
22/tcp (v6)                DENY IN     Anywhere (v6)
```

## verify ufw status after reboot

```
sudo systemctl status ufw
```

Output

```
● ufw.service - Uncomplicated firewall
     Loaded: loaded (/lib/systemd/system/ufw.service; enabled; vendor preset: enabled)
     Active: active (exited) since Mon 2023-04-03 23:37:50 CDT; 14h ago
       Docs: man:ufw(8)
    Process: 296 ExecStart=/lib/ufw/ufw-init start quiet (code=exited, status=0/SUCCESS)
   Main PID: 296 (code=exited, status=0/SUCCESS)

Apr 03 23:37:50 vmi1240539.contaboserver.net systemd[1]: Finished Uncomplicated firewall.
```

To view the logs for ufw on a system that has been rebooted, you can use the journalctl command with the -u option to specify the ufw service. For example, to view the ufw logs for the current boot, you can run the following command:

```
sudo journalctl -u ufw.service
```

This will display the ufw logs for the current boot, including any log entries that were created during the previous boot. If you want to view the logs for a specific time range, you can use the --since and --until options. For example, to view the ufw logs for the past 24 hours, you can run the following command:

```
sudo journalctl -u ufw.service --since "24 hours ago"
```

This will display the ufw logs for the past 24 hours, including any log entries that were created during the previous boot. You can adjust the time range as needed to view the logs for a specific period.

## Step 5 — Allowing Other Connections

At this point, you should allow all of the other connections that your server needs to respond to. The connections that you should allow depends on your specific needs. Luckily, you already know how to write rules that allow connections based on a service name or port; we already did this for SSH on port 22. You can also do this for:

- HTTP on port 80, which is what unencrypted web servers use, using sudo ufw allow http or sudo ufw allow 80
- HTTPS on port 443, which is what encrypted web servers use, using sudo ufw allow https or sudo ufw allow 443
