
<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Install Data Server](/Setup/fr0305_Setup-Data-Server-Ubuntu.md)
</div><div class="page-next">

[My HTML Custom App - NEXT](/formR/fr020100_My-HTML-Custom.md)
</div>
<div style="margin-top:35px">&nbsp;</div>
<!-- ------------------------------------------------------------------------- -->

## 2.6 Run Website SSL 1:35 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0306_Setup-Website-SSL-Ubuntu.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/931218167236276224" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- In this step you will:
    1. Configue publickey access from Bitvice to your server
    2. Clone SimpleApp to your server
    3. Configure your server to run the app
    4. Obtain a Domain Name and update your DNS record
    5. Personalize your app
    6. Add an SSL certificate
    7. Clean up protocols
    8. Test your new website for SSL security

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

2. Click New terminal console

![Restart VM](./images/fr0301-09_Vultr-New-Profile-Console.png "Restart VM")

#### 3. Enter:

```
reboot
```
![Restart VM](./images/fr0300-01_restart-vm4.png "Restart VM")

- Close the Terminal window and wait for Bitvise to automatically login

----
### 2. Configure Login via Public Key (SSH keys are more secure than passwords) 0:15
----
#### 1. In Bitvise click New SFTP window icon

![BitVise New SFTP window](./images/fr0306-05_Ubuntu-Bitvise-New-SFTP-window.png "BitVise New SFTP window")

![BitVise New SFTP window2](./images/fr0306-05_Ubuntu-Bitvise-New-SFTP-window2.png "BitVise New SFTP window2")

#### 2. Click in Remote files pane (right) and enter: /root

#### 3. Right click in blank space and click Create Folder, then enter: .ssh

![BitVise Create SSH Folder](./images/fr0306-05_Ubuntu-Bitvise-Create-SSH-Folder.png "BitVise Create SSH Folder")

![BitVise Create SSH Folder2](./images/fr0306-05_Ubuntu-Bitvise-Create-SSH-Folder2.png "BitVise Create SSH Folder2")

#### 4. navigate to folder /root/.ssh and create file: authorized_keys

![BitVise Create File authorized_keys](./images/fr0306-05_Ubuntu-Bitvise-Create-File-authorized_keys.png "BitVise Create File authorized_keys")

![BitVise Create File authorized_keys2](./images/fr0306-05_Ubuntu-Bitvise-Create-File-authorized_keys2.png "BitVise Create File authorized_keys2") 

#### 5. In Local files panes (left)
#### 6. Navigate to C:/users/Local_Admin/.ssh and edit the public key (.pub) file for Vultr_formR0_nimda
#### 7. Right click and select Edit


<div class="notice-tip">
  <div class="notice-tip-header">
    Note: You may need to expand the name column to see the .pub extension.
  </div>  
</div>

![BitVise Copy public key](./images/fr0306-05_Ubuntu-Bitvise-Copy-public-key.png "BitVise Copy public key") 

#### 8. Copy the one line of text. e.g.
    ssh-rsa AAAAB3NzaC1yc2...brucetroutman_v210511

![BitVise Copy public key2](./images/fr0306-05_Ubuntu-Bitvise-Copy-public-key2.png "BitVise Copy public key2")  


#### 9. In the Remote Files pane (right)
#### 10. Edit the file /root/.ssh/authorized_keys

![BitVise Edit authorized_keys](./images/fr0306-05_Ubuntu-Bitvise-Edit-authorized_keys.png "BitVise Edit authorized_keys") 

#### 11. Paste the public key text and Save

![BitVise Paste public key](./images/fr0306-05_Ubuntu-Bitvise-Paste-public-key.png "BitVise Paste public key")


#### 12. close SFTP window

#### 13. From the Profile window
#### 14. Logout 
#### 15. Change Authentication, Initial method from 'password' to 'public key' and 
#### 16. Click the Client Key Manager link in the middle of the form, then 
#### 17. Click Import

