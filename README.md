## What is DBpedia?

(Sean) This is where we talk about what DBpedia is woo

## Okay... So what is SPARQL?

(Hao and Brian) This is where we talk about SPARQL and how to use that, with sample queries set up like this (I (Dylan) wrote this one feel free to use it
```markdown
PREFIX owl: <http://www.w3.org/2002/07/owl#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX dc: <http://purl.org/dc/elements/1.1/>
PREFIX : <http://dbpedia.org/resource/>
PREFIX dbpedia2: <http://dbpedia.org/property/>
PREFIX dbpedia: <http://dbpedia.org/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX albums: <http://dbpedia.org/resource/Category:Green_Day_albums>
SELECT ?term ?title WHERE {
    ?term ?property albums: .
    ?term dbpedia2:title ?title .
    ?title dbo:musicalArtist :Green_Day
} ORDER BY ?term
```

## Okay then... How do I put it into my project?

(Dylan and Peiyuan) This is where we talk about how to integrate DBpedia into a project. I found the thing on a Python package to make SPARQL queries with, I'll add it later.

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
