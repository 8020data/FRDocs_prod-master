<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Install App Server ](/Setup/fr0304_Setup-App-Server-Ubuntu.md)
</div><div class="page-next">

[Website SSL - NEXT](/Setup/fr0306_Setup-Website-SSL-Ubuntu.md)
</div><div style="margin-top:35px">&nbsp;</div>

<!-- ------------------------------------------------------------------------- -->

## 2.5 Install Data Server 0:25 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0305_Setup-Data-Server-Ubuntu.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/932678480863305770" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- MySql will be your database on your server.
- In this step you will install and secure it.
- You will test your access from your local workstation.

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
### 2. Install MySQL 0:05
----
#### 1. Install MySQL

```
apt-get install mysql-server
```

- Enter Y to continue, if asked

![Install MySQL](./images/fr0305-01_Ubuntu-install-mysql.png "Install MySQL")

#### 2. Check installation
```
mysql --version
```

![Check MySQL](./images/fr0305-02_Ubuntu-check-mysql.png "Check MySQL")

----
### 3. Secure MySQL 0:10
----
#### 1. Lock down MySQL - Running this script will ask you

```
mysql_secure_installation
```

- Add VALIDATE PASSWORD PLUGIN: Yes
- Enter a "password validation policy level": 2
- Enter a password for the user, root, to login to MySQL: FormR!1234

- Enter to save password: Yes
- Remove anonymous users? Yes
- Disallow root login remotely? No (Yes on a production server)
- Remove test database and access to it? No 
- Reload privilege tables now? Yes


![Secure MySQL](./images/fr0305-03_Ubuntu-secure-mysql.png "Secure MySQL")

![Secure MySQL part 2](./images/fr0305-03_Ubuntu-secure-mysql2.png "Secure MySQL part 2")

#### 2. Allow remote access to MySQL 

```
nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
- Change line:         bind-address = 127.0.0.1
- to:                  bind-address = 0.0.0.0


![Mysql-setup-nano-bind-address](./images/fr0305-04_Ubuntu-nano-bind-address-mysql.png "Mysql-setup-nano-bind-address")

#### 3. Save the file by pressing Ctrl-X, then Y and then Enter to save the file name.

#### 4. Restart mysql and comfirm its running

```
systemctl restart mysql.service
```
```
systemctl status mysql.service
```

![Mysql-setup-allow-remote-access](./images/fr0305-05_Ubuntu-allow-remote-access-mysql.png "Mysql-setup-allow-remote-access")


<div class="notice-tip">
  <div class="notice-tip-header">
    Note: If you get a "lines ... (END)" message, press ctrl-c then Enter to continue.
  </div>  
</div>

![Check Unattended Upgrades](./images/fr0302-06_Ubuntu-Check-Unattended-Upgrades1.png "Check Unattended Upgrades")

#### 5. Open firewall rule for port 3306

```
ufw allow 3306/tcp
```
```
ufw status   
```

![Mysql-setup-open-firewall-port-3360](./images/fr0305-06_Ubuntu-open-firewall-port-3360-mysql.png "Mysql-setup-open-firewall-port-3360")

#### 6. Create and Grant Privileges to user account: nimdas with host %


<div class="notice-tip">
  <div class="notice-tip-header">
    Note: root@localhost has all rights and nimdas@% will have all rights.
  </div>  
</div>
 

#### 7. From the  New terminal console prompt enter:

```
mysql -p
```

#### 8. Enter : the root password -> FormR!1234

- Password:

```
FormR!1234
```

#### !! Remember to write your passwords in a safe place !!
----

#### 9. Enter the following from the mysql prompt:

```
CREATE USER 'nimdas'@'%' IDENTIFIED WITH mysql_native_password BY 'FormR!1234
';
```
```
GRANT ALL PRIVILEGES ON *.* TO 'nimdas'@'%';
```
```
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
![Mysql-setup-create-admin](./images/fr0305-07_Ubuntu-create-admin-mysql.png "Mysql-setup-create-admin")

#### 10. Exit mysql
```
mysql> \quit
```

![Mysql-quit-to-console](./images/fr0305-08_Ubuntu-quit-to-console-mysql.png "Mysql-quit-to-console")

#### 11. Stop, Start and check status of MySQL
```
systemctl stop mysql
```
```
systemctl start mysql
```
```
systemctl status mysql.service
```

![Mysql-setup-check-status](./images/fr0305-09_Ubuntu-check-status-mysql.png "Mysql-setup-check-status")

- Note: If you get a "lines ... (END)" message, press ctrl-c then Enter to continue

![Check Unattended Upgrades](./images/fr0302-06_Ubuntu-Check-Unattended-Upgrades1.png "Check Unattended Upgrades")


----
### 4. Login as nimdas remotely from your local PC with MySQL Shell.  0:05
----
#### 1. From Windows command prompt enter the following: (Use your Vultur server IP address)

![GetVultrIP](./images/fr0302-12_Get-Vultr-IP.png "GetVultrIP")

- Command prompt:

```
mysqlsh /connect nimdas@xxx.xxx.xxx.xxx:3306
```

- Password:

```
FormR!1234
```

- Enter v to never save the password

```
v
```

![Mysql-setup-login-admin-mysqlsh-local](./images/fr0305-10_Ubuntu-login-admin-mysqlsh-local.png "Mysql-setup-login-admin-mysqlsh-local")

#### 2. Check Version. From the mysql command prompt enter the following:

```js
\sql SELECT VERSION();
```

![Mysql-setup-login-admin-mysqlsh-local](./images/fr0305-10_Ubuntu-login-admin-mysqlsh-local1.png "Mysql-setup-login-admin-mysqlsh-local")
 
#### 3. Exit mysqlsh. From the mysql command prompt enter the following:

```
\quit
```
![Mysql-setup-login-admin-mysqlsh-local](./images/fr0305-10_Ubuntu-login-admin-mysqlsh-local2.png "Mysql-setup-login-admin-mysqlsh-local")

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have installed a Database server on your Ubuntu server.
  </div>
</div>

----

<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Install App Server ](/Setup/fr0304_Setup-App-Server-Ubuntu.md)
</div><div class="page-next">

[Website SSL - NEXT](/Setup/fr0306_Setup-Website-SSL-Ubuntu.md)
</div>

<!-- ------------------------------------------------------------------------- -->
