# This content is under construction - please do not use yet

# Securing Azure Search Credentials in Web App using Azure Key Vault

This section outlines how to leverage Azure Key Vault to secure secrets such as the Azure Search API-Key in a safe location as opposed to storing the secrets in the code of the Web App.

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
