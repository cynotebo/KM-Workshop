# Advanced Search

In this module we are going to cover two advanced search topics:
* Custom Analyzers 
* Scoring Profiles

We briefly touched on custom analyzers in the previous module, however we are going to take a closer look at these and how to leverage it through search queries.  Scoring Profiles is an important topic because it allows you to have a high level of control over the search ranking process which is important to ensure the search results are well suited to the needs of your users and your business.

## Custom Analyzers

In the previous module, we created an index that contained a field called customPhonetic which leverages one of the available Token Filters called the PhoneticTokenFilter.  The token filter has the ability to take search terms provided by the user and reduce them to a value that can be compared to within the index.  Let's take an example.  Imagine we had a disease in the index called "Gaucher's Disease", but a physician who wanted to learn more about this disease tried to search for it as "Gowchers Diseases".  There is a capability within Azure Search to do fuzzy matching that would allow you to handle simple spelling mistakes, however this example is far more than a simple spelling mistake.  

There are various phoentic encoders that encode words in different ways.  The one I chose is called doubleMetaphone and this encodes both Gaucher's and Gowchers to a code of KXRS.  Since it is stored in the field as KXRS, when someone searches for either Gaucher's or Gowchers, they both get encoded to the same value and as a result you get a match.

You can validate what this encoding looks like by executing the following two requests using the Azure Search Analyze API against your search index and the phonetic analyzer "my_phonetic" that was created in the previous module.:

```
GET: https://[search service].search.windows.net/indexes/[search index]/analyze?api-version=2019-05-06
BODY:
{
  "text": "Gaucher's",
  "analyzer": "my_phonetic"
}
```
and
```
GET: https://[search service].search.windows.net/indexes/[search index]/analyze?api-version=2019-05-06
BODY:
{
  "text": "Gowchers",
  "analyzer": "my_phonetic"
}
```

Notice how both result in a token with the value: KXRS.

Try sending various different words and phrases to see how they get encoded.

There are a lot of other intersting custom analyzers and tokenizers that can be used such (Regular Expression)[https://docs.microsoft.com/en-us/azure/search/index-add-custom-analyzers#property-reference] (RegEx) that allows you to leverage patters to find distinct tokens.  

```json
{
            "token": "KXRS",
            "startOffset": 0,
            "endOffset": 8,
            "position": 0
}
```
