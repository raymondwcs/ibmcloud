# Getting Started with IBM Cloud
This tutorial demonstrates how to deploy a simple Node.js app to IBM Cloud.  The app you are going to deploy is a server-side app that responds to HTTP `GET` requests and returns a simple text message `Hello World!`

# Preparation
1. Create a **free** account at https://cloud.ibm.com.  Write down your ID and password.

2. Download the sample app to your *home* directory.
```
cd ~
git clone https://github.com/raymondwcs/ibmcloud
```
3. It is always a good idea to verify that the app is working fine in your local machine *before* deploying it to the cloud.

Go into the folder containing the server-side app.
```
cd ~/ibmcloud/helloworld
```

Install the app's dependencies.
```
npm install
```

Run the server app.
```
npm start
```
4. Test your app by sending to it a HTTP `GET` request.  Open http://127.0.0.1:8099 in your web browser.
5. Stop your app by pressing Ctrl-C in your terminal.


# Deploy to IBM Cloud
1. Make sure you are inside the folder containing the app.
```
cd ~/ibmcloud/helloworld
```
2. Login to IBM cloud. Enter your ID and password when prompted.
```
bx login
bx target --cf
```
When prompted to **Select a region**, selet `us-south`
        
3. Deploy (upload) your app to IBM Cloud
You need to find a **unique** name for your app.  Apps on IBM Cloud are named XXXXXXXX@mybluemix.net where XXXXXXXX is the name of your app.
I use `rs202009011306` as the name of my app in this tutorial.  If the deployment is successful, you will be able to see your app running at `http://rs202009011306.mybluemix.net`.
```
rm -rf node_modules
bx cf push -m 64m rs202009011306
```
It takes 3-4 minutes to upload and activate for your app in the cloud.  If things go well, you will see the following messages at the end of deployment.
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
5. Test your app.  Open the URL shown in `routes` above in your web broswer.  In this tutorial, the URL is `http://rs202009011306.mybluemix.net`.

# Other Useful Commands
1. To redeploy an app.  Let's say we made some changes to `rs202009011306` and we want to redeploy it.
```
bx cf push -m 64m rs202009011306
```
2. To see a list of apps that you have deployed to IBM Cloud
```
bx cf apps
```
This command returns a list of apps that are running in IBM Cloud
```
Invoking 'cf apps'...

Getting apps in org comps381f01@study.ouhk.edu.hk / space dev as comps381f01@study.ouhk.edu.hk...
OK

name             requested state   instances   memory   disk   urls
rs202009011306   started           1/1         64M      1G     rs202009011306.mybluemix.net
```
3. To delete `rs202009011306` in IBM cloud.
```
bx cf delete rs202009011306
```
Type `yes` when prompted to confirm delete.
```
Invoking 'cf delete rs202009011306'...


Really delete the app rs202009011306?> yes
Deleting app rs202009011306 in org comps?????@study.ouhk.edu.hk / space dev as comps?????@study.ouhk.edu.hk...
OK
```
