# Installation and Tutorial

- [Installation](#installation)
- [Creating a project](#creating-a-project)
- [Creating a device](#creating-a-device)
- [Creating a screen](#creating-a-screen)
- [Screen Items](#screen-items)
- [Connections](#connections)
  - [Browse IE Databus from WinCC Unified Online Engineering](#browse-ie-databus-from-wincc-unified-online-engineering)
- [Tags](#tags)
  - [Create tags out of connection](#create-tags-out-of-connection)
  - [Create internal tags](#create-internal-tags)
  - [Import tags from TIA Portal](#import-tags-from-tia-portal)
- [Connect tags to screen items](#connect-tags-to-screen-items)
- [Scripting](#scripting)
  - [Global Scripts](#global-scripts)
  - [Shortcuts](#shortcuts)
- [OPC UA Server](#opc-ua-server)
- [Load a project into runtime](#load-a-project-into-runtime)
  - [Remote Download](#remote-download)
  - [Offline Download](#offline-download)
- [Alarms](#alarms)
- [Logs](#logs)
- [Trends](#trends)
- [Start the runtime](#start-the-runtime)
- [Trace Settings](#trace-settings)

## Installation

Download the app and "WinCC Unified Runtime" from the Industrial Edge HUB into your Industrial Edge Management. The application should now be available in the IEM catalog.

1. Login on the IEM where you control your IED
2. Go to the catalog
3. Open the app "WinCC Unified Runtime" and install it on your IED
4. Login to the IED where you installed the apps
5. Click on the app icon of "WinCC Unified Runtime" to open this app

Download the Hardware Support Package from [SIOS](https://support.industry.siemens.com/cs/document/10996394?dti=-1&lc=en-WW) and install the HSP following the next steps:

1. Open TIA Portal in your Engineering station.
2. Go to **Options** -> **Support packages**.

![SupportPackages](graphics/supportpackages.png)

3. Select **Add from file system** and click install.

![addInfo](graphics/addInfo.png)

4. Restart TIA Portal after the installation.

## Creating a project

Once you are in the TIA Portal you can click on **Project** -> **New** to start a new engineering project:

![createproject1](graphics/createproject1.png)

Now you will a popup asking for the Project Name and folder where you want to store your created project where you can click **Create** and start working on it:

![createproject2](graphics/createproject2.png)

## Creating a device

Clicking on a created project will lead you to the following screen. On the left bar there will be available a tree with all the devices created. Click on the **Add new device** button to create a new one.

Unified Runtime for Industrial Edge can be found in TIA – Hardware catalog under SIMATIC HMI applications


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

![screenitems1](graphics/screenitmes1_new.jpg)

Place the item in the screen area and when it is created you will see all the properties of the item:

![screenitems3](graphics/screenitmes3_new.jpg)

## Connections

To create a connection between the WinCC Unifed on Industrial Edge and a PLC go to You first need to add an Ethernet communication module:

![connections1](graphics/connections1.png)

Connect the ports from the PLC to the added communication module in the **Network** view and in the **Connection** view:

![connections2](graphics/connections2.png)

### Browse IE Databus from WinCC Unified Online Engineering

It is needed to configure a connection from TIA Portal and Industrial Edge, to do so, you can refer to the following [documentation](https://github.com/industrial-edge/opc-ua-application-getting-started/blob/main/docs/Installation.md#configuration) that explains how to set up the connection.

Then, in the WinCC Unified Runtime, click on 'Settings' and add the databus credentials:

![iedatabus5](graphics/iedatabus5.PNG)

Go to configuration and in the 'Tags' part select the ones that are needed to be published and suscribed. Also, enable the services for 'Tag Publishing' and 'Tag Suscribe':

![iedatabus6](graphics/iedatabus6.PNG)


## Tags

There are different ways to create tags in our WinCC Unifed on Industrial Edge.

### Create tags out of connection

When we establish a connection to a PLC, we can use these tags within our WinCC Unifed on IE project just by clicking on the 'Created' checkbox:

![tags1](graphics/tags1.png)

### Create internal tags

Also internal tags can be manually created under 'Internal tags' in the left side menu:

![tags3](graphics/tags3.png)

### Import tags from TIA Portal

The TIA Portal extension **'SIMATIC SCADA Export'** provides a mechanism to export the PLC configuration data (variables and alarms). The exported PLC data can be then imported as tags into the WinCC Unified Online Engineering.

To download the SIMATIC SCADA Export, open our SIOS-Portal and search for the entry "109748955" or click on this [link](https://support.industry.siemens.com/cs/document/109748955/simatic-scada-export-for-tia-portal?dti=0&lc=en-US). Download and install the fitting version for your TIA Portal version.

Right click on the PLC and click on Export to SIMATIC SCADA and enter the filename and define the path:

![import5](graphics/import5.png)
![import6](graphics/import6.png)

Open the project in WinCC Unified Online Engineering and go to 'Tags' on the left side menu. Click on the three dots > "Import S7/S7+ connection". Select the exported file and click on 'OK'.

The connection has been imported. You can see the tags imported and you can choose the desired PLC tags and PLC data types you want to use in the project by selecting 'created':

![import9](graphics/import9.png)

If you go to 'Tags', all the ones that were selected are ready to be used in the project:

![import10](graphics/import10.png)

Also if you go to 'Connections', both interfaces have been imported and if you have some certificates for secure communication, they are imported as well:

![import11](graphics/import11.png)

## Connect tags to screen items

Once the tags are created, they can be connected to the screen items. Insert a screen item:

![tagstoscreen1](graphics/tagstoscreen1_new.jpg)

In properties go to three dots of the dynamization rectangle and select "Tags":

![tagstoscreen2](graphics/tagstoscreen2-1.PNG)

Select 'Tag...' and then choose a tag that you want to connect:

![tagstoscreen3](graphics/tagstoscreen3.png)

Repeat the process for any screen item that you want to connect. You can easily Drag & Drop a tag into your screen to create automatically an IO-field with connected HMI tag:

![tagstoscreen4](graphics/tagstoscreen4-1_new.jpg)

## Scripting

As same as working with Tia Portal in the WinCC part, scripting is also allowed in the app. For this part we are creating another screen to create a simple script to switch between two screens:

![script1](graphics/script1.png)

Place a button on the first screen, go to the 'Events' tabs in the right side menu and click on 'Add script':

![script2](graphics/script2_upd_new.jpg)

A scripting window opens. On the left side menu several predefined code templates are provided:

![script3](graphics/script3.png)

In this case, we can open the 'Screen' dropdown on the left side and drag the template 'Change base screen' into the script. Don't forget to rename the screen name inside the code:

![script4](graphics/script4.png)

Click on OK and the script will be applied for the button:

![script5](graphics/script5.png)

### Global scripts

To create a global module for your scripts go to 'Scripts' in the left side menu and create a global module with all the functions needed:

![script7](graphics/script7.png)

Then, on the scripting part of an item you can import all your global and predefined scripts to use them:

![script6](graphics/script6.png)

### Shortcuts

You can select system functions and enums via intellisense or autocompletion just by clicking 'ctrl' + 'space' shortcut on the keyboard:

![script8](graphics/script8.png)

By using the 'alt' + '.' shortcut you can jump to the definition of a function:

![script9](graphics/script9.png)

And using the 'ctrl' + 'i' shortcut the info about the function pops out:

![script10](graphics/script10.png)

## OPC UA Server

To operate as an OPC UA server go to the 'Runtime settings' in the left side menu and click on the opc ua server checkbox. The OPC UA Server can be accesed via Default port: 34002.

![connections6](graphics/connections6.png)

## Load a project into runtime

To load a project, select your device on the left side menu and scroll down to 'Runtime status':

![load1](graphics/load1.png)

Click on 'Download' and when the procces is finished click on 'OK':

![load2](graphics/load2.png)

Then click on 'Start runtime' and wait until the runtime status is on running:

![load3](graphics/load3.png)

### Remote Download

To load the project in runtime on other Edge Device, you just need to configure its IP adress on the device configuration:

![remote2](graphics/remotedown2.png)

![remote1](graphics/remotedown1.png)

### Offline Download

You can create an offline runtime project in WinCC Unified Online Engineering by clicking on the 'Download' button in the section 'Offline download':

![offdown1](graphics/offdwon1.png)

Then, in WinCC Unified Runtime on IE you can upload the file that was downloaded by clicking on the 'Upload' button:

![offdown2](graphics/offdwon2.png)

## Alarms

The alarms are created at the desired trigger tag - in this case at an internal tag. We can create two different types: analog and discrete alarms. The alarm type depends on the selected tag data type. For this example we are creating both.

For the analog alarms, an 'Int' tag is created:

![alarms1](graphics/alarms1.png)

On the bottom menu, tab 'Analog alarms', we create all the alarms we need with it's conditions:

![alarms2](graphics/alarms2.png)

For the discrete alarms, the creation is made in the same way, but the data type must be 'Word':

![alarms3](graphics/alarms3.png)

On the bottom menu, tab 'Analog alarms', the alarms are created:

![alarms4](graphics/alarms4.png)

In this example, we are creating another screen with alarm control screen item and some different buttons to pop up the alarms:

![alarms5](graphics/alarms5_new.jpg)

When the runtime is active and the alarms are popped out they will appear in the chart:

![alarms6](graphics/alarms6.png)

## Logs

The logs can be created for each tag - in this case at an internal tag. We can choose two different logging modes: 'Cyclic' and 'On change'.

Create a logging with 'Cyclic' mode:

![logs1](graphics/logs1.png)

On the bottom menu, tab 'Logging tags', the logging is created:

![logs12](graphics/logs2.png)

Create a logging with 'On change' mode:

![logs3](graphics/logs3.png)

![logs4](graphics/logs4.png)

Introduce the process controll item to a screen:

![logs5](graphics/logs5.png)

Finally the logs are shown in the runtime:

![logs6](graphics/logs6.png)

## Trends

To add a trend go to the add screen items and in the advanced bar select trend control:

![trends1](graphics/trends1_new.jpg)

In its properties to add different trends to appear in the item, go to Trends:

![trends2](graphics/trends2.png)

And select the tag you want to control:

![trends3](graphics/trends3.png)

In the runtime the trend will be filled:

![trends4](graphics/trends4.png)

## Start the runtime

To start the runtime go to the Wincc Runtime app:

![start1](graphics/start1.png)

If the project downloaded is running you will see a green light that indicates that the runtime is ready:

![start2](graphics/start2.png)

Click on the WinCC Unified Runtime button:

![start3](graphics/start3.png)

And the Start Screen that is indicated in the project will appear:

![start4](graphics/start4.png)

To stop the runtime go back to your device and click on Stop runtime:

![start5](graphics/start5.png)

Wait until the runtime status is on not started:

![start6](graphics/start6.png)

And in the WinCC Runtime app a red light will be now on the project:

![start7](graphics/start7.png)

## Trace Settings

To download or forward traces from the WinCC Unified Online Engineering app go to the settings and enable the following settings:

![trace1](graphics/trace1.png)

Also you can download each trace separately .csv file going to the app's more info site:

![trace2](graphics/trace2.png)

You can also activate the trace forwarder and receive the traces with Trace Viewer foe analyzing the app:

- Trace Viewer is installed by WinCC Unified (Tia Portal)
- Activate the 'Receiver' mode via the following command on remote host:

`
C:\ProgramFiles\Siemens\Automation\WinCCUnified\bin\RTILtraceTool.exe -mode receiver -tcp -host <IP of Edgebox> -port 35505
`

![trace3](graphics/trace3.png)
