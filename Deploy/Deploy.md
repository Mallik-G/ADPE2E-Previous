# Deploy Azure Data Platform End2End to your subscription

In this section you will automatically provision all Azure resources required to complete labs 1 though to 5. We will use a pre-defined ARM template with the definition of all Azure services used to ingest, store, process and visualise data. 

## Azure services provisioned for the workshop

The following Azure services will be deployed in your subscription:

Name                        | Type | Pricing Tier | Pricing Info |
----------------------------|------|--------------|--------------|
mdwcosmosdb-*suffix*        | Azure Cosmos DB account | 400 RU/sec | https://azure.microsoft.com/en-us/pricing/details/cosmos-db/
MDWDatabricks-*suffix*      | Azure Databricks Service | Standard | https://azure.microsoft.com/en-us/pricing/details/databricks/
MDWComputerVision	        | Cognitive Services | S1 | https://azure.microsoft.com/en-us/pricing/details/cognitive-services/computer-vision/
MDWTextAnalytics	        | Cognitive Services | Standard | https://azure.microsoft.com/en-us/pricing/details/cognitive-services/text-analytics/
MDWDataFactory-*suffix*	    | Data factory (V2) | Data pipelines | https://azure.microsoft.com/en-us/pricing/details/data-factory/
MDWEventHubs-*suffix*       | Event Hubs Namespace | Standard | https://azure.microsoft.com/en-us/pricing/details/event-hubs/
MDWKeyVault-*suffix*        | Key vault | Standard | https://azure.microsoft.com/en-us/pricing/details/key-vault/
MDWLogicApp	                | Logic app | | https://azure.microsoft.com/en-au/pricing/details/logic-apps/
MDWASQLDW                   | SQL data warehouse | DW200c | https://azure.microsoft.com/en-us/pricing/details/sql-data-warehouse/gen2/
NYCDataSets                   | SQL database | Standard S1 | https://azure.microsoft.com/en-au/pricing/details/sql-database/single/
mdwsqlvirtualserver-*suffix*| SQL server || 
mdwdatalakesuffix	        | Storage account || https://azure.microsoft.com/en-us/pricing/details/storage/blobs/
MDWStreamAnalytics-*suffix*	| Stream Analytics job | 3 SU | https://azure.microsoft.com/en-us/pricing/details/stream-analytics/
MDWDesktop	                | Virtual machine | A4 v2 | https://azure.microsoft.com/en-us/pricing/details/virtual-machines/windows/
MDWDesktop_OsDisk	        | Disk | E10 | https://azure.microsoft.com/en-us/pricing/details/managed-disks/
MDWDesktop-nic	            | Network interface ||
MDWDesktop-publicip	        | Public IP address || https://azure.microsoft.com/en-us/pricing/details/ip-addresses/
MDWVirtualNetwork	        | Virtual network || https://azure.microsoft.com/en-us/pricing/details/virtual-network/


 <br>**IMPORTANT**: When you deploy the lab resources in your own subscription you are responsible for the charges related to the use of the services provisioned. If you don't want any extra charges associated with the lab resources you should delete the lab resource group and all resources in it.

The estimated time to complete this lab is: 30 minutes.

## Prepare your Azure subscription
In this section you will use the Azure Portal to create a Resource Group that will host the Azure Data Services used in labs 1 through to 5.

**IMPORTANT**|
-------------|
**Execute these steps on your host computer**|

1.	Open the browser and navigate to https://portal.azure.com

    ![](./Media/Lab0-Image01.png)

2.	Log on to Azure using your account credentials

    ![](./Media/Lab0-Image02.png)

3.	Once you have successfully logged on, locate the **Favourites** menu on the left-hand side panel and click the **Resource groups** item to open the **Resource groups** blade.

4.	On the **Resource groups** blade, click the **+ Add** button to create a new resource group.

    ![](./Media/Lab0-Image03.png)

5.	On the **Create a resource group** blade, select your subscription in **Subscription** drop down list.

6.	In the Resource group text box enter “MDW-Lab”

    **IMPORTANT**: If you are deploying this workshop to multiple students using the same subscription then add the student alias to the resources group name so they can identify their own set of resources and avoid confusion during the labs. Example: "MDW-Lab-*Student01*"

    **IMPORTANT**: The name of the resource group chosen is *not* relevant to the successful completion of the labs. If you choose to use a different name, then please proceed with the rest of the lab using your unique name for the resource group.

    ![](./Media/Lab0-Image04.png)

8.	In the Region drop down list, select one of the regions from the list below.

    **IMPORTANT**: The ARM template you will use to deploy the lab components uses the Resource Group region as the default region for all services. To avoid deployment errors when services are not available in the region selected, please use one of the recommended regions in the list below.

    Recommended Regions|
    -------------------|
    Central US|
    East US|
    East US 2|
    South Central US|
    West US|
    West US 2|
    UK South|
    Japan East|
    Central India|
    West Europe|
    North Europe|
    Canada Central|
    Australia East|
    Southeast Asia|

9.	Proceed to create the resource group by clicking **Review + Create**, and then **Create**.

--------------------------------------
## Deploy Azure Services
In this section you will use automated deployment and ARM templates to automate the deployment of all Azure Data Services used in labs 1 through to 5.

1. You can deploy all Azure services required in each lab by clicking the **Deploy to Azure** button below. 

    [![Deploy to Azure](https://azuredeploy.net/deploybutton.png)](https://azuredeploy.net/)

2. On the **Deploy to Azure - Setup** page provide:
    <br>- Your organisation directory
    <br>- The subscription you want to use
    <br>- The resource group you created in the previous section

    ![](./Media/Lab0-Image06.png)

3. Click **Next**

4. On the **Deploy to Azure - Preview** just click **Deploy**

    ![](./Media/Lab0-Image07.png)

5. On the Azure Portal, navigate to your resource group.

6. On the **Overview** panel, click on the **Deployments** link to follow the progress of your deployment. A successful deployment should last less than 10 minutes.

    ![](./Media/Lab0-Image08.png)

7. Once your deployment is complete you are ready to start your labs. Enjoy!

    ![](./Media/Lab0-Image09.png)

## Workshop cost management

The approximate cost to run the resources provisioned for the estimated duration of this workshop (2 days) is around USD 100.00. Remember that you will start get charged from the moment the resource template deployment completes successfully. You can minimise costs during the execution of the labs by taking the following actions below:

Azure Resource | Type | Action |
---------------|------|--------|
MDWASQLDW      | Azure SQL Data Warehouse | Pause it after completing Lab 3|
MDWDatabricks | Databricks Workspace | Stop cluster after completing Lab 4
MDWCosmosDB   | Cosmos DB | Delete ImageMetadata container after completing Lab 4
MDWDesktop | Virtual Machine | Stop it after completing Lab 4
MDWLogicApp | Logic App | Disable it after completing Lab 5
MDWStreamAnalytics | Stream Analytics job | Pause job after completing Lab 5

Some of the services still incur costs even when not running. If you don't want any extra charges associated with the lab resources you should delete the lab resource group and all resources in it.