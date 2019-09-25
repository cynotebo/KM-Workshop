# This content is under construction - please do not use yet
## Configure 
# Securing Secrets in Web App using Azure Key Vault

This section outlines how to leverage Azure Key Vault to secure secrets such as the Azure Search and Azure Blob API-Keys in a safe location as opposed to storing the secrets in the code of the Web App.

## Create the Key Vault
From Azure Portal, create a new “Key Vault”
![](/images/create-kv-1.png)
![](/images/create-kv-2.png)

Once the Key Vault resource has been created, choose "Secrets" from the menu.  This is where we will store the api-key of the Azure Search service.  From this page choose "Generate/Import"

![](/images/kv-create-secret.png)

Set the following values:
* Name: azure-search-api-key
* Value: [Enter your Azure Search Admin API Key]

NOTE: To get your Azure Search API Key, open your Azure Search service and choose "Keys".  You can use your Admin API key for this demo, however, it is best practice to use least priviledges, so you may want to create and use a [Query API Key](https://docs.microsoft.com/en-us/azure/search/search-security-api-keys).

![](/images/kv-set-secret.png)

Choose "Create" to add this key to the key vault.

Once again, choose "Generate/Import" to create a secret to store the Azure Blob API Key.  

Set the following values:
* Name: azure-blob-api-key
* Value: [Enter your Azure Blob API Key]

![](/images/kv-set-secret-blob.png)

Choose "Create" to add this key to the key vault and you should see two secrets as follows:

![](/images/kv-view-list.png)

## Configure Web App to use Key Vault

This section assumes you have at least completed Module 2 which created an Web App to search and visualize data from Azure Search.  In this section, we will remove the "SearchApiKey" and "StorageAccountKey" stored in the appsettings.json file and update the code to load the Azure Search API and Azure Blob API key from Key Vault when the application starts.


### Add Nuget Package

From Visual Studio, open the CognitiveSearch.UI project and from the Solution Explorer, right click on Dependancies and choose "Manage Nuget Packages".  Search for and add "Microsoft.Extenstions.Configuration.AzureKeyVault".  At the time of writing, version 3.0.0 was used.
![](/images/kv-nuget.png)

### Remove SearchApiKey

From Visual Studio, open the CognitiveSearch.UI project and open appsettings.json.

Remove the lines:
```
"SearchApiKey": ...
"StorageAccountKey": ...
```

