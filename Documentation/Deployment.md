## Depoloying the Regalia-Share Application  

### Prerequisites  
What needs to be installed before starting:  

#### Your local machine.  
1.  Navigate to https://github.com/ndd99/academic-regalia-loan-app/blob/master/Documentation/Development.md  
2.  Follow the documentation and replicate the development environment before trying to host.  
3.  Once you reach the following page, you are ready to move on.  
  * ![mainPage](DevImages/mainPage.PNG)  
* This applcation will be hosted by Ball State through AWS.  
* In order to host it, an Elastic Beanstalk environment will be configuerd through AWS.  
  * Open the Elastic Beanstalk console using this preconfigured link: console.aws.amazon.com/elasticbeanstalk/home#/newApplication?applicationName=tutorials&environmentType=LoadBalanced  
  * For Platform, select the platform and platform branch that match the language used by your application.  




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
  * When the deployment completes, you can choose the site URL to open your website in a new tab.  
  * When the process completes, click the URL to open your CakePHP application in the browser  
  
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
  * 
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
 

