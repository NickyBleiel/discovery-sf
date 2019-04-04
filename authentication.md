---

copyright:
  years: 2015, 2018, 2019
lastupdated: "2019-04-04"

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

# Connecting to the IBM Cloud and Watson Discovery
{: #connecting}

For the list of {{site.data.keyword.Bluemix}} prerequisites and supported browsers, see [Prerequisites ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/overview?topic=overview-prereqs-platform#prereqs){: new_window}.

## Getting your IBM Cloud credentials and creating an instance of Discovery
{: #cloud}

{{site.data.keyword.discoveryfull}} is hosted on the {{site.data.keyword.Bluemix}}. 
    
To sign up for a free {{site.data.keyword.Bluemix}} account, go to the [{{site.data.keyword.Bluemix}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/){: new_window} and click **Create a free account**. You will need to confirm your new account via email to activate it. If you already have an account, click **Login**. 

When creating an instance of {{site.data.keyword.discoveryshort}}, choose Washington, DC (US East) or Sydney (au-syd) as your region. 

If you do not have an existing {{site.data.keyword.discoveryfull}} plan, see [Discovery pricing plans ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-discovery-pricing-plans#discovery-pricing-plans){: new_window} to review the benefits and limits of each plan. {{site.data.keyword.discoveryfull}} for Salesforce is not supported on Premium and Dedicated plans.

For additional {{site.data.keyword.Bluemix}} resources, see [{{site.data.keyword.Bluemix}} Platform Overview ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/overview?topic=overview-whatis-platform#overview){: new_window}.   


## Connect to Watson Discovery with your API Key
{: #key}

After you have created your {{site.data.keyword.discoveryshort}} instance, the service will appear on the {{site.data.keyword.Bluemix}} dashboard. Click on your service to view the **Credentials** section. The API key is used for connecting your {{site.data.keyword.discoveryshort}} instance to {{site.data.keyword.discoveryfull}} for Salesforce.

To navigate back to the dashboard at any time on the [{{site.data.keyword.Bluemix}} site ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/catalog/){: new_window}, click the menu icon on the top left and choose **Dashboard**.

**Note:** If you have an existing {{site.data.keyword.discoveryshort}} instance on Washington, DC (US East) or Sydney (au-syd) that you wish to use for {{site.data.keyword.discoveryfull}} for Salesforce, you should migrate it first. See [Migrating Cloud Foundry service instances to a resource group ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/resources?topic=resources-migrate#migrate){: new_window}. 


    
