
<!-- ------------------------------------------------------------------------- -->

<div class="page-back">


[BACK - Website SSL](/Setup/fr0306_Setup-Website-SSL-Ubuntu.md)
</div><div class="page-next">

[Clone formR - NEXT](/formR/fr0401_Clone-formR.md)
</div><div style="margin-top:35px">&nbsp;</div>



<!-- ------------------------------------------------------------------------- -->

## 3.1 Deploy My Custom App 0:25 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0307_Setup-React-Apps-Ubuntu.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/931217970355667016" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- In this step using 5c-my-teact-app you will:
1. Run the app from development code locally
2. Build a production version
3. Run the production version locally
4. Deploy the production version to your server
5. Configure the app on your server
6. Run the app on your server from your local browser

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
### 1. Run 5c-my-react-app  0:05
----
#### 1. From File Explorer navigate to:

```
C repos FRApps
```
- double click on FRApps.code-workspace to open VSCode

![FRApps-Deploy-1](/images/fr0103-FRApps-Deploy-1.png "FRApps-Deploy-1")

- Pull from github to get the latest changes, by clicking the VSCode Source Control charm

![FRApps-Deploy-1](/images/fr0103-FRApps-Deploy-1a.png "FRApps-Deploy-1")

- then click the three dots next to the refresh icon and click Pull

![FRApps-Deploy-1](/images/fr0103-FRApps-Deploy-1b.png "FRApps-Deploy-1")


2. Right click on the client/5c-my-react-app folder, then
click Open in Integrated Terminal, then 

![FRApps-Clone-67](../Setup/images/fr0103-FRApps-Clone-67.png "FRApps-Clone-67") 

- Enter:

```
npm start
```

![FRApps-Deploy-11](/images/fr0103-FRApps-Deploy-11.png "FRApps-Deploy-11")

- If you are prompted, click Allow Access

![FRApps-Clone68a](../Setup/images/fr0103-FRApps-Clone-22a.png "FRApps-Clone-68a")

![FRApps-Deploy-11a](/images/fr0103-FRApps-Deploy-11a.png "FRApps-Deploy-11a")

----
### 2. Build 5c-my-react-app  0:05
----
#### 1. Right click on the client/5c-my-react-app folder
2. Click Open in Integrated Terminal, then 

![FRApps-Clone-67](../Setup/images/fr0103-FRApps-Clone-67.png "FRApps-Clone-67") 

```
npm run build
```

![FRApps-Deploy-12](/images/fr0103-FRApps-Deploy-12.png "FRApps-Deploy-12")

3. View the build folder

![FRApps-Deploy-12a](/images/fr0103-FRApps-Deploy-12a.png "FRApps-Deploy-12a")

### 3. Run Production version of 5c-my-react-app locally 0:05
----
#### 1. Right click on the client/5c-my-react-app folder
2. Click Open in Integrated Terminal, then 

![FRApps-Clone-67](../Setup/images/fr0103-FRApps-Clone-67.png "FRApps-Clone-67") 

```
npm run prod
```

![FRApps-Deploy-13](/images/fr0103-FRApps-Deploy-13.png "FRApps-Deploy-13")

- Enter the URL into your browser

![FRApps-Deploy-13a](/images/fr0103-FRApps-Deploy-13a.png "FRApps-Deploy-13a")

### 4. Deploy Production Build to Remote Server 5c-my-react-app  0:05
----
#### 1. Right click on the client/5c-my-react-app folder
2. Click Open in Integrated Terminal, then 

![FRApps-Clone-67](../Setup/images/fr0103-FRApps-Clone-67.png "FRApps-Clone-67") 

```
npm run deploy
```

![FRApps-Deploy-14](/images/fr0103-FRApps-Deploy-14.png "FRApps-Deploy-14")

3. Confirm that the build folder was transferred

- Login to your remote server using Bitvse and open new SFTP window

![FRApps-Deploy-14a](/images/fr0103-FRApps-Deploy-14a.png "FRApps-Deploy-14a")

- Navigate to

```
/webs/FRApps/client/5c-my-react-app/build
```

![FRApps-Deploy-14b](/images/fr0103-FRApps-Deploy-14b.png "FRApps-Deploy-14b")

### 5. Configure your remote server to run my-react-app 0:10 

#### 1. Login using Bitvise and open New SFTP Window

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15.png "FRApps-Deploy-15")

2. Navigate to:

```
/etc/nginx/apps-enabled
```

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15a-1.png "FRApps-Deploy-15")


3. Right click to create a new file and enter the name:

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15b.png "FRApps-Deploy-15")

```
formR-xxx-00.com_5c-my-react-app.conf
```

4. Right-click on formR-xxx-00.com_my-react-app.conf and select Edit.

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15c.png "FRApps-Deploy-15")

- Add the following and then save the file

```
location      /5c-my-react-app {      

	alias       /webs/FRApps/client/5c-my-react-app/build/;      

}    
```

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15d.png "FRApps-Deploy-15")

- Save the file

5. In Bitvise open New terminal console and restart the nginx service:

```
systemctl restart nginx
```

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15e.png "FRApps-Deploy-15")

6. From your browser visit

```
formR-<your initials>-00.com/5c-my-react-app

e.g. formR-cbt-00.com/5c-my-react-app
```

![FRApps-Deploy-15](/images/fr0103-FRApps-Deploy-15f.png "FRApps-Deploy-15")

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have deployed and run the my-react-app successfully on your remote server.
  </div>
</div>

----


<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Website SSL](/Setup/fr0306_Setup-Website-SSL-Ubuntu.md)
</div><div class="page-next disabled">

[Clone formR - NEXT](/formR/fr0401_Clone-formR.md)
</div>

<!-- ------------------------------------------------------------------------- -->