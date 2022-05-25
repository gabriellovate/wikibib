# Taking notes and using Wikidata Bib

WikidataBib gathers a number of different purposes:

    - Make it easy to read a long list of articles
    - Provide searchable notes/highlights
    - Capture the timeline of academic readings
    - Provide personal visualization of reading statistics
    - Insert a reading routine in the context of Wikidata
    - Record notes in a device-independent fashion

This usage tutorial explains bit by bit  different parts of the project. 

## Reading articles on-demand

The basic usage of Wikidata Bib starts by reading articles on demand. 

Explaining by example, let's consider you want to read  an article titled "Wikidata as a knowledge graph for the life sciences" ([https://elifesciences.org/articles/52614](https://elifesciences.org/articles/52614)). 
After searching for the title, or doi, on [wikidata.org](https://wikidata.org) you will get a Q-identifier for the article.
In this case it is  [Q87830400](https://www.wikidata.org/wiki/Q87830400).
In the command line, run: 

```bash
bib read Q87830400
```

The system will open a markdown notes file and (if possible) download a pdf for the document.
The notes file will contain some general info for the paper and sessions for:
    
    - copying "highlights" from the paper
    - adding comments 
    - adding "tags" to facilitate search later
    - links to Scholia, Wikidata and Author Disambiguator 

By going to Wikidata or Author Disambiguator you can improve the metadata on the articles you are interested, improving the dashboards you will use later. 

After reading the article, you can commit your changes to GitHub, so as to update the repository. 
While you can do your update manually, the short script `bib log` logs your reading to GitHub in a quick way. 

## Reading articles from a list

To really benefit from Wikidata Bib, you will want to do more than just read articles on demand.

You will want to have an ordered stack of articles to read. 

The list of article QIDs stay in the `toread.md` file, and there are two basic usage modes:

- One single list of articles to read
- Multiple lists divided by topics 

Let's started with the single list to get familiar with the system. 

### Single list

The idea is a list that you can "pop" articles out whenever you sit down to read. 

To populate the list, just add the Wikidata Q-ID of your articles of interest

The code `bib pop` will look for the first Q-ID in the `toread.md` and process it as in the on-demand reading step. 

It will also remove the Q-ID from the file, so you can advance in your reading articles.


# Future sessions

This tutorial is currently incomplete. In the near future, there should be documentation here for: 

- Reading a paper with Wikidata Bib
- Adding an article to Wikidata
- Tagging and retrieving content. 
- Adding a new list via ./wadd and SPARQL queries
- Adding multiple new lists via wadd_all



# Repository structure
- docs
- downloads
- src
  - data
  - notes
  - wiki_bib

### The `src/data` folder

The data folder contains the configuration files and the database for your readings

- toread.yaml 

A yaml file recording the Wikidata QIDs of the articles you intend to read. 

- config.yaml

A configuration file mapping shortcuts to use in the command line to categories in the `toread.md`. These shortcuts are used when invoking the scripts from the command line. 

- read.ttl

An RDF file linking the wikidata URIs for the articles you are reading to your notes. 
Each note file will have an URI. For now I`ll use the property wb:has_notes, where wb is this repository URL

- read.csv 

A csv file linking article titles/human readable info to Wikidata ids.

### The `src/notes` folder

A folder containing markdown notes for each article. Each article get its on file, named by Wikidata ID. 
If the material does not fit on Wikidata, just add it as a new header to other.md.

### The `docs` folder
  
The html content for GitHub Pages, providing analytics on what has been read. 

### Commands

To list the possible commands just run "wikibib" or "wikibib --help" from your command line. 
## Notes structure

The notes opened for every work has a structure like this: 

# The title of the work
    The citation in [Manubot](https://manubot.org/) syntax

## A header saying "Highlights"

Copy-and-pasted highlights from the text. No copy-right claim can be made on this session, and all copy-paste content must fall under fair use guidelines for proprietary content. Basically, that means you should not use the copy-pasted content for anything else other than personal notes.

You can comment using html commenting syntax:

```html
<!-- Use this for a comment -->
```
And then you can continue highlighting.

## A header saying "Comments"

Any general comments that did not fit inlinely. 
