# Wikidata vs. custom Wikibases: Community history case studies

## Introduction

### What is Wikidata? What is Wikibase?

For those who aren’t familiar, [Wikidata](https://www.wikidata.org/wiki/Wikidata:Main_Page) is a free, collaborative knowledge base under the Wikimedia umbrella. It currently (as of 2022-04-26) has over 97 million items, representing both concrete real-world entities and abstract concepts. Anyone can view or edit this data.[^1]

[Wikibase](https://wikiba.se/) is the underlying software suite; it was originally written for Wikidata, and Wikidata is probably the most famous and widely used instance of Wikibase.[^2] But you can also set up your own Wikibase and populate it however you want.[^3] So when I refer to Wikibase in this talk, I’ll mostly be using that as shorthand for custom, non-Wikidata instances of Wikibase.

### Wikibase data model
We don’t really have time to get deep into the Wikibase data model in this presentation; there are other great resources out there, if you’re interested.[^5]

To give you a sense of what data looks like in Wikibase, here is [the Wikidata item](https://www.wikidata.org/wiki/Q85783364) representing the Make Way for Duckings sculpture in Boston Common. You can see that it has a unique identifier (the Q number at the top), multilingual labels, descriptions, and aliases, and a bunch of statements representing facts about the sculpture. Those statements are made up of Properties (e.g., [instance of](https://www.wikidata.org/wiki/Property:P31), [image](https://www.wikidata.org/wiki/Property:P18), [inception](https://www.wikidata.org/wiki/Property:P571)) that would be defined similarly--that is, via multilingual labels, descriptions, and aliases and statements--and values that can take on [different types](https://www.wikidata.org/wiki/Help:Data_type) (e.g., other items, points in time, files on Wikimedia Commons).


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

Looking ahead, we’re going to be working on custom visualizations using this data. We also have a number of photos of these works from the Boston Public Library that we’re going to ingest into our institutional repository, and we want to connect those to the relevant items somehow (unfortunately, US copyright laws mean we can’t put most of them in Wikimedia Commons). And finally, more edit-a-thons and classroom activities around this material.

## Wikibase: Chinatown Collections Survey

### Background and goals
The BRC initially met with community organizations around Boston’s Chinatown, asking about what sort of digital history projects would be useful to them. It turned out that lots of oral histories and other projects were already happening in that community and they didn’t need Northeastern’s help in facilitating those. What we could help with was creating a directory of all those projects. 

So, in collaboration with the Boston Public Library, we sent out a survey (with versions in English and simplified and traditional Chinese) to people and organizations around Boston asking them to tell us about any materials they have related to Boston’s Chinatown.[^6]

The eventual goal is then to structure and translate the free-text responses from that survey more to create a searchable and browsable multilingual directory of collections.

### Database needs
This is not very much data, but there are a few specific needs that mean we probably want to go beyond spreadsheets in handling it.

The ultimate interface will need to be multilingual, so that means we want to be able to store field names and values in English and Chinese in the database.

We’re also trying to represent multiple types of entities and the different types of relationships between them--at the moment, collections, people, and organizations, although in the future we might also want to add in things like events and topics. 

In addition, it would be nice to have something lightweight and easy to implement (again, this is not Big Data), a user friendly editing interface that we don’t have to build ourselves, and enough flexibility in the schema (or no schema) to expand the project scope down the line and deal with idiosyncratic entities. That last point is key: we’re defining “collection” really broadly here, so we’re not just capturing information about formal archival collections but also art installations, blogs, personal collections…

### Why Wikibase?
Wikibase--and by extension Wikidata--fits a lot of those needs; in particular, the way that multilingual labels, descriptions, and aliases are handled for both Items and Properties is one of the major reasons we’re going with it. 

But there are reasons why a custom Wikibase is a better fit than Wikidata for this particular project.

Not all of the items we’re creating would be appropriate for inclusion in Wikidata, whether that’s because they don’t meet [Wikidata’s notability guidelines](https://www.wikidata.org/wiki/Wikidata:Notability) or because we want to protect people’s privacy.[^4] Using Wikibase gives us more control over modeling practices; we don’t have to inherit Wikidata modeling efforts that may not make sense in this localized context, and we can create properties specific to our usage that may not make sense in Wikidata. The custom Wikibase gives us more control over editing access and visibility, so we don’t have to be as concerned about vandalism.

And while this is maybe not the best reason to adopt a technology–there has been some discussion/interest in using Wikibase more broadly in the library, and this seemed like a good pilot project.

### Project status
Right now, we’re still processing and following up on survey responses. We do have an instance of the Wikibase Suite deployed on AWS. We’ve started populating it--this has meant copying over labels, descriptions, and aliases of a handful of items and properties from Wikidata, so that we can reuse the sort of language work done there, as well as creating new items and properties for local use.

Once we’ve finished processing the survey responses, we can finish populating the Wikibase and get someone in to translate the content. And then the major work of building an interface to display all this information in a more user-friendly way and set up better searching and browsing capabilities.

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

[^1]: See also: the [Wikidata Introduction page](https://www.wikidata.org/wiki/Wikidata:Introduction) on Wikidata

[^2]: See also: the [Wikibase FAQ](https://www.mediawiki.org/wiki/Wikibase/FAQ) on MediaWiki

[^3]: Some cool examples of custom Wikibases in the wild: [Enslaved.org](https://lod.enslaved.org/wiki/Meta:Main_Page), [Rhizome Artbase](https://artbase.rhizome.org/wiki/Main_Page), [Semantic Lab at Pratt](http://base.semlab.io/wiki/Main_Page)

[^4]: For example, we may want to keep track of the contact information for the archivists who responded to the survey, so that we can ask them for more details about their collections down the line, but they are not public figures and may not want to have associated Wikidata items.

[^5]: For example, the [Wikibase Data Model Primer](https://www.mediawiki.org/wiki/Wikibase/DataModel/Primer) on MediaWiki

[^6]: See: [Chinatown Collections Survey post on the BRC blog](https://bostonresearchcenter.org/bringing-history-together-the-chinatown-collections-survey-project/) and/or the [Chinatown Collections Survey post on the BPL blog](https://www.bpl.org/blogs/post/bringing-history-together-a-chinatown-collections-survey-project/)

[^7]: Somewhat related, and an interesting read: 
 > Charles Chuankai Zhang, Mo Houtti, C. Estelle Smith, Ruoyan Kong, and Loren Terveen. 2022. Working for the Invisible Machines or Pumping Information into an Empty Void? An Exploration of Wikidata Contributors’ Motivations. _Proc. ACM Hum.-Comput. Interact._ 6, CSCW1, Article 135 (April 2022), 21 pages. https://doi.org/10.1145/3512982