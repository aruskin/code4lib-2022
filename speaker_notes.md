# Wikidata vs. custom Wikibases: Community history case studies

## Introduction

### Boston Research Center
The two projects I’m going to discuss are for the [Boston Research Center](https://bostonresearchcenter.org/) (BRC), which is a digital community history and archives lab based in the Northeastern University Library. The BRC is focused on building collections and partnerships with Boston-area social justice organizations; right now, we’re working on projects based in the Boston neighborhoods of Chinatown, Roxbury, East Boston, and the South End. 

The collaboration with groups outside of the university is key here: our role is to provide technical infrastructure for local history projects, and the decisions we make are informed by the needs of our community partners.

## Wikidata: Neighborhood Public Art in Boston

### Background and goals
For some background on the project, there’s a local artist donating her archives to Northeastern, and among those materials are some spreadsheets with detailed information about works of public art around the city, since she’s been tracking this data for over a decade. We’ve been using those as a starting point to gather and preserve information about works of public art in the neighborhoods that BRC is focused on. Eventually, we’d like to use this data to create public art maps and walking tours around different neighborhoods and themes.

Right now, a lot of other individuals and organizations are tracking data about public art in Boston--the City of Boston somewhat recently released a [map of Boston murals](https://www.boston.gov/departments/arts-and-culture/boston-mural-map), various arts programs and initiatives (e.g., [Now + There](https://www.nowandthere.org/), [Nubian Square Public Art Initiative](https://blackmarketnubian.com/), [Sea Walls](https://seawalls.org/)) will publish information about their work, journalists/researchers/enthusiasts dedicated to this work (e.g., [Greg Cook](https://gregcookland.com/wonderland/category/public-art/)).

All of these groups have different agendas and focuses; no one group seems to have a complete list of the works of public art around Boston.

In discussing this project with potential partners, it didn’t seem like trying to get all of this data into one local repository was the right answer. Different groups have different local needs for how they’re using this data, and the question of who should, essentially, control this data...is tricky.

### Why Wikidata?

Using Wikidata gets around the tricky situation of centralization and ownership. We can facilitate the standardization and aggregation of data around Boston neighborhood public art in Wikidata, but we don’t ultimately own or exclusively control it. Since anyone can view and edit Wikidata, it allows us to make the data we have accessible for people to do whatever they want with and invites people to contribute their own knowledge.

On the more technical side, there are the structural capabilities of Wikidata, which let us capture more complex information than spreadsheets, while also offering more flexibility than a relational database. In particular, for works of public art, you might have statues that have moved and would thus have multiple locations with different start and end times, conflicting or uncertain information about installation date--things that you can handle pretty well in Wikidata! This also lets us take advantage of work that’s already been done in Wikidata and link to existing items to build up this connected world of knowledge about Boston neighborhood public art--so not just works and their artists, but also the art schools that people went to, the activist organizations they participated in, and more.

The visualization tools bundled with the Wikidata Query Service make it easy to get [maps](https://w.wiki/57np), [graphs](https://w.wiki/58ZE), and [charts](https://w.wiki/58ZF) right off the bat that we could show to potential partners or funders as proof of concept.

In addition, there were already some [established community practices](https://www.wikidata.org/wiki/Wikidata:WikiProject_Public_art) for modeling items of public art on Wikidata, so we could build off of that rather than starting from scratch.

### Project status

We’ve already added or modified Wikidata items for [over 200 works of art](https://www.wikidata.org/wiki/Wikidata:WikiProject_Neighborhood_Public_Art_in_Boston/List_of_works) and [over 100 artists](https://www.wikidata.org/wiki/Wikidata:WikiProject_Neighborhood_Public_Art_in_Boston/List_of_artists). Some of these were bulk uploaded from spreadsheets via OpenRefine, some of these were manual edits. We’ve created a [WikiProject page](https://www.wikidata.org/wiki/Wikidata:WikiProject_Neighborhood_Public_Art_in_Boston) to document this work; this includes our data models, example queries, and lists of research resources. We're hoping this can be a useful reference for people to participate in this project as well as anyone interested in starting similar projects. We’ve hosted two little edit-a-thons so far.

We've had a student working on building a custom map visualization using this data, which has more functionality than the built-in map visualization that comes with the Wikidata Query Service: https://dsgsites.neu.edu/brcdemo/

(Still need to do a bit more work to have this draw directly from thhe Wikidata SPARQL endpoint, rather than querying that, saving the data as a JSON file, and sending it over)

We have a number of photos of these works from the Boston Public Library that we’ve cataloged and ingested into our institutional repository (unfortunately, US copyright laws mean we can’t put most of them in Wikimedia Commons); we've included the Wikidata URI in the metadata for photos of works with corresponding Wikidata items, and we intend to add the URLs of the photos to the Wikidata items (using the non-free artwork image URL property). 

(Future development work to make better use of these relationships as well)

Set up a Wordpress site to highlight this work--custom map, additional visualizations from WDQS, gallery of photos, etc. Will hopefully curate themed exhibits/add more narrative content here.

Finally, more edit-a-thons and classroom activities around this material.

## Wikibase: Chinatown Collections Survey

### Background and goals
In the spring of 2021, the BRC met with community organizations around Boston’s Chinatown, asking about what sort of digital history projects would be useful to them. It turned out that lots of oral histories and other projects were already happening in that community and they didn’t need Northeastern’s help in facilitating those. What we could help with was creating a directory of all those projects, to serve as a launching point for neighborhood research.

### Boston Chinatown Collections Survey

So as a first step, the BRC team worked to develop a survey to find out about what sort of materials various people and organizations around Boston may have relating to Chinatown. The eventual goal is then to structure and translate the free-text responses from that survey to create a searchable and browsable multilingual directory of collections.

We reviewed the survey with our community partners, had it translated into simplified and traditional Chinese,[^6] and publicized it via blog posts on the Boston Public Library and Boston Research Center websites (maybe elsewhere too--reaching out to individuals and orgs?). The initial responses were gathered into a spreadsheet. We then reinvited non-respondents to take the survey, updated our community partners on what we'd received so far, and republicized the survey via the community partners.

You can see screenshots of the English-language survey here; note that it's all free-text entry. Some respondents, such as the representative for the Chinese Historical Society of New England (CHSNE), mentioned multiple collections in their responses. 

### Data models and controlled vocabularies

The next step was to figure out the key entities, fields, and relationships we want to capture and present, based on the results of the Chinatown Collections Survey and our understanding of potential user needs. For this initial version, we decided that the collections and the organizations and people linked to them were the most important entities to represent.

Collections are defined pretty broadly here--many of these are archival collections held at universities, but we are also including Wordpress blogs, art installations, personal collections, etc. Archival "collections" may be entire fonds, series, or files with specific relevance to Boston's Chinatown, as well as fonds, series, or files that happen to include materials related to Boston's Chinatown. So we wanted the collections data model to be general enough to cover all of those, but still be in line with how, for example, archival collections are described elsewhere. 

For organizations and people, there are already so many existing models and ontologies to draw from that there's really no need to reinvent the wheel. Some things we're mindful of, however:
- For community organizations that might not have a huge online presence, it probably is our role to become a reliable source of information and to preserve the history of the organization. 
- Not all of the people linked to collections (e.g., as donors or maintainers) are public figures, so we need to be careful about how much information about them we gather and store 

Part of this process also involved identifying any controlled vocabularies that we would need to select from existing sources or develop ourselves. And this was all iterative; we started modeling with the intention of modifying/refining our models as user needs become clearer and we assess difficulty of coding responses. In coming up with our data models and controlled vocabularies, we also looked at similar projects, such as [COURAGE](http://cultural-opposition.eu/), which is a database of collections in Europe dealing with cultural opposition in the former socialist countries, and consulted with Northeastern's archivists (asking if data models seem reasonable based on their expertise).

### Coding survey responses

BRC staff parsed and coded the initial survey responses according to these data models, following up with respondents to get additional information about their collections where necessary. 

We used an Airtable base for this process. This serves as a staging area before the data can be uploaded into the final database.

Once the coding process was completed in English, we hired a translator to translate the relevant text into simplified Chinese.

### Choosing to use Wikibase

#### Database needs

This is not very much data, but there are a few specific needs that mean we probably want to go beyond spreadsheets in handling it.

The ultimate interface will need to be multilingual, so that means we want to be able to store field names and values in English and Chinese in the database.

We’re also trying to represent multiple types of entities and the different types of relationships between them--at the moment, collections, people, and organizations, although in the future we might also want to add in things like events and topics. 

In addition, it would be nice to have something lightweight and easy to implement (again, this is not Big Data), a user friendly editing interface that we don’t have to build ourselves, and enough flexibility in the schema (or no schema) to expand the project scope down the line and deal with idiosyncratic entities. That last point is key: we’re defining “collection” really broadly here, so we’re not just capturing information about formal archival collections but also art installations, blogs, personal collections…

#### Why Wikibase?
Wikibase--and by extension Wikidata--fits a lot of those needs; in particular, the way that multilingual labels, descriptions, and aliases are handled for both Items and Properties is one of the major reasons we’re going with it. 

But there are reasons why a custom Wikibase is a better fit than Wikidata for this particular project.

Not all of the items we’re creating would be appropriate for inclusion in Wikidata, whether that’s because they don’t meet [Wikidata’s notability guidelines](https://www.wikidata.org/wiki/Wikidata:Notability) or because we want to protect people’s privacy.[^4] Using Wikibase gives us more control over modeling practices; we don’t have to inherit Wikidata modeling efforts that may not make sense in this localized context, and we can create properties specific to our usage that may not make sense in Wikidata. The custom Wikibase gives us more control over editing access and visibility, so we don’t have to be as concerned about vandalism.

And while this is maybe not the best reason to adopt a technology–there has been some discussion/interest in using Wikibase more broadly in the library, and this seemed like a good pilot project.

### Installing instance of Wikibase suite

We have the full Wikibase suite deployed in an EC2 instance on AWS with Docker. Getting this set up wasn't totally starightforward; there were a lot of kinks to work out and not much documentation to work from, in terms of diagnosing and resolving issues with the Wikibase installation (also, so many moving parts--difficult to source and isolate issues).

Contact [Rob Chavez](https://library.northeastern.edu/about/library-staff-directory/robert-chavez), the Senior Digital Scholarship Group Developer, for more details about this process.

Still have more customization to do here--e.g., adding logo, making sure statements appear in a particular order on item pages, setting the formatURI property so identifiers show up as URIs, etc.

### Loading data into Wikibase

Once we had the Wikibase suite installed, we started loading in the properties and items required for the data models. So not any of the collections, organizations, and people just yet, but the properties representing the fields in the data models and items for terms in controlled vocabularies. As much as possible, we tried to find corresponding items and properties in Wikidata for the items and properties used in our data models (and this was part of the consideration in the initial design of the data models). We wrote a Python script to copy labels, descriptions, and aliases for entities from Wikidata to our Wikibase (makes use of the Wikimedia API--need bot credentials for the target Wikibase, but not the source) and to store the original Wikidata PID/QID associated with the entity in a "corresponding Wikidata property" or "corresponding Wikidata item" statement. (Since we also wanted to use some custom properties, it didn't make sense to use federated properties here, based on our understanding of how that's currently implemented).

We also had a script to bulk create items and properties from a CSV file with monolingual labels and descriptions. (We couldn't initially get QuickStatements working, which was part of the reason for doing this via custom Python scripts.)

The remaining editing work was mostly manual--adding statements to items, copying in the Chinese text we got back from the translator. This was such a small amount of data that it seemed easier to add it in this way than to figure out QuickStatements/write more scripts, but a larger project should probably use a more systematic approach.

### Building front-end

Finally, we developed a website that pulls in data from the Wikibase, in order to present it in a more user-friendly manner and allow users to navigate the data without having to write SPARQL queries.

The web interface for the project currently uses Snowman, a static site generator for SPARQL backends. This was plan B, after our initial development plan fell through, so we haven't explored the potential functionality there super thoroughly just yet. But what we have now allows the user to:

- See the full lists of collections, organizations, and people in the Wikibase
- View an individual entity and the information we have about it, organized more logically than it would be in the Wikibase user interface
- Browse collections organized by various categories (maintainers, subject terms, material types)
- (Read contextual narrative text for all of that)
- (Switch between English and simplified Chinese for all of that)

Which is basically what we were trying to do--ideally, we'd have an interface for searching over all of the entities with faceted browsing, but this is still probably a more useful interface for our intended users than the barebones Wikibase UI.

### Future work

- Develop Wordpress plug-in to interact with Wikibase, replace Snowman site
- Add support for traditional Chinese
- Add more types of entities (e.g., events)

## Takeaways
There are a lot of finer distinctions here, but I think these are the main takeaways on choosing Wikidata vs Wikibase, certainly for how we’ve gone about our projects.

When you work on a project in Wikidata, you become part of this larger community or ecosystem. The edits you make can impact (for better or worse) all of these services that pull information from Wikidata. People might come in and (for better or worse) edit items you’ve created.[^7] There’s all of this existing work–the 97 million items, the various community efforts at coming up with standards for different domains–that you can build off of and add to. 

Which isn’t to say that custom Wikibases can’t also be community-oriented–you can open your Wikibase up to allow anyone to edit, but you don’t have to.

Essentially, a custom Wikibase gives you more control over various aspects of the project, which can be a double-edged sword.

- You’re responsible for installing, setting up, and maintaining the Wikibase instance. [Wikibase Cloud](https://addshore.com/2022/01/pre-launch-announcement-of-wikibase-cloud-wikidatacon/) will probably make this easier in the future, but so far, every presentation I’ve heard about custom Wikibases has mentioned what a pain they were to set up, and our experience was no different.
- You’re responsible for deciding how you want to populate the Wikibase instance. You can create whatever properties you want, without going through the proposal process you’d have to go through on Wikidata, and enforce how they’re used.
- You can control who edits your Wikibase. If you’re worried about vandalism or just about unexpected changes to the data that might affect how it’s being used in other applications, that’s easier to mitigate with a custom Wikibase. 
- You can control who views your Wikibase, and thus what sort of external applications might access the data stored there.

---

[^4]: For example, we may want to keep track of the contact information for the archivists who responded to the survey, so that we can ask them for more details about their collections down the line, but they are not public figures and may not want to have associated Wikidata items.

[^5]: For example, the [Wikibase Data Model Primer](https://www.mediawiki.org/wiki/Wikibase/DataModel/Primer) on MediaWiki

[^6]: See: [Chinatown Collections Survey post on the BRC blog](https://bostonresearchcenter.org/bringing-history-together-the-chinatown-collections-survey-project/) and/or the [Chinatown Collections Survey post on the BPL blog](https://www.bpl.org/blogs/post/bringing-history-together-a-chinatown-collections-survey-project/)

[^7]: Somewhat related, and an interesting read: 

    Charles Chuankai Zhang, Mo Houtti, C. Estelle Smith, Ruoyan Kong, and Loren Terveen. 2022. Working for the Invisible Machines or Pumping Information into an Empty Void? An Exploration of Wikidata Contributors’ Motivations. _Proc. ACM Hum.-Comput. Interact._ 6, CSCW1, Article 135 (April 2022), 21 pages. https://doi.org/10.1145/3512982
