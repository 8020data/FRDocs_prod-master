<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Harden Ubuntu     ](/Setup/fr0302_Setup-Hardening-Ubuntu.md)
</div><div class="page-next">

[Install App Server - NEXT](/Setup/fr0304_Setup-App-Server-Ubuntu.md)
</div><div style="margin-top:35px">&nbsp;</div>

<!-- ------------------------------------------------------------------------- -->

## 2.3 Install Web Server 0:20 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0303_Setup-Web-Server-Ubuntu.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/931217213539635200" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- On your server you will use the web service, NGINX, which is similar to Apache.
- You will also install, Certbot, which will use the LetsEncrypt stategy for SSL certificates.
- You will create the /webs folder, which will hold you application files.

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
### 2. Install nginx 0:05

#### 1. Install
----

```
apt-get install nginx
```

- Enter Y to continue, if asked

![Install NGINX](./images/fr0303-01_Ubuntu-install-nginx.png "Install NGINX")

#### 2. Check
```
nginx -t
```

![Check NGINX](./images/fr0303-02_Ubuntu-check-nginx.png "Check NGINX")

#### 3. Enable nginx to auto start

```
systemctl enable nginx
```

![Enable NGINX](./images/fr0303-03_Ubuntu-enable-nginx.png "Enable NGINX")

#### 4. Allow http & https through firewall
```
ufw allow 'Nginx Full'
```

![Allow NGINX Ports](./images/fr0303-04_Ubuntu-allow-nginx-ports.png "Allow NGINX Ports")

#### 5. Test the default web site by IP. 

#### 6. Get the server IP from Vultr

![GetVultrIP](./images/fr0302-12_Get-Vultr-IP.png "GetVultrIP")

#### 7. Browse to your server's IP address.

```
http://xxx.xxx.xxx.xxx
```

![Test Web Site](./images/fr0303-05_Ubuntu-test-web-site.png "Test Web Site")

----
### 3. Install Certbot 0:05
----
#### 1. Install  (Certbot is used to create SSL certificates using LetsEncrypt.) This takes several minutes. Be patient.

```
snap install --classic certbot
```

![Install Certbot](./images/fr0303-06_Ubuntu-install-certbot.png "Install Certbot")

----
### 4. Create webs directory 0:05
----
#### 1. Create a directory to hold your applications.

```
mkdir /webs
```

#### 2. Check that /webs directory was created

```
cd /
```
```
ls -ld /webs
```

![Create Webs Directory](./images/fr0303-07_Ubuntu-create-webs-directory.png "Create Webs Directory")


----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have installed a Web server on your Ubuntu server.

  </div>
</div>

----

<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Harden Ubuntu     ](/Setup/fr0302_Setup-Hardening-Ubuntu.md)
</div><div class="page-next">

[Install App Server - NEXT](/Setup/fr0304_Setup-App-Server-Ubuntu.md)
</div>

<!-- ------------------------------------------------------------------------- -->

