# Databricks & Front Door

## Using Front Door to Provide Fixed Connections Strings for BI Clients

In order for BI clients, such as PowerBI or Tableau, to connect with Databricks clusters, Databricks creates a connection string containing the hostname for the workspace and a http path for a specific cluster. Both the hostname and the http path vary as soon as a new workspace or a cluster is deployed. 

Azure Front Door can be used to create a fixed connection string for the clients to connect to Databricks. 


## Creating Front Door Profile and Rule Set for Databricks Use Case

1. Select Front Door and CDN profiles in Azure Marketplace

2. Choose Standard or Premium Tier according to requirements (https://docs.microsoft.com/en-us/azure/frontdoor/standard-premium/tier-comparison)

3. Click "Add and endpoint" in Endpoint tab and specify a name for the endpoint which is going to be the fixed hostname the clients are connecting to
![image](https://user-images.githubusercontent.com/22439398/189684490-4d4072a6-7be5-4188-a160-ac0bf43425f4.png) A mask appears to edit route and security policy

4. Click on add route and specify a name for the route

5. Click on "Add a new origin group" under the Origin group field and specify a name for the origin group (where the Front Door fixed hostname is pointing to, in this case the Databricks hostname)

6. Click on "Add an origin" to specify name of origin, select Custom for Origin type, type in the Databricks hostname in Host name and leave default entries for the remaining fiels

7. Select the newly created origin group in the Origin group field and click on Add to add route

8. Review and Create resource

We have created the endpoint, the fixed Front Door hostname and the routing to the Databricks hostname. However, the http path has to be added as rule.

9. Select the newly created Front Door profile and select Rule set in the blade

10. Click on Add to add a new rule set

11. Specify a name for the rule set and a name for the first rule

In this example we are going to use the request path /1 to get forwarded to our destination databricks cluster path.

12. Add the following condition and action and replace path in Destination with Databricks cluster http path.

![image](https://user-images.githubusercontent.com/22439398/189690336-e833cdc4-b331-478c-954c-877bc24889e2.png)

13. Save rule and wait a few minutes for the settings to get propagated through the network

14. Use the newly created Front Door endpoint hostname as hostname for the BI client connection with Databricks and /1 as http path.

## For more infortion about Front Door:

https://docs.microsoft.com/en-us/azure/frontdoor/create-front-door-portal

https://docs.microsoft.com/en-us/azure/frontdoor/front-door-rules-engine?pivots=front-door-standard-premium


