## Installation and Tutorial

- [Installation](#installation)
- [Creating a project](#creating-a-project)
- [Creating a device](#creating-a-device)
- [Creating a screen](#creating-a-screen)
- [Connections](#connections)
- [Tags](#Tags)
- [Export tags from TIA Portal and import them with WebES](#export-tags-from-tia-portal-and-import-them-with-webes)
- [Connect tags to screen items](#connect-tags-to-screen-items)
- [Scripting](#scripting)
- [Load a project into runtime](#Load-a-project-into-runtime)
  - [Remote Download](#remote-download)
  - [Offline Download](#offline-download)
- [Alarms](#alarms)
- [Loggs](#loggs)
- [Trends](#trends)
- [Start the runtime](#start-the-runtime)

## Installation

Download the app from the Siemens HUB and then import both app files into your app catalog of your Industrial Edge Management and start the installation:
1.	Login on the IEM where you control your IED.
2.	Go to the catalog.
3.	Import the application.
4.	Browse the app files and import them.

  ![installation1](graphics/installation1.PNG)
  ![installation2](graphics/installation2.PNG)

5.  Click on the app icon.
6.  Install the app.
7.  Select your IED.
8.  Click on Install now.

  ![installation3](graphics/installation3.PNG)
  ![installation4](graphics/installation4.PNG)
  ![installation5](graphics/installation5.PNG)


9.	Login on the IED where you installed the apps and then: Click on the app icon to start WinCC Unified Online Engineering.
10.	Login on the IED where you installed the apps and then: Click on the app icon to start WinCC Unified Runtime.

  ![installation6](graphics/installation6.JPG)


## Creating a project

Once you are in the WinCC Unified Online Engineering you can click on create a project to start a new engineering project:

![createproject1](graphics/createproject1.PNG)

Now you will see your created project where you can click on and start working on it:

![createproject2](graphics/createproject2.PNG)


## Creating a device

Clicking on a created project will lead you to the following screen:

![device1](graphics/device1.PNG)

On the left bar there will be available a tree with all the projects created. On the right bar we can start to deploy and create our device. Click on the add device button to create a new one:

![device2](graphics/device2.PNG)

Now, the device should appear created in the project:

![device3](graphics/device3.PNG)


## Creating a screen

Once we have created a device, its properties are shown when it is accessed:

![createscreen1](graphics/createscreen1.PNG)

On the left side menu, click on 'Screens' to create our first one and click on add screen button to add the new one:

![createscreen2](graphics/createscreen2.PNG)

The screen created will appear in our Screens:

![createscreen3](graphics/createscreen3.PNG)


## Screen items

Once the screen is created and opened, items can be created by clicking on add screen items button:

![screenitems1](graphics/screenitems1.PNG)

A new bar will appear with all the options available:

![screenitems2](graphics/screenitems2.PNG)

Place the item in the screen area and when is created you will see in the right bar all the properties of the item:

![screenitems3](graphics/screenitems3.PNG)

On the properties bar you will see the 'most important proporties' section. It depends on the screen item and are displayed in separate section.

![screenitems5](graphics/screenitems5.PNG)

Add all the items you need and do not forget to click on the save button. An orange reminder will appear until you save the progress:

![screenitems4](graphics/screenitems4.PNG)


## Connections

To create a connection between the WinCC Unifed on Industrial Edge and a PLC go to connections:

![connections1](graphics/connections1.PNG)

Write a name for your connection, slect the connection type (OPC-UA/S7 Classic/S7 Plus) and enter the adress of the PLC:

![connections2](graphics/connections2.PNG)

Underneath 'Tags' in the left side menu, you will see the new connection created:

![connections3](graphics/connections3.PNG)

Click on the three dots and select 'Browse OPC UA server' to start searching for the data on the PLC:

![connections4](graphics/connections4.PNG)

When the search is done, the data will appear:

![connections5](graphics/connections5.PNG)


## Tags

There are different ways to create tags in our WinCC Unifed on Industrial Edge. When we make a connection to a Tia Portal project we can import the tags created in that project to our WinCC Unifed on IE project just by clicking on the created checkbox:

![tags1](graphics/tags1.PNG)

The selected tags will appear in the tab 'Tags':

![tags2](graphics/tags2.PNG)

Also tags can be created manually on the interanl Tags part:

![tags3](graphics/tags3.PNG)


## Export tags from TIA Portal and import them with WebES

First of all, open our SIOS-Portal and search for the entry "109748955" or click on this [link](https://support.industry.siemens.com/cs/document/109748955/simatic-scada-export-for-tia-portal?dti=0&lc=en-US) :

![import1](graphics/import1.PNG)

Download and install the fitting version for your TIA Portal version:

![import2](graphics/import2.PNG)

Right click on the PLC and click on Export to SIMATIC SCADA and enter the filename and define the path:

![import5](graphics/import5.PNG)
![import6](graphics/import6.PNG)

Open the project in WinCC Unified Online Engineering and go to "Tags". Click on the three dots > "Import S7/S7+ connection":

![import7](graphics/import7.PNG)

Select the exported file and click on "OK":

![import8](graphics/import8.PNG)

The connection has been imported. You can see the tags imported and you can choose the desired PLC tags and PLC data types you want to use in the project by selecting "created":

![import9](graphics/import9.PNG)

If you go to "Tags" all the ones that were clicked are ready to be used in the project:

![import10](graphics/import10.PNG)

Also if you go to "connections" both interfaces have been imported and if you have some certificates for secure communication, they are imported as well:

![import11](graphics/import11.PNG)


## Connect tags to screen items

Once the tags are created, they can be connected to the screen items. Insert a screen item:

![tagstoscreen1](graphics/tagstoscreen1.PNG)

In properties go to process value dynamic:

![tagstoscreen2](graphics/tagstoscreen2.PNG)

Select Tags and then the tag that you want:

![tagstoscreen3](graphics/tagstoscreen3.PNG)

Repeat the process for any screen item that you want to connect. In this case we are introducing an I/O field to see how the tag changes for the runtime part tutorial:

![tagstoscreen4](graphics/tagstoscreen4.PNG)


## Scripting

As same as working with Tia Portal in the WinCC part, scripting is also allowed in the app. For this part we are creating another screen to create a simple script to switch between two screens:

![script1](graphics/script1.PNG)

Place a button on the first screen and go to the events tabs and click on add script:

![script2](graphics/script2_upd.png)

An scrpiting window will be opened. To be more easily for the user a lot of code templates are created:

![script3](graphics/script3.PNG)

In this case, we can go to screen, change base screen. The templates can be dragged:

![script4](graphics/script4.PNG)

Click on OK, and the script will be visible:

![script5](graphics/script5.PNG)


## Load a project into runtime

To load a project, select 'MyDevice' on the left menu and scroll down to 'Runtime status':

![load1](graphics/load1.PNG)

Click on download and when the procces is finished click on OK:

![load2](graphics/load2.PNG)

Then click on Start runtime and wait until the Runtime status is on running:

![load3](graphics/load3.PNG)

### Remote Download

To load the a project in rnutime on other Edge Device, you just need to configure its IP adress on the device configuration:

![remote2](graphics/remotedown2.PNG)

![remote1](graphics/remotedown1.PNG)

### Offline Download

You can create an offline runtime project in WinCC Unified Online Engineering by clicking on the download offline project button:

![offdown1](graphics/offdwon1.PNG)

Then, in WinCC Unified Runtime on IE you can upload the file that was downloaded by clicking on the upload button:

![offdown2](graphics/offdwon2.PNG)

## Alarms

The alarms are created at the desired trigger tag. In this case at a internal tag. We can create two different types: analog and discrete alarms. The alarm type depends on the selected tag data type. For this example we are creating both.
For the analog ones, an int tag is created:

![alarms1](graphics/alarms1.PNG)

On the bottom, in the analog alarms part we create all the alarms we need with its conditions:

![alarms2](graphics/alarms2.PNG)

For the discrete alarms, the creation is made in the same way, but the data type must be Word:

![alarms3](graphics/alarms3.PNG)

And on the bottom as same as before, the alarms are created:

![alarms4](graphics/alarms4.PNG)

In this example, we are creating another screen with alarm control screen item and some different buttons to pop up the alarms:

![alarms5](graphics/alarms5.PNG)

When the runtime is active and the alarms are popped out they will appear in the chart:

![alarms6](graphics/alarms6.PNG)


## Loggs

To create loggs, go again to the internal tags part. In this example we are creating two different loggs.
First one:

![loggs1](graphics/logs1.PNG)

On the bottom the logging tag with its properties is modified:

![loggs12](graphics/logs2.PNG)

The second one is created in the same way:

![loggs3](graphics/logs3.PNG)

![loggs4](graphics/logs4.PNG)

Introduce the process controll item to a screen:

![loggs5](graphics/logs5.PNG)

In the runtime the loggs will be shown:

![loggs6](graphics/logs6.PNG)


## Trends

To add a trend go to the add screen items and in the advanced bar select trend control:

![trends1](graphics/trends1.png)

In its properties to add different trends to appear in the item, go to Trends:

![trends2](graphics/trends2.PNG)

And select the tag you want to control:

![trends3](graphics/trends3.PNG)

In the runtime the trend will be filled:

![trends4](graphics/trends4.PNG)


## Start the runtime

To start the runtime go to the Wincc Runtime app:

![start1](graphics/start1.PNG)

If the project downloaded is running you will see a green light that indicates that the runtime is ready:

![start2](graphics/start2.PNG)

Click on the WinCC Unified Runtime button:

![start3](graphics/start3.PNG)

And the Start Screen that is indicated in the project will appear:

![start4](graphics/start4.PNG)

To stop the runtime go back to your device and click on Stop runtime:

![start5](graphics/start5.PNG)

Wait until the runtime status is on not started:

![start6](graphics/start6.PNG)

And in the WinCC Runtime app a red light will be now on the project:

![start7](graphics/start7.PNG)
