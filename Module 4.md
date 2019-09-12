# Advanced Search

In this module we are going to cover two advanced search topics:
* Custom Analyzers 
* Scoring Profiles

We briefly touched on custom analyzers in the previous module, however we are going to take a closer look at these and how to leverage it through search queries.  Scoring Profiles is an important topic because it allows you to have a high level of control over the search ranking process which is important to ensure the search results are well suited to the needs of your users and your business.

## Custom Analyzers

In the previous module, we created an index that contained a field called customPhonetic which leverages one of the available Token Filters called the PhoneticTokenFilter.  The token filter has the ability to take search terms provided by the user and reduce them to a value that can be compared to within the index.  Let's take an example.  Imagine we had a disease in the index called "Gaucher's Disease".  
