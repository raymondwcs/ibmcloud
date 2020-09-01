# Getting Started with IBM Cloud
This tutorial shows you how to deploy a sample Node.js app to IBM Cloud.  The sample app that you are going to deploy is a server app that responds to `HTTP GET` requests and returns a simple text message `Hello World!`

# Preparation
1. Create a **free** account at https://cloud.ibm.com

2. Download the Node.js app
```
git clone https://github.com/raymondwcs/ibmcloud
```
3. It is always a good idea to verify that the app is working fine before deploying it.  Prepare and run the app in your local machine.
```
cd ibmcloud/helloworld
npm install
npm start
```
4. Test your app.  Go to the following URL
```
http://localhost:8099
```

# Deplpy a simple Node.js app to IBM Cloud
1. Make sure you are in the folder that contains the Node.js app
```
cd ibmcloud/helloworld
```
2. Login to IBM cloud
```
bx cf login
```
3. Select a **region** for your app
```
bx target --cf
```
Select `us-south` when prompted
```
Select a Cloud Foundry instance:
1. public CF us-south (https://api.us-south.cf.cloud.ibm.com)
2. public CF eu-de (https://api.eu-de.cf.cloud.ibm.com)
3. public CF eu-gb (https://api.eu-gb.cf.cloud.ibm.com)
4. public CF au-syd (https://api.au-syd.cf.cloud.ibm.com)
5. public CF us-east (https://api.us-east.cf.cloud.ibm.com)
Enter a number> 1
Targeted Cloud Foundry (https://api.us-south.cf.cloud.ibm.com)

Targeted org comps381f01@study.ouhk.edu.hk

Targeted space dev
                  
API endpoint:      https://cloud.ibm.com   
Region:               
User:              comps381f01@study.ouhk.edu.hk   
Account:           R S's Account (0dab305e49d942809feacf8edb0cf86b)   
Resource group:    No resource group targeted, use 'bx target -g RESOURCE_GROUP'   
CF API endpoint:   https://api.us-south.cf.cloud.ibm.com (API version: 2.152.0)   
Org:               comps381f01@study.ouhk.edu.hk   
Space:             dev  
```
4. Deploy (upload) your app to IBM Cloud
You need to find a **unique** name for your app.  I use `rs202009011306` in this tutorial.  If the deployment is successful, you will be able to run your app at `http://rs202009011306.mybluemix.net`.
```
bx cf push -m 64m rs202009011306
```
It takes 2 to 3 minutes to upload for your.  If things go well, you will see the following messages.
```
Waiting for app to start...

name:              rs202009011306
requested state:   started
routes:            rs202009011306.mybluemix.net
last uploaded:     Tue 01 Sep 15:06:50 CST 2020
stack:             cflinuxfs3
buildpacks:        sdk-for-nodejs

type:            web
instances:       1/1
memory usage:    64M
start command:   npm start
     state     since                  cpu    memory         disk          details
#0   running   2020-09-01T07:07:13Z   0.0%   45.7M of 64M   85.3M of 1G   
```
5. Test your app.  Go to the URL shown in the `routes`.  In this tutorial the URL is `http://rs202009011306.mybluemix.net`

