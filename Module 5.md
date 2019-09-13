# Visualizing the Results with a Demo FrontEnd
Objective: Get familiar with the [Knowledge Mining solution accelerator](https://github.com/Azure-Samples/azure-search-knowledge-mining) , and use it to create a front-end to visualize the search results.

1. git clone https://github.com/Azure-Samples/azure-search-knowledge-mining.git
2. Open **CognitiveSearch.UI.csproj** in Visual Studio 
3. Update appsettings.json with the key information copied from the Azure Portal.

```
  "SearchServiceName": "kmworkshop",
  "SearchApiKey": "Your Search Service key",
  "SearchIndexName": "clinical-trials-small",
  "InstrumentationKey": "",
  "StorageAccountName": "kmworkshop",
  "StorageAccountKey": "Your Storage Account Key",
  "StorageContainerAddress": "Your Storage Container Address",
  "KeyField": "metadata_storage_path",
  "IsPathBase64Encoded": true,
  "GraphFacet": "diseases"
```

**Importan Note:** While this tutorial is optimizing for efficiency of allowing you to see results, and investigate the code, please note that entering your credentials into code is not a good practice to follow. We recommend you use a service like [Azure Key Vault](https://docs.microsoft.com/en-us/azure/key-vault/key-vault-overview) to do this.

3. Set Startup Project:
 
 ![](images/setstart.png)
 
4. Run
5. Should get this:
 
![](images/results.png)


