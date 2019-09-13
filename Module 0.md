# Knowledge Mining Workshop

Welcome to the Knowledge Mining workshop!  This training is meant to walk you through building out your own knowledge mining solution.  You'll learn how to build an Azure Search Index and Knowledge Store repository through the Azure Portal.  From there, we'll explore more advanced concepts in Azure Search, build custom skills to extend the solution and create a basic web page front end to visualize your search results.  Finally, you will build a PowerBI dashboard on top of your Knowledge Store to demonstrate how you can use your data store for data visualization and advanced analytics.  We have also included an Optional Module 7  which is a stand alone module that will walk y you through indexing data from an AzureSQL datasource.  We encourage you to walk through this module on your own time and review how this further extends the data available in your solution.

Please make sure to complete all of  pre-requisites listed below before moving on, as you will not be able to complete the excercises in this lab without them.

## Pre-Requisites
Please make sure you fulfill the following pre-requisites before starting the workshop.
1.	Have your own Azure account 
2.	Be familiar [Azure Portal](https://portal.azure.com)
3.	Make sure you can create Azure resources (including paid resources).
4. Create a resource group for this workshop where you will add each of the resources you will create in the next steps.
4. **Create** an [Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal).
Select Performance: *Standard* tier, not Premium
Select Account kind: *StorageV2 (general purpose v2)*

5.	In the Azure storage account, **create** an [Azure Storage resource (Blob) container](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal) called *clinical-trials-small*.
6. **Unzip and copy** the clinical trials files from [clinical-trials-small.zip](./data) in the /data folder of this repository to the newly created clinical-trials-small container.
7.	**Create** an [Azure Search](https://docs.microsoft.com/en-us/azure/search/search-create-service-portal) resource. (A Free Tier should be sufficient for this workshop).
[Learn more](https://docs.microsoft.com/en-us/azure/search/search-sku-tier)

8.	**Create** a [Cognitive Services resource](https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-apis-create-account?tabs=multiservice%2Cwindows).

  *Note - You need to create the Cognitive Services resource in the same region as you Azure Search resource*. 

9.	**Install** [Visual Studio 2019](https://visualstudio.microsoft.com/) or later. Make sure you can create ASP.Net websites with it.
10. **Install** [Postman](https://www.getpostman.com/)
11. **Install** [PowerBI desktop](https://powerbi.microsoft.com/en-us/desktop/).
12. **Install** [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/)


## Agenda

+ Module 1 - Using Azure Portal to Build a Search Index and Knowledge Store
+ Module 2 - Introduction to Custom Skills and Azure Functions
+ Module 3 - Learn the Object Model and Advanced Skills
+ Module 4 - Advanced Azure Search: Analyzers and Scoring Profiles
+ Module 5 - Visualizing Your Results in a Web Page
+ Module 6 - Analyzing Your Data with PowerBI
+ Module 7 - Using Azure Search to index structured data
