
<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Build Workstation](/Setup/fr0101_Setup-Developer-Workstation.md)
</div><div class="page-next">

[Clone FRApps - NEXT](/Setup/fr0103_Clone-FR-Apps.md)
</div><div style="margin-top:35px">&nbsp;</div>

<!-- ------------------------------------------------------------------------- -->

## 1.2 Test NodeJS 1:00 <!-- {docsify-ignore} -->
<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="../Setup/purposes/pfr0102_Test-Node.md" target="_blank">Link to Background and Purposes</a> 
  </div>  
</div>

<div class="notice-tip">
  <div class="notice-tip-header">
    Tip: <a href="https://discord.com/channels/928752444316483585/931216136853413958" target="_blank">Link to Discord for Your Comments</a> 
  </div>  
</div>

#### Introduction <!-- {docsify-ignore} -->
- The following steps create several basic node applications. 
- There are script, server, client and MySQL testing applications. Each has special requirements. You will create a folder structure and install the required packages. Everything will be installed in the repos/myProject folder. All activities will be done in VSCode.   

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
### 1. Test the Node version 0:05
----
#### 1. In File Explorer navigate to C repos myProject, then double click on myProject.code-workspace, then

![Node-test-terminal](images/fr0102-01_Node-test-terminal0.png "Node-test-terminal")

- In VSCode right click on the myProject folder and click on Open terminal

![Node-test-terminal](images/fr0102-01_Node-test-terminal.png "Node-test-terminal")

![Node-test-terminal-1](images/fr0102-01_Node-test-terminal-1.png "Node-test-terminal-1")

#### 2. From terminal enter:

```
     node --version 
```

![Node-test](images/fr0102-02_Node-test.png "Node-test")

----
### 2. Create sub-folders in myProject 0:05
----
#### 1. Right-click on the myProject folder and create a new folder:

![Node-new-folder](images/fr0102-03_Node-new-folder.png "Node-new-folder")

- Enter - client


![Node-new-folder](images/fr0102-03_Node-new-folder1.png "Node-new-folder")

#### 2. Repeat step 1. for the following:

- Create folders for:
  - docs
  - scripts
  - server


#### 3. Right-click on the server folder and create a new folder:

![Node-create-folders](images/fr0102-04_Node-create-server-folder.png "Node-create-folders")

- Enter -  app01s

![Node-create-folders](images/fr0102-04_Node-create-server-folder1.png "Node-create-folders")

- Your new folders:

![Node-create-folders](images/fr0102-04_Node-create-folders.png "Node-create-folders")

----
### 3. Create a new file, batch.js, in the scripts folder and run it with Nodejs. 0:10
----
#### 1. Right-click on the scripts folder, then click New File

![Node-create-empty-file0](images/fr0102-05_Node-create-empty-file0.png "Node-create-empty-file0")

#### 2. In the blank area enter:

```
batch.js
```

![Node-create-empty-file1](images/fr0102-05_Node-create-empty-file1.png "Node-create-empty-file1")

#### 3. Click on batch.js to open it in the editor

![Node-create-empty-file](images/fr0102-05_Node-create-empty-file.png "Node-create-empty-file")

#### 4. Add some code to batch.js:
<br/>

```js
console.log("Hello, World!");
```

![Node-add-to-batch](images/fr0102-06_Node-add-to-batch.png "Node-add-to-batch")

#### 5. Right click on batch.js in the scripts folder and select Open in Integrated Terminal and click in the Terminal window 

![Node-add-to-batch](images/fr0102-06_Node-add-to-batch-1.png "Node-add-to-batch")

#### 6. In Terminal window enter:
<br/>

```
node batch.js
```

![Node-run-batch](images/fr0102-07_Node-run-batch.png "Node-run-batch")


----
### 4. Create a new file, server.js in the server folder and run it with Nodejs. 0:10
----
#### 1. Right click on the server folder and Select Open in Intgrated Terminal and enter:

![Node-install-express](images/fr0102-09_Node-install-express.png "Node-install-express")

a. Initialize - Enter: npm init

```
npm init
```

- Press enter to accept all defaults


![Node-npm-init](images/fr0102-09_Node-npm-init.png "Node-npm-init")

