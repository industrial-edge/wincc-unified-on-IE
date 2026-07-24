# Installation and Tutorial

- [Installation](#installation)
- [Creating a project](#creating-a-project)
- [Creating a device](#creating-a-device)
- [Creating a screen](#creating-a-screen)
- [Screen Items](#screen-items)
- [Connections](#connections)
- [Tags](#tags)
  - [Create tags out of connection](#create-tags-out-of-connection)
  - [Create internal tags](#create-internal-tags)
- [Connect tags to screen items](#connect-tags-to-screen-items)
- [Scripting](#scripting)
  - [Global Scripts](#global-scripts)
  - [Shortcuts](#shortcuts)
- [OPC UA Server](#opc-ua-server)
- [Load a project into runtime](#load-a-project-into-runtime)
  - [Offline Download](#offline-download)
  - [Offline Download via IEM](#offline-download-via-industrial-edge-management)
- [Alarms](#alarms)
- [Logs](#logs)
- [Trends](#trends)
- [Further engineering workflows](#further-engineering-workflows)
- [TIA Portal guidelines](#tia-portal-guidelines)
- [How to use WinCC Unified Runtime Manager](#how-to-use-wincc-unified-runtime-manager)
  - [Start the runtime](#start-the-runtime)
  - [Stop the runtime](#stop-the-runtime)
  - [Secure download](#secure-download)
  - [Auto Scale](#autoscale)
  - [Media files](#media-files)
- [Migration workflow from V5.0.0 to V21 Upd 2](#migration-workflow-from-v500-to-v21-upd-2)
- [Trace Settings](#trace-settings)

## Installation

Download the app "WinCC Unified Runtime for Industrial Edge" from the Industrial Edge HUB into your Industrial Edge Management. The application should now be available in the IEM catalog.

1. Login on the IEM where you control your IED
2. Go to the catalog
3. Open the app "WinCC Unified Runtime" and install it on your IED
4. Login to the IED where you installed the apps
5. Click on the app icon of "WinCC Unified Runtime" to open this app

## Creating a project

Once you are in the TIA Portal you can click on **Project** -> **New** to start a new engineering project:

![createproject1](graphics/createproject1.png)

Now you will a popup asking for the Project Name and folder where you want to store your created project where you can click **Create** and start working on it:

![createproject2](graphics/createproject2.png)

## Creating a device

After creating a project, open the project view. The project tree on the left displays all configured devices. Click **Add new device** to create a device.

Add the **Unified Edge Device V21.0.1.0** from the device catalog.

![device1](graphics/device1.png)

## Creating a screen

Once we have created a device, its properties are shown when it is accessed:

![createscreen1](graphics/createscreen1.png)

In the left side menu, click on **Screens** and then click on **Add new screen** button to add a new one:

![createscreen2](graphics/createscreen2.png)

Now the created screen will appear under **Screens** and, since it is the first screen created, the screen will be set as the **Start Screen**:

![createscreen3](graphics/createscreen3.png)

## Screen items

Once the screen is created and opened, items can be created by drag and drop from the toolbox:

![screenitems1](graphics/screenitmes1_new.png)

Place the item in the screen area and when it is created you will see all the properties of the item:

![screenitems3](graphics/screenitmes3_new.jpg)

## Connections

To create a connection between the Industrial Edge device and a PLC, an Ethernet communication module is required to be added to the device:

![connections1](graphics/connections1.png)

Connect the ports from the PLC to the added communication module in the **Network** view and in the **Connection** view:

![connections2](graphics/connections2.png)

## Tags

There are different ways to create tags in our WinCC Unified project for Industrial Edge.

### Create tags out of connection

When we establish a connection to a PLC, we can drag and drop a tag from the PLC to the HMI Tags:

![tags3](graphics/tags/tags3.png)

### Create internal tags

Also internal tags can be manually created in a HMI Tag Table and connection type must be set to **Internal Tag**:

![tags1](graphics/tags/tags1.png)

## Connect tags to screen items

Once the tags are created, they can be connected to the screen items. Insert a screen item:

![tagstoscreen1](graphics/tags/tagstoscreen1_new.jpg)

In properties go to three dots of the dynamization rectangle and select **Tag**:

![tagstoscreen2](graphics/tags/tagstoscreen2-1.jpg)

Select 'Tag...' and then choose a tag that you want to connect:

![tagstoscreen3](graphics/tags/tagstoscreen3.png)

Repeat the process for any screen item that you want to connect. You can easily Drag & Drop a tag into your screen to create automatically an IO-field with connected HMI tag:

![tagstoscreen4](graphics/tags/tagstoscreen4.jpg)

## OPC UA Server

To operate as an OPC UA server, go to 'Runtime settings' in the left-side menu and enable the OPC UA server checkbox. The default port is 34002 in WinCC Unified Edge RT.

![connections6](graphics/connections6.png)

## Load a project into runtime

To load the project in runtime on the Edge Device, you just need to configure its IP adress on the device configuration:

![remote2](graphics/remotedown2.png)

![remote1](graphics/remotedown1.png)

### Offline Download

In case there is no online connection established to the IED, you have the chance to create an offline runtime project in TIA Portal by drag and drop to the card reader:

![offdown1](graphics/offdown1.png)

Then, in WinCC Unified Runtime on IE you can upload the file that was downloaded by clicking on the 'Upload' button:

![offdown2](graphics/offdown2.png)

### Offline download via Industrial Edge Management

An offline download to the IE Device is also possible via the IEM. Open the IEM, go to **My Installed Apps** and select **WinCC Unified Runtime**

![iemdownload](graphics/iem_download.png)

Once the app's tab is open, click on the **Update configuration** button. Then, add the file in the **+** button within **autoDownload**. After the file is loaded, click on **Update Now**

![iemdownload3](graphics/iem_download3.png)

## Alarms

The alarms are created at the desired trigger tag - in this case at an internal tag. We can create two different types: analog and discrete alarms. The alarm type depends on the selected tag data type. For this example we are creating both.

For the analog alarms, an 'Int' tag is created:

![alarms1](graphics/alarms1.png)

On the bottom menu, tab 'Analog alarms', we create all the alarms we need with it's conditions:

![alarms2](graphics/alarms2.png)

For the discrete alarms, the creation is made in the same way, but the data type must be 'Word'. On the bottom menu, tab 'Analog alarms', the alarms are created:

![alarms4](graphics/alarms3.png)

In this example, we are creating another screen with alarm control screen item and some different buttons to trigger different alarms:

![alarms5](graphics/alarms5_new.png)

When the runtime is active and the alarms are raised, they will appear in the alarm control:

![alarms6](graphics/alarms6.png)

## Logs

The logs can be created for each tag - in this case at an internal tag. We can choose two different logging modes: 'Cyclic' and 'On change'.

Create a logging with 'Cyclic' mode. On the bottom menu, tab 'Logging tags', the logging is created. 

![logs1](graphics/logs1.png)

Create a logging with 'On change' mode:

![logs3](graphics/logs2.png)

Finally the logs are shown in the runtime:

![logs6](graphics/logs6.png)

## Trends

To add a trend go to the Toolbox, select trend control and drag and drop into the screen:

![trends1](graphics/trends1.png)

In its properties to add different trends to appear in the item, go to Trends and select the tag/logging tag you want to control::

![trends2](graphics/trends2.png)

In the runtime the trend will be filled:

![trends4](graphics/trends4.png)

## Further engineering workflows

For additional engineering workflows, see:

* [How to display Industrial Edge applications within WinCC Unified Runtime](further_engineering_workflows.md#how-to-display-industrial-edge-applications-within-wincc-unified-runtime)
* [Connect WinCC Unified Runtime on Edge with IIH via OPC UA](further_engineering_workflows.md#connect-wincc-unified-runtime-on-edge-with-iih-via-opc-ua)
* [How to exchange HMI variables with IIH Essentials](further_engineering_workflows.md#how-to-exchange-hmi-variables-with-iih-essentials)

## TIA Portal guidelines

In case you need more information related to the engineering of the project in TIA Portal, you can refer to the following [documentation](https://support.industry.siemens.com/cs/document/109782433/simatic-wincc-unified-tutorial-center-(videos)?dti=0&lc=en-WW). In addition, there is an available guideline for efficient engineering in [SIOS](https://support.industry.siemens.com/cs/document/109827603/engineering-guideline-for-wincc-unified?dti=0&lc=en-US).

## How to use WinCC Unified Runtime Manager

To open the **SIMATIC WinCC Unified Runtime Manager**, open the **SIMATIC WinCC Unified Runtime** app:

![Open the SIMATIC WinCC Unified Runtime app](graphics/runtime_manager/start1.png)

### First access and mandatory password change

When the SIMATIC WinCC Unified Runtime Manager is opened for the first time, the default password must be changed before the first sign-in.

The default credentials are:

* **User name:** `uoeuser`
* **Password:** `User@uoe`

To change the default password, proceed as follows:

1. Enter the user name `uoeuser` on the login page.
2. Click **Change Password**.
3. Enter the default password in the **Old password** field.
4. Enter and confirm the new password.
5. Click **Change** to complete the password change.

After changing the password, sign in with the user name `uoeuser` and the new password.

> **Important:**
> Use the default password only to complete the initial password change. Store the new password in a safe location and use it for subsequent sign-ins.

![First access and mandatory password change](graphics/runtime_manager/first_access_runtime_manager.gif)

At least one user with administrator rights is required to access the SIMATIC WinCC Unified Runtime Manager.

After downloading user administration data from TIA Portal, sign in with the credentials configured in the TIA Portal project.

To add a user or modify access rights, configure the user in the TIA Portal project:

![Configure users in TIA Portal](graphics/runtime_manager/addUser.png)

When the downloaded project is running, a green status indicator shows that the runtime is ready:

![Runtime project ready](graphics/runtime_manager/start2.png)

### Start the runtime

Click on the WinCC Unified Runtime button:

![start3](graphics/runtime_manager/start3.png)

And the Start Screen that is indicated in the project will appear:

![start4](graphics/runtime_manager/start4.jpg)

### Stop the runtime

To stop the runtime, select **Stop Project** in the WinCC Unified Web Runtime Manager:

![start5](graphics/runtime_manager/start5.png)

Wait until the runtime status is on not started, and in the WinCC Runtime app a red light will be now on the project:

![start7](graphics/runtime_manager/start7.png)

### Secure download

To prevent unauthorized runtime access, activate the secure download option in the TIA Project as well as the WinCC Unified Runtime Manager.

TIA Portal:

![secureDown2](graphics/runtime_manager/secureDown2.png)

WinCC Unified Runtime Manager:

![secureDown1](graphics/runtime_manager/secureDown.png)

### AutoScale

Enabling AutoScale option adapts screen automatically on window size of client / web browser. Screens designed on a certain device with is displayed on another device with different window size maintaining consistency.

![autoScale](graphics/runtime_manager/autoScale.png)

### Media files

Upload media files via the Web Runtime Manager to your Unified application and display them via Web Control or Media Control.

![mediaFiles](graphics/runtime_manager/mediaFiles.png)

## Migration workflow from V5.0.0 to V21 Upd 2

For the migration workflow from WinCC Unified Runtime for Industrial Edge V5.0.0 to V21 Upd 2, see:

[Migration workflow from V5.0.0 to V21 Upd 2](migration_workflow_v5_to_v21upd2.md)

## Trace Settings

For information about collecting diagnostic logs, exporting trace files and forwarding live traces to Trace Viewer, see:

[Trace Settings](trace_settings.md)
