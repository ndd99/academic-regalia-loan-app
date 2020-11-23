## Depoloying the Regalia-Share Application  

### Prerequisites  
What needs to be installed before starting:  

#### Your local machine.  
1.  Navigate to https://github.com/ndd99/academic-regalia-loan-app/blob/master/Documentation/Development.md  
2.  Follow the documentation and replicate the development environment before trying to host.  
3.  Once you reach the following page, you are ready to move on.  
  * ![mainPage](DevImages/mainPage.png)  
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
  * When the process completes, click the URL to open your CakePHP application in the browser:




