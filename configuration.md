---

copyright:
  years: 2015, 2018
lastupdated: "2018-09-10"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Configuring your app
{: #configureapp}

After you have finished setting up your data sources you can configure and personalize your {{site.data.keyword.discoveryfull}} for Salesforce app.

All of your {{site.data.keyword.discoveryshort}} collections will appear in the list, disabled by default. Enable the collections your would like to use in your app.

If you choose to **Edit Data** or **Add Source** you will be returned to the appropriate screen to make those changes.

This is the end of the {{site.data.keyword.discoveryfull}} for Salesforce setup. You can now utilize your new app in the Salesforce Lightning App Builder. Click **Lightning App Builder** to add the {{site.data.keyword.discoveryfull}} for Salesforce app to your page and configure it further. 

To edit or add data sources, configure search filters, view the Performance dashboard, change your {{site.data.keyword.discoveryshort}} credentials, or view the {{site.data.keyword.discoveryfull}} for Salesforce documentation from the **Lightning App Builder**, click the **Configuration** tab to open the {{site.data.keyword.discoveryfull}} Configuration screen. 

If you would like to configure search filters for your app, and no data sources appear in your **Search filters** drop-down, verify that you have enabled one or more collections in the **Data Sources** section of the {{site.data.keyword.discoveryfull}} Configuration screen. You can rename and delete the filters that you add for each data source if you wish.

## Assigning user permissions

When you configure the {{site.data.keyword.discoveryfull}} for Salesforce app: 

- Assign your users the **Watson Discovery User** permission.
- Grant them **Read** access on **Knowledge Article Types**.

To search for information, view content, attach articles to cases, and highlight results, **Read** access is sufficient. For information about how to assign Salesforce permissions and other access levels, consult the [Salesforce documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.salesforce.com/docs/atlas.en-us.securityImplGuide.meta/securityImplGuide/admin_userperms.htm){: new_window}.