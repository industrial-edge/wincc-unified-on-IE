## INDEX

- [Installation](#installation)
- [Creating a project](#creating-a-project)
- [Creating a device](#creating-a-device)
- [Creating a screen](#creating-a-screen)
- [Connections](#connections)
- [Tags](#Tags)
- [Connect tags to screen items](#connect-tags-to-screen-items)
- [Scripting](#scripting)
- [Alarms](#alarms)
- [Loggs](#loggs)
- [Trends](#trends)
- [Load a project into runtime](#Load-a-project-into-runtime)
- [Start the runtime](#start-the-runtime)

## Installation

Import both app files into your app catalog of your Industrial Edge Management and start the installation:
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

9.	Click on the app icon to start WinCC Unified Online Engineering.
10.	Click on the app icon to start WinCC Unified Runtime.

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

Click on Screens to create our first one and click on add screen button to add the new one:

![createscreen2](graphics/createscreen2.PNG)

The screen created will appear in our Screens:

![createscreen3](graphics/createscreen3.PNG)


## Screen items

Once the screen is created, items can be created by clicking on add screen items button:

![screenitems1](graphics/screenitems1.PNG)

A new bar will appear with all the options available:

![screenitems2](graphics/screenitems2.PNG)

Place the item in the screen area and when is created you will see in the right bar all the properties of the item:

![screenitems3](graphics/screenitems3.PNG)

Add all the items you need and do not forget to click on the save button. An orange reminder will appear until you save the progress:

![screenitems4](graphics/screenitems4.PNG)


## Connections

To create a connection between the WinCC and a PLC go to connections:

![connections1](graphics/connections1.PNG)

Write a name for your connection, the connection type (how you are connected to the PLC, in this case via OPC-UA) and the adress of the connection:

![connections2](graphics/connections2.PNG)

Above Tags, you will see the new connection created:

![connections3](graphics/connections3.PNG)

Click on the three dots to start searching for the data on the PLC:

![connections4](graphics/connections4.PNG)

When the search is done, the data will appear:

![connections5](graphics/connections5.PNG)


## Tags

There are different ways to create tags in our WinCC. When we make a connection to a Tia Portal project we can import the tags created in that project to our WinCC project just by clicking on the created checkbox:

![tags1](graphics/tags1.PNG)

The tags will appear in the Tags window:

![tags2](graphics/tags2.PNG)

Also tags can be created manually on the interanl Tags part:

![tags3](graphics/tags3.PNG)


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

As same as working with Tia Portal in the WinCC part, scrpting is also allowed in the app. For this part we are creating another screen to create a simple script to switch between two screens:

![script1](graphics/script1.PNG)

Place a button on the first screen and go to the events tabs and click on add script:

![script2](graphics/script2.PNG)

An scrpiting window will be opened. To be more easily for the user a lot of code templates are created:

![script3](graphics/script3.PNG)

In this case, we can go to screen, change base screen. The templates ca be dragged:

![script4](graphics/script4.PNG)

Click on OK, and the script will be visible:

![script5](graphics/script5.PNG)


## Alarms

The alarms are created in the internal tags part. We can create two different types: analogs and discrete alarms. For this example we are creting both.
For the analog ones, an int tag is created:

![alarms1](graphics/alarms1.PNG)

On the bottom, in the analog alarms part we create all the alarms we need with its conditions:

![alarms2](graphics/alarms2.PNG)

For the discrete alarms, the creation is made in the same way, but the data type must be Word:

![alarms3](graphics/alarms3.PNG)

And on the bottom as same as before, the alarms are created:

![alarms4](graphics/alarms4.PNG)

In this example, we are creting another screen with alarm control screen item and some different buttoms to pop up the alarms:

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


## Load a project into runtime

To load a project go to the device and in the bottom you will see:

![load1](graphics/load1.PNG)

Click on download and when the procces is finished click on OK:

![load2](graphics/load2.PNG)

Then click on Start runtime and wait until the Runtime status is on running:

![load3](graphics/load3.PNG)


## Start the runtime

To sart the runtime go to the Wincc Runtime app:

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
