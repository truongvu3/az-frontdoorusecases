# Databricks & Front Door

## Using a Front Door to Provide Fixed Connections Strings for BI Clients

In order for BI clients, such as PowerBI or Tableau, to connect with Databricks clusters, Databricks creates a connection string containing the hostname for the workspace and a http path for a specific cluster. Both the hostname and the http path vary as soon as a new workspace or a cluster is deployed. 

Azure Front Door can be used to create a fixed connection string for the clients to connect to Databricks. 


## Creating Front Door Profile

### Select Front Door and CDN profiles in Azure Marketplace

2. Choose Standard or Premium Tier according to requirements (https://docs.microsoft.com/en-us/azure/frontdoor/standard-premium/tier-comparison)

3. Click "Add and endpoint in Endpoint tab.
a. 
