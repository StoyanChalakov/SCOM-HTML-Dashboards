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
/OperationsManager/data/scomGroups
```

The dashboards also reference shared JavaScript and image assets under `/dashboardlibs/`, for example:

```text
/dashboardlibs/jquery.js
/dashboardlibs/highcharts.js
/dashboardlibs/Company_Logo.png
```

Make sure these files exist in your SCOM web environment, or adjust the paths in the HTML files to match your own location.

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
