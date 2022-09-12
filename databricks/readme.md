# Databricks & Front Door

## Creating a Front Door Profile to Provide Fixed Connections Strings for BI Clients

In order for BI clients, such as PowerBI or Tableau, to connect with Databricks clusters, Databricks creates a connection string containing the hostname for the workspace and a http path for a specific cluster. Both the hostname and the http path vary as soon as a new workspace or a cluster is deployed. 

Azure Front Door can be used to create a fixed connection string for the clients to connect to Databricks. 


