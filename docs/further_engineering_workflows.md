# Further engineering workflows

This chapter describes additional engineering workflows that can be used together with **SIMATIC WinCC Unified Runtime for Industrial Edge**.

## How to display Industrial Edge applications within WinCC Unified Runtime

Industrial Edge applications, such as **Energy Manager** or **Performance Insight**, can be displayed inside **SIMATIC WinCC Unified Runtime** by using a **Web browser control** in a WinCC Unified screen.

This allows operators to open Industrial Edge dashboards directly from the WinCC Unified Runtime user interface.

### Prerequisites

Before configuring the Web browser control, verify the following points:

* The Industrial Edge application that should be displayed is installed and available.
* The dashboard URL of the Industrial Edge application is known.
* The dashboard URL can be reached from the runtime client where the WinCC Unified screen is opened.
* The required user permissions for the Industrial Edge application are available.
* The WinCC Unified project is available in TIA Portal.

> **Note:**
> Depending on the Industrial Edge application and the system configuration, additional login, permissions or certificate handling may be required.

### Engineering workflow

To display an Industrial Edge application within WinCC Unified Runtime, proceed as follows:

1. Open the WinCC Unified project in TIA Portal.
2. Open the screen where the Industrial Edge application should be displayed.
3. Add a **Web browser control** to the screen.
4. Resize and position the Web browser control according to the required screen layout.
5. Configure the URL of the Industrial Edge application or dashboard.
6. Download the project to **WinCC Unified Runtime for Industrial Edge**.
7. Start the runtime project.
8. Open the configured screen and verify that the Industrial Edge application is displayed inside the Web browser control.

### Dashboard URL

Use the direct URL of the Industrial Edge application or dashboard that should be displayed.

Example for an Energy Manager dashboard:

```text
https://<ip-address-of-IED>/energymanager/#/my-plant/<plant-id>/dashboard/<dashboard-id>
```

If the Energy Manager dashboard should be displayed without the side bar or navigation bar, add the following HTTP parameter to the end of the URL:

```text
?embeddedViewMode=readOnly
```

Example:

```text
https://<ip-address-of-IED>/energymanager/#/my-plant/<plant-id>/dashboard/<dashboard-id>?embeddedViewMode=readOnly
```

> **Note:**
> If the URL already contains an HTTP query parameter, append additional parameters with `&` instead of `?`.

### Runtime validation

After downloading the project, open the corresponding screen in WinCC Unified Runtime.

Check that the dashboard is displayed inside the Web browser control.

If the dashboard is not displayed, verify the following points:

* The configured URL is correct.
* The URL can be reached from the runtime client.
* The Industrial Edge application is running.
* The user has the required permissions to access the dashboard.
* Required certificates or browser permissions have been accepted.
* The dashboard can be opened directly in a browser outside of WinCC Unified Runtime.

## Connect WinCC Unified Runtime on Edge with IIH via OPC UA

This section describes the engineering workflow to establish an OPC UA connection between **WinCC Unified Runtime on Edge** and **IIH Semantics** by using TIA Portal.

The workflow starts in IIH Semantics, where the asset model is exposed via OPC UA. The OPC UA server is then browsed from TIA Portal and variables from the IIH asset model are assigned to HMI tags in the WinCC Unified project. After the project has been compiled and downloaded to **SIMATIC WinCC Unified Runtime for Industrial Edge**, the configured HMI tags can be validated in runtime.

This workflow covers the following steps:

1. Expose the IIH asset model via OPC UA.
2. Copy the OPC UA Server Final URL from IIH Semantics.
3. Create an OPC UA connection in TIA Portal.
4. Assign the OPC UA connection to the required HMI tags.
5. Browse the IIH asset model and assign OPC UA addresses to the HMI tags.
6. Compile the WinCC Unified project.
7. Adapt the OPC UA server URL for runtime communication on the Industrial Edge Device.
8. Download the project to WinCC Unified Runtime for Industrial Edge.
9. Validate the exchanged variables in runtime.

### Prerequisites

Before starting the workflow, verify the following points:

* **SIMATIC WinCC Unified Runtime for Industrial Edge** is installed on the Industrial Edge Device.
* IIH Essentials is installed and available on the Industrial Edge Device.
* IIH Semantics is installed and available on the Industrial Edge Device.
* The IIH asset model contains the variables that should be used in the WinCC Unified project.
* A WinCC Unified project is available in TIA Portal.
* The required HMI tags are available in the WinCC Unified project.
* The required user permissions are available in IIH Essentials, IIH Semantics and TIA Portal.

