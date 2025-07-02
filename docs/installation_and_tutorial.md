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
- [TIA Portal guidelines](#tia-portal-guidelines)
- [How to use WinCC Unified Runtime Manager](#how-to-use-wincc-unified-runtime-manager)
  - [Start the runtime](#start-the-runtime)
  - [Stop the runtime](#stop-the-runtime)
  - [Secure download](#secure-download)
  - [Auto Scale](#autoscale)
  - [Media files](#media-files)
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

Clicking on a created project will lead you to the following screen. On the left bar there will be available a tree with all the devices created. Click on the **Add new device** button to create a new one.

Use WinCC Unified PC Runtime version V19 Upd2 or newer from the hardware catalog

![device1](graphics/device1.png)

### Post-configuration checks

After adding the WinCC Unified PC Runtime device, verify and adjust the following settings to work around unsupported Industrial Edge features:

- **Runtime Collaboration**  
  Do *not* activate Runtime Collaboration.

  ![Runtime Collaboration disabled](graphics/runtime_collaboration.png)

- **Database Type**  
  Set to **SQLite** (Microsoft SQL is not supported).   
  
  ![Database Type: SQLite](graphics/database_type.png)

- **GMP / Audit Option**  
  Disable the Audit feature (WinCC Unified “Audit” is not supported). 

  ![GMP / Audit option disabled](graphics/gmp_audit.png)

- **User Management**  
  Switch to Local user management only (central user management is not supported). 

- **Redundancy**  
  Do *not* enable Redundancy (unsupported).

  ![Redundancy disabled](graphics/redundancy.png)

- **Reporting**  
  Do *not* enable Reporting (unsupported).

  ![Reporting disabled](graphics/reporting.png)

## Creating a screen

Once we have created a device, its properties are shown when it is accessed:

![createscreen1](graphics/createscreen1.png)

In the left side menu, click on **Screens** and then click on **Add new screen** button to add a new one:

![createscreen2](graphics/createscreen2.png)

Now the created screen will appear under **Screens** and, since it is the first screen created, the screen will be set as the **Start Screen**:

![createscreen3](graphics/createscreen3.png)

## Screen items

Once the screen is created and opened, items can be created by drag and drop from the toolbox:

![screenitems1](graphics/screenitmes1_new.jpg)

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

![tags3](graphics/tags3.png)

### Create internal tags

Also internal tags can be manually created in a HMI Tag Table and connection type must be set to **Internal Tag**:

![tags1](graphics/tags1.png)

## Connect tags to screen items

Once the tags are created, they can be connected to the screen items. Insert a screen item:

![tagstoscreen1](graphics/tagstoscreen1_new.jpg)

In properties go to three dots of the dynamization rectangle and select **Tag**:

![tagstoscreen2](graphics/tagstoscreen2-1.jpg)

Select 'Tag...' and then choose a tag that you want to connect:

![tagstoscreen3](graphics/tagstoscreen3.png)

Repeat the process for any screen item that you want to connect. You can easily Drag & Drop a tag into your screen to create automatically an IO-field with connected HMI tag:

![tagstoscreen4](graphics/tagstoscreen4.jpg)

## OPC UA Server

To operate as an OPC UA server go to the 'Runtime settings' in the left side menu and click on the opc ua server checkbox. If you check below, you can see the port which will be used to access the OPC UA Server, this needs to be changed to the port 34002.

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

## TIA Portal guidelines

In case you need more information related to the engineering of the project in TIA Portal, you can refer to the following [documentation](https://support.industry.siemens.com/cs/document/109782433/simatic-wincc-unified-tutorial-center-(videos)?dti=0&lc=en-WW). In addition, there is an available guideline for efficient engineering in [SIOS](https://support.industry.siemens.com/cs/document/109827603/engineering-guideline-for-wincc-unified?dti=0&lc=en-US).

## How to use WinCC Unified Runtime Manager

To start the runtime go to the Wincc Runtime app:

![start1](graphics/start1.png)

You will see a login page, where you can login with the credentials downloaded within the project. At least one user with administration rights is required to access the Web Runtime Manager.
<br>Note: Default user: **uoeuser**, Default password: **User@uoe**. Please, keep in mind that this credentials will be overwritten once a TIA Portal project is downloaded with UMC-users.

![login](graphics/login.png)

If you want to add a user to change the access rights or any other reason, you can do it in the TIA Project:

![addUser](graphics/addUser.png)

If the project downloaded is running you will see a green light that indicates that the runtime is ready:

![start2](graphics/start2.png)

### Start the runtime

Click on the WinCC Unified Runtime button:

![start3](graphics/start3.png)

And the Start Screen that is indicated in the project will appear:

![start4](graphics/start4.jpg)

### Stop the runtime

To stop the runtime, select **Stop Project** in the WinCC Unified Web Runtime Manager:

![start5](graphics/start5.png)

Wait until the runtime status is on not started, and in the WinCC Runtime app a red light will be now on the project:

![start7](graphics/start7.png)

### Secure download

To prevent unauthorized runtime access, activate the secure download option in the TIA Project as well as the WinCC Unified Runtime Manager.

TIA Portal:

![secureDown2](graphics/secureDown2.png)

WinCC Unified Runtime Manager:

![secureDown1](graphics/secureDown.png)

### AutoScale

Enabling AutoScale option adapts screen automatically on window size of client / web browser. Screens designed on a certain device with is displayed on another device with different window size maintaining consistency.

![autoScale](graphics/autoScale.png)

### Media files

Upload media files via the Web Runtime Manager to your Unified application and display them via Web Control or Media Control.

![mediaFiles](graphics/mediaFiles.png)

## Trace Settings

To enable Logging Service from the WinCC Unified Runtime app go to the configuration and enable the following settings. Also you can download each trace separately .csv file clicking in the **Download Logs** at the top right corner:

![trace1](graphics/trace1.png)

You can also activate the trace forwarder and receive the traces with Trace Viewer foe analyzing the app:

- Trace Viewer is installed by WinCC Unified (Tia Portal)
- Activate the 'Receiver' mode via the following command on remote host:

`
C:\ProgramFiles\Siemens\Automation\WinCCUnified\bin\RTILtraceTool.exe -mode receiver -tcp -host <IP of Edgebox> -port 35000
`

![trace3](graphics/trace3.png)

![trace4](graphics/trace4.png)
