
<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Deploy my-react-app](/formR/fr0401_Deploy-My-Custom-App.md)
</div><div class="page-next">

[Deploy formR - NEXT](/formR/fr0401_Deploy-formR.md)
</div><div style="margin-top:35px">&nbsp;</div> 

<!-- ------------------------------------------------------------------------- -->

## 3.2 Clone formR 0:45 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0103_Clone-formR.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/959888948623187969" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->  
- In this topic you will clone the formR and test the applications on your local workstation.

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
### 1. Cloning formR repository  0:05
----
#### 1. Clone into the local repos folder using the Windows Command prompt

```
cd C:\repos\
```
 
![formR-Clone-01](images/fr0103-formR-Clone-01.png "formR-Clone-01")
 
```
git clone https://github.com/8020data/formR_prod-master.git FormR
```
```
cd FormR
```
```
dir
```

![formR-Clone-02](images/fr0103-formR-Clone-02.png "formR-Clone-02")

#### 2. From Windows command propt open with VSCode

```
code formR_prod-master.code-workspace
```

![formR-Clone-03](images/fr0103-formR-Clone-03.png "formR-Clone-03")

- If prompted, click "Yes I trust the authors".

![formR-Clone-03](images/fr0103-formR-Clone-03a.png "formR-Clone-03")

![formR-Clone-03](images/fr0103-formR-Clone-03b.png "formR-Clone-03")


----
### 2. Install Node modules  0:10
----
#### 1. Right click on the client folder

#### 2. Click Open in Integrated Terminal, then 

![formR-Clone-04](images/fr0103-formR-Clone-04.png "formR-Clone-04")

```
npm install --legacy-peer-deps
```

![formR-Clone-05](images/fr0103-formR-Clone-05.png "formR-Clone-05")


![formR-Clone-06](images/fr0103-formR-Clone-06.png "formR-Clone-06")

- This process takes several minutes. 

#### 3. Test for vulnerabilities for production

```
npm audit --production
```

![formR-Clone-06](images/fr0103-formR-Clone-06a.png "formR-Clone-06")

#### 4. Right click on the server folder

#### 5. Click Open in Integrated Terminal, then 

![formR-Clone-07](images/fr0103-formR-Clone-07.png "formR-Clone-07")

```
npm install 
```

![formR-Clone-08](images/fr0103-formR-Clone-08.png "formR-Clone-08")

![formR-Clone-09](images/fr0103-formR-Clone-09.png "formR-Clone-09")

#### 3. Test for vulnerabilities for production

```
npm audit --production
```

![formR-Clone-06](images/fr0103-formR-Clone-06a.png "formR-Clone-06")

----
### 3. Install RAuth and World databases 0:05
----


<div class="notice-tip">
  <div class="notice-tip-header">
    Note: The World sample database has been modified so that all tables contain ID primary key fields.
  </div>  
</div>



----

#### 1. Open MySQL Workbench by clicking its icon in your task bar or by searching for Workbench in the Windows search, then

![formR-Clone-10](images/fr0103-formR-Clone-10-1.png "formR-Clone-10")

#### 2. Click the Local Instance under MySQL Connections

![formR-Clone-10](images/fr0103-formR-Clone-10.png "formR-Clone-10")

#### 3. Run Script file

- Click on Schemas to show your current databases

- Click on the Open a script file in this editor


![formR-Clone-11](images/fr0103-formR-Clone-11.png "formR-Clone-11")

#### 4. Navigate to and Open: 

```
 C:\repos\formR\prod-master\_3\SQLs\formR_RAuth-DB-Create.
 sql
```
 
 - then repeat these steps for:

```
 C:\repos\formR\prod-master\_3\SQLs\formR_World-DB-Create.sql
```

![formR-Clone-12](images/fr0103-formR-Clone-12.png "formR-Clone-12") 

![formR-Clone-13](images/fr0103-formR-Clone-13.png "formR-Clone-13")

#### 5. Click the Execute icon

![formR-Clone-14](images/fr0103-formR-Clone-14.png "formR-Clone-14")

#### 6. Click the refesh icon above the schema list

![formR-Clone-15](images/fr0103-formR-Clone-15.png "formR-Clone-15")

![formR-Clone-16](images/fr0103-formR-Clone-16.png "formR-Clone-16")

#### 7. IMPORTANT - Go back to Step #### 4. and repeat these same steps for the World DB file

```
 C:\repos\formR\prod-master\_3\SQLs\formR_World-DB-Create.sql
```

#### 8. Close Workbench

----
### 4. Make sure that your MySQL password for root  is set to:  FormR!1234
 0:05
