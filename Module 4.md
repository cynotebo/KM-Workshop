# Visualizing the Results with a Demo FrontEnd
Objective: Get familiar with the solution accelerator (aka.ms/kmsolutions), and create a front-end to visualize the search results.

1. git clone https://github.com/Azure-Samples/azure-search-knowledge-mining.git
2. Open CognitiveSearch.UI.csproj in VS2019 
2. Update appsettings.json

  "SearchServiceName": "kmworkshop",
  "SearchApiKey": "B8365AC95521089B7E3FA4CC98435F32",
  "SearchIndexName": "clinical-trials-small",
  "InstrumentationKey": "",
  "StorageAccountName": "kmworkshop",
  "StorageAccountKey": "mpTDjv3gC6RXN05tv9INonG1Dnzlsja0eLQOjew5R0kx7UFr3wg3W3R4lk4LZH72ZywNpEigXPTujRXg8RJb7A==",
  "StorageContainerAddress": "https://kmworkshop.blob.core.windows.net/clinical-trials-small",
  "KeyField": "metadata_storage_path",
  "IsPathBase64Encoded": true,
  "GraphFacet": "diseases"

3. Set Startup Project:
 
4. Run
5. Should get this:
 

Note the 
