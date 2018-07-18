---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-09"

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

# Welcome to Watson Discovery for Salesforce

The {{site.data.keyword.discoveryfull}} for Salesforce app is an AI-powered insight engine for Salesforce Service Cloud users. 

This setup assistant will guide you through the steps of connecting to the data that will power your {{site.data.keyword.discoveryfull}} for Salesforce app. The app will use that data to help your customer service representatives find the answers they need to manage and solve customer cases. 

Your data will be stored on the IBM Cloud, within collections located in your {{site.data.keyword.discoveryshort}} service. You can connect to and import data from Salesforce, Microsoft SharePoint Online, and Box, as well as set up a synchronization schedule so your data is always up-to-date. If you have other data you would like to use that is not stored in those data sources, you can create a collection and upload those documents to {{site.data.keyword.discoveryshort}}. All of these data sources will be used by the {{site.data.keyword.discoveryfull}} app in Salesforce.

An overview of the steps to setup a {{site.data.keyword.discoveryfull}} for Salesforce app follows. If you already have an IBM Cloud account or {{site.data.keyword.discoveryshort}} instance in the US East region, you are not required to create new ones.

- Create an [IBM Cloud account](/docs/services/discovery-sf/authentication.html#cloud) (or log into your existing account).
- Create an instance of the {{site.data.keyword.discoveryshort}} service in the **US East** region (or use an instance you already have in that region).
- [Connect to the data](/docs/services/discovery-sf/connect.html) you have stored in Salesforce, Microsoft SharePoint Online, or Box and specify how often you'd like that data to be updated. You also have the option to create your own data source.
- [Configure](/docs/services/discovery-sf/configuration.html) your new {{site.data.keyword.discoveryfull}} for Salesforce app.  

If you do not have an existing {{site.data.keyword.discoveryfull}} service plan, see [Discovery pricing plans ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/discovery/pricing-details.html){: new_window} to review the benefits and limits of each plan. {{site.data.keyword.discoveryfull}} for Salesforce is not supported on Premium and Dedicated plans.

If you are interested in {{site.data.keyword.discoveryfull}} for Salesforce contact your IBM representative for more information.

## Prerequisites and browser support
{: #prereqs}

Prerequisites for {{site.data.keyword.discoveryfull}} for Salesforce:
- An {{site.data.keyword.Bluemix}} account
- To connect to Microsoft SharePoint Online data: credentials and data locations from your Microsoft SharePoint Online administrator
- To connect to Box data: credentials and data locations from your Box administrator
- To connect to Salesforce data: Enterprise Salesforce using the Lightning platform

**Notes for existing {{site.data.keyword.discoveryshort}} service users:** 
- The {{site.data.keyword.discoveryshort}} service now supports token-based Identity and Access Management (IAM) authentication. IAM uses access tokens rather than service credentials for authentication with a service. If you have an existing {{site.data.keyword.discoveryshort}} instance on US East that you wish to use for {{site.data.keyword.discoveryfull}} for Salesforce, you must migrate it first. See [Migrating Cloud Foundry service instances to a resource group ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/resources/instance_migration.html#migrate){: new_window}.
- Existing {{site.data.keyword.discoveryshort}} collections can't be used with {{site.data.keyword.discoveryfull}} for Salesforce.

For the list of {{site.data.keyword.Bluemix}} prerequisites and supported browsers, see [Prerequisites ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/overview/prereqs.html#prereqs){: new_window}.

For additional {{site.data.keyword.Bluemix}} resources, see [IBM Cloud Support Center ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/unifiedsupport/supportcenter){: new_window}.


