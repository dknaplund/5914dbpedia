## What is DBpedia?

(Sean) This is where we talk about what DBpedia is woo

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




# Kept for reference for styles and techniques for if y'all are new to this like me

## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/dknaplund/5914dbpedia/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/dknaplund/5914dbpedia/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
