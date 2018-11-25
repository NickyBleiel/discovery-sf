---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-25"

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

# Connecting to Data Sources
{: #sources}

With {{site.data.keyword.discoveryfull}} for Salesforce, you can connect to Salesforce, Box, and Microsoft SharePoint Online data sources and import documents into {{site.data.keyword.discoveryshort}} collections. Each data source is stored in a separate {{site.data.keyword.discoveryshort}} collection. You can also [create your own {{site.data.keyword.discoveryshort}} data source](/docs/services/discovery-sf/connect.html#private) if you have want to utilize additional documents that are not stored in Salesforce, Box, or Microsoft SharePoint Online.

The {{site.data.keyword.discoveryshort}} service pulls documents from the data source using a process called crawling. Crawling is the process of systematically browsing and retrieving documents from the specified start location. Only items explicitly specified by you from the following data sources are crawled by the {{site.data.keyword.discoveryshort}} service:

-  [Box](/docs/services/discovery-sf/connect.html#connectbox)
-  [Salesforce](/docs/services/discovery-sf/connect.html#connectsf)
-  [Microsoft SharePoint Online](/docs/services/discovery-sf/connect.html#connectsp)

The following applies to all data sources:

- The individual document file size limit for Salesforce, Microsoft SharePoint Online, and Box is 10MB.
-  You will need the credentials and file locations (or URLs) for each data source - these are typically provided by a developer/system administrator of the data source.
-  You will need to know which resources of the data source to crawl. This information can be provided by the source administrator. When crawling Box or Salesforce, a list of available resources is presented when configuring those data sources.
-  Crawling a data source will use the resources (API calls) of that data source. The number of calls depends on the number of documents crawled. Consult with the source system administrator before starting a crawl. Also confirm that you have the appropriate level of service - for example, Enterprise Salesforce. See [Prerequisites and browser support](/docs/services/discovery-sf/index.html#prereqs).
-  The following file types can be ingested by {{site.data.keyword.discoveryshort}}, all other document types are ignored:
   -  Microsoft Word
   -  PDF
   -  HTML
   -  JSON
-  {{site.data.keyword.discoveryshort}} source crawls do not delete documents that are stored in a collection. When a source is synced (re-crawled), new documents are added, updated documents are modified to the current version, and documents deleted in the original data source remain in the collection as the version last stored.
- If you modify anything on the Salesforce, Microsoft SharePoint Online, or Box configuration screen and then click the **Save and Sync** button, a crawl is started (or restarted if one is already running) at that time.

## Box
{: #connectbox}

You'll need to create a new Box custom application to connect to {{site.data.keyword.discoveryfull}}. The Box application you create requires either Enterprise level or Application level access.

-  If you are not the Box administrator for your organization, [**Application level** access](/docs/services/discovery/connect.html#applevelbox) is recommended. You will need an administrator to approve your application.

-  If you are the Box administrator for your organization, [**Enterprise level** access](/docs/services/discovery/connect.html#entlevelbox) is recommended.

**Note:** The steps to setup Box access may change if there is a Box update. Consult the [Box developer documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.box.com/){: new_window} for updates.

### Setting up Application level access
{: #applevelbox}

1.   Navigate to `https://app.box.com/developers/console` (use your company's Box URL) and click **Create New App**.
1.   From the **Create a New App** screen, select **Enterprise Integration** and click **Next**.
1.   On the **Authentication Method** screen, select **OAuth 2.0 with JWT (Server Authentication)** and click **Next**.
1.   Name your app and click the **Create App** button. Once your Box app has been created, click **View Your App**.
1.   While viewing your app, select **Application access** of **Application**. You can use your existing managed users as you continue; you are not required to create new ones.
1.   Scroll down to the **Application Scopes** section of the page and enable the following checkboxes: 
     - `Read and write all folders stored in Box`
     - `Manage Users`
     - `Manage Enterprise Properties`
1.   Scroll down to the **Advanced Features** section and enable the following toggles:
     - `Perform Actions as Users`
     - `Generate User Access Tokens` 
1.  Click the **Save Changes** button.

The next few steps will require assistance from the Administrator of your organization's Box account. If you are not your organization's Box Administrator, you can identify the Administrator by opening the Box developer's console and looking under **Account settings** > **Account details** > **Settings**.

1.  [Administrator step] Authorize your application client id at `https://app.box.com/master/settings/openbox` by clicking the **Authorize New App** button.
1.  [Administrator step] Type the **client ID** from `https://app.box.com/developers/console` into the **API key** field and then click the **Authorize** button.
1.  [Administrator step] Retrieve a developer token for the application. To do this, navigate to `https://app.box.com/developers/console`, scroll to the **Developer Token** section and generate your token.
1.  Now that the application has been authorized by the Administrator, navigate to `https://developer.box.com/reference#page-create-an-enterprise-user` and create the Box user using the API reference page.

   Sample curl command [from the box API](https://api.box.com/2.0/users):

   ```bash
    curl -X POST -H "Authorization: Bearer <YOUR_DEVELOPER_TOKEN_GOES_HERE>" -d '{"login": "<YOUR_APP_USER_EMAIL>@<YOUR_COMPANY_DOMAIN>", "name": "<YOUR_APP_USER_NAME>"}' 
   ```
   {: pre}

1.  Copy the newly generated **id** field contents and provide them to the non-administrator connecting the Box application to {{site.data.keyword.discoveryfull}}.
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
1.  While viewing your app, select **Application access** of **Application**. You can use your existing managed users as you continue; you are not required to create new ones.
1.  Scroll down to the **Application Scopes** section of the page and enable the following checkboxes: 
    - `Read and write all folders stored in Box`
    - `Manage Users`
1.  Scroll down to the **Advanced Features** section and enable the following toggles:
    - `Perform Actions as Users`
    - `Generate User Access Tokens` 
1.  Click the **Save Changes** button.

The next few steps will require assistance from the Administrator of your organization's Box account. If you are not your organization's Box Administrator, you can identify the Administrator by opening the Box developer's console and looking under **Account settings** > **Account details** > **Settings**.

1.  [Administrator step] Authorize your application client id at `https://app.box.com/master/settings/openbox` by clicking the **Authorize New App** button.
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

-  Knowledge Articles are only crawled if their **version** is `published` and their languages is `en-us`.

## Microsoft SharePoint Online
{: #connectsp}

When connecting to a Microsoft SharePoint Online source, verify that the instance is an Enterprise (E1) plan or higher.

The following credentials are required to connect to a SharePoint Online source; request them from your SharePoint administrator:

-  **Username** - The `client_id` of the source that these credentials connect to.
-  **Password** - The `password` of the source that these credentials connect to. This value is never returned and is only used when creating or modifying credentials.
-  **Organization URL** - The `organization_url` of the source that these credentials connect to.
-  **Site collection path** - The `site_collection.path` of the source that these credentials connect to.

When identifying credentials, it might be useful to consult the [Microsoft SharePoint developer documentation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://docs.microsoft.com/en-us/sharepoint/dev/){: new_window}.

Other items to note when crawling Microsoft SharePoint Online:

-  When crawling SharePoint, you will need to have a list of SharePoint site collection paths that you want to crawl. {{site.data.keyword.discoveryshort}} lets you browse and select which content to crawl. To crawl your entire SharePoint Online site, do not select multiple paths (URLs) in this field. In that scenario, enter a `/` in the `site_collection.path` field.

## Create your own data source
{: #private}

If you have Microsoft Word, PDF, HTML, or JSON documents that are not stored in Salesforce, Box, or Microsoft SharePoint Online, you can create your own {{site.data.keyword.discoveryshort}} collection and manually upload those documents. Click **Upload documents** under **Select a data source** to get started.

When adding documents to your collection, remember :

- The maximum file size that can be uploaded is 50MB.
- When creating a collection, you can select the document language (English is the default). See [Language support ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/discovery/language-support.html){: new_window} for the list of languages. Do not mix languages within the same collection.
- By default, the documents in your collection will be converted using the configuration file provided, which is named **Default Configuration**. If you need to create a custom configuration file, see [Custom configuration ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/discovery/building.html#custom-configuration){: new_window}.
- When documents are uploaded to a data collection, they are converted and enriched using the configuration file chosen for that collection. If you later decide to switch your collection to a different configuration file, any documents that are not re-uploaded remain in the collection converted by the original configuration file unless you do one of the following:
  - Create a new collection, select the new configuration file, then re-upload all of your documents.
  - Retain your existing collection, switch to the new configuration file, delete any documents that you can't re-upload.

The following limits apply when uploading documents:

- 21 in-flight documents in Lite and Standard plans
- 105 in-flight documents in Advanced plans
    
These limits are subject to change. 

When using the {{site.data.keyword.discoveryshort}} service, uploading in-flight represents the document being uploaded and processed before it is added to the collection.

## Labeling and deleting documents
{:# source_customer_id}

For information about GDPR, as well as assigning and deleting `customer_ ID` labels, see [Information security ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/discovery/information-security.html){: new_window} and [Specifying a customer_id ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/discovery/connect.html#specifying-a-customer_id-){: new_window}.