> **Note:**
> If the data from IIH Essentials should be available in IIH Semantics, make sure that the required data mapping between IIH Essentials and IIH Semantics is available.

### Step 1: Expose the IIH asset model via OPC UA

Open **IIH Semantics** on the Industrial Edge Device.

Open **Settings** and select **OPC UA**.

In the **Asset Model Configuration** section, enable the option to expose the asset model via OPC UA.

After this option has been enabled, the IIH asset model can be accessed through the OPC UA server provided by IIH Semantics.

### Step 2: Copy the OPC UA Server Final URL

In **IIH Semantics**, stay in **Settings > OPC UA**.

In the **Server Security Configuration** section, locate the **OPC UA Server Final URL**.

Copy this URL.

The URL is required in TIA Portal to browse the IIH Semantics OPC UA server during engineering.

### Step 3: Create an OPC UA connection in TIA Portal

Open the WinCC Unified project in TIA Portal.

In the project tree, open the WinCC Unified device and go to **Connections**.

Create a new connection.

Set the **Communication driver** to **OPC UA**.

In the OPC UA server settings, paste the **OPC UA Server Final URL** copied from IIH Semantics.

During engineering, the URL can use the IP address of the Industrial Edge Device. This allows TIA Portal to browse the IIH Semantics OPC UA server.

### Step 4: Assign the OPC UA connection to the HMI tags

Open the HMI tag table that contains the HMI tags to be linked with variables from the IIH asset model.

For each relevant HMI tag, select the OPC UA connection in the **Connection** column.

This links the HMI tag to the OPC UA connection that was created in the previous step.

For information about creating HMI tags in the WinCC Unified project, see [Tags](installation_and_tutorial.md#tags).

### Step 5: Browse the IIH asset model from the Address column

In the HMI tag table, open the address browser from the **Address** column.

Browse the OPC UA server structure.

Navigate to the IIH asset model.

Select the required variable from the IIH asset model and assign it to the corresponding HMI tag.

Repeat this step for all HMI tags that should be connected to variables from the IIH asset model.

### Step 6: Compile the WinCC Unified project

After the required IIH variables have been assigned to the HMI tags, compile the WinCC Unified project.

Make sure that the project compiles without errors before downloading it to the runtime.

### Step 7: Adapt the OPC UA server URL for runtime communication

Before downloading the project to **SIMATIC WinCC Unified Runtime for Industrial Edge**, adapt the OPC UA server URL in the connection settings.

During engineering, the **OPC UA Server Final URL** copied from IIH Semantics can use the IP address of the Industrial Edge Device. This allows TIA Portal, running outside the Industrial Edge Device, to browse the IIH Semantics OPC UA server.

For runtime communication, the WinCC Unified Runtime app communicates with IIH Semantics from inside the Industrial Edge Device. Therefore, replace the IP address part of the OPC UA server URL with the corresponding local service or container name of the IIH Semantics OPC UA server.

Example engineering URL:

```text
opc.tcp://<IED_IP_address>:62520/<server-path>
```

Example runtime URL:

```text
opc.tcp://pmd-core-service:62520/<same-server-path>
```

Only replace the host part required for the runtime connection. Keep the protocol, port and remaining OPC UA server path unchanged, unless the target Industrial Edge environment requires a different service name or endpoint configuration.

> **Important:**
> The OPC UA server URL used during engineering and the OPC UA server URL used during runtime communication are not necessarily the same. Before downloading the project, make sure that the configured OPC UA server URL can be resolved by the WinCC Unified Runtime app on the Industrial Edge Device.


### Step 8: Download the project to WinCC Unified Runtime

Download the project to **SIMATIC WinCC Unified Runtime for Industrial Edge**.

Wait until the download has finished successfully.

Start the runtime project.

### Step 9: Validate the exchanged variables in runtime

Open the screen or HMI object that uses the configured HMI tags.

Verify that the values from the IIH asset model are displayed or used as expected in WinCC Unified Runtime.

If the values are not available, verify the following points:

* The IIH asset model is exposed via OPC UA.
* The OPC UA Server Final URL was copied correctly.
* The OPC UA connection in TIA Portal uses the correct communication driver.
* The HMI tags are assigned to the correct OPC UA variables.
* The project compiles without errors.
* The OPC UA server address was adapted correctly before downloading the project.
* The WinCC Unified runtime project is running.
* IIH Semantics is running on the Industrial Edge Device.
* The required mapping between IIH Essentials and IIH Semantics is available, if the data should originate from IIH Essentials.

## How to exchange HMI variables with IIH Essentials
