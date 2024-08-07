---
title: Looker connector
description: Provides basic information and prerequisites for the Looker connector for Power Query.
author: kenrickyap
ms.topic: conceptual
ms.date: 6/21/2024
ms.author: dougklo
---

# Looker

![Here's the Looker logo](./media/index/looker-64.png)

## Summary

| Item | Description |
| ---- | ----------- |
| Release State | General Availability |
| Products | Power BI (Semantic models) |
| Authentication Types Supported | Organizational account |

> [!NOTE]
> The following connector article is provided by Google, the owner of this connector and a member of the Microsoft Power Query Connector Certification Program. If you have questions regarding the content of this article or have changes you would like to see made to this article, visit the [Google website](https://cloud.google.com/looker/docs/best-practices/looker-support-details) and use the support channels there.

> [!NOTE]
> Some capabilities may be present in one product but not others due to deployment schedules and host-specific capabilities.

## Prerequisites

To connect to Looker, you'll need an account on a Looker-hosted Looker instance. See details in the [Looker documentation](https://cloud.google.com/looker/docs/powerbi-connector#requirements).

You'll also need to confirm that a Looker admin has enabled the Power BI connector on this Looker instance. See details in the [Looker documentation](https://cloud.google.com/looker/docs/powerbi-connector#enable_connector).

## Supported capabilities

* Import Mode
* DirectQuery

## Connect to Looker data from Power Query Desktop

To connect to Looker from Power Query Desktop, follow these steps:

1. In the **Get Data** experience, search for and select **Looker**.

1. In **Host**, enter your Looker instance URL, for example, https://example.cloud.looker.com.

1. The default value of **Disable Preview Optimization** if left blank is True. This is the recommended setting. Setting the value to False will result in a potentially expensive preview query being sent to Looker. Read more in the [Looker documentation](https://cloud.google.com/looker/docs/powerbi-connector#preview_optimization).

1. The default value of **Show Hidden Fields** if left blank is False. This will mimic the default visual behavior on Looker where fields with the hidden tag will not be shown. If this parameter is set to True, all fields will be visible in the Power BI report, including those with hidden tags.

1. It is recommended to select **Direct Query**. Selecting **Import** may result in a potentially expensive query that includes all fields from all the views that are referenced in the Looker Explore. In addition, Import mode comes with certain [limitations](#import-mode-limitations).

1. Select **OK** to continue.

   ![Image showing initial dialog box](./media/google-looker/host-connection-filled-desktop.png)

1. The Looker connector supports connecting using an Organizational account. You will use your existing Looker credentials. Select **Sign In** to continue.

1. The traditional Looker login screen appears. Sign in the same way you would normally log in to Looker.

1. Once you're signed in, select **Connect** to continue.

1. Once you successfully connect, a **Navigator** window appears and displays the data available in your Looker instance. First, select a Looker model. Within each model, you will see the available Explores. Select the Explore that you would like to connect to, and click **Load**.

   ![Image showing navigation window](./media/google-looker/navigator-view-desktop.png)

## Limitations and considerations

### Import Mode Limitations

When using the Import Mode of the Looker connector, users should be aware of the following limitations:

* **Performance Issues with Large Models**:
  * Import Mode reports attempting to access larger models may experience performance degradation.
  * If the "Get Data" process does not resolve or times out, it is recommended that users switch to "Direct Query Mode" to improve performance and reliability.

* **Disabled Fields**:
  * In Import Mode, filter-only fields and parameter fields are disabled. Therefore, these fields should not be used when operating in this mode.

* **Evaluation of Measures**:
  * Import Mode does not allow Looker to correctly evaluate measures within the Explore. This limitation can impact the accuracy and functionality of your reports.

Given these limitations, it is generally better to use Direct Query Mode when possible to ensure optimal performance and functionality.

### Query Folding Limitations

Please note that the following Table functions are not foldable:

* Table.Distinct
* Table.Join
* Table.NestedJoin
* Table.Skip

### Additional Limitations and Considerations

Please see the [Looker documentation](https://cloud.google.com/looker/docs/powerbi-connector#things_to_consider) for additional limitations and considerations of the Looker connector.

## Troubleshooting and escalation path

For any issues with the Looker connector, refer to the official [Looker API Troubleshooting Guide](https://cloud.google.com/looker/docs/api-troubleshooting) for detailed information on common error messages and their resolutions.

If issues persist, gather error details and contact Looker Support using the [Looker Support Details Guide](https://cloud.google.com/looker/docs/best-practices/looker-support-details). You can also seek help from the [Looker Studio Community](https://support.google.com/looker-studio/community?hl=en&sjid=12736577235379517573-NC).