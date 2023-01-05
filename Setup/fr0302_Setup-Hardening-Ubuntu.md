<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Setup-Vultr-Ubuntu](/Setup/fr0301_Setup-Vultr-Ubuntu.md)
</div><div class="page-next">

[Install Web Server - NEXT](/Setup/fr0303_Setup-Web-Server-Ubuntu.md)
</div><div style="margin-top:35px">&nbsp;</div>

<!-- ------------------------------------------------------------------------- -->

## 2.2 Harden Ubuntu 1:35 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0302_Setup-Hardening-Ubuntu.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/931217151241642005" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- When you secure a server on the internet it is called "hardening". 
- In this step you will perform a number of tasks that will make it very difficult for malicious people to harm your server.

<details class="details-style">
    <summary class="summary-style">
More Info: Names, Caps, Picts, Code Copy
    </summary>
    <div class="popup">

- In this tutorial please be careful to use the Exact Spelling and Capitalization. You will be using Windows, Unix and GitBash command prompts. Improper captialization will cause commands to fail. Some examples are: Local_Admin, myProject, repos, remotes and .ssh.

- This documentation was produced in 2021-2022. You will experience differences in some of the pictures due to the changes made over time by the developers of the softwares and web sites that are used.

- We recommend that you copy and paste code snippets from the documentation into your workstation/server. This will reduce the errors caused by hand typing.
Hover over the snippet and click copy, then paste as appropriate.

</div>
</details>
----
### 1. Restart your Vultr VM and Login 0:05
----
#### 1. Open Bitvise and Load profile for Vultr-formR0-root and click Login

![Restart VM](./images/fr0300-01_restart-vm.png "Restart VM")

![Restart VM](./images/fr0300-01_restart-vm1.png "Restart VM")

![Restart VM](./images/fr0300-01_restart-vm2-root.png "Restart VM")

#### 2. Click New terminal console

![Restart VM](./images/fr0301-09_Vultr-New-Profile-Console-root.png "Restart VM")

#### 3. Enter:

```
reboot
```

![Restart VM](./images/fr0300-01_restart-vm4.png "Restart VM")

- Close the Terminal window and wait for Bitvise to automatically login

#### 4. From Bitvise click New terminal console

![Restart VM](./images/fr0301-09_Vultr-New-Profile-Console-root.png "Restart VM")

<div class="notice-tip">
  <div class="notice-tip-header">
    Note: To paste commands into the terminal, right-click at the terminal prompt 
  </div>  
</div>

----
### 2. Create a new sudo user 0:05
----

#### 1. Create a new user alias with root privileges. This user will login remotely.

```
useradd -ou 0 -g 0 -d /root -s /bin/bash -G sudo nimda
```

![New User](./images/fr0302-02_Ubuntu-New-User.png "New User")

- Tip: To clear the console at the console prompt enter: clear

#### 2. Add the nimda password: FormR!1234
 and retype it

```
passwd nimda
```

```
FormR!1234

```

![New User](./images/fr0302-02_Ubuntu-New-User1.png "New User")


#### 3. Check to see if nimda is in sudo group

```
grep '^sudo' /etc/group
```

![New User](./images/fr0302-02_Ubuntu-New-User2.png "New User")

#### 4. Check user info

```
cat /etc/passwd
```

![New User](./images/fr0302-02_Ubuntu-New-User3.png "New User")


![Check User Info](./images/fr0302-03_Ubuntu-Check-User-Info.png "Check User Info")

----
### 3. Update and upgrade server 0:05
----
#### 1. Update

```
apt-get update && apt-get upgrade
```

(Enter Y to continue, if asked)


![Update and Upgrade](./images/fr0302-04_Ubuntu-Update-Upgrade.png "Update and Upgrade")

----
### 4. Install and Configure unattended-updates 0:10
----
#### 1. Install

```
apt-get install unattended-upgrades
```

(Enter Y to continue, if asked)

![Install Unattended Upgrades](./images/fr0302-05_Ubuntu-Install-Unattended-Upgrades.png "Install Unattended Upgrades")

