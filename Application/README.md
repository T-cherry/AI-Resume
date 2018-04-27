# Watson Assistant (formerly Conversation) Car Dashboard Demo Application
[![Build Status](https://travis-ci.org/watson-developer-cloud/car-dashboard.svg?branch=master)](http://travis-ci.org/watson-developer-cloud/car-dashboard)
[![codecov.io](https://codecov.io/github/watson-developer-cloud/conversation-simple/coverage.svg?branch=master)](https://codecov.io/github/watson-developer-cloud/car-dashboard?branch=master)


This application demonstrates how the Watson Assistant service uses intent capabilities in an animated car dashboard UI.

For more information about Watson Assistant, see the [detailed documentation](https://console.bluemix.net/docs/services/conversation/index.html#about).

[See the demo](http://conversation-demo.mybluemix.net/).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<img src="readme_images/bluemix.png" width="200"/>](#bluemix)     &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<img src="readme_images/local.png" width="200"/>](#local)

## How the app works
The app interface is designed and trained for chatting with a cognitive car. The interface allows the user to enter input either
using text, in the edit field at the bottom of the UI or via speech via by pressing the mic button.
Your questions and commands are run against a
small set of sample data trained with intents like these:

* `turn_on`
* `weather`
* `capabilities`

These intents help the system to understand variations of questions and commands that you might submit.
For example, if you say *"Wipers on"* or *"I want to turn on the windshield wipers"*, the system
understands that in both cases your intent is the same and responds accordingly.

# <a name="bluemix"></a> Getting Started using IBM Cloud

![](readme_images/deploy-on-bluemix-simple-app.png)

## Before you begin
1 Ensure that you have an [IBM Cloud account](https://console.ng.bluemix.net/registration/).

2 Ensure that you have the necessary space available in your IBM Cloud account. This action deploys 1 application and 3 services.
   * You can view this on your IBM Cloud Dashboard. Tiles will show what space you have available.
   * For example, for Services & APIS
   
   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/services.PNG)

## Deploy the App
1 Click this button to Deploy to IBM Cloud.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [![Deploy to IBM Cloud](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://github.com/watson-developer-cloud/car-dashboard)

2 Log in with an existing IBM Cloud account or sign up.

3 Select your Organization, Toolchain Name, Region, and Space, then click the`Deploy`buton.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/deploy.PNG)

* This performs multiple actions:
  - Creates the app
  - Creates a Watson Assistant service instance that the user needs for workspace creation
  - Creates instances for a Speech To Text service and Text To Speech service

* Your`car-dashboard`app is ready now, click`Delevery Pipeline`to deploy your app.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/toolchain-ready.png)

5 Once your app has been built and deployed, navagate to your IBM Cloud Dashboard and [import a workspace](#workspace).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/deploy-finished.png)

## <a name="usingCloudfoundry"></a> Using Cloudfoundry CLI tool to deploy your application

To build the application:

1 Download and install the [Cloudfoundry CLI](https://github.com/cloudfoundry/cli) tool.

2 Git clone the project `https://github.com/watson-developer-cloud/car-dashboard`

3 Navigate to the `car-dashboard` folder

4 Connect to IBM Cloud in the command-line tool:

 For US Region

 ```sh

 $ cf api https://api.ng.bluemix.net

 ```

 ```sh

 $ cf login -u <your user ID>

 ```

5 Create the Watson Assistant service in IBM Cloud (our CLI is being updated, for now, use the `create-service` conversation command):

 ```sh

 $ cf create-service conversation free watson-assistant-service

 ```

6 Push it live:

 ```sh

 $ cf push <application-name>

 ```
 The name you use determinates your application URL initially, such as `<application-name>.mybluemix.net`.

# <a name="local"></a> Getting Started locally

## Before you begin

1 Ensure that you have an [IBM Cloud account](https://console.ng.bluemix.net/registration/). While you can do part of this deployment locally, you must still use Bluemix.

2 In IBM Cloud, [create a Watson Assistant Service](https://console.bluemix.net/docs/services/conversation/getting-started.html#gettingstarted).
- Copy the Service Credentials for later use.
- [Import a workspace](#workspace)

3 **OPTIONAL**: If you want to use **Text To Speech** and/or **Speech To Text** in your locally runnning app, create a `text-to-speech` service and/or a `speech-to-text` service like you did in step 2.
- Copy the Service Credentials for later use.

## Running locally

  The application uses [Node.js](http://nodejs.org/) and [npm](https://www.npmjs.com/).

1 Copy the credentials from your `watson-assistant-service` service in IBM Cloud to a `.env` file in the root.
- Look at `.env.example` as an example to create your `.env` file.

2 **OPTIONAL**: If you want to use Text To Speech and/or Speech To Text in your locally runnning app, copy the credentials from your `text-to-speech` service and/or `speech-to-text` service in IBM Cloud to a `.env` file in the root.
- Look at `.env.example` as an example to add to your `.env` file.

3 Use the Watson Assistant tooling app to create a workspace, as described above, and add the workspace ID environment variable to the `.env` file. For details about obtaining the workspace ID, see Step 6 - 7 in the next section.

4 Install [Node.js](http://nodejs.org/).

5 Open the terminal, go to the project folder, and run this command:
```sh

npm install

```

6  Build the UI by running this command:
```sh

npm run build

```

7  Start the application by running this command:
```sh

npm start

```

8 Open `http://localhost:3000` in a browser.

_Note: If you are interested in deploying you local application or the changes you have made locally to IBM Cloud, go to [this section](#usingCloudfoundry)_

# <a name="workspace"></a> Import a workspace

1 You need to import the app's workspace. To do that, go to the IBM Cloud Dashboard and select the Watson Assistant service instance. Once there, select the **Service Credentials** menu item.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/credentials.png)

2 Select **ADD CREDENTIALS**. Name your credentials then select **ADD**.

3 Return to the **Manage** menu item and select **Launch Tooling**. This opens a new tab in your browser, where you are prompted to login if you have not done so before. Use your IBM Cloud credentials.

4 Download the [exported JSON file](https://raw.githubusercontent.com/watson-developer-cloud/conversation-simple/master/training/car_workspace.json) that contains the Workspace contents.

5 Select **Import**. Browse to (or drag and drop) the JSON file that you downloaded in Step 4. Choose to import **Everything(Intents, Entities, and Dialog)**. Then select **Import** to finish importing the workspace.

6 Refresh your browser. A new workspace tile is created within the tooling. Select the _menu_ button within the workspace tile, then select **View details**:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![Workpsace Details](readme_images/details.PNG)

<a name="workspaceID">
In the Details UI, copy the 36 character UNID **ID** field. This is the **Workspace ID**.
</a>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ![](readme_images/workspaceid.PNG)


7 Return to your application, either in your local dev environment, or in IBM Cloud. If running on IBM Cloud, you need to [add environment variables](#env).

For more information on workspaces, see the full  [Watson Assistant service documentation](https://console.bluemix.net/docs/services/conversation/configure-workspace.html#configuring-a-conversation-workspace).

# <a name="env"></a> Adding environment variables in IBM Cloud

1 In IBM Cloud, open the application from the Dashboard. Select **RUNTIME** on the left side menu.

2 Select **ENVIRONMENT VARIABLES** and scroll down to **USER-DEFINED**.

3 Select **ADD**.

4 Add a variable with the name **WORKSPACE_ID**. For the value, paste in the Workspace ID you [copied earlier](#workspaceID). Select **SAVE**.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/env.png)

5 Restart your application.


# Troubleshooting in IBM Cloud

#### In the Classic Experience:
- Log in to IBM Cloud, you'll be taken to the dashboard.
- Navigate to the the application you previously created.
- Select **Logs**.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/logs.PNG)

- If you want, filter the LOG TYPE by "APP".

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/filter.PNG)

#### In the new IBM Cloud:
- Log in to IBM Cloud, you'll be taken to the dashboard.
- Select **Compute**

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/compute.PNG)

- Select the application you previously created.
- Select **Logs**.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/logs1.PNG)

- If you want, filter the Log Type by selecting the drop-down and selecting **Application(APP)**.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![](readme_images/filter1.PNG)

### With CLI

```
$ cf logs < application-name > --recent
```

# License

  This sample code is licensed under Apache 2.0.
  Full license text is available in [LICENSE](LICENSE).

# Contributing

  See [CONTRIBUTING](CONTRIBUTING.md).


## Open Source @ IBM

  Find more open source projects on the
  [IBM Github Page](http://ibm.github.io/).
