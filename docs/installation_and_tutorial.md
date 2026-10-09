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

Download **SIMATIC WinCC Unified Runtime for Industrial Edge** from the Industrial Edge Hub to your Industrial Edge Management (IEM). The application is then available in the IEM catalog.

To install the application on an Industrial Edge Device:

1. Sign in to the IEM that manages the target Industrial Edge Device.
2. Open the **Catalog**.
3. Select **SIMATIC WinCC Unified Runtime** and install it on the target Industrial Edge Device.
4. Sign in to the Industrial Edge Device after the installation has completed.
5. Open the **Apps** page and select **SIMATIC WinCC Unified Runtime**.

## Creating a project

In TIA Portal, select **Project > New** to create a new engineering project:

![Create a new project](graphics/createproject1.png)

Enter the project name and select the folder where the project should be stored. Then click **Create**:

![Configure the new project](graphics/createproject2.png)

## Creating a device

After creating the project, open the project view.

In the project tree, select **Add new device**.

Add **Unified Edge Device V21.0.1.0** from the device catalog:

![Add a Unified Edge Device](graphics/device1.png)

## Creating a screen

After adding the Unified Edge Device, expand the device in the project tree:

![Open the Unified Edge Device](graphics/createscreen1.png)

Open **Screens** and select **Add new screen**:

![Add a new screen](graphics/createscreen2.png)

The newly created screen appears under **Screens**. If it is the first screen created for the device, it is automatically configured as the **Start Screen**:

![Created start screen](graphics/createscreen3.png)

## Screen items

Open the required screen in TIA Portal.

Screen objects can be added by dragging them from the **Toolbox** onto the screen:

![Add a screen object from the Toolbox](graphics/screenitmes1_new.png)

Select a screen object to view and configure its properties:

![Configure the properties of a screen object](graphics/screenitmes3_new.jpg)

## Connections

To configure communication between the Unified Edge Device and a PLC, add the required communication module to the device:

![Add a communication module](graphics/connections1.png)

In the **Network view**, connect the PLC interface to the communication module of the Unified Edge Device. Then configure the corresponding connection in the **Connections** view:

![Configure the PLC connection](graphics/connections2.png)

## Tags

WinCC Unified projects can use both tags connected to external data sources and internal HMI tags.

### Create tags from a connection

After a connection to the PLC has been configured, PLC tags can be added to the WinCC Unified project.

Drag the required PLC tag into an HMI tag table:

![Create an HMI tag from a PLC tag](graphics/tags/tags3.png)

### Create internal tags

Internal tags can also be created manually in an HMI tag table.

Create the required tag and set its connection to **Internal tag**:

![Create an internal HMI tag](graphics/tags/tags1.png)

## Connect tags to screen items

HMI tags can be used to dynamize properties of screen objects.

Select the required screen object:

![Select a screen object](graphics/tags/tagstoscreen1_new.jpg)

In the **Properties** tab, open the dynamization dialog for the required property and select **Tag**:

![Configure tag dynamization](graphics/tags/tagstoscreen2-1.jpg)

Select the HMI tag that should be assigned to the property:

![Select an HMI tag](graphics/tags/tagstoscreen3.png)

Alternatively, drag an HMI tag directly onto the screen. TIA Portal automatically creates an I/O field connected to the selected tag:

![Create an I/O field by dragging an HMI tag onto the screen](graphics/tags/tagstoscreen4.jpg)

## OPC UA Server

WinCC Unified Runtime can provide HMI data through its integrated OPC UA server.

In the project tree, open **Runtime settings** and enable the **OPC UA server**.

The default OPC UA server port for WinCC Unified Runtime for Industrial Edge is `34002`.

![Enable the OPC UA server](graphics/connections6.png)

## Load a project into runtime

To download a WinCC Unified project directly from TIA Portal to the Industrial Edge Device, configure the IP address of the target device in the device properties:

![Configure the Industrial Edge Device IP address](graphics/remotedown2.png)

Start the download from TIA Portal and select the configured Industrial Edge Device as the target:

![Download the project to WinCC Unified Runtime](graphics/remotedown1.png)

### Offline download

If a direct online connection between TIA Portal and the Industrial Edge Device is not available, an offline runtime project can be generated in TIA Portal.

Create the offline runtime project by using the card reader functionality in TIA Portal:

![Create an offline runtime project](graphics/offdown1.png)

Open **SIMATIC WinCC Unified Runtime Manager** on the Industrial Edge Device and upload the generated runtime project:

![Upload an offline runtime project](graphics/offdown2.png)

### Offline download via Industrial Edge Management

An offline runtime project can also be transferred through the Industrial Edge Management (IEM).

In the IEM, open **My Installed Apps** and select **SIMATIC WinCC Unified Runtime**:

![Open WinCC Unified Runtime in the IEM](graphics/iem_download.png)

Select **Update configuration**.

In the **autoDownload** configuration, click **+** and add the generated offline runtime project file.

After the file has been uploaded, click **Update Now** to transfer the configuration to the Industrial Edge Device:

![Configure autoDownload in the IEM](graphics/iem_download3.png)

## Alarms

WinCC Unified supports both analog and discrete alarms. The alarm type and trigger configuration depend on the tag and its data type.

In this example, internal HMI tags are used to trigger both alarm types.

For the analog alarm example, create an `Int` tag:

![Create the tag used for analog alarms](graphics/alarms1.png)

Open the **Analog alarms** tab and create the required alarms. Configure the trigger tag and the corresponding alarm conditions:

![Configure analog alarms](graphics/alarms2.png)

For discrete alarms, create or use a tag with a suitable data type, such as `Word`, and configure the alarms in the **Discrete alarms** tab:

