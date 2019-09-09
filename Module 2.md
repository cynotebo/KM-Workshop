# Introduction to Azure Functions and Custom Skills
Objective: Introduction to custom skills and to the concept of Power Skills.

In this module we will extend the data that was indexed in the previous module.  The goal of this will be to extract all diseases found in the content and store them as entities in a separate field attached to the document.  By doing this, it will allow us to leverage capabilities such as:

1) Leverage facets to show the diseases and their counts that are mentioned in the corpus of search results
2) Filter documents that refer to a specific disease

To do this, we will leverage a custom built Azure Functions that will be called by Cognitive Search with the text from the underlying document.  The function will process this text and respond with the entities found in that text.  These entities will then be stored in a separate Azure Search Collection field.

## Creating the Azure Function

The Azure Function will use a "dictionary" based technique to search the underlying text and respond with any terms or phrases that match what is stored in the dictionary.  With advances in ML and AI, there are much more advanced methods for doing this "named entity extraction", however in many cases this method often works quite well and is very simply to implement.  

To get started, we will clone the github repository: 