![BitVise Client Key Manager](./images/fr0306-05_Ubuntu-Bitvise-Client-Key-Manager.png "BitVise Client Key Manager")

![BitVise Client Key Manager2](./images/fr0306-05_Ubuntu-Bitvise-Client-Key-Manager2.png "BitVise Client Key Manager2")

#### 18. Navigate to Local-Admin/.ssh folder
#### 19. Select 'All files' in the Bitvise Keypair drop down then 
#### 20. Select the Private key file that matched the previously used Public key then 
#### 21. Click Open
#### 22. Click Import in the Import Client Key window

![BitVise Select Private Key](./images/fr0306-05_Ubuntu-Bitvise-Select-Private-Key.png "BitVise Select Private Key")

#### 23. Click Import in the Import Client Key window

![BitVise Select Private Key2](./images/fr0306-05_Ubuntu-Bitvise-Select-Private-Key2.png "BitVise Select Private Key2")

#### 24. Click to close Client Key Manager

![BitVise Select Private Key3](./images/fr0306-05_Ubuntu-Bitvise-Select-Private-Key3.png "BitVise Select Private Key3")

#### 25. Select the just imported key (Profile 1) from the Client key drop down and 
#### 26. Click Login (You will be logged in via public key)

![BitVise Select Client Key](./images/fr0306-05_Ubuntu-Bitvise-Select-Client-Key.png "BitVise Select Client Key")

#### IMPORTANT -- Click Save Profile !!!
</br>

![BitVise Save Profile](./images/fr0306-05_Ubuntu-Bitvise-Save-Profile.png "BitVise Save Profile")

- Select - Any account on this computer - and click OK

![BitVise Save Profile2](./images/fr0306-04_Ubuntu-Bitvise-Save-Profile2.png "BitVise Save Profile2")

#### 27. Configure ssh key Access to your Vultr server

- In Windows Explorer navigate to and  open the file 'config' with notepad

```
C:\Users\Local_Admin\.ssh
```

![ssh-key-to-vultr](./images/fr0306-06_Ubuntu-ssh-key-to-vultr.png "ssh-key-to-vultr")

- then paste in the following:

```
Host vultr-formR0-nimda
    HostName       <paste your formR0 server IP address here>
    IdentityFile   C:/Users/Local_Admin/.ssh/<paste your key here>
    User           nimda
    ServerAliveInterval 60
    ServerAliveCountMax 10
```

- then change the Hostname to the IP address of your Vultr server
- and change the IdentityFile to your private key for vultr-form0-nimda.
- and save the file

![ssh-key-to-vultr](./images/fr0306-06_Ubuntu-ssh-key-to-vultr1.jpg "ssh-key-to-vultr")

#### 28. Login to your Vultr server using your private key

- From the Windows Command prompt enter:

```
ssh vultr-formR0-nimda
```

![ssh-key-to-vultr](./images/fr0306-06_Ubuntu-ssh-key-to-vultr2.png "ssh-key-to-vultr")


----
### 3. Using Bitvise New Terminal console delete nginx default files  0:05
----
#### 1. Open New Terminal console

![BitVise New Terminal](./images/fr0306-06_Ubuntu-Bitvise-new-terminal.png "BitVise New Terminal")

```
unlink /etc/nginx/sites-enabled/default
```

![BitVise Unlink nginx default](./images/fr0306-06_Ubuntu-Bitvise-Unlink-nginx-default.png "BitVise Unlink nginx default")

----
### 4. Using Bitvise New Terminal console Clone simpleApp using git 0:05
----

#### 1. Open New Terminal console

