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


# Sections to add

- Reading a paper with Wikidata Bib
- Adding an article to Wikidata
- Tagging and retrieving content. 
- Adding a new list via ./wadd and SPARQL queries
- Adding multiple new lists via wadd_all



# Repository structure
- docs
- src
- notes
    - Q1123.md
    - Q2234.md
- toread.md
- read.ttl
- read.csv
- config.yaml
- pop
- wadd
- wlog
- wread

### Scaffolding files

- toread.md

A markdown stack/list of titles of papers.

The papers can be organized by sections, with section headers corresponding to the names in the `config.yaml` file.
Articles are stored as Wikidata identifiers, to automatically pull the information when actually reading. 

You can, of course, store just the name of the article or other information and later locate and update the file with the Wikidata QID. 

- config.yaml

A configuration file mapping shortcuts to use in the command line to categories in the `toread.md`. These shortcuts are used when invoking the scripts from the command line.

- read.ttl

An RDF file linking the wikidata URIs for the articles you are reading to your notes. 
Each note file will have an URI. For now I`ll use the property wb:has_notes, where wb is this repository URL

- read.csv 

A csv file linking article titles/human readable info to Wikidata ids.

- notes
A folder containing markdown notes for each article. Each article get its on file, named by Wikidata ID. 
If the material does not fit on Wikidata, just add it as a new header to other.md.

- docs
  
The html content for GitHub Pages, providing analytics on what has been read. 

### Scripts for use

- wadd

Adds a set of new articles to one of the lists in toread.md using Wikidata. 
Example for single-cell transcriptomics articles in either Nature or Science: https://w.wiki/3LhF
`$ ./wadd https://w.wiki/3MDs -p --new`

- wlog
Adds a commit to git for the articler read and pushes it to GitHub.
`$ ./wlog`

- wread
Read an article that is not on the list in toread.md. 

`$ ./wread Q107542983`

- pop

Pops the first QID in one of the lists in the toread.md file. The command is followed by a shortcut, specifying which list to look for (this is set up in the config.yaml file). 

For example, `$ ./pop ct` will remove the first QID from the "Cell Types" list and open the article for note-taking.

## Notes structure

# The title of the work
    The citation in [Manubot](https://manubot.org/) syntax

## A header saying "Highlights"

Copy-and-pasted highlights from the text. No copy-right claim can be made on this session, and all copy-paste content must fall under fair use guidelines for proprietary content. Basically, that means you should not use the copy-pasted content for anything else other than personal notes.

--> Any comments made by you should be preceeded by an arrow. And
    if they take another line, it is enough that they are indented.

And then you can continue highlighting.

## A header saying "Comments"

Any general comments that did not fit inlinely. 
