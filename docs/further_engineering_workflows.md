## Further engineering workflows

This chapter describes additional engineering workflows that can be used together with **SIMATIC WinCC Unified Runtime for Industrial Edge**.

### How to display Industrial Edge applications within WinCC Unified Runtime

Industrial Edge applications, such as Energy Manager or Performance Insight, can be displayed inside the **SIMATIC WinCC Unified Runtime** app by using a **Web browser control** in a WinCC Unified screen.

This allows operators to view Edge application dashboards directly within the WinCC Unified Runtime user interface.

To display an Industrial Edge application within WinCC Unified Runtime, proceed as follows:

1. Open the WinCC Unified project in TIA Portal.
2. Open the screen where the Industrial Edge application should be displayed.
3. Add a **Web browser control** to the screen.
4. Resize and position the control according to the required layout.
5. Configure the URL of the Industrial Edge application or dashboard.
6. Download the project to **WinCC Unified Runtime for Industrial Edge**.
7. Start the runtime project and verify that the Industrial Edge application is displayed inside the Web browser control.

For example, an Energy Manager dashboard can be opened directly by using the dashboard URL.

If the Energy Manager dashboard should be displayed without the side bar or navigation bar, add the following HTTP parameter to the end of the URL:

```text
?embeddedViewMode=readOnly
```

Example:

```text
https://<ip-address-of-IED>/energymanager/#/my-plant/<plant-id>/dashboard/<dashboard-id>?embeddedViewMode=readOnly
```

> **Note:**
> The URL must be reachable from the runtime client where the WinCC Unified screen is opened. Depending on the Industrial Edge application, additional login, permissions or certificate handling may be required.