```
cd /webs 
```
```
git clone https://github.com/8020Data/simpleApp.```
```
```
git simpleApp
```

-  Confim clone

```
cd simpleApp
```
```
ls -l
```

![BitVise Clone simpleApp](./images/fr0306-07_Ubuntu-Bitvise-Clone-simpleApp.png "BitVise Clone simpleApp")


#### 2. Open port 5000 through the firewall

```
ufw allow 5000
```
```
ufw status
```

![BitVise Clone simpleApp](./images/fr0306-07_Ubuntu-Bitvise-Clone-simpleApp1.png "BitVise Clone simpleApp")

#### 3. Install and start app.js on the server

```
npm install
```

![BitVise Run simpleApp](./images/fr0306-07_Ubuntu-Bitvise-Run-simpleApp.png "BitVise Run simpleApp")

```
node app.js
```

![BitVise Run simpleApp](./images/fr0306-07_Ubuntu-Bitvise-Run-simpleApp1.png "BitVise Run simpleApp")

#### 4. Use your local browser to test your server

- Get your IP address from the Bitvise console

![BitVise Browse simpleApp0](./images/fr0306-07_Ubuntu-Bitvise-Browse-simpleApp0.png "BitVise Browse simpleApp0")

- Browse to:

- (your server ip address here):5000

![BitVise Browse simpleApp](./images/fr0306-07_Ubuntu-Bitvise-Browse-simpleApp.png "BitVise Browse simpleApp")

----
### 5. Setup pm2 to run website automatically 0:05
----
#### 1. Go to the Bitvise New terminal console
#### 2. Navigate to 

```
cd /webs/simpleApp
```

#### 3. Start app.js

```
pm2 start app.js 
```

![BitVise PM2 start](./images/fr0306-08_Ubuntu-Bitvise-PM2-start.png "BitVise PM2 start")

#### 4. Allow pm2 to start on boot up

```
pm2 startup systemd
```

![BitVise PM2 startup](./images/fr0306-08_Ubuntu-Bitvise-PM2-startup.png "BitVise PM2 startup")

#### 5. Save pm2 configuration, then Reboot

```
pm2 save --force
```
```
reboot
```

![BitVise PM2 save](./images/fr0306-08_Ubuntu-Bitvise-PM2-save.png "BitVise PM2 save")

#### 6. Wait a few minutes for server to reboot then test from local browser, 

```
<your server ip address here>:5000
```

![BitVise Browse simpleApp](./images/fr0306-07_Ubuntu-Bitvise-Browse-simpleApp.png "BitVise Browse simpleApp")

----
### 6. Setup nginx proxy 0:05
----

#### 1. Go to the Bitvise New terminal console

- Copy new folder and files into the nginx folder

```
cp -r /webs/simpleApp/etc/nginx/* /etc/nginx/
```
![BitVise nginx conf file](./images/fr0306-08_Ubuntu-Bitvise-nginx-conf-file.png "BitVise nginx conf file")

#### 2. Create symbolic link to /etc/nginx/sites-enabled

```
cd /etc/nginx/sites-enabled
```
```
ln -s ../sites-available/formR-xxx-00.com_all-apps.conf
```

![BitVise nginx conf file](./images/fr0306-08_Ubuntu-Bitvise-nginx-conf-file1.png "BitVise nginx conf file")

#### 3. Test and Reload nginx
```
nginx -t
```

```
systemctl reload nginx
```

![BitVise nginx reload](./images/fr0306-08_Ubuntu-Bitvise-nginx-reload.png "BitVise nginx reload")

----
### 7. Create a domain for public access to your server 0:15
----

<div class="notice-tip">
  <div class="notice-tip-header">
Note:

To install a Letsencrypt SSL certificate you will need a Domain Name. Our example creates a domain at GoDaddy.com.

There are many domain providers. You can expect to pay about $19/yr. Often there are sales promotions. Also all of them offer many extra services. --- In our formR example we decline all extra services from the domain provider. 

The GoDaddy web site changes frequently, so the screen shots below may not match. The steps are repeatable. Contact GoDaddy support for more assistance.

  </div>  
</div>

----
#### 1. Create a new Domain Name e.g. formR-cbt-00.com at GoDaddy.com. (cbt = my initials. Use yours or something else that is unique)

#### 2. Browse to

```
godaddy.com 
```

#### 3. Enter domain name

```
formR-<your initials>-00.com
```
e.g. formR-cbt-00.com


![Create Domain](./images/fr0306-09_Ubuntu-create-domain.png "Create Domain")

![Create Domain1](./images/fr0306-09_Ubuntu-create-domain1.png "Create Domain1")

#### 4. Follow the instructions to use or create your account and place your order

![Create Domain2](./images/fr0306-09_Ubuntu-create-domain2.png "Create Domain2")

![Create Domain3](./images/fr0306-09_Ubuntu-create-domain3.png "Create Domain3") 

![Create Domain3](./images/fr0306-09_Ubuntu-create-domain4.png "Create Domain3") 

----
### 8. Update your DNS record to point YourURL to your server IP address. 0:10
----
#### 1. Login to your GoDaddy.com account
#### 2. Click Your Account
#### 3. Click My Products
#### 4. Click YourURL e.g. formR-cbt-00.com

![BitVise Point DNS](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS.png "BitVise Point DNS")

#### 5. Click DNS dropdown
#### 6. Select Manage Zones

![BitVise Point DNS1](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS1.png "BitVise Point DNS1")

#### 7. Enter Your domain e.g. formR-cbt-00.com
#### 8. Click it

![BitVise Point DNS2](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS2.png "BitVise Point DNS2")

#### 9. Click the Edit icon for the A record

![BitVise Point DNS3](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS3.png "BitVise Point DNS3")

#### 10. Change the Points to = Parked to - the IP address of your Vultr server

#### 11. Get your IP address from the Vultr console

![GetVultrIP](./images/fr0302-12_Get-Vultr-IP.png "GetVultrIP")

#### 12. Change Parked

![BitVise Point DNS4](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS4.png "BitVise Point DNS4")
 
To Your server IP address and Save

![BitVise Point DNS5](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS5.png "BitVise Point DNS5")

![BitVise Point DNS6](./images/fr0306-09_Ubuntu-Bitvise-Point-DNS6.png "BitVise Point DN65")

#### 13. Wait 10-15 minutes then 
#### 14. Browse to your web site via http

```
http://formR-<your initials>-00.com
```

- e.g http://formR-cbt-00.com


![BitVise Browse your website](./images/fr0306-10_Ubuntu-Bitvise-Browse-your-website.png "BitVise Browse your website")

----
### 9. Modify formR-xxx-00.com_all-apps.conf to use your new URL 0:05
----
#### 1. Open Bitvise 
#### 2. Load Profile: Vultr-formR0-nimda.tlp
#### 3. Login
#### 4. From your Bitvise SFTP window navigate to 

```
/etc/nginx/sites-available
```
#### 5. On "formR-xxx-00.com_all-apps" right click and select Edit 

![BitVise simpleApp1](./images/fr0306-10_Ubuntu-Bitvise-simpleApp1.png "BitVise simpleApp1")

#### 6. Change yourURL e.g. formR-cbt-00.com

![BitVise simpleApp2](./images/fr0306-10_Ubuntu-Bitvise-simpleApp2.png "BitVise simpleApp2")
 
![BitVise simpleApp3](./images/fr0306-10_Ubuntu-Bitvise-simpleApp3.png "BitVise simpleApp3")

#### 7. Save then close this file

----
### 10. Personalize the formR Home Page 0:05
----
#### 1. From your Bitvise SFTP window navigate to 

```
/webs/simpleApp/

```
#### 2. On "app.js" right click and select Edit 

![BitVise appjs1](./images/fr0306-10_Ubuntu-Bitvise-appjs1.png "BitVise appjs1")

#### 3. Add something personal to the "Welcome to" line. e.g. Welcome to Bruce's formR 

![BitVise appjs2](./images/fr0306-10_Ubuntu-Bitvise-appjs2.png "BitVise appjs2")
 

#### 4. Save then close this file then close the SFTP window

#### 5. Reboot from the Bitvise New terminal console (Bitvise will reconnect when server is back up)

```
reboot
```

#### 6. Browse to your IP e.g. 155.138.210.79:5000

```
http:<your VM IP>:5000
```

![BitVise appjs3](./images/fr0306-10_Ubuntu-Bitvise-appjs3.png "BitVise appjs3")

#### 7. Close Bitvise by clicking X in upper right corner

![BitVise Close](./images/fr0306-13_Ubuntu-Bitvise-Close.png "BitVise Close")


----
### 11. Add SSL certificate using Letsencrypt 0:05
----
#### 1. Open Bitvise New Terminal Console and enter (You might use notpad to build yourURL)

```
certbot --nginx -d <yoururl>  
```

- yoururl =  formR-yourinitials-00.com 

- e.g. formR-cbt-00.com

#### 2. Enter your email address to get renewal notices and then Y to register:

![BitVise Add SSL](./images/fr0306-11_Ubuntu-Bitvise-add-ssl.png "BitVise Add SSL")

#### 3. Enter Y to Share your email with Lets Encrypt

![BitVise Add SSL2](./images/fr0306-11_Ubuntu-Bitvise-add-ssl2.png "BitVise Add SSL2")

#### 4. Browse to your web via https

```
https://yoururl
```

- e.g. https://formR-cbt-00.com


![BitVise Browse with https](./images/fr0306-12_Ubuntu-Bitvise-Browse-with-https.png "BitVise Browse with https")

----
### 12. Disable TLSv1.0 and TLSv1.1 and enable TLSv1.3 protocols 0:10

- This is for improved SSL security
----
#### 1. Edit nginx.conf

```
nano /etc/nginx/nginx.conf
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS1.png "BitVise TLS")

#### 2. Modify SSL Settings

- Remove

```
ssl_protocols TLSv1 TLSv1.1 TLSv1.2; # Dropping SSLv3, ref: POODLE
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS2.png "BitVise TLS")


- Add

```
ssl_protocols TLSv1.2 TLSv1.3;
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS3.png "BitVise TLS")


#### 3. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 4. Edit options-ssl-nginx.conf

```
nano /etc/letsencrypt/options-ssl-nginx.conf
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS4.png "BitVise TLS")

#### 6. Modify SSL Settings

- Remove

```
ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS5.png "BitVise TLS")


- Add

```
ssl_protocols TLSv1.2 TLSv1.3;
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS6.png "BitVise TLS")


#### 7. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 8. Test nginx and reload it

```
nginx -t
```
```
service nginx reload
```

![BitVise TLS](./images/fr0306-13_Ubuntu-Bitvise-TLS7.png "BitVise TLS")


#### 9.  Close Bitvise by clicking X in upper right corner

![BitVise Close](./images/fr0306-13_Ubuntu-Bitvise-Close.png "BitVise Close")



#### 10. Test your SSL settings by browsing to:

```
ssllabs.com/ssltest/
```

- Enter your URL into Hostname e.g. formR-cbt.00.com

![SSL Test](./images/fr0306-11_Ubuntu-SSL-test1.png "SSL Test")

- Your test results

![SSL Test](./images/fr0306-11_Ubuntu-SSL-test2.png "SSL Test")

----
#### Email us your test results picture. We would love to hear from you!!
#### 8020data@gmail.com
----
----
### 13. Close Port 5000  0:05
----
#### 1. From the Bitvise New terminal console enter:

```
ufw status numbered 
```
```
ufw delete 8
```
```
ufw delete 4
```

![BitVise Close Port 5000](./images/fr0306-13_Ubuntu-Bitvise-Close-Port-5000.png "BitVise Close Port 5000")

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations your Ubuntu server is secure and ready for action.
  </div>
</div>

----

<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Install Data Server](/Setup/fr0305_Setup-Data-Server-Ubuntu.md)
</div><div class="page-next">

[My HTML Custom App - NEXT](/formR/fr020100_My-HTML-Custom.md)
</div>
<!-- ------------------------------------------------------------------------- -->
