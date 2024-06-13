---
Conference: ECS24
Date: 16.05.2024 10:20
Speaker: Kasper Larsen (@kasperbolarsen)
Type: Personal Notes
Categories: Microsoft 365
---

# Using Search to break down information silos

## Intro to Graph Connectors
Although the idea to bring data from 3rd party services into M365 ist nothing new, Graph Connectors stand for this data integration layer.
Once we've integrated the data, we can use it where ever we want:

![Wed-2.1.png](./assets/Wed-2.1.png)

Get a closer look to **Custom Connectors** to integrate your business data.
Having a quick look at PnP Modern Search, the tool is considered to use for Custom Search needs – and not to replace general search scenarios.

## Setting up the solution (DEMO)
Fully demo-packed session – with a great enlightning effect: 
Ingest your business-related data ...
1. ...coming from Azure SQL 
1. ...integrated via a data source that was set up in the Search & Intelligence Admin Center (could also have been a custom Microsoft Graph Connector) 
1. ... to show up in the Microsoft Search index
1. ... and to be used in a PnP Search Result webpart in highly customized page in SharePoint Online

GREAT BALLS OF FIRE! 🔥

### Please consider when ingest data into Microsoft Graph
For each E5 licensed user in the tenant, you will get "credits" for data ingestion. By ingesting data into Microsoft Graph, make sure your data ingestion credits match your needs.
