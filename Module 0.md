# Pre-Requisites for Knowledge Mining Workshop

Please make sure you fulfill the following pre-requisites before starting the workshop.

1.	Have your own Azure account 
2.	Be familiar [Azure Portal](https://portal.azure.com)
3.	Make sure you can create Azure resources in your subscription (including paid resources).
 + *Note, if your organizations policy prohibits you from creating resources in the subscription, you can use a [free subscription](aka.ms/freesubscription) for the purposes of this lab*.
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

9.	**Install** [Visual Studio 2019](https://visualstudio.microsoft.com/). Make sure you can create ASP.Net websites with it.
10. **Install** [Postman](https://www.getpostman.com/)
11. **Install** [PowerBI desktop](https://powerbi.microsoft.com/en-us/desktop/).
12. **Install** [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/)


