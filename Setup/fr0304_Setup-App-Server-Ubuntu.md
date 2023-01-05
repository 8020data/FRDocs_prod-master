<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Install Web Server     ](/Setup/fr0303_Setup-Web-Server-Ubuntu.md)
</div><div class="page-next">

[Install Data Server - NEXT](/Setup/fr0305_Setup-Data-Server-Ubuntu.md)
</div><div style="margin-top:35px">&nbsp;</div>

<!-- ------------------------------------------------------------------------- -->


## 2.4 Install App Server 0:25 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0304_Setup-App-Server-Ubuntu.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/931218086256857118" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- You will be using NodeJS to run your applications.
- nvs (node versuion selector) will help you manazge Nodejs
- pm2 will be used for running your simpleApp.
- express will be used for ?????????

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

![Restart VM](./images/fr0300-01_restart-vm2.png "Restart VM")

#### 2. Click New terminal console

![Restart VM](./images/fr0301-09_Vultr-New-Profile-Console.png "Restart VM")

#### 3. Enter:

```
reboot
```

![Restart VM](./images/fr0300-01_restart-vm4.png "Restart VM")

- Close the Terminal window and wait for Bitvise to automatically login

#### 4. From Bitvise click New terminal console

![Restart VM](./images/fr0301-09_Vultr-New-Profile-Console.png "Restart VM")

<div class="notice-tip">
  <div class="notice-tip-header">
    Note: To paste commands into the terminal, right-click at the terminal prompt
  </div>  
</div>  

----
### 2. Install nvs (node version selector) 0:05
----

#### 1. Install 

- Clone nvs

```
git clone https://github.com/jasongin/nvs .nvs
```

![Install NodeJS](./images/fr0304-01_Ubuntu-install-nodejs1.png "Install NodeJS")

- Install nvs

```
source .nvs/nvs.sh install
```

![Install NodeJS](./images/fr0304-01_Ubuntu-install-nodejs2.png "Install NodeJS")


----
### 3. Install nodejs and npm Node package Manager 0:05
----

#### 1. Add and use node version 16 latest version 

```
nvs add 16
```
```
nvs use 16
```
```
nvs link
```

- nvs link sets version 16 as the default

![Install NodeJS](./images/fr0304-01_Ubuntu-install-nodejs3.png "Install NodeJS")

#### 2. Check

```
node --version
```
```
npm --version
```

![Check NodeJS](./images/fr0304-01_Ubuntu-install-nodejs4.png "Check NodeJS")

----
### 4. Install  pm2 0:05
----

#### 1. Install
```
npm install -g pm2
```

![Install PM2](./images/fr0304-05_Ubuntu-install-pm2.png "Install PM2")

#### 2. Check
```
ps -aux | egrep 'pm2'
```

![Check PM2](./images/fr0304-06_Ubuntu-check-pm2.png "Check PM2")

#### 3. Configure pm2 to start automatically on system startup
```
pm2 startup systemd
```

![Autostart PM2](./images/fr0304-07_Ubuntu-autostart-pm2.png "Autostart PM2")

----
### 5. Install Express 0:05
----

#### 1. Install 

```
cd /webs
```
```
npm init
```

- Select all defaults by pressing enter,
then enter Y for "Is this ok?"


![npm init](./images/fr0304-10_Ubuntu-npm-init.png "npm init")

```
npm install express
```

![Install Express](./images/fr0304-11_Ubuntu-install-express.png "Install Express")

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have installed an Application server on your Ubuntu server.
  </div>
</div>

----

<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Install Web Server     ](/Setup/fr0303_Setup-Web-Server-Ubuntu.md)
</div><div class="page-next">

[Install Data Server - NEXT](/Setup/fr0305_Setup-Data-Server-Ubuntu.md)
</div>

<!-- ------------------------------------------------------------------------- -->