b. Install express

```
npm install express
```

![Node-npm-express](images/fr0102-09_Node-npm-express.png "Node-npm-express") 

<div class="notice-tip">
  <div class="notice-tip-header">
    Note: In the previous steps we installed using npm (node package manager) which created and populated a new folder node_modules. This folder can be very large in size but does not need to be tracked in GitHub. Files in .gitignore will not be tracked in GitHub. 
  </div>  
</div>

#### 2. Create a new file in the myProject folder, .gitignore and add:

![Node-gitignore](images/fr0102-08_Node-gitignore.png "Node-gitignore")

![Node-gitignore](images/fr0102-08_Node-gitignore1.png "Node-gitignore")

- Enter:

```
node_modules
```

![Node-gitignore](images/fr0102-08_Node-gitignore2.png "Node-gitignore")

#### 3. Create a new file, server.js in the server/app01s folder

![Node-create-server-js](images/fr0102-11_Node-create-server-js0.png "Node-create-server-js")

![Node-create-server-js](images/fr0102-11_Node-create-server-js1.png "Node-create-server-js")



- Add this code:

```js
const express = require("express")
const app = new express();
app.use('/',myPage)

function myPage(req, res){
    var url = req.originalUrl;
    //send to browser
    res.send(`Hello, World from ${url} !`)
}

// set port
const PORT       =   process.env.PORT || 8080; 
// listen for requests
app.listen( PORT, () => {
    console.log(   `Server is running on port ${PORT}.` );
    } );

```

![Node-create-server-js](images/fr0102-11_Node-create-server-js.png "Node-create-server-js")

#### 4. Right click on the app01s folder and Select Open in Integrated Terminal and click in the Terminal window

#### 5. Enter:
<br/>

```
node server.js
```

#### 6. Allow Access in Microsoft Firewall and click Private networks

![Node-terminal-server-js](images/fr0102-12_Node-terminal-allow-access.png "Node-terminal-server-js")


#### 7. Terminal shows server running on port 8080

![Node-terminal-server-js](images/fr0102-12_Node-terminal-server-js.png "Node-terminal-server-js")

#### 8. Browse to:
<br/>

```
http://localhost:8080/myProject/server/app01s
```

![Node-browser-server-js](images/fr0102-13_Node-browser-server-js.png "Node-browser-server-js")


#### 9. Push your changes to GitHub

1. Click the Source Control charm

![Node-github-open-source](images/fr0102-14_Node-github-open-source.png "Node-github-open-source")

2. Add Message:
<br/>

```
Add Node App - batch.js
```

![Node-github-message](images/fr0102-14_Node-github-message.png "Node-github-message")

![Node-github-message-1](images/fr0102-14_Node-github-message-1.png "Node-github-message-1")

3. Click on Commit checkmark -

![Node-github-checkmark](images/fr0102-15_Node-github-checkmark.png "Node-github-checkmark")

4. Push

- Click on 3 dots then click Push 

![Node-github-push](images/fr0102-15_Node-github-push.png "Node-github-push")

5. The following message may show the first time. 

- Click on: Ok, Don't show again


![Node-ok-dont-show](images/fr0102-15_Node-ok-dont-show.png "Node-ok-dont-show")

*** End of Push to Github

----
### 5. Create a basic react app in the client folder and run it with Nodejs. 0:10
----
#### 1. Right click in the - client - folder and select Open in Integrated Terminal and click in the Terminal window

![Node-client](images/fr0102-16_Node-client.png "Node-client")

#### 2. Enter:

```
npm init
```

![Node-npm-init](images/fr0102-16_Node-npm-init.png "Node-npm-init")

#### 3. Create the react app:

```
npx create-react-app app01c
```


![Node-create-react-app](images/fr0102-16_Node-create-react-app.png "Node-create-react-app")

![Node-create-react-app-finish](images/fr0102-17_Node-create-react-app-finish.png "Node-create-react-app-finish")

#### 4. Right click in the - client/app01c - folder and select Open in Integrated Terminal and click in the Terminal window

![Node-app01c](images/fr0102-18_Node-app01c.png "Node-app01c")

#### 5. Enter: 

