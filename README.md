# Knowledge Mining Workshop

Welcome to the Knowledge Mining workshop! This training is meant to walk you through building out your own knowledge mining solution. 

During this lab, we will be exploring a data set that is comprised of anonymzed patient notes in PDF format.  This demo data set contains over 200 records and contains complex medical terms and disease information in an unstructured format - meaning that there is no easy way to search the data set for information or records pertainins to a specific disease, like cirrhosis,  And worse yet, if (like the authors of this lab) you can't accurately spell cirrhosis, you may have no way of ever finding the information you're looking for - structured or otherwise.

This is where the power of Knowledge Mining with Azure Search comes to the rescue.  Using the skills and techniques we'll be teaching you today, you will be able to quickly and easily ingest this content, build custom skills to identify and extract specific medical terms related to disease conditions and then either search for information through a web front end - or project the data into powerful visuals  you create in PowerBI.  Along the way, we will also show you how easy and powerful it is to introduce more advanced search topics like phoentic search to your index (so that your users can find the information they are looking for regardless of their spelling skills) and boost relevancy of results.  The end result of today's workshop will be a fully searchable medical respository that will allow users to find and extract really powerful information, even if they are not trained medical professionals.



More concretely, you'll learn how to build an Azure Search Index and Knowledge Store repository through the Azure Portal. From there, we'll explore more advanced concepts in Azure Search, build custom skills to extend the solution and create a basic web page front end to visualize your search results. Finally, you will build a PowerBI dashboard on top of your Knowledge Store to demonstrate how you can use your data store for data visualization and advanced analytics. We have also included an Optional Module 7 which is a stand alone module that will walk you through indexing data from an AzureSQL datasource. We encourage you to walk through this module on your own time and review how this further extends the data available in your solution.

+ *Note: Please make sure to complete all of pre-requisites listed in Module 0 before moving on, as you will not be able to complete the excercises in this lab without them*.

## Agenda

+ Module 0 - Pre-Requisites 
+ Module 1 - Using Azure Portal to Build a Search Index and Knowledge Store
+ Module 2 - Introduction to Custom Skills and Azure Functions
+ Module 3 - Learn the Object Model and Advanced Skills
+ Module 4 - Advanced Azure Search: Analyzers and Scoring Profiles
+ Module 5 - Visualizing Your Results in a Web Page
+ Module 6 - Analyzing Your Data with PowerBI
+ Module 7 - Using Azure Search to index structured data
