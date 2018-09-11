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

# Connecting to the IBM Cloud and Watson Discovery

For the list of {{site.data.keyword.Bluemix}} prerequisites and supported browsers, see [Prerequisites ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/overview/prereqs.html#prereqs){: new_window}.

## Getting your IBM Cloud credentials and creating an instance of Discovery
{: #cloud}

{{site.data.keyword.discoveryfull}} is hosted on the {{site.data.keyword.Bluemix}}. 
    
To sign up for a free {{site.data.keyword.Bluemix}} account, go to the [IBM Cloud ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/){: new_window} and click **Create a free account**. You will need to confirm your new account via email to activate it. If you already have an account, click **Login**. 

When creating an instance of {{site.data.keyword.discoveryshort}}, choose **US East** or **Sydney** as your region. 

If you do not have an existing {{site.data.keyword.discoveryfull}} service plan, see [Discovery pricing plans ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/discovery/pricing-details.html){: new_window} to review the benefits and limits of each plan. {{site.data.keyword.discoveryfull}} for Salesforce is not supported on Premium and Dedicated plans.

For additional {{site.data.keyword.Bluemix}} resources, see [IBM Cloud Platform Overview ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/overview/ibm-cloud.html#overview){: new_window}.   


## Connect to the Watson Discovery Service with your API Key
{: #key}

After you have created your {{site.data.keyword.discoveryshort}} instance, the service will appear on the {{site.data.keyword.Bluemix}} dashboard. Click on your service to view the **Credentials** section. The API key is used for connecting your {{site.data.keyword.discoveryshort}} instance to {{site.data.keyword.discoveryfull}} for Salesforce.

To navigate back to the dashboard at any time on the [{{site.data.keyword.Bluemix}} site ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/){: new_window}, click the menu icon on the top left and choose **Dashboard**.

**Note:** If you have an existing {{site.data.keyword.discoveryshort}} instance on **US East** or **Sydney** that you wish to use for {{site.data.keyword.discoveryfull}} for Salesforce, you should migrate it first. See [Migrating Cloud Foundry service instances to a resource group ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/resources/instance_migration.html#migrate){: new_window}. 


    