```
npm start
``` 

![Node-start-app](images/fr0102-18_Node-start.png "Node-start-app")

![Node-start-app](images/fr0102-18_Node-start-1.png "Node-start-app")

![Node-start-app](images/fr0102-18_Node-start-2.png "Node-start-app")

![Node-start-app](images/fr0102-18_Node-start-3.png "Node-start-app")

#### 6. Adjust package.json for React-Scripts (prevent npm audit from returning development vulnerabilities list for react-scripts)

- In VScode edit myProject/client/package.json, Cut the following react-scripts line from the dependencies section of package.json

```
    "react-scripts": "^5.0.0",
```

- Insert the following devdependencies section:

```js
  "devdependencies": {
    "react-scripts": "^5.0.0"
  },

```

![Node-package-json](images/fr0102-18_Node-Package.png "Node-package-json")

- Test by running npm audit. From client folder, right click and click Open in integated Terminal

![Node-terminal](images/fr0102-18_Node-Terminal.png "Node-terminal")

- Test for vulnerabilities in production

```
npm audit --production
```
![Node-audit](images/fr0102-18_Node-Audit.png "Node-audit")


#### ---Push your changes to GitHub

1. Click the Source Control charm
2. Add description of your choice
3. Click the Commit button
4. Click the Sync Changes button to push to github

----
### 6. Create a Nodejs routine to access the local MySQL database and return information. 0:10
----
#### 1. Install Sequelize. It will be used to connect to and access information in MySQL. 

#### 2. Right click in the - server - folder and select Open in Integrated Terminal and click in the Terminal window

![Open-Terminal-Server](images/fr0102-19_Open-Terminal-Server.png "Open-Terminal-Server")

#### 3. Enter:

```
npm install --save sequelize
```

![Node-install-sequelize](images/fr0102-19_Node-install-sequelize.png "Node-install-sequelize")

```
npm install --save mysql2
```
![Node-install-mysql2](images/fr0102-20_Node-install-mysql2.png "Node-install-mysql2")

#### 4. Search for Mysql WorkBench and open it

![Node-open-mysql-workbench](images/fr0102-20_Node-open-mysql-workbench.png "Node-open-mysql-workbench")

#### 5. Right click on the icon and Pin to TaskBar

![Node-pin-workbench-to-taskbar](images/fr0102-20_Node-pin-workbench-to-taskbar.png "Node-pin-workbench-to-taskbar")

#### 6. In Workbench click on the Local Instance that was created when MySQL was installed

![Node-click-local-instance](images/fr0102-20_Node-click-local-instance.png "Node-click-local-instance")

#### 7. In the query 1 window enter:

```js
CREATE DATABASE practice
```
#### 8. Then click the execute icon

![Node-create-database](images/fr0102-20_Node-create-database.png "Node-create-database")

#### 9. Click on the Schemas tab, then the refresh icon and your new database, practice, will appear 

![Node-schemas-refresh](images/fr0102-20_Node-schemas-refresh.png "Node-schemas-refresh")

#### 10. From VSCode Explorer navigate to the folder server/app01s and create a new file, queryDB.js, then enter the following code:

```js
const Sequelize = require("sequelize");
const sequelize = new Sequelize("practice", "root", "FormR!1234
", {
  host: "localhost", 
  dialect: "mysql", 
});
 
// 1. CREATE TABLE 
//const SQLstr = "CREATE TABLE customers (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255), address VARCHAR(255))"

// 2. SHOW TABLES 
//const SQLstr = "SHOW TABLES"

// #### 3. INSERT 1 ROW
//const SQLstr = "INSERT INTO customers (name, address) VALUES ('Company Inc', 'Highway 37')"

// #### 4. UPDATE 1 ROW 
//const SQLstr = "UPDATE customers SET address = 'Highway 40' where id = 1"

// #### 5. Create a Stored Procedure
//const SQLstr = "CREATE PROCEDURE sp_getcustomers() Select id, name,address from customers ;"

// #### 6. Execute a Stored Procedure
//const SQLstr = "Call sp_getcustomers"

//------------------------------------------------------------

runQuery();
async function runQuery() {
  try { 
  const values = await sequelize.query(SQLstr);
  console.log(values);
  } catch (error) {
    console.log(error);  
  }
}
```

