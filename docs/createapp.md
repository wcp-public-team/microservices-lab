# Create your first application

The IBM Cloud Platform includes a collection of `Starter Kits` to help you get started with your first application.  We will use one of these starter kits to create and deploy our microservice.

In the middle of the dashboard page there is a section called `Create enterprise-level web apps`.  Click on the `View App Service starter kits` button.

![View App Service starter kits](./images/AppServiceStarterKitsButton.png)

!!! note
    *If you are using an existing IBM Cloud Lite account and you have created any resources you will not see the screen above.  If this happens to you, click on the ![hamburger](./images/HamburgerButton.png) icon at the top left, scroll down and click on `Web Apps`.  Then click `Starter Kits` on the left navigation menu.*

These are the starter kits that are available today.  Scroll down through the list and click on feel free to click on them to learn more about their contents.  If you need to get back to this page you can click on the `Starter Kits` link in the left navigation menu.

Scroll down and find the starter kit named Express.js Microservice.

![Express.js Microservice](./images/ExpressMicroservice.png)

Click on the tile.  This page describes the contents of the starter kit.

Click on the `Create App` button to create the application.  You will need to provide details for your application.  The Details panel contains default information for your app name and host; you can keep them or you can change them if you wish.  If you change either value remember that the hostname must be unique and needs to be a valid hostname, as the host name and domain are what make up your application's URL.

![App Details](./images/AppDetails.png)

When you are happy with the details click the `Create` button at the top right.  You should see a page similar to the one below.  You have just created your app!!

![App created](./images/AppCreated.png)

Right now it's just a definition; we haven't deployed it anywhere yet.  Also, you can see that it doesn't have any of the resources from the catalog added to it yet.  Before we deploy the app let's add one.

Click on the `Add Resource` button.  You will see a dialog with a list of the categories of resources to choose from.  Click on `Data` then click `Next`.

![Add Data resource](./images/ResourcesData.png)

Next you will see a list of available services in the `Data` category.  

!!! note
    *This list may be different from the list of services in the `Data` category in the catalog.  Not all services in the catalog are available for use with an IBM Lite Account.*

![Resources in Data catagory](./images/DataCloudant.png)

Click on `Cloudant` and click `Next`.  You will be prompted to select the region in which you want to create the resource.  

![Select a region](./images/CloudantRegion.png)
<br><br><br>
Make sure you select `US South` as the region and click `Create`.  You will see messages that your service is being created and will be taken back to your application details page.  You can see that now the service is bound to your application and you will see the service credentials for it.

![App details with resource](./images/AppDetailsWithResource.png)
<br><br><br>
Now you are ready to deploy your app!

Click on the `Deploy to Cloud` button in the `Deploy your App` tile.

![Deploy your application](./images/DeployAppCloudFoundry.png)

In the dialog that pops up Click the `Cloud Foundry App` tile.  Cloud Foundry organizes resources into `Spaces`; notice that the `space` dropdown has the value of `dev` already selected.  This space was created for you automatically when you created your account.  Your organization got created automatically as well, and your email address was used to name your organization.  You can change this later if you wish.

Click `Create`.

You will see some messages that resources are being allocated and that your toolchain was created successfully.  The App Details page should show that your toolchain is configured.

![Application Deployed](./images/AppDeployedCloudFoundry.png)
<br><br><br>
Click on the `View Toolchain` button.  A toolchain is a set of tool integrations that support development, deployment, and operations tasks.
<br><br><br>
![Application toolchain](./images/Toolchain.png)

The Continuous Delivery service in IBM Cloud provides a collection of developer tools that can be linked together into toolchains.  The toolchain in the screen shot above is a typical starter toolchain that contains tools for you to store your code, track issues, deploy your application and to edit your code right in the browser.  

Click on the `Git` tile.

![Code repository](./images/CodeGithub.png)

!!! note
    *You may see some orange banners at the top when you first open your repo.  These are normal, and are warning you that you need to create a Personal Access Token if you want to clone the repo locally to your machine.  We will not be doing that in the lab so you can close those alerts.  Dang, yes we do need to do this, as Orion also requires it*

IBM Cloud provides a built-in instance of Git that you can use to manage your code.  To keep things simple the starter kit uses this internal repository to manage your code, but toolchains support integrations to Github, GitLab, Bitbucket, Rational Team Concert and other tools as well.

Click the `Back` button on your browser to return to the toolchain.

Click on the `Delivery Pipeline` tile in the toolchain to see the delivery pipeline for your application.  Your delivery pipeline should look similar to the one in the screen shot below.

![Delivery pipeline](./images/DeliveryPipeline.png)

You can see that the delivery pipeline consists of a Build stage and a Deploy stage.  The build stage for a node.js application that essentially runs the `npm build` command and packages up the directory into a zip file that gets stored internally and passed to the Deploy stage.  The Deploy stage uses the Cloud Foundry CLI to push your application to IBM Cloud.

!!! note
    *You might see that the Deploy stage is still running.  This is okay, just wait for it to finish before proceeding.  If the Deploy stage shows as `Failed` just click the Play button to run it again.*

When the Deploy stage shows that it has passed and your application has a little green dot next to it go ahead and click the URL for your application.

OOPS!  You got a Not Found error, right?  Not to worry, this was expected.  It occurred because we haven't actually add any of our own logic to the app yet, and the code doesn't currently handle the default route.  However, the initial code does include a couple of routes that are used by IBM Cloud to monitor the health of your application.  

In your browser add `/health` to the end of your app URL and hit enter.  You should see some JSON in the browser:

```{"status":"UP"}```

That means your application is up and running!
