---

copyright:
  years: 2015, 2018, 2019
lastupdated: "2019-02-01"

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

# Viewing metrics and improving query results with the Performance dashboard
{: #performance}

The Performance dashboard can be used to view query metrics, as well as improve query results.

You can access the Performance dashboard by clicking the **View data metrics** icon on the left. The dashboard is not available in Premium and Dedicated environments.

There are two options to improve natural language query results:
- [Fix queries with no results by adding more data](/docs/services/discovery-sf?topic=discovery-sf-performance#data)
- [Bring relevant results to the top by training your data](/docs/services/discovery-sf?topic=discovery-sf-performance#relevancy)

You can view data metrics in the [query overview](/docs/services/discovery-sf?topic=discovery-sf-performance#overview). 

## Fix queries with no results by adding more data
{: #data}

In this section of the dashboard, you can review queries that returned zero results, and add more data so that those queries will return results in the future. Click the **View all and add data** button to get started. 

## Bring relevant results to the top by training your data
{: #relevancy}

In this section, you can train your collections to improve the relevance of natural language query results. Click the **View all and perform relevancy training** button to get started. Then see [Adding queries and rating the relevancy of results ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#results){: new_window} for additional instructions.

For more about training requirements and options, see [Improving result relevance with the tooling ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/docs/services/discovery?topic=discovery-improving-result-relevance-with-the-tooling#improving-result-relevance-with-the-tooling){: new_window}.

## Query overview
{: #overview}

The **Query overview** section displays information you can use to improve performance:

- The total number of queries made by users
- The percentage of queries with one or more results clicked
- The percentage of queries with no results clicked
- The percentage of queries with no results returned
- A graph that displays these results over time, so that you can track how adding more data and relevancy training are improving performance