![Configure discrete alarms](graphics/alarms3.png)

To display the alarms in Runtime, add an **Alarm control** to a screen.

In this example, buttons are also added to the screen to trigger the configured alarms:

![Configure an Alarm control and alarm trigger buttons](graphics/alarms5_new.png)

When the Runtime project is running and an alarm is triggered, the corresponding alarm appears in the Alarm control:

![Display alarms in Runtime](graphics/alarms6.png)

## Logs

HMI tags can be logged to record their values over time.

In this example, an internal HMI tag is used to demonstrate two logging modes: **Cyclic** and **On change**.

Open the **Logging tags** configuration and create a logging tag with **Cyclic** acquisition mode:

![Configure cyclic tag logging](graphics/logs1.png)

A logging tag can also be configured with **On change** acquisition mode:

![Configure on-change tag logging](graphics/logs2.png)

After the Runtime project has been started and values have been logged, the recorded data can be displayed in Runtime:

![Display logged values in Runtime](graphics/logs6.png)

## Trends

To visualize current or logged tag values over time, add a **Trend control** to a screen.

In the **Toolbox**, select the Trend control and drag it onto the required screen:

![Add a Trend control to a screen](graphics/trends1.png)

Select the Trend control and open its **Trends** properties. Add the required tag or logging tag as a data source:

![Configure a trend data source](graphics/trends2.png)

After the Runtime project has been started, the configured values are displayed in the Trend control:

![Display trend data in Runtime](graphics/trends4.png)

## Further engineering workflows

For additional engineering workflows, see:

* [How to display Industrial Edge applications within WinCC Unified Runtime](further_engineering_workflows.md#how-to-display-industrial-edge-applications-within-wincc-unified-runtime)
* [Connect WinCC Unified Runtime with IIH Semantics via OPC UA](further_engineering_workflows.md#connect-wincc-unified-runtime-with-iih-semantics-via-opc-ua)
* [How to exchange HMI variables with IIH Essentials](further_engineering_workflows.md#how-to-exchange-hmi-variables-with-iih-essentials)

## TIA Portal guidelines

For additional information about engineering WinCC Unified projects in TIA Portal, refer to the following Siemens resources:

* [SIMATIC WinCC Unified Tutorial Center](https://support.industry.siemens.com/cs/document/109782433/simatic-wincc-unified-tutorial-center-(videos)?dti=0&lc=en-WW)
* [Engineering Guideline for WinCC Unified](https://support.industry.siemens.com/cs/document/109827603/engineering-guideline-for-wincc-unified?dti=0&lc=en-US)

## How to use WinCC Unified Runtime Manager

To open the **SIMATIC WinCC Unified Runtime Manager**, open the **SIMATIC WinCC Unified Runtime** app on the Industrial Edge Device:

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

When the downloaded project is running, a green status indicator shows that the Runtime project is ready:

![Runtime project ready](graphics/runtime_manager/start2.png)

### Start the runtime

In the SIMATIC WinCC Unified Runtime Manager, open the Runtime project:

![Open the Runtime project](graphics/runtime_manager/start3.png)

The configured **Start Screen** is displayed in Runtime:

![Display the configured Start Screen](graphics/runtime_manager/start4.jpg)

### Stop the runtime

To stop the running project, select **Stop Project** in the SIMATIC WinCC Unified Runtime Manager:

![Stop the Runtime project](graphics/runtime_manager/start5.png)

Wait until the project status indicates that the Runtime project is no longer running. The status indicator changes accordingly:

![Stopped Runtime project](graphics/runtime_manager/start7.png)

### Secure download

Secure download can be used to protect project transfer to the Runtime.

Enable secure download both in the TIA Portal project and in the SIMATIC WinCC Unified Runtime Manager.

Configure secure download in TIA Portal:

![Configure secure download in TIA Portal](graphics/runtime_manager/secureDown2.png)

Then enable the corresponding secure download setting in the SIMATIC WinCC Unified Runtime Manager:

![Configure secure download in Runtime Manager](graphics/runtime_manager/secureDown.png)

### AutoScale

Enable **AutoScale** to automatically adapt the Runtime screen to the available browser or client window size.

This allows screens designed for a specific resolution to be scaled when they are displayed on a device with a different window size:

![Configure AutoScale](graphics/runtime_manager/autoScale.png)

### Media files

Media files can be uploaded to the Runtime project through the **SIMATIC WinCC Unified Runtime Manager**.

Open the media file management section and upload the required file:

![Upload media files in Runtime Manager](graphics/runtime_manager/mediaFiles.png)

Uploaded files are made available through the Runtime web server and can be accessed using the following URL:

```text
https://<IED-IP>/WebRH/mediafiles/<FileName>
```

For example:

```text
https://<IED-IP>/WebRH/mediafiles/changePassword.png
```

The URL can be used in a **Web control** to display the uploaded content inside a WinCC Unified screen.

The following file types have been verified with the Web control in V21 Update 2:

* `.png` images
* `.gif` animations
* `.mp4` videos

> **Note:**
> Support for uploading a file through Runtime Manager and support for displaying that file in a specific WinCC Unified control are separate aspects. The target control and client browser must support the corresponding file format.

## Migration workflow from V5.0.0 to V21 Upd 2

For the migration workflow from WinCC Unified Runtime for Industrial Edge V5.0.0 to V21 Upd 2, see:

[Migration workflow from V5.0.0 to V21 Upd 2](migration_workflow_v5_to_v21upd2.md)

## Trace Settings

For information about collecting diagnostic logs, exporting trace files and forwarding live traces to Trace Viewer, see:

[Trace Settings](trace_settings.md)
