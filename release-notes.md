---

copyright:
  years: 2015, 2018, 2019
lastupdated: "2019-02-08"

subcollection: discovery-sf

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:important: .important}
{:deprecated: .deprecated}
{:codeblock: .codeblock}
{:screen: .screen}
{:download: .download}
{:hide-dashboard: .hide-dashboard}
{:apikey: data-credential-placeholder='apikey'} 
{:url: data-credential-placeholder='url'}
{:curl: #curl .ph data-hd-programlang='curl'}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:ruby: .ph data-hd-programlang='ruby'}
{:swift: .ph data-hd-programlang='swift'}
{:go: .ph data-hd-programlang='go'}

# Release notes
{: #release-notes}

The release notes provide information about changes to {{site.data.keyword.discoveryfull}} for Salesforce since the previous release.
{: shortdesc}

## Beta features
{: #beta-features}

IBM will release services, features, and language support that are classified as beta or experimental. These capacities can be unstable, can change frequently, and can be discontinued with short notice. They are provided so you can evaluate their functionality. A beta or experimental capacity might not provide the same level of performance or compatibility that generally released capacities provide. These capacities are not designed for use in a production environment, and any such use is at your own risk.

## Changes
{: #change-log}

The following new features and changes are available.

If you are interested in {{site.data.keyword.discoveryfull}} for Salesforce contact your IBM representative for more information.

## 8 February 2019
{: #8feb19}

- Added the option to connect to and sync with IBM Cloud Object Storage. This data source is not available in Dedicated environments. See [IBM Cloud Object Storage](/docs/services/discovery-sf?topic=discovery-sf-sources#connectcos) for more information.

## 21 December 2018
{: #21dec18}

- Added the option to connect to and sync with Microsoft SharePoint 2016 On-Premise. This data source is not available in Dedicated environments. See [SharePoint 2016 On-Premise](/docs/services/discovery-sf?topic=discovery-sf-sources#connectsp_op) for more information.
- Added the beta version of the Web Crawl connector, which can be used connect to, crawl, and sync with websites. This data source is not available in Dedicated environments. See [Web crawl](/docs/services/discovery-sf?topic=discovery-sf-sources#connectwebcrawl) for more information. A statement explaining beta features can be found [here](/docs/services/discovery-sf?topic=discovery-sf-release-notes#beta-features).
- The Microsoft SharePoint Online, Salesforce, and Box data sources are now available in Premium environments. They are not available in Dedicated environments.


### 10 September 2018
{: #10sept18}

- You can now create search filters for each of your data sources. See [Configuring your app](/docs/services/discovery-sf?topic=discovery-sf-configureapp#configureapp) for more information.

### 2 August 2018
{: #2aug18}

- {{site.data.keyword.discoveryfull}} for Salesforce now supports English, Spanish, German, Italian, Portuguese, French, Arabic, Korean, and Japanese language collections when connecting and syncing to Box, Salesforce, and SharePoint Online with the {{site.data.keyword.discoveryshort}} tooling. 

### General Availability release, 29 June 2018
{: #ga}

The following notes apply to the General Availability (GA) release of {{site.data.keyword.discoveryfull}} for Salesforce.

- {{site.data.keyword.discoveryfull}} for Salesforce supports only English language collections when connecting and syncing to Salesforce, Microsoft SharePoint Online, or Box with the {{site.data.keyword.discoveryshort}} tooling. [Resolved](/docs/services/discovery-sf?topic=discovery-sf-release-notes#2aug18)
- The individual document file size limit for Salesforce, Microsoft SharePoint Online, and Box is 10MB.
- Premium and Dedicated Plans are not available at this time for {{site.data.keyword.discoveryfull}} for Salesforce.
- The Performance dashboard is not available in Premium and Dedicated environments.