#### 11. In each step 1 - 6 there is a 'const SQLStr..' line. The symbol // is a comment. For each step, one at a time, remove the comment on  the 'const SQLStr..' line, then go to the terminal and run: node queryDB.js. 

#### 12. After the execution of a step, Comment out the 'const SQLStr..' line for this step and uncomment the line in the next step

#### 13. Repeat for all steps. 

- Be aware, if you execute the same step twice in a row you will get an error. For example, step 1. creates a table. If you run it a second time  You will get an error that tells you that the table already exists.

#### 14. Uncomment Step 1 Create Table

![Node-create-table](images/fr0102-21_Node-create-table.png "Node-create-table")

#### 15. Right click in the - server/app01s - folder and select Open in Integrated Terminal and click in the Terminal window

![Open-Terminal-app01s](images/fr0102-19_Open-Terminal-app01s.png "Open-Terminal-app01s")

#### 16. Enter:

```
node queryDB
```

![Node-create-table](images/fr0102-24_Node-create-table.png "Node-create-table")

#### 17. Check in Workbench that the customers table was created

![Node-create-table-workbench](images/fr0102-24_Node-create-table-workbench.png "Node-create-table-workbench")

#### 18. Comment out "Create Table" and uncomment "Show Tables" then run node queryDB

![Node-show-tables](images/fr0102-25_Node-show-tables.png "Node-show-tables")

#### 19. Comment out "Show Tables" and uncomment "Insert 1 Row" then run node queryDB

![Node-Insert-1-row](images/fr0102-26_Node-Insert-1-row.png "Node-Insert-1-row")

#### 20. Check Workbench - Insert

![Node-Insert-1-row-workbench](images/fr0102-26_Node-Insert-1-row-workbench.png "Node-Insert-1-row-workbench")

#### 21. Comment out "Insert 1 Row" and uncomment "Update 1 Row" then run node queryDB

![Node-update-1-row](images/fr0102-27_Node-update-1-row.png "Node-update-1-row")

#### 22. Check Workbench - Update

![Node-update-1-row-workbench](images/fr0102-27_Node-update-1-row-workbench.png "Node-update-1-row-workbench")

#### 23. Comment out "Update 1 Row" and uncomment "Create Stored Procedure" then run node queryDB

![Node-create-stored-procedure](images/fr0102-28_Node-create-stored-procedure.png "Node-create-stored-procedure")

#### 24. Check Workbench - Create Stored Procedure

![Node-create-stored-procedure-workbench](images/fr0102-28_Node-create-stored-procedure-workbench.png "Node-create-stored-procedure-workbench")

#### 25. Comment out "Create Stored Procedure" and uncomment "Execute Stored Procedure" then run node queryDB

![Node-execute-stored-procedure](images/fr0102-29_Node-execute-stored-procedure.png "Node-execute-stored-procedure")

#### 26. Check Workbench - Create Stored Procedure

![Node-execute-stored-procedure-workbench](images/fr0102-29_Node-execute-stored-procedure-workbench.png "Node-execute-stored-procedure-workbench")

#### 27. Comment out "Execute Stored Procedure" and go to workbench and Drop Database practice to reset so these routines can be run again.

![Node-clean-up](images/fr0102-30_Node-clean-up.png "Node-clean-up")

![Node-clean-up-workbench](images/fr0102-30_Node-clean-up-workbench.png "Node-clean-up-workbench")

#### ---Push your changes to Github

1. Click the Source Control charm
2. Add description of your choice
3. Click the Commit button
4. Click the Sync Changes button to push to github

----
<div class="notice-success">
  <div class="notice-success-header">
    Congratulations! You have successfully run the Node applications that test your development environment.
    </div>
</div>

----

<!-- ------------------------------------------------------------------------- -->

<div class="page-back">

[BACK - Build Workstation](/Setup/fr0101_Setup-Developer-Workstation.md)
</div><div class="page-next">

[Clone FRApps - NEXT](/Setup/fr0103_Clone-FR-Apps.md)
</div>

<!-- ------------------------------------------------------------------------- -->

