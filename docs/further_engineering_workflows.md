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