- Restart Unattended Upgades

```
systemctl restart unattended-upgrades
```

![Install Unattended Upgrades](./images/fr0302-05_Ubuntu-Install-Unattended-Upgrades-1.png "Install Unattended Upgrades")


#### 2. Check installation
```
systemctl status unattended-upgrades
```

![Check Unattended Upgrades](./images/fr0302-06_Ubuntu-Check-Unattended-Upgrades.png "Check Unattended Upgrades")

<div class="notice-tip">
  <div class="notice-tip-header">
    Note: If you get a "lines ... (END)" message, press ctrl-c then Enter to continue.
  </div>  
</div>


![Check Unattended Upgrades](./images/fr0302-06_Ubuntu-Check-Unattended-Upgrades1.png "Check Unattended Upgrades")

#### 3. Using the nano editor, modify apt.conf.d/50unattended-upgrades

```
nano /etc/apt/apt.conf.d/50unattended-upgrades
```

#### 4. Uncomment the “updates” line by deleting the two slashes at the beginning of it:

```
"${distro_id}:${distro_codename}-updates";
```

![Modify apt.conf.d](./images/fr0302-07_Ubuntu-Modify-apt-conf-d.png "Modify apt.conf.d")

#### 5. Uncomment and modify: (Note: Use your down arrow to find these items. They are near the bottom of the file.)

```
Unattended-Upgrade::Remove-Unused-Kernel-Packages "true";
```
```
Unattended-Upgrade::Remove-Unused-Dependencies "true";
```
```
Unattended-Upgrade::Automatic-Reboot "true";
```
```
Unattended-Upgrade::Automatic-Reboot-Time "02:30";
```

![Modify apt.conf.d-2](./images/fr0302-08_Ubuntu-Modify-apt-conf-d-2.png "Modify apt.conf.d-2")

#### 6. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 7. Using nano, enable Automatic Updates

```
nano /etc/apt/apt.conf.d/20auto-upgrades
```

#### 8. Add these lines:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

![Modify apt.conf.d-3](./images/fr0302-09_Ubuntu-Modify-apt-conf-d-3.png "Modify apt.conf.d-3")

#### 9. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 10. Check if Unattended Upgrades works

```
unattended-upgrades --dry-run --debug
```

![Check Unattended Upgrades](./images/fr0302-10_Ubuntu-Check-Unattended-Upgrades.png "Check Unattended Upgrades")

- For your information only... here's a sample Reboot Warning that will occur on the console at 2:30am

![Sample Console Warning](./images/fr0302-10_Ubuntu-Sample-Console-Warning.png "Sample Console Warning")

#### 11. Reboot the server

- From the console prompt enter:

```
reboot 
```

- Close the terminal window and Bitvise will automatically reconnect

- Open a New terminal window

----
### 5. Secure Shared Memory 0:05
----
#### 1. Edit  fstab

```
nano /etc/fstab
```

#### 2. Add the following line to the bottom of that file:

```
tmpfs /run/shm tmpfs defaults,noexec,nosuid 0 0  
``` 

![Secure Shared Memory](./images/fr0302-11_Ubuntu-secure-shared-memory.png "Secure Shared Memory")

#### 3. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 4. Reboot the server

- From the console prompt enter:

```
reboot 
```

- Close the terminal window and Bitvise will automatically reconnect

- Open a New terminal window

----
### 6. Enable SSH Login for Specific Users Only 0:10
----
#### 1. Get your IP address at:

```
https://whatismyipaddress.com/
``` 

![Get-IP](./images/fr0302-12_Ubuntu-Get-IP.png "Get-IP")
 
#### 2. Edit sshd_config

```
nano /etc/ssh/sshd_config
```

#### 3. At the bottom of the file, add the line: (Use your own workstation's IP address. 


```
AllowUsers nimda@xxx.xxx.xxx.xxx
```

![SSH-AllowUsers](./images/fr0302-12_Ubuntu-ssh-allowusers.png "SSH-AllowUsers")

#### 4. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 5. Restart sshd with this command:

```
systemctl restart sshd
```

#### - Test local access to your Vultr formR VM. 

#### 6. Get the VM IP address from your Vultr-formR0 VM i.e 45.76.252.191

![GetVultrIP](./images/fr0302-12_Get-Vultr-IP.png "GetVultrIP")


#### 7. Open the Windows command prompt on your Developer Workstation

#### 8. Paste the following:

```
ssh nimda@<your VM IP address>
```
- If you are asked to continue enter: yes 

![SSH-AllowUsers](./images/fr0302-12_Ubuntu-ssh-allowusers2.png "SSH-AllowUsers")

#### 9. Enter the password: FormR!1234


![SSH-AllowUsers](./images/fr0302-12_Ubuntu-ssh-allowusers1.png "SSH-AllowUsers")

#### 10. Logout of Bitvise and then change the Username and Password and Login

Username:
```
nimda
```

Password:

```
 FormR!1234
```

![SSH-AllowUsers](./images/fr0302-12_Ubuntu-ssh-allowusers4.png "SSH-AllowUsers")

#### 11. Save the Profile

![SSH-AllowUsers](./images/fr0302-12_Ubuntu-ssh-allowusers3.png "SSH-AllowUsers")

- If asked, select"Any account on this computer"

![SSH-AllowUsers](./images/SavingSensitiveInfo.png "SSH-AllowUsers")

----
### 7. Include a Security Login Banner 0:05
----
#### 1. Create a banner file

```
nano /etc/issue.net
```

#### 2. - Remove the "Ubuntu..." line and add the following warning message

```
************************************************************************

 Warning!!! This server is dedicated for formR purposes.
     
 Malicious users will be subject to civil and/or criminal prosecution.
     
************************************************************************
```

#### 3. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

![SSH-Banner Issue.net](./images/fr0302-13_Ubuntu-ssh-banner-issue-net.png "SSH-Banner Issue.net")

#### 4. Disable the banner message from Message Of The Day (motd).

```
nano /etc/pam.d/sshd
```

#### 5. Comment out the following two lines (adding a # to the beginning of each line):

```
#session optional pam_motd.so motd=run/motd.dynamic
#session optional pam_motd.so noupdate
```

![SSH-Comment Out](./images/fr0302-14_Ubuntu-ssh-comment-out-pam-d.png "SSH-Comment Out")
     
#### 6. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 7. Edit sshd_config

```
nano /etc/ssh/sshd_config
```

#### 8. Replace

- #Banner none   with:

```
Banner  /etc/issue.net
```
- Be sure to Remove the #

![SSH-Banner Config](./images/fr0302-15_Ubuntu-ssh-banner-config.png "SSH-Banner Config")

#### 9. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 10. Restart the sshd service
     
```
systemctl restart sshd
```

#### 11. When someone logs into your server using SSH, they see your newly added banner warning them of any consequences of further action. 

----
### 8. Install Fail2ban 0:10
----
#### 1. Install (Enter Y or y to continue, if asked.)

```
apt-get install fail2ban
```

- Enter Y to continue, if asked

![Install Fail2Ban](./images/fr0302-16_Ubuntu-install-fail2ban.png "Install Fail2Ban")

#### 2. Configure Fail2Ban

```     
nano /etc/fail2ban/jail.local
```

#### 3. In this new file, add the following contents:

```
[sshd]
enabled = true
port = 22
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
```

![SSH-jail-local](./images/fr0302-17_Ubuntu-ssh-jail-local.png "SSH-jail-local")

#### 4. This configuration enables the jail, sets the SSH port to be monitored to 22, uses the sshd filter, sets the max login tries, and sets the log file to be monitored.

#### 5. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 6. Restart fail2ban with the command:

```
systemctl restart fail2ban
```

#### 7. Attempting to login to the server and failing three times, access is blocked. 


<div class="notice-tip">
  <div class="notice-tip-header">
    Special Fail2ban Note: To flush all bans enter the following 2 times from the formR0 Ubuntu console:
  </div>  
</div>

```
fail2ban-client unban --all
```

