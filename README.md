## DBpedia History?

(Sean) This is where we talk about what DBpedia is woo

## DBpedia Introduction (peiyuan)

DBpedia is a crowd-sourced community effort to extract structured content from the information created in various Wikimedia projects. This structured information resembles an open knowledge graph (OKG) which is available for everyone on the Web. A knowledge graph is a special kind of database which stores knowledge in a machine-readable form and provides a means for information to be collected, organised, shared, searched and utilised. Google uses a similar approach to create those knowledge cards during search. We hope that this work will make it easier for the huge amount of information in Wikimedia projects to be used in some new interesting ways. 

DBpedia data is served as Linked Data, which is revolutionizing the way applications interact with the Web. One can navigate this Web of facts with standard Web browsers, automated crawlers or pose complex queries with SQL-like query languages (e.g. SPARQL). Have you thought of asking the Web about all cities with low criminality, warm weather and open jobs? That's the kind of query we are talking about.


## Okay... So what is SPARQL?

(Hao and Brian) This is where we talk about SPARQL and how to use that, with sample queries set up like this (I (Dylan) wrote this one feel free to use it)

This is a query that finds all songs by Green Day paired with the albums they are found on.
```markdown
PREFIX : <http://dbpedia.org/resource/>
PREFIX dbpedia2: <http://dbpedia.org/property/>
PREFIX albums: <http://dbpedia.org/resource/Category:Green_Day_albums>
SELECT ?album ?title WHERE {
    ?album ?property albums: .
    ?album dbpedia2:title ?title .
    ?title dbo:musicalArtist :Green_Day
} ORDER BY ?term
```

## Okay then... How do I put it into my project?

"SPARQLWrapper" (information can be found [here](https://rdflib.github.io/sparqlwrapper/) ) is one convenient resource for integrating SPARQL queries into your project. Simply install the SPARQLWrapper package with 
```markdown
pip install SPARQLWrapper
```
and you are on your way! This package allows you to make SPARQL queries (and thus query DBpedia) from Python without any further hassle! An example is shown below, using an example query from earlier:
```markdown
from SPARQLWrapper import SPARQLWrapper, JSON

sparql = SPARQLWrapper("http://dbpedia.org/sparql")
sparql.setQuery("""
PREFIX dbpedia2: <http://dbpedia.org/property/>
PREFIX : <http://dbpedia.org/resource/>
PREFIX albums: <http://dbpedia.org/resource/Category:Green_Day_albums>
SELECT ?album ?title WHERE {
    ?album ?property albums: .
    ?album dbpedia2:title ?title .
    ?title dbo:musicalArtist :Green_Day
} ORDER BY ?term
""")
sparql.setReturnFormat(JSON)
results = sparql.query().convert()

for result in results["results"]["bindings"]:
    print("%s %s" % (result["album"]["value"], result["title"]["value"]))
```
If you are copying this example, you will have to change the "album" or "title" to whatever your variables are in your query.
When code this is run, you will get an output with each line containing the album and title of the result, like
```markdown
http://dbpedia.org/resource/Warning_(Green_Day_album) http://dbpedia.org/resource/Warning_(Green_Day_song)
http://dbpedia.org/resource/21st_Century_Breakdown http://dbpedia.org/resource/East_Jesus_Nowhere
http://dbpedia.org/resource/Awesome_as_Fuck http://dbpedia.org/resource/East_Jesus_Nowhere
...
```
These results are returned as links, which are resources in dbpedia, referring to the objects / properties.

This is just one way to integrate these queries into your project, but hopefully it's a good foothold to get started!

## Thank you for visiting our tutorial!

## Questions for you guys
Why DBPedia is a revoluntionized technology?
How does DBPedia reflect decentralization?

## Reference
https://web.archive.org/web/20100202094110/http://www.wiwiss.fu-berlin.de/en/institute/pwo/bizer/research/publications/Bizer-etal-DBpedia-CrystallizationPoint-JWS-Preprint.pdf

# Kept for reference for styles and techniques for if y'all are new to this like me