----
#### 1. Open MySQL Workbench by clicking its icon in your task bar or by searching for Workbench in the Windows search, then

#### 2. Click the Local Instance under MySQL Connections

![formR-Clone-10](images/fr0103-formR-Clone-10.png "formR-Clone-10")

#### 3. Click the File tab, then click 'New Query Tab'

![formR-Clone-17](images/fr0103-formR-Clone-17.png "formR-Clone-17") 

#### 4. Enter the following into the Query window, then

```js
ALTER USER 'root'@'localhost' IDENTIFIED BY 'FormR!1234
';
```

#### 5. Click the Execute icon


![formR-Clone-18](images/fr0103-formR-Clone-18.png "formR-Clone-18")

![formR-Clone-19](images/fr0103-formR-Clone-19.png "formR-Clone-19")

#### 6. Close workbench and reopen it, then

#### 7. Right click on the Local Instance, then

#### 8. Click Edit Connection, then

![formR-Clone-20](images/fr0103-formR-Clone-20.png "formR-Clone-20")

#### 9. Click Store in Vault, then

#### 10. Enter the new password: FormR!1234
 and click OK

![formR-Clone-20a](images/fr0103-formR-Clone-20a.png "formR-Clone-20a")

#### 11. Click Test Connection then

![formR-Clone-20b](images/fr0103-formR-Clone-20b.png "formR-Clone-20b")

#### 12. Click Close and then close Workbench


----
 ### 5. Run Client and Server applications 0:10
----

#### 1. Right click on the server/1s-world folder and
#### 2. Click Open in Integrated Terminal, then 

![formR-Clone-21](images/fr0103-formR-Clone-21.png "formR-Clone-21") 

```
npm start
```

![formR-Clone22](images/fr0103-formR-Clone-22.png "formR-Clone-22")

![formR-Clone22a](images/fr0103-formR-Clone-22a.png "formR-Clone-22a")

#### 3. Right click on the client/1c-world folder and
#### 4. Click Open in Integrated Terminal, then 

<div class="notice-tip">
  <div class="notice-tip-header">
    Note: The client application can take up to 15 minutes to start for the first time.
  </div>  
</div>

![formR-Clone-23](images/fr0103-formR-Clone-23.png "formR-Clone-23")

```
npm start
```

![formR-Clone-24](images/fr0103-formR-Clone-24.png "formR-Clone-24")

![formR-Clone-24a](images/fr0103-formR-Clone-24a.png "formR-Clone-24a")

![formR-Clone-24b](images/fr0103-formR-Clone-24b.png "formR-Clone-24b")

----
### 6. Test the applications on your local workstation 0:10
----
#### 1. Enter each of the following in your browser to test the server:

```
localhost:50251
```
```
localhost:50251/api/world/cities/test
```
```
localhost:50251/api/world/cities/model
```
```
localhost:50251/api/world/cities/
```
```
localhost:50251/api/world/cities/1
```
```

localhost:50251/api/world/countries/test
```
```
localhost:50251/api/world/countries/model
```
```
localhost:50251/api/world/countries/
```
```
localhost:50251/api/world/countries/1
```

#### 2.  Enter the following in your browser to test the client:

```
    localhost:50201
```

----
 ### 6. Install FRTools 0:10
----

# Not Ready Yet

![Not Ready Yet](./images/fr0000-01_not-ready.png "Not Ready Yet")




#### 1. Set System Path to contain: C:\repos\formR\_2\bin

- Click Start, type env, select: Edit the system environment variables
- Click on button, Environment Variables
- Under System (not User) variables, select Path, then click Edit...
- Click on button, New, then type: C:\repos\formR\_2\bin
- Click Ok three times

#### 2. Get formR Tools from 8020data GitHub repository

   - From Windows command prompt enter: 

```
cd C:/Repos/formR
```
```
git https://github.com/8020data/FRTools.git     tools
```

#### 3. Create a link from ./formR/_2  ./formR/tools/_2 to

- Open Windows Command prompt Run as Administrator  BT-NEED screen shot

``` 
cd C:\Repos\formR
```
```
mklink /d _2 tools\_2
```

#### 4. Run FRTools command
   
```
$ frt  
```

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have Cloned formR successfully to your  local workstation.
  </div>
</div>

----

<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Deploy my-react-app](/formR/fr0401_Deploy-My-Custom-App.md)
</div><div class="page-next">

[Deploy formR - NEXT](/formR/fr0401_Deploy-formR.md)
</div>

<!-- ------------------------------------------------------------------------- -->
