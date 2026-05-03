# SCOM HTML Dashboards

Reusable standalone HTML dashboard examples for Microsoft System Center Operations Manager (SCOM). The dashboards show different ways to visualize SCOM health state, alert, performance, and operations overview data by using the SCOM web console endpoints from custom HTML widgets.

## Dashboard Examples

### Alert Dashboards

- `AlertHotspotsByComputer_EN.html`
- `AlertHotspotsByComputer_EN_dark.html`
- `AlertSharePerServerityColumns.html`
- `AlertSharePerServerityColumns_dark.html`
- `AlertsSharePerSeverity.html`
- `AlertsSharePerSeverity_dark.html`
- `AlertsTrendOverTime_EN.html`
- `AlertsTrendOverTime_EN_dark.html`

### Health State Dashboards

- `HealthStateAllComputers.html`
- `HealthStateAllComputers_dark.html`
- `ServerStateGroup_EN.html`
- `ServerStateWithAlertDetails_EN.html`
- `ServerStateGroupHostedRelatedObjects_EN.html`
- `ServerStateGroupHostedSqlEngines_EN.html`

### Performance Dashboards

- `PerformanceStateAndMultiuCountersComplex.html`
- `PerformanceStateAndMultiuCountersComplexWithAlerts.html`
- `PerformanceStateAndMultiuCountersComplexWithAlerts_dark.html`
- `PerfWidgetGroupAllCounters_EN.html`
- `PerfWidgetGroupCompCountersOldStyle_EN.html`
- `PerfWidgetMSLearnExampleOptimized_EN.html`
- `PerfWidgetMSLearnExample_EN.html`

### Operations Overview

- `OperationsPulseOverview_EN.html`
- `OperationsPulseOverview_EN_dark.html`

## Requirements

These examples are designed for environments where the HTML files are loaded in the context of the SCOM web console and can call SCOM web endpoints such as:

```text
/OperationsManager/data/state
/OperationsManager/data/alert
/OperationsManager/data/performance
/OperationsManager/data/scomGroups
/OperationsManager/data/objectInformation/{id}
/OperationsManager/data/performanceCounters/{id}
```

The dashboards read the `SCOM-CSRF-TOKEN` browser cookie and send it back as the `SCOM-CSRF-TOKEN` request header. Missing or invalid CSRF token handling can cause SCOM REST calls to fail.

## JavaScript Libraries and Assets

The dashboard examples reference shared files under `/dashboardlibs/`. The current code uses these library files:

| File | Used for |
| --- | --- |
| `/dashboardlibs/jquery.js` | DOM handling, events, CSRF token handling, and SCOM REST API calls through `$.ajax`. This is the base dependency for the examples. |
| `/dashboardlibs/canvasjs.min.js` | Charting for the performance widgets, small-multiple views, and explorer-style dashboards. |
| `/dashboardlibs/highcharts.js` | Core charting library for alert, health, hotspot, and operations overview dashboards. |
| `/dashboardlibs/highcharts-3d.js` | Highcharts 3D extension used by severity and health-state chart examples. |
| `/dashboardlibs/modules/exporting.js` | Highcharts export module used by the Highcharts-based dashboards. |
| `/dashboardlibs/Company_Logo.png` | Optional logo image displayed by the dashboards that include branding. |

Dependency map by dashboard type:

| Dashboard type | Typical dependencies |
| --- | --- |
| State, alert, and hosted-object widgets | jQuery |
| Performance widgets, small multiples, and explorer dashboards | jQuery + CanvasJS |
| Highcharts-based visualizations | jQuery + Highcharts |
| Highcharts charts with export buttons | jQuery + Highcharts + `modules/exporting.js` |

Download third-party libraries from their official sources and review their license terms for your intended use.

## Hosting the Libraries with an IIS Virtual Directory

The HTML files use absolute paths such as:

```html
<script src="/dashboardlibs/jquery.js"></script>
<script src="/dashboardlibs/highcharts.js"></script>
<script src="/dashboardlibs/modules/exporting.js"></script>
```

Because the paths start with `/dashboardlibs/`, create the virtual directory at the root of the IIS site that hosts the SCOM web console, not inside the `OperationsManager` application.

Short IIS setup:

1. Create a physical folder on the SCOM web console server, for example:

   ```text
   C:\inetpub\dashboardlibs
   ```

2. Copy the required JavaScript files and `Company_Logo.png` into that folder. Keep the Highcharts export module in a `modules` subfolder:

   ```text
   C:\inetpub\dashboardlibs\jquery.js
   C:\inetpub\dashboardlibs\canvasjs.min.js
   C:\inetpub\dashboardlibs\highcharts.js
   C:\inetpub\dashboardlibs\highcharts-3d.js
   C:\inetpub\dashboardlibs\modules\exporting.js
   C:\inetpub\dashboardlibs\Company_Logo.png
   ```

3. Open IIS Manager.

4. Select the IIS site that hosts the SCOM web console.

5. Add a virtual directory with:

   ```text
   Alias: dashboardlibs
   Physical path: C:\inetpub\dashboardlibs
   ```

6. Make sure the IIS application pool identity or web server users can read the folder.

7. Test the virtual directory from a browser:

   ```text
   https://<your-scom-web-server>/dashboardlibs/jquery.js
   ```

   If the file downloads or displays, the dashboard script references can resolve correctly.

## Customization

Before using a dashboard, replace the placeholder group ID with a real SCOM group ID from your environment:

```text
Put your SCOM group ID here
```

You may also want to customize:

- the group display name, for example `Demo Windows Computers`
- the company logo filename or path
- dashboard titles and summary text
- SQL class IDs in the SQL-related examples, if your management pack classes differ
- styling, colors, and chart options

## Notes

These dashboards are examples and starting points. They are not a packaged SCOM management pack and may require adjustment for your SCOM version, web console configuration, management packs, groups, classes, and security model.

No environment-specific server names, demo domain names, or credentials are intentionally included. Review the files before using them in your own public or production context.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
