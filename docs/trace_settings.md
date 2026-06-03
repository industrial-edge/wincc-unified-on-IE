# Trace Settings

This document describes how to collect diagnostic information from the **WinCC Unified Runtime for Industrial Edge** app.

Trace and log data can be collected in two different ways:

1. Export logs directly from the WinCC Unified Web Runtime Manager.
2. Forward live traces to Trace Viewer and export them from there.

> **Important:**  
> Enable the required logging or trace settings before reproducing the behavior or issue that should be analyzed.

## Procedure 1: Export logs from the WinCC Unified Web Runtime Manager

This procedure can be used to export log files directly from the WinCC Unified Web Runtime Manager.

### Step 1: Open the Logs and Traces settings

Open the **WinCC Unified Runtime** app on the Industrial Edge Device.

In the **WinCC Unified Web Runtime Manager**, open the configuration settings from the left-side navigation bar. In the configuration menu, select **Logs and Traces**.

![Open Logs and Traces settings](graphics/trace/trace_settings_1_logs_and_traces_menu_blur.gif)

### Step 2: Enable App Logging

In the **Logs and Traces** view, select the **App Logging** tab.

Enable the **Logging Service**.

Configure the required severity level and log size settings according to the diagnostic information required.

Click **Save** to apply the settings.

![Enable App Logging](graphics/trace/trace_settings_2_app_logging_enabled.gif)

### Step 3: Reproduce the behavior or issue

After the logging settings have been enabled, reproduce the behavior or issue that should be analyzed.

It is recommended to note the approximate timestamp when the issue occurs. This helps to find the relevant entries in the exported log files.

### Step 4: Download the logs

After the issue has been reproduced, click **Download Logs** in the upper-right corner of the **Logs and Traces** page.

![Download logs](graphics/trace/trace_settings_4_download_logs.gif)

The log files are then downloaded. Store the downloaded files in a safe location.

### Step 5: Prepare the diagnostic package

Collect the downloaded log files and add relevant context information.

Recommended information to include:

* WinCC Unified Runtime for Industrial Edge app version
* Industrial Edge Device version
* TIA Portal version used for the project
* Approximate timestamp when the issue occurred
* Short description of the performed steps
* Screenshots or additional diagnostic information, if available

## Procedure 2: Forward live traces to Trace Viewer

This procedure can be used to collect live trace data with Trace Viewer.

Trace Viewer is installed together with WinCC Unified / TIA Portal.

### Step 1: Open the Logs and Traces settings

Open the **WinCC Unified Runtime** app on the Industrial Edge Device.

In the **WinCC Unified Web Runtime Manager**, open the configuration settings from the left-side navigation bar. In the configuration menu, select **Logs and Traces**.

![Open Logs and Traces settings](graphics/trace/trace_settings_1_logs_and_traces_menu_blur.gif)

### Step 2: Enable Trace Forwarding

In the **Logs and Traces** view, select the **Trace Forwarding** tab.

Enable **Forward Trace**.

Configure the trace forwarding settings according to the Trace Viewer receiver configuration.

Click **Save** to apply the settings.

![Enable Trace Forwarding](graphics/trace/trace_settings_5_trace_forwarding_enabled.gif)

After saving the settings, the WinCC Unified Runtime is prepared to forward trace data to Trace Viewer.

### Step 3: Start Trace Viewer in receiver mode

On the engineering or service PC, open a command prompt.

Start Trace Viewer in receiver mode by using the following command:

```cmd
"C:\Program Files\Siemens\Automation\WinCCUnified\bin\RTILtraceTool.exe" -mode receiver -tcp -host <IED IP address> -port 35000
```

Replace `<IED IP address>` with the IP address of the Industrial Edge Device.

If the Trace Viewer executable is installed in a different directory, adapt the path accordingly.

Keep the command prompt open while collecting traces.

### Step 4: Check that traces are received

After Trace Viewer has been started in receiver mode, check that traces are received.

If no traces are received, verify the following points:

* Trace Viewer is running in receiver mode.
* The configured Industrial Edge Device IP address is correct.
* The configured port is correct.
* The Industrial Edge Device and the engineering or service PC can reach each other in the network.
* **Forward Trace** is enabled in the WinCC Unified Web Runtime Manager.
* The required trace settings are enabled.

### Step 5: Reproduce the behavior or issue

After trace forwarding has been enabled and traces are received in Trace Viewer, reproduce the behavior or issue that should be analyzed.

It is recommended to note the approximate timestamp when the issue occurs. This helps to find the relevant entries in the collected trace data.

### Step 6: Export the trace data from Trace Viewer

After the relevant behavior or issue has been reproduced, save or export the received traces from Trace Viewer.

Store the exported trace data in a safe location.

### Step 7: Prepare the diagnostic package

Collect the exported trace data and add relevant context information.

Recommended information to include:

* WinCC Unified Runtime for Industrial Edge app version
* Industrial Edge Device version
* TIA Portal version used for the project
* Approximate timestamp when the issue occurred
* Short description of the performed steps
* Screenshots or additional diagnostic information, if available
