Named Entity rEcognition and Linking (NEEL) dataset for Italian tweets
======================================================================

One of the main limitations to the development of specific algorithms for tweet-based entity linking in Italian lies on the dearth of datasets for training and assessing the quality of such techniques.

Hence, we built a new dataset by following the guidelines proposed in the \#Microposts2015 Named Entity Linking (NEEL) challenge: http://ceur-ws.org/Vol-1395/microposts2015_neel-challenge-report/.

We randomly selected 1,000 tweets from the TWITA dataset, the first corpus of Italian tweets. For each tweet, we first select the named entities (NE).
A NE is a string in the tweet representing a proper noun, excluding the preceding article (like *il*, *lo*, *la*, etc.) and any other prefix (e.g. *Dott.*, *Prof.*) or post-posed modifier.
More specifically, an entity is any proper noun that: 1) belongs to one of the categories specified in a taxonomy and/or 2) can be linked to a DBpedia concept.
This means that some concepts have a NIL DBpedia reference; these concepts belong to one of the categories but they have no corresponding concept in DBpedia. The taxonomy is defined by the following categories: Thing, Event, Character, Location, Organization, Person and Product.

We annotated concepts by using the canonicalized dataset of Italian DBpedia 2014. For specific Italian concepts that are not linked to an English article, we adopt the localized version of DBpedia.
Finally, some concepts have an Italian Wikipedia article but they are not in DBpedia; in that case we linked the entity by using the Wikipedia URL.
Entities represented neither in DBpedia nor Wikipedia are linked to NIL.

This first version of the dataset was annotated by only one annotator, and comprises 756 entity mentions, with a mean of about 0.75 entities for each tweet. The distribution of entities in categories is as follows: *301 Persons*, *197 Organizations*, *124 Locations*, *96 Products*, *18 Things*, *11 Events* and *9 Characters*.
63% of tweets links to a DBpedia concept, about 30% of them is annotated as NIL, 6% links to an URL of a Wikipedia page, while only one entity links to an Italian DBpedia concept.



The dataset is composed of three files:

1.  **it_neel_v1_25062015.id** contains the id of each annotated tweet. Following the Twitter API, guidelines we cannot release the tweet's content, but only the id.
2.  **it_neel_v1_25062015.it.gold** contains entity annotations using Italian DBpedia URIs
3.  **it_neel_v1_25062015.gold** contains entity annotations using English DBpedia URIs


The annotation files consist of a line for each tweet id, which is followed by the start and the end offset (starting from 0) of the annotation, the linked concept and the category.
All values are separated by the TAB character. For example, for the tweet:
>290460612549545984 @CarlottaFerlito io non ho la forza di alzarmi e prendere il libro! Help me

we have the annotation:

>290460612549545984 1 16  http://dbpedia.org/resource/Carlotta_Ferlito	Person

If you use this dataset, please cite our paper:

*Pierpaolo Basile, Annalina Caputo and Giovanni Semeraro* Entity Linking for Italian Tweets. In: Second Italian Conference on Computational Linguistics CLiC-it 2015. Trento, 2015. (to appear)
