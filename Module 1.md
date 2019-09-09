
# Module 1: Using Azure Portal to Create Your Index - No Code Required

This module uses the Azure Portal to create your first Azure Search index wihtout writing any code.  Following these steps you will: ingest a set of files (clinical-trials), extract both structured and unstructured text from those files, and index their content.

## Using the Portal Import Data Flow:

Navigate to your search service, and click the **Import Data** button. This will launch the Import Data Wizard.

 ![](images/importdata.png)
 
1.	Create data source called: *clinical-trials-mini*.

![](images/datasource.png)
 
2. Pick **Azure Blob Storage**, and navigate to your **clinical-trials-small** container.
 Name it *clinical-trials-small*, and then click on **Choose existing connection**
 
 ![](images/chooseconnection.png)
 
3. Select the clinical-trials-small container.

![](images/selectcontainer.png)

4. Now click **Next** to add cognitive enrichments to it.

## Skillset
A skillset refers to an enrichment that you are adding to the data extraction process.  Examples of skillsets are key phrase extraction, image extraction and entity recognition.  When building and index through the Azure Portal, you have several built-in enrichments available to use.  

Follow these steps to select and add built-in skillsets to your index:

1. Attach the Cognitive Service resource you created earlier to this enrichment process. It will be used to power any of your pre-built AI models.

![](images/skillset.png)

2. Add enrichments:

    Name your skillset: *clinical-trials-small*

3. Make sure to select the **OCR enrichment** to extract merged_content field.  Now we can apply an enrichment to the merged_content field to extract the **locations** (lowercase 'l').  For consistency’s sake, let’s call the field name locations. 

## Add a Knowledge store. 
As you recall from the introductory session, the knowledge store is a new capability that we introduced into Public Preview in May.  Using the Knowledge Store enables you to use your data in scenarios that do not lend themselves naturally to search.  Once your data has been loaded into the Knowledge Store, you can do things like kick off RPA, run analytics or visualize in tools like PowerBI.

We're going to go ahead and create the Knowledge Store now through the Azure Portal and will come back to the visualizations in a later module.

*Note - Using the Document Cracking Pipeline, you can load your data into an Azure Search Index, the Knowledge Store or both.*
1. Click choose an existing connection, select your storage account and create a container called *clinical-trials-small-ks*
2. Click **Next** to customize the target index.

3.	In the index definition, rename to it to *clinical-trials-small*,
- Make sure all the field are retrievable. 
- Make sure that the locations field is retrievable / facetable / filterable / searchable
- Optional: You can make layoutText not searchable/retrievable since we won’t need it for this workshop.

 
4.	Name the indexer *clinical-trials-small* (we only need to run it once for now). **Note that the index key is encoded by default*.
 

Wait 2 or 3 minutes or so for the indexing to occur – then go check the status of your indexer on the portal.  
 
 
After having indexed clinical trials using the portal experience, let’s go query the service.
 
### Knowledge Store Data Format
Let's look at the tables we've created in the Knowledge Store:

We see two tables, one for the documents and another one for each of the entities identified in those documents 
 
This data could be useful for analytics, to train an ML model, or simply to maintain a cache of any extractions we produced. In Module 3 we will create a visualization using data from the Knowledge Store.
