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
POST: https://[search service].search.windows.net/indexes/[search index]/analyze?api-version=2019-05-06
BODY:
{
  "text": "Gaucher's",
  "analyzer": "my_phonetic"
}
```
and
```
POST: https://[search service].search.windows.net/indexes/[search index]/analyze?api-version=2019-05-06
BODY:
{
  "text": "Gowchers",
  "analyzer": "my_phonetic"
}
```

Notice how both result in a token with the value: KXRS.

```json
{
   "token": "KXRS",
   "startOffset": 0,
   "endOffset": 8,
   "position": 0
}
```

Try sending various different words and phrases to see how they get encoded.

There are a lot of other intersting custom analyzers and tokenizers that can be used such [Regular Expression](https://docs.microsoft.com/en-us/azure/search/index-add-custom-analyzers#property-reference) (RegEx) that allows you to leverage patters to find distinct tokens.  

## Ranking using Scoring Profiles 

Azure Search uses a number of textual based factors to determine what is the most relevent document to send back, and this is prmarily based on an algorithm called TF/IDF which basically looks at the Term Frequency, or how often a term that is queried matches in the document and then uses Inverse Document Frequency to help move words that are extremely frequently found across many documents (such as is or the). 

In some cases, the ranking of results that Azure Search provided by default is not optimal for a user.  Let's take the example we used for Custom Analyzers which was to allow people who search for "Gowcher" to find a match of "Gaucher's" in the diseasesPhonetic field.  But what if there was a disease called "Gowchirs" which also got tokenized as KXRS (see above).  That means that if someone actually searches for "Gaucher's", the search engine would potentially give similar scoring to hits of "Gaucher's" or "Gowchirs" resulting in a potentially confused user.

Luckily you have a lot of control over this in Azure Search.  One of the easiest ways to handle this is to create what is called a [scoring profile](https://docs.microsoft.com/en-us/azure/search/index-add-scoring-profiles).  You can have one or more scoring profiles created for a search index and each scoring profiles has a set of weights and functions that can be used to adjust the default scoring (and resulting ordering) of the search results.  For our example, we might want to create a scoring profile that gives more weighting to the diseases field than the diseasesPhonetic field.  That way if someone searched for "Gaucher's" and there was a match in the diseases field, it would be boosted higher than that of one found in the diseasesPhonetic field.  However, if someone searched for "Gowchirs" and it was not found in the diseases field, the lower boosting from a hit in the diseasesPhonetic field would still return a result.

Let's create a scoring profile for this.  

* Open the Azure Portal and choose your Index
* Choose Scoring Profiles and choose "Add Scoring Profile"
* Name it "diseaseBoost" and choose "Add Scoring Profile" to save it

 ![](images/scoring_profile.png)
 
* In the resulting scoring profile, choose "Add Weights"
* Set diseases to get a boosting of 3
* Set diseasesPhonetic to get a boosting of 1 (which is actually not needed since the default is 1)
* Click OK
* Click Save, to save this updated scoring profiles

 ![](images/field_boosting.png)
 
Next, open the Search Explorer and we will try a few queries that with and without this scoring profile:

```
&scoringProfile=diseaseBoost
```

There are a number of other functions that can be used to adjust the scoring of search results which we will not be covering including:

- freshness should be used when you want to boost by how new or old an item is. This function can only be used with datetime fields (edm.DataTimeOffset). Notice the boostingDuration attribute is used only with the freshness function.
- magnitude should be used when you want to boost based on how high or low a numeric value is. Scenarios that call for this function include boosting by profit margin, highest price, lowest price, or a count of downloads. This function can only be used with double and integer fields.
For the magnitude function, you can reverse the range, high to low, if you want the inverse pattern (for example, to boost lower-priced items more than higher-priced items). Given a range of prices from $100 to $1, you would set boostingRangeStart at 100 and boostingRangeEnd at 1 to boost the lower-priced items.
- distance should be used when you want to boost by proximity or geographic location. This function can only be used with Edm.GeographyPoint fields.
- tag should be used when you want to boost by tags in common between documents and search queries. This function can only be used with Edm.String and Collection(Edm.String) fields.
