## Deploying the Regalia-Share Application  

### Prerequisites  
What needs to be installed before starting:  

#### Your local machine.  
* Because this application must go through simplesamlphp, it will not be available to be deployed on a local machine, or anywhere aside from regalia.community.bsu.edu.




### Uploading To the Web Server  

* Create a source bundle containing the files created by Composer. The following command creates a source bundle named ```cake-default.zip.``` It excluded files in the vendor folder,
which take up a lot of space and are not necessary for deploying your application to Elastic Beanstalk.  
```  
eb-cake zip ../cake-default.zip -r * .[^.]* -x "vendor/*"  
```  
  * Upload the source bundle to Elastic Beanstalk to deploy CakePHP to your environment.  
* To Deploy a source bundle  
  * Open the Elastic Beanstalk console, and in the Regions list, select your AWS Region.  
  * In the navigation pane, choose Environments, and then choose the name of your environment from the list.  
  * On the environment overview page, choose Upload and deploy.  
  * Use the on-screen dialog box to upload the source bundle.  
  * Choose Deploy.
  * The following commands must be ran via an AWS ssh connection in order to set up Ball State's SSO using simplesamlphp
    * In /var/www/html/webroot run 
      * sudo ln -s /var/www/html/vendor/simplesamlphp/simplesamlphp/www simplesaml
    * In /var/www/html/config/simplesaml run
      * sudo cp acl.php authsources.php config.php /var/www/html/vendor/simplesamlphp/simplesamlphp/config cd metadata
    * In /var/www/html/config/simplesaml/metadata run
      * sudo cp adfs-idp-hosted.php adfs-sp-remote.php saml20-idp-hosted.php saml20-idp-remote.php saml20-sp-remote.php shib13-idp-hosted.php shib13-idp-remote.php shib13-sp-hosted.php shib13-sp-remote.php wsfed-idp-remote.php wsfed-sp-hosted.php /var/www/html/vendor/simplesamlphp/simplesamlphp/metadata



  
### Add a database to your environment  

* Launch an Amazon RDS database instance in your Elastic Beanstalk environment. You can use MySQL, SQLServer, or PostgreSQL databases with CakePHP on Elastic Beanstalk. For this example, we'll use PostgreSQL.  
* To add an Amazon RDS DB instance to your Elastic Beanstalk environment.  
 * Open the Elastic Beanstalk console, and in the Regions list, select your AWS Region.  
 * In the navigation pane, choose Environments, and then choose the name of your environment from the list.  
 * In the navigation pane, choose Configuration.  
 * Under Database, choose Edit.  
 * For DB engine, choose postgres.
 * Type a master username and password. Elastic Beanstalk will provide these values to your application using environment properties.  
 * Choose Apply.

* CakePHP's database configuration is in a file named app.php in the config folder in your project code. Open this file and add some code that reads the environment variables from ```$_SERVER``` and assigns them to local variables. Insert the highlighted lines in the below example after the first line ```(<?php)```:  
 * ```Example ~/Eb-cake/config/app.php```   
  ```
   <?php
if (!defined('RDS_HOSTNAME')) {
  define('RDS_HOSTNAME', $_SERVER['RDS_HOSTNAME']);
  define('RDS_USERNAME', $_SERVER['RDS_USERNAME']);
  define('RDS_PASSWORD', $_SERVER['RDS_PASSWORD']);
  define('RDS_DB_NAME', $_SERVER['RDS_DB_NAME']);
}
return [
...
 ```
 * The database connection is configured further down in app.php. Find the following section and modify the default datasources configuration with the name of the driver that matches your database engine (Mysql, Sqlserver, or Postgres), and set the host, username, password and database variables to read the corresponding values from Elastic Beanstalk.   
### To update your Elastic Beanstalk environment:
 1. Create a new source bundle:
  ```
  ~/eb-cake$ zip ../cake-v2-rds.zip -r * .[^.]* -x "vendor/*"
  ```  
 2. Open the Elastic Beanstalk console, and in the Regions list, select your AWS Region.  
 3. In the navigation pane, choose Environments, and then choose the name of your environment from the list.  
 4. Choose Upload and Deploy.  
 5. Choose Browse and upload cake-v2-rds.zip.  
 6. Choose Deploy. 
 
### Starting and Stopping the Webserver:
  
Navigate to the XAMPP control panel and select start or stop for the Apache Webserver or MySQL.  

### How to Troubleshoot the application:  
* Navigate to where the application is located in ```C:\XAMPP\htdocs\regalia\regalia-loan-app-code``` and run  
 ```
 composer update
 ```  
### Where to find source of errors:  
* Navigate to ```C:\XAMPP\htdocs\regalia\regalia-loan-app-code\config\app.php```  
 * Define this logger:  
 ```
 use Cake\Log\Log;

// Short classname
Log::config('debug', [
    'className' => 'File',
    'path' => LOGS,
    'levels' => ['notice', 'info', 'debug'],
    'file' => 'debug',
]);

// Fully namespaced name.
Log::config('error', [
    'className' => 'Cake\Log\Engine\FileLog',
    'path' => LOGS,
    'levels' => ['warning', 'error', 'critical', 'alert', 'emergency'],
    'file' => 'error',
]);
```  
### Most Vulnerable Components:  
 * Given the nature of the SSO integration it may be a weak point as it is not able to be tested and has only been recently implemented.


