# Deployment
## Apache Server
* Install XAMPP(7.4.12) https://www.apachefriends.org/index.html
* Run the Apache and mysql by running xampp-control.exe (or corresponding executable if you are in MAC).
* ![XAMPP](DevImages/XAMPP.png)
## Create DB Tables
* Browse to http://localhost/phpMyAdmin/
    * Default username should be root without a password if asked.
* Create a database by using the new button on the top-left
    * ![MyAdmin](DevImages/MyAdmin.png)
    * Database name: regalia
    * Leave everything else the same and click create
* Click on the new regalia and select SQL tab
    * Copy and paste the contents of the files found in config/schema/regalia-complete.sql and click the go button in the bottom right.
* Go to the User Accounts tab and select edit privileges where the username is root
    * ![EditPrivileges](DevImages/EditPrivileges.png)
* Then select change password at the top. enter '1234' in both fields and hit go in the bottom right.

## Clone Repositories
* Browse to the C:/xampp/htdocs folder
* Clone the repo in that folder
    * https://github.com/etmitchell2022/regalia-loan-app-code.git
* Refactor app.default.php in the IDE of your choice and rename it to app.php
## Composer
* Download composer in whatever way applies to you in https://getcomposer.org/download/
* Browse to the folder containing the project in a command window and run
 ```console 
$ composer update
```
## Testing the Development Environment
* 2 Users are included in the sql 
    * user:jdoe1@bsu.edu password: password foo, normal user
    * user jperson1@bsu.edu password foo, admin
* Once logged in all pages will be available.


