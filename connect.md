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

# Connecting to Data Sources
{: #sources}

With {{site.data.keyword.discoveryfull}} for Salesforce, you can connect to Salesforce, Box, Microsoft SharePoint Online, IBM Cloud Object Storage, and Microsoft SharePoint 2016 On-Premise data sources (or do a web crawl) and import documents into {{site.data.keyword.discoveryshort}} collections. You can also [create your own {{site.data.keyword.discoveryshort}} data source](/docs/services/discovery-sf?topic=discovery-sf-sources#private) if you want to utilize additional documents not stored in those data sources. 

If using the {{site.data.keyword.discoveryshort}} tooling, each collection can be configured to use a single data source; if using the API, you can send documents from multiple data sources into a single collection.

{{site.data.keyword.discoveryshort}} pulls documents from the data source using a process called crawling. Crawling is the process of systematically browsing and retrieving documents from the specified start location. Only items explicitly specified by you from the following data sources are crawled by {{site.data.keyword.discoveryshort}}:

-  [Box](/docs/services/discovery-sf?topic=discovery-sf-sources#connectbox)
-  [Salesforce](/docs/services/discovery-sf?topic=discovery-sf-sources#connectsf)
-  [Microsoft SharePoint Online](/docs/services/discovery-sf?topic=discovery-sf-sources#connectsp)
-  [Microsoft SharePoint 2016 On-Premise](/docs/services/discovery-sf?topic=discovery-sf-sources#connectsp_op)
-  [Web Crawl](/docs/services/discovery-sf?topic=discovery-sf-sources#connectwebcrawl) (beta)
-  [IBM Cloud Object Storage](/docs/services/discovery-sf?topic=discovery-sf-sources#connectcos) 

The following applies to all data sources:

- The individual document file size limit for Salesforce, Microsoft SharePoint Online, Microsoft SharePoint 2016, IBM Cloud Object Storage, Web Crawl, and Box is 10MB.
-  You will need the credentials and file locations (or URLs) for each data source - these are typically provided by a developer/system administrator of the data source.
-  You will need to know which resources of the data source to crawl. This information can be provided by the source administrator. When crawling Box or Salesforce, a list of available resources is presented when configuring those data sources.
-  Crawling a data source will use resources (API calls) of the data source. The number of API calls depends on the number of documents that need to be crawled. Also confirm that you have the appropriate level of service - for example, Enterprise Salesforce - and that the source system administrator is consulted. See [Prerequisites and browser support](/docs/services/discovery-sf?topic=discovery-sf-welcome#prereqs).
-  The following file types can be ingested by {{site.data.keyword.discoveryshort}} for Salesforce, all other document types are ignored:
   
Collection | Lite plans | Advanced plans 
---------------- | ------------------------------ | ------------------------------------------- 
Existing collections created specifically for {{site.data.keyword.discoveryfull}} before the release of [Smart Document Understanding (SDU) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-release-notes#22jan19){: new_window} | Microsoft Word, PDF, HTML, JSON | Microsoft Word, PDF, HTML, JSON     
Collections created after the release of [SDU](/docs/services/discovery?topic=discovery-sdu#sdu) | PDF, Word, PowerPoint, Excel, JSON\*, HTML\* | PDF, Word, PowerPoint, Excel, PNG\*\*, TIFF\*\*, JPG\*\*, JSON\*, HTML\* 
    
\* JSON and HTML documents are supported by {{site.data.keyword.discoveryfull}}, but can not be edited using the SDU editor. To change the configuration of HTML and JSON docs, you need to use the API. For more information, see the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/discovery/){: new_window}.

\*\* Individual image files (PNG, TIFF, JPG) are scanned and the text (if any) is extracted. PNG, TIFF, and JPEG images embedded in PDF, Word, PowerPoint, and Excel files will also be scanned and the text (if any) extracted.

-  {{site.data.keyword.discoveryshort}} source crawls do not delete documents that are stored in a collection. When a source is synced (re-crawled), new documents are added, updated documents are modified to the current version, and documents deleted in the original data source remain in the collection as the version last stored.
-  If you modify anything on the Salesforce, Microsoft SharePoint Online, IBM Cloud Object Storage, Microsoft SharePoint 2016 On-Premise, web crawl, or Box configuration screen and then click the **Save and Sync** button, a crawl is started (or restarted if one is already running) at that time.
-  If you select an on-premise data source, you must first install and configure IBM Secure Gateway. See [Installing IBM Secure Gateway for on-premise data](/docs/services/discovery-sf?topic=discovery-sf-sources#gateway) for more information.
-  Synchronization options are:
    -  `Every five minutes`: runs every five minutes
    -  `Hourly`: runs every hour
    -  `Daily`: runs every day between the hours of 00:00 and 06:00 in the specified time zone
    -  `Weekly`: runs every week on Sunday between hours of 00:00 and 06:00 in the specified time zone
    -  `Monthly`: runs every month on the first Sunday of the month between the hours of 00:00 and 06:00 in the specified time zone  

## Box
{: #connectbox}

You'll need to create a new Box custom application to connect to {{site.data.keyword.discoveryfull}}. The Box application you create requires either Enterprise level or Application level access.

-  If you are not the Box administrator for your organization, [**Application level** access](/docs/services/discovery-sf?topic=discovery-sf-sources#applevelbox) is recommended. You will need an administrator to approve your application.
-  If you are the Box administrator for your organization, [**Enterprise level** access](/docs/services/discovery-sf?topic=discovery-sf-sources#entlevelbox) is recommended.

**Note:** The steps to setup Box access may change if there is a Box update. Consult the [Box developer documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.box.com/){: new_window} for updates.

### Setting up Application level access
{: #applevelbox}

1.   Navigate to `https://app.box.com/developers/console` (use your company's Box URL) and click **Create New App**.
1.   From the **Create a New App** screen, select **Enterprise Integration** and click **Next**.
1.   On the **Authentication Method** screen, select **OAuth 2.0 with JWT (Server Authentication)** and click **Next**.
1.   Name your app and click the **Create App** button. Once your Box app has been created, click **View Your App**.
1.   While viewing your app, select **Application access** as **Application**. You can use your existing managed users as you continue; you are not required to create new ones.
1.   Scroll down to the **Application Scopes** section of the page and enable the following checkboxes: 
     - `Read and write all folders stored in Box`
     - `Manage Users`
1.   Scroll down to the **Advanced Features** section and enable the following toggles:
     - `Perform Actions as Users`
     - `Generate User Access Tokens` 
1.  Click the **Save Changes** button.

The next few steps will require assistance from the Administrator of your organization's Box account. If you are not your organization's Box Administrator, you can identify the Administrator by opening the Box developer's console and looking under **Account settings** > **Account details** > **Settings**.

1.  [Administrator step] Authorize your application client id at `https://app.box.com/master/settings/openbox` by clicking the **Authorize New App** button.
1.  [Administrator step] Type the **client ID** from `https://app.box.com/developers/console` into the **API key** field and then click the **Authorize** button.
1.  [Administrator step] Retrieve a developer token for the application. To do this, navigate to `https://app.box.com/developers/console`, scroll to the **Developer Token** section and generate your token.
1.  Now that the application has been authorized by the Administrator, navigate to `https://developer.box.com/reference#page-create-an-enterprise-user` and create an App User using the API reference page.

   Curl example to create an App User:

   ```bash
    curl https://api.box.com/2.0/users -H "Authorization: Bearer ACCESS_TOKEN" -d '{"name": "NedStark", "is_platform_access_only": true}' -X POST
   ```
   {: pre}

1.  Copy the newly generated **id** field contents and provide them to the non-administrator connecting the Box application to {{site.data.keyword.discoveryfull}}.
1.  Once the App User is created, the folders you want to crawl need to be shared with the App User, and the App User must be given `Viewer` permissions on those folders. This requires the App User login name from the above curl command response. Example:`"login":"AppUser_737729_jmUo@boxdevedition.com"`.
1.  Return to the Box developer console `https://app.box.com/developers/console` and scroll to the **Add and Manage Public Keys** section. Click the **Generate the public/private keypair** and download your keypair file. Open the file.
1.  From the keypair file, cut and paste the following fields into the {{site.data.keyword.discoveryshort}} tooling.
    -  `client_id`
    -  `enterprise_id`
    -  `client_secret` 
    -  `public_key_id` 
    -  `private_key` 
    -  `passphrase` 

### Setting up Enterprise level access
{: #entlevelbox}

1.  Navigate to `https://app.box.com/developers/console` (use your company's Box URL) and click **Create New App**.
1.  From the **Create a New App** screen, select **Enterprise Integration** and click **Next**.
1.  On the **Authentication Method** screen, select **OAuth 2.0 with JWT (Server Authentication)** and click **Next**.
1.  Name your app and click the **Create App** button. Once your Box app has been created, click **View Your App**.
1.  While viewing your app, select **Application access** as **Enterprise**. You can use your existing managed users as you continue; you are not required to create new ones.
1.  Scroll down to the **Application Scopes** section of the page and enable the following checkboxes: 
    - `Read and write all folders stored in Box`
    - `Manage Users`
    - `Manage Enterprise Properties`
1.  Scroll down to the **Advanced Features** section and enable the following toggles:
    - `Perform Actions as Users`
    - `Generate User Access Tokens` 
1.  Click the **Save Changes** button.

`Refresh` is only supported with Enterprise level access.
{: note}

If you change your Box App settings, `Reauthorize` your App so the changes take effect.
{: tip}

The next few steps will require assistance from the Administrator of your organization's Box account. If you are not your organization's Box Administrator, you can identify the Administrator by opening the Box developer's console and looking under **Account settings** > **Account details** > **Settings**.

1.  [Administrator step] Authorize your application client id by navigating to **Admin console** > **Enterprise settings** > **Apps** and scrolling to `Custom applications`. Example URL:`https://app.box.com/master/settings/openbox`.
1.  [Administrator step] Type the **client ID** from `https://app.box.com/developers/console` into the **API key** field and then click the **Authorize** button.
1.  Return to the Box developer console `https://app.box.com/developers/console` and scroll to the **Add and Manage Public Keys** section. Click the **Generate the public/private keypair** and download your keypair file. Open the file.
1.  From the keypair file, cut and paste the following fields into the {{site.data.keyword.discoveryshort}} tooling.
    -  `client_id`
    -  `enterprise_id`
    -  `client_secret` 
    -  `public_key_id` 
    -  `private_key` 
    -  `passphrase` 

Other items to consider when crawling Box:

-  Box notes are stored in JSON format, so any Box notes in the specified folders will be ingested by {{site.data.keyword.discoveryshort}}.
-  When using the API, you will need to have a list of Folders IDs and the associated Owner ID for each folder that you want to crawl. The {{site.data.keyword.discoveryshort}} tooling lets you browse and select which content to crawl.

## Salesforce
{: #connectsf}

When connecting to a Salesforce source, verify that the instance is an Enterprise plan or higher.

The following credentials are required to connect to a Salesforce source; request them from your Salesforce administrator:

-  **URL** - The `url` of the source that these credentials connect to.
-  **Username** - The `username` of the source that these credentials connect to.
-  **Password plus service token** - The `password` consists of the Salesforce password and a valid Salesforce security token concatenated. This value is never returned and is only used when creating or modifying credentials.

When identifying credentials, it might be useful to consult the [Salesforce developer documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.salesforce.com/docs/){: new_window}.

Other items to note when crawling Salesforce:

-  Knowledge Articles are only crawled if their **version** is `published` and their language is `en-us`.

## Microsoft SharePoint Online
{: #connectsp}

When connecting to a Microsoft SharePoint Online source, verify that the instance is an Enterprise (E1) plan or higher.

The following credentials are required to connect to a SharePoint Online source; request them from your SharePoint administrator:

-  **Username** - The `client_id` of the source that these credentials connect to. This user must have access to all sites and lists that need to be crawled and indexed.
-  **Password** - The `password` of the source that these credentials connect to. This value is never returned and is only used when creating or modifying credentials.
-  **Organization URL** - The `organization_url` of the source that these credentials connect to.
-  **Site collection path** - The `site_collection.path` of the source that these credentials connect to.

When identifying credentials, it might be useful to consult the [Microsoft SharePoint developer documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.microsoft.com/en-us/sharepoint/dev/){: new_window}.

Other items to note when crawling Microsoft SharePoint Online:

- To crawl SharePoint Online, the `Crawl User` account must have `SiteCollection Administrator` permissions.
-  When crawling SharePoint, you will need the list of SharePoint site collection paths that you want to crawl. {{site.data.keyword.discoveryshort}} does not support folder paths as an input.

## Web Crawl
{: #connectwebcrawl}

This beta feature can be used crawl public websites that don’t require a password. You can select how often you'd like {{site.data.keyword.discoveryshort}} to sync with the websites, the language, and the number of hops.

-  **Sync my data** - You can choose to sync every 5 minutes, hourly, daily, weekly, or monthly.  
-  **Select language** - Choose the language of the websites from the list of supported languages. See [Language support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-language-support#supported-languages){: new_window} for the list of languages supported by {{site.data.keyword.discoveryshort}}. It is recommended that you create a separate collection for each language.
-  **URL group to sync** - Enter your URL and click the plus sign to add it to the URL group. To specify the **Crawl settings** for this URL group, click the **Cog** icon. You can set the **Maximum hops**, which is the number of consecutive links to follow from the starting URL (the starting URL is `0`). The default number of hops is `2` and the maximum is `20` (if using the API, the maximum is `1000`). 

For this beta release, the number of web pages crawled will be limited, so the web crawler may not crawl all the websites specified and reach the maximum number of hops.
{: note}

If you require different **Crawl settings** for other URLs, click **Add URL group** and create a new group. You can create as many URL groups as you need.
{: tip}

## Installing IBM Secure Gateway for on-premise data 
{: #gateway}

To connect to an on-premise data source, you first need to download, install, and configure IBM Secure Gateway. After you have installed IBM Secure Gateway for your first on-premise data source, you won't need to repeat this process.

1.  From the **Manage data** page of the {{site.data.keyword.discoveryshort}} tooling, select **Connect a data source**.
1.  Select the data source that you want to connect to. When you select an on-premise data source, go to the **Connect to your on-premise network** section and click the **Make connection** button.
1.  On the **Download and install the Secure Gateway Client** screen, download the appropriate version of IBM Secure Gateway.
1.  After you have completed the download, click the **Download Secure Gateway and Continue** button. During installation, you will need the **Gateway ID** and **Token** provided on the screen when prompted by the Secure Gateway Client. See [Installing the client ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/SecureGateway?topic=securegateway-client-install#installing-the-client){: new_window} in the Secure Gateway documentation for installation instructions.
1.  On the machine running the Secure Gateway Client, open the Secure Gateway dashboard at http://localhost:9003.
1.  Click **add ACL** on the dashboard. Add the endpoint URL of each SharePoint collection to the **Allow access** list. For example, Hostname: `appconnmssharep` and port: `80`.
1.  Return to the {{site.data.keyword.discoveryshort}} tooling and click **Continue**. If the connection is successful you will see the `Connection successful` message. If the connection was not successful, open the Secure Gateway dashboard and verify that the endpoints on the **Allow access** list are correct.

After the connection is successful you can begin entering the credentials for your on-premise data source.

## SharePoint 2016 On-Premise
{: #connectsp_op}

Microsoft SharePoint 2016 (also known as SharePoint Server 2016) is an on-premise data source. To connect to it, you must first install and configure IBM Secure Gateway. See [Installing IBM Secure Gateway for on-premise data](/docs/services/discovery-sf?topic=discovery-sf-sources#gateway) for more information.
{: note}

The following credentials are required to connect to a SharePoint 2016 data source, they should be obtained from your SharePoint administrator:

-  **Username** - The `client_id` of the source that these credentials connect to. This user must have access to all sites and lists that need to be crawled and indexed.
-  **Password** - The `password` of the source that these credentials connect to. This value is never returned and is only used when creating or modifying credentials.
-  **Web Application Url** - The SharePoint 2016 `web_application_url`; for example, https://sharepointwebapp.com:8443. If the port is not supplied, it defaults to port `80` for http and port `443` for https.
-  **Domain** - The `domain` of the SharePoint 2016 account.

When identifying the credentials, it might be useful to consult the [Microsoft SharePoint developer documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.microsoft.com/en-us/sharepoint/dev/){: new_window}.

Other items to note when crawling Microsoft SharePoint 2016:

- To crawl SharePoint 2016, the `Crawl User` account must have `SiteCollection Administrator` permissions.
-  When crawling SharePoint, you will need the list of SharePoint site collection paths that you want to crawl. {{site.data.keyword.discoveryshort}} does not support folder paths as an input.

## IBM Cloud Object Storage
{: #connectcos}

When connecting to an IBM Cloud Object Storage source, the following credentials are required. They should be obtained from your IBM Cloud Object Storage administrator:

-  **Endpoint** - The `endpoint` used to interact with IBM Cloud Object Storage data.
-  **Access key id** - `access_key_id` obtained when the IBM Cloud Object Storage instance was created.
-  **Secret access key** - `secret_access_key` to sign requests obtained when the IBM Cloud Object storage instance was created.

After this information is entered, you can choose how often you'd like to sync your data and select the buckets you want to sync to.

Other items to note when crawling IBM Cloud Object Storage:

-  This connector doesn't support crawling private endpoints.
-  There is a slight performance issue if all buckets are selected. In this case, there may be a delay before the documents complete indexing.

## Create your own data source
{: #private}

If you have documents that are not stored in Salesforce, Box, Microsoft SharePoint Online, SharePoint 2016, or available using Web Crawl, you can create your own {{site.data.keyword.discoveryshort}} collection and manually upload those documents. Click **Upload documents** under **Select a data source** to get started.

When creating your collection, remember:

- The maximum file size that can be uploaded is 50MB.
- When creating a collection, you can select the document language (English is the default). See [Language support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-language-support#language-support){: new_window} for the list of languages. Do not mix languages within the same collection.
- You will configure your documents using [Smart Document Understanding (SDU) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-sdu#sdu){: new_window}.

The following limits apply when uploading documents:

- 21 in-flight documents in Lite and Standard plans
- 105 in-flight documents in Advanced plans
    
These limits are subject to change. 

When using {{site.data.keyword.discoveryshort}}, uploading in-flight represents the document being uploaded and processed before it is added to the collection.

## Labeling and deleting documents
{: #source_customer_id}

For information about GDPR, as well as assigning and deleting `customer_ ID` labels, see [Information security ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-information-security#information-security){: new_window} and [Specifying a customer_id ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-sources#specifying-a-customer_id-){: new_window}.