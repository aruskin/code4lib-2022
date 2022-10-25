# Wikidata vs. custom Wikibases: Community history case studies

## Introduction

### Boston Research Center
The project I’m going to discuss are for the [Boston Research Center](https://bostonresearchcenter.org/) (BRC), which is a digital community history and archives lab based in the Northeastern University Library and built in partnership with the Boston Public Library (BPL). The BRC is focused on building collections and partnerships with Boston-area social justice organizations; right now, we’re working on projects based in the Boston neighborhoods of Chinatown, Roxbury, East Boston, and the South End. 

The collaboration with groups outside of the university is key here: our role is to provide technical infrastructure for local history projects, and the decisions we make are informed by the needs of our community partners.

## Wikibase: Chinatown Collections Survey

### Background and goals
In the spring of 2021, the BRC met with community organizations around Boston’s Chinatown, asking about what sort of digital history projects would be useful to them. It turned out that lots of oral histories and other projects were already happening in that community and they didn’t need Northeastern’s help in facilitating those. What we could help with was creating a directory of all those projects, to serve as a launching point for neighborhood research.

### Boston Chinatown Collections Survey

So as a first step, the BRC team worked to develop a survey to find out about what sort of materials various people and organizations around Boston may have relating to Chinatown. The eventual goal is then to structure and translate the free-text responses from that survey to create a searchable and browsable multilingual directory of collections.

We reviewed the survey with our community partners, had it translated into simplified and traditional Chinese,[^6] and publicized it via blog posts on the Boston Public Library and Boston Research Center websites, as well as some more direct outreach. The initial responses were gathered into a spreadsheet. We then reinvited non-respondents to take the survey, updated our community partners on what we'd received so far, and republicized the survey via the community partners.

You can see screenshots of the English-language survey here; note that it's all open-ended questions and text input boxes. 

And in terms of what that looks like in the results: note that some respondents, such as the representative for the Schlesinger Library, mentioned multiple collections in their responses. (So number of collections > number of respondents)

### Data models and controlled vocabularies

The next step was to figure out the key entities, fields, and relationships we want to capture and present, based on the results of the Chinatown Collections Survey and our understanding of potential user needs. 

This was all iterative; we started modeling with the intention of modifying/refining our models as user needs become clearer and we assess difficulty of coding responses. In coming up with our data models and controlled vocabularies, we also looked at similar projects, such as [COURAGE](http://cultural-opposition.eu/), which is a database of collections in Europe dealing with cultural opposition in the former socialist countries, and consulted with Northeastern's archivists (asking if data models seem reasonable based on their expertise).

For this initial version, we decided that the collections and the organizations and people linked to them were the most important entities to represent.

Collections are defined pretty broadly here--many of these are archival collections held at universities, but we are also including Wordpress blogs, art installations, personal collections, etc. Archival "collections" may be entire fonds, series, or files with specific relevance to Boston's Chinatown, as well as fonds, series, or files that happen to include materials related to Boston's Chinatown. So we wanted the collections data model to be general enough to cover all of those, but still be in line with how, for example, archival collections are described elsewhere. 

For all of these types of entities, there are already so many existing models and ontologies to draw from that there's really no need to reinvent the wheel. Some things we're mindful of, however:

- For community organizations that might not have a huge online presence, it probably is our role to become a reliable source of information and to preserve the history of the organization. 
- Not all of the people linked to collections (e.g., as donors or maintainers) are public figures, so we need to be careful about how much information about them we gather and store 

Part of this process also involved identifying any controlled vocabularies that we would need to populate the fields to allow for faceted browsing in the future. We were able to reuse and/or modify existing controlled vocabularies for some fields and had to develop our own for others. For example, we looked at the various [authority lists published by the National Archives](https://www.archives.gov/research/catalog/lcdrg/authority_lists) and decided to use their terms for [general types of materials included in collections](https://www.archives.gov/research/catalog/lcdrg/authority_lists/grtlist.html) and [collection access status](https://www.archives.gov/research/catalog/lcdrg/authority_lists/accesslist.html). For collection subjects, which are very specific to this project, we had the student coding the survey responses do an initial assessment and assign tags. 

(See [Chinatown Collections Scan data models](https://docs.google.com/document/d/1XokKocOTSIFoLLm-mnaIZsnoJr6eXFXh-r2h1FiEtqw/edit?usp=sharing) for more details on data models/considerations that went into modeling process)

### Coding survey responses

BRC staff parsed and coded the initial survey responses according to these data models, following up with respondents to get additional information about their collections where necessary. 

We used an Airtable base for this process. This serves as a staging area before the data can be uploaded into the final database.

Once the coding process was completed in English, we hired a translator to translate the relevant text into simplified Chinese.

### Choosing to use Wikibase

#### Database needs

This is not very much data (~40 collections, ~20 organizations, ~15 people), but there are a few specific needs that mean we probably want to go beyond spreadsheets in handling it.

The ultimate interface will need to be multilingual, so that means we want to be able to store field names and values in English and Chinese in the database.

We’re also trying to represent multiple types of entities and the different types of relationships between them--at the moment, collections, people, and organizations, although in the future we might also want to add in things like events and topics. 

In addition, it would be nice to have something lightweight and easy to implement (again, this is not Big Data), a user friendly editing interface that we don’t have to build ourselves, and enough flexibility in the schema (or no schema) to expand the project scope down the line and deal with idiosyncratic entities. That last point is key: we’re defining “collection” really broadly here, so we’re not just capturing information about formal archival collections but also art installations, blogs, personal collections…

#### Why Wikibase?
Wikibase--and by extension Wikidata--fits a lot of those needs; in particular, the way that multilingual labels, descriptions, and aliases are handled for both Items and Properties is one of the major reasons we’re going with it. 

But there are reasons why a custom Wikibase is a better fit than Wikidata for this particular project.

Not all of the items we’re creating would be appropriate for inclusion in Wikidata, whether that’s because they don’t meet [Wikidata’s notability guidelines](https://www.wikidata.org/wiki/Wikidata:Notability) or because we want to protect people’s privacy.[^4] Using Wikibase gives us more control over modeling practices; we don’t have to inherit Wikidata modeling efforts that may not make sense in this localized context, and we can create properties specific to our usage that may not make sense in Wikidata. The custom Wikibase gives us more control over editing access and visibility, so we don’t have to be as concerned about vandalism.

And while this is maybe not the best reason to adopt a technology–there has been some discussion/interest in using Wikibase more broadly in the library, and this seemed like a good pilot project.

### Installing instance of Wikibase suite

We have the full Wikibase suite deployed in an EC2 instance on AWS with Docker. Getting this set up wasn't totally straightforward; there were a lot of kinks to work out and not much documentation to work from, in terms of diagnosing and resolving issues with the Wikibase installation (also, so many moving parts--ElasticSearch, MySQL, WDQS, etc.--difficult to source and isolate issues. Sometimes ElasticSearch stops indexing data?).

Contact [Rob Chavez](https://library.northeastern.edu/about/library-staff-directory/robert-chavez), the Senior Digital Scholarship Group Developer, for more details about this process.

Still have more customization to do here if we ever want to make it public--e.g., adding logo, making sure statements appear in a particular order on item pages, setting the formatURI property so identifiers show up as URIs, etc.

### Loading data into Wikibase

Once we had the Wikibase suite installed, we started loading in the properties and items required for the data models. So not any of the collections, organizations, and people just yet, but the properties representing the fields in the data models and items for terms in controlled vocabularies. As much as possible, we tried to find corresponding items and properties in Wikidata for the items and properties used in our data models (and this was part of the consideration in the initial design of the data models). We wrote a Python script to copy labels, descriptions, and aliases for entities from Wikidata to our Wikibase (makes use of the Wikimedia API--need bot credentials for the target Wikibase, but not the source) and to store the original Wikidata PID/QID associated with the entity in a "corresponding Wikidata property" or "corresponding Wikidata item" statement. .

We also had a script to bulk create items and properties from a CSV file with monolingual labels and descriptions. (We couldn't initially get QuickStatements working, which was part of the reason for doing this via custom Python scripts.)

(The GitHub repository with these scripts is here: [NEU-DSG/wikibase-utilities](https://github.com/NEU-DSG/wikibase-utilities))

The remaining editing work was mostly manual--adding statements to items, copying in the Chinese text we got back from the translator. This was such a small amount of data that it seemed easier to add it in this way than to figure out QuickStatements/write more scripts, but a larger project should probably use a more systematic approach.

### Building front-end

Finally, we developed a website that pulls in data from the Wikibase, in order to present it in a more user-friendly manner.

The web interface for the project currently uses [Snowman](https://github.com/glaciers-in-archives/snowman), a static site generator for SPARQL backends. This was plan B, after our initial development plan fell through, so we haven't explored the potential functionality there super thoroughly just yet. But what we have now allows the user to:

- See the full lists of collections, organizations, and people in the Wikibase
- View an individual entity and the information we have about it, organized more logically than it would be in the Wikibase user interface
- Browse collections organized by various categories (maintainers, subject terms, material types)
- (Read contextual narrative text for all of that)
- (Switch between English and simplified Chinese for all of that)

Which is basically what we were trying to do--ideally, we'd have a more traditional search and browse interface that lets the user input terms and filter results by various facets.

(The GitHub repository for the site is here: [NEU-DSG/chinatown-collections-site](https://github.com/NEU-DSG/chinatown-collections-site)) 

### Future work

- Improve the user interface (if nothing else make it a bit prettier w.r.t. colors and pictures)
- Add traditional Chinese (content needs to be translated, site restructured)
- Generate visualizations (timelines and/or maps of community organizations?)

More long-term: 
- Develop Wordpress plug-in to interact with Wikibase, replace Snowman site
- Add more types of entities (e.g., events)

---

[^4]: For example, we may want to keep track of the contact information for the archivists who responded to the survey, so that we can ask them for more details about their collections down the line, but they are not public figures and may not want to have associated Wikidata items.

[^6]: See: [Chinatown Collections Survey post on the BRC blog](https://bostonresearchcenter.org/bringing-history-together-the-chinatown-collections-survey-project/) and/or the [Chinatown Collections Survey post on the BPL blog](https://www.bpl.org/blogs/post/bringing-history-together-a-chinatown-collections-survey-project/)
