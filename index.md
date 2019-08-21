---

copyright:
  years: 2015, 2018, 2019
lastupdated: "2019-04-04"

keywords: discovery,discovery for salesforce,IBM cloud,cognitive,exploration,insights,data,unstructured data,query,enrich,ai,artificial intelligence,watson

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

# Welcome to Watson Discovery for Salesforce
{: #welcome}

The {{site.data.keyword.discoveryfull}} for Salesforce app is an AI-powered insight engine for Salesforce Service Cloud users. 

This setup assistant will guide you through the steps of connecting to the data that will power your {{site.data.keyword.discoveryfull}} for Salesforce app. The app will use that data to help your customer service representatives find the answers they need to manage and solve customer cases. 

Your data will be stored on the {{site.data.keyword.Bluemix}}, within collections located in {{site.data.keyword.discoveryshort}}. You can connect to and import data from Salesforce, Microsoft SharePoint Online, IBM Cloud Object Storage, Microsoft SharePoint 2016 On-Premise, and Box, or do a web crawl. You can set up a synchronization schedule so your data is always up-to-date. If you have other data you would like to use that is not stored in those data sources, you can create a collection and upload those documents to {{site.data.keyword.discoveryshort}}. All of these data sources will be used by the {{site.data.keyword.discoveryfull}} app in Salesforce.

An overview of the steps to setup a {{site.data.keyword.discoveryfull}} for Salesforce app follows. If you already have an {{site.data.keyword.Bluemix}} account or {{site.data.keyword.discoveryshort}} instance in the Washington, DC (US East) or Sydney (au-syd) region, you are not required to create new ones.

- Create an [{{site.data.keyword.Bluemix}} account](/docs/services/discovery-sf?topic=discovery-sf-connecting#cloud) (or log into your existing account).
- Create an instance of {{site.data.keyword.discoveryshort}} in the Washington, DC (US East) or Sydney (au-syd) regions (or use an instance you already have in one of those regions). **Note:** If you already have an {{site.data.keyword.Bluemix}} account, {{site.data.keyword.discoveryfull}} for Salesforce will automatically create an instance of {{site.data.keyword.discoveryshort}} for you using a Lite plan.
- [Connect to the data](/docs/services/discovery-sf?topic=discovery-sf-sources#sources) you have stored in Salesforce, Microsoft SharePoint Online, IBM Cloud Object Storage, Microsoft SharePoint 2016 On-Premise, Box, or Web Crawl and specify how often you'd like that data to be updated. You also have the option to create your own data source.
- [Configure](/docs/services/discovery-sf?topic=discovery-sf-configureapp#configureapp) your new {{site.data.keyword.discoveryfull}} for Salesforce app.  

If you do not have an existing {{site.data.keyword.discoveryfull}} plan, see [Discovery pricing plans ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-discovery-pricing-plans#discovery-pricing-plans){: new_window} to review the benefits and limits of each plan. {{site.data.keyword.discoveryfull}} for Salesforce is not supported on Premium and Dedicated plans.

If you are interested in {{site.data.keyword.discoveryfull}} for Salesforce contact your IBM representative for more information.

## Prerequisites and browser support
{: #prereqs}

Prerequisites for {{site.data.keyword.discoveryfull}} for Salesforce:
- An {{site.data.keyword.Bluemix}} account
- To connect to Microsoft SharePoint Online and SharePoint 2016 data: credentials and data locations from your Microsoft SharePoint administrator
- To connect to Box data: credentials and data locations from your Box administrator
- To connect to Salesforce data: Enterprise Salesforce using the Lightning platform
- To connect to IBM Cloud Object Storage: endpoints and access keys from your IBM Cloud Object Storage administrator

**Notes for existing {{site.data.keyword.discoveryshort}} users:** 
- {{site.data.keyword.discoveryshort}} now supports token-based Identity and Access Management (IAM) authentication. IAM uses access tokens rather than service credentials for authentication with a service. If you have an existing {{site.data.keyword.discoveryshort}} instance on Washington, DC (US East) or Sydney (au-syd) that you wish to use for {{site.data.keyword.discoveryfull}} for Salesforce, you must migrate it first. See [Migrating Cloud Foundry service instances to a resource group ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/resources?topic=resources-migrate#migrate){: new_window}.
- Existing {{site.data.keyword.discoveryshort}} collections can't be used with {{site.data.keyword.discoveryfull}} for Salesforce.

For the list of {{site.data.keyword.Bluemix}} prerequisites and supported browsers, see [Prerequisites ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/overview?topic=overview-prereqs-platform#prereqs){: new_window}.

For additional {{site.data.keyword.Bluemix}} resources, see [{{site.data.keyword.Bluemix}} Support Center ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/unifiedsupport/supportcenter){: new_window}.


