# Knowledge Mining Workshop
## Introduction
In this workshop, you will be working through a series of modules that will guide you in creating a searchable index and an application that will allow you to see the search results. We will be indexing a set of clinical trials.

## Pre-Requisites
Please make sure you fulfill the following pre-requisites before starting the workshop.
1.	Have your own Azure account 
2.	Be familiar [Azure Portal](https://portal.azure.com)
3.	Make sure you can create Azure resources (including paid resources).
4. Create a resource group for this workshop where you will add each of the resources you will create in the next steps.
4. **Create** an [Azure Storage Account](https://docs.microsoft.com/en-us/azure/storage/common/storage-quickstart-create-account?tabs=azure-portal). Make sure this is a *Standard* tier, not Premium. 
5.	In the Azure storage account, **create** an [Azure Storage resource (Blob) container](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal) called *clinical-trials-small*.
6. **Unzip and copy** the clinical trials files from clinical-trials-small.zip in the /data folder of this repository to the newly created clinical-trials-small container.
7.	**Create** an [Azure Search](https://docs.microsoft.com/en-us/azure/search/search-create-service-portal) resource (We recommend the Basic Tier at a minimum).
[Learn more](https://docs.microsoft.com/en-us/azure/search/search-sku-tier)

8.	**Create** a [Cognitive Services resource](https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-apis-create-account?tabs=multiservice%2Cwindows).

  *Note - You need to create the Cognitive Services resource in the same region as you Azure Search resource*. 

9.	**Install** [Visual Studio 2017](https://visualstudio.microsoft.com/) or later.
10. **Install** [Postman](https://www.getpostman.com/)
11. **Install** [PowerBI desktop](https://powerbi.microsoft.com/en-us/desktop/).
12. **Install** [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/)