----
### 9. Enable firewall 0:05
----
#### 1. Allow ssh connections through firewall

```
ufw allow OpenSSH
```

#### 2. Enable firewall

```
ufw --force enable
```

#### 3. Check firewall status

```
ufw status
```

![Enable Firewall](./images/fr0302-18_Ubuntu-enable-firewall.png "Enable Firewall")

----
### 10. Set the server time zone 0:05
----
#### 1. Enter into the server console:

```
timedatectl set-timezone America/New_York 
```

#### 2. Check TimeZone

```
timedatectl
```

![Set Time Zone](./images/fr0302-19_Ubuntu-set-timezone.png "Set Time Zone")

----
### 11. Install Rootkit Hunter and perform check 0:05
----

#### 1. Enter into the server console:

```
apt-get install rkhunter -y
```

![Install Lynis](./images/fr0302-19_Ubuntu-install-rkhunter.png "Install rkhunter")

#### 2. Check rkhunter version

```
rkhunter --version
```

![Install rkhunter](./images/fr0302-19_Ubuntu-install-rkhunter1.png "Install rkhunter")

#### 3. Audit your system

```
rkhunter --check
```

![Install rkhunter](./images/fr0302-19_Ubuntu-install-rkhunter2.png "Install rkhunter")

- Press Enter for each of 4 pauses

![Install rkhunter](./images/fr0302-19_Ubuntu-install-rkhunter3.png "Install rkhunter")

- Summary

![Install rkhunter](./images/fr0302-19_Ubuntu-install-rkhunter4.png "Install rkhunter")

----
### 12. Clone Lynis and perform audit 0:10
----

#### 1. Enter into the server console:

```
cd /etc
```
```
git clone https://github.com/CISOfy/lynis
```

![Install Lynis](./images/fr0302-19_Ubuntu-install-lynis.png "Install Lynis")

#### 2. Check Lynis version

```
cd /etc/lynis
```
```
./lynis --version
```

![Install Lynis](./images/fr0302-19_Ubuntu-install-lynis1.png "Install Lynis")

#### 3. Audit your system

```
./lynis audit system --quick
```

![Install Lynis](./images/fr0302-19_Ubuntu-install-lynis2.png "Install Lynis")

![Install Lynis](./images/fr0302-19_Ubuntu-install-lynis3.png "Install Lynis")

#### 4. Study the suggestions

![Install Lynis](./images/fr0302-19_Ubuntu-install-lynis4.png "Install Lynis")


<div class="notice-tip">
  <div class="notice-tip-header">
    Note: Issues reported by both rkhunter and lynis require more attention than formR can offer.
  </div>  
</div>


- For more information: 

<br/>

[How To Use RKHunter to Guard Against Rootkits on an Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps)

<br/>

[Lynis Security Tool for Audit and Hardening](https://www.geeksforgeeks.org/lynis-security-tool-for-audit-and-hardening-linux-systems/)


----
### 13. Test local access after Hardening 0:05
----
#### 1. Test local access to your Vultr formR VM. 

#### 2. Get the VM IP address from your Vultr-formR0 VM

![GetVultrIP](./images/fr0302-12_Get-Vultr-IP.png "GetVultrIP")

#### 3. Open the Windows command prompt on your Developer Workstation

#### 4. Paste the following:

```
ssh nimda@<your Vultr IP address>
```

![SSH-AllowUsers](./images/fr0302-12_Ubuntu-ssh-allowusers1.png "SSH-AllowUsers")

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have hardened your Ubuntu server on Vultr.
  </div>
</div>

----

<div class="notice-tip">
  <div class="notice-tip-header">
    Note: This setup protects your server from the most common vulnerabilites. Continue to add protection as threats are discovered.
  </div>  
</div>

----


<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Setup-Vultr-Ubuntu](/Setup/fr0301_Setup-Vultr-Ubuntu.md)
</div><div class="page-next">

[Install Web Server - NEXT](/Setup/fr0303_Setup-Web-Server-Ubuntu.md)
</div>

<!-- ------------------------------------------------------------------------- -->

