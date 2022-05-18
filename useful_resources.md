# Useful Wikibase Resources

## Articles/reports

- [Wikibase Report for LD4P2](https://docs.google.com/document/d/1sOPWK9Ps_dC23kIOi3y1_SiyIxaewhMaUq1J1_SQJWA/edit) (2019)
    - Includes sample of Wikibase projects with reasons for using Wikibase (over Wikidata/other databases), challenges encountered
- [Use cases for institutional Wikibase instances](https://github.com/timothy-mendenhall/wikibase-use-cases/blob/master/UseCases-2020.md) (2020)
    - Developed by university library staff at various institutions

## LibGuides
- UCLA: https://guides.library.ucla.edu/semantic-web/wikidata
- Vanderbilt: https://heardlibrary.github.io/digital-scholarship/host/wikidata/

## Tutorials

- Getting started with Wikibase
    - [Wikibase: configure, customize, and collaborate](https://stuff.coffeecode.net/2018/wikibase-workshop-swib18.html) (Dan Scott & Stacy Allison-Cassin, 2018 workshop)
    - [Wikibase for Research Infrastructure](https://medium.com/@thisismattmiller/wikibase-for-research-infrastructure-part-1-d3f640dfad34) (Matt Miller, Linked Jazz project)
- Loading in data
    - [Building A Bot to Interact with Wikidata or Wikibase](https://heardlibrary.github.io/digital-scholarship/host/wikidata/bot/)
    - [Putting Data into Wikidata using Software](http://baskauf.blogspot.com/2019/06/putting-data-into-wikidata-using.html)
- Installing on AWS
    - [2020-05-18 Wikibase Installation Demo](https://docs.google.com/document/d/1jrEX9ChM-mXXsQmiWsWSoya3Ovul7nRI2auM40n_e8I/edit)

## MediaWiki documentation
- [Wikibase Docker Installation](https://www.mediawiki.org/wiki/Wikibase/Docker)
- [Wikibase Installation - Advanced configuration](https://www.mediawiki.org/wiki/Wikibase/Installation/Advanced_configuration)
- [Wikibase API](https://www.mediawiki.org/wiki/Wikibase/API)
- [Wikibase Documentation](https://doc.wikimedia.org/Wikibase/master/php/index.html) (detailed technical documentation)
    - [Description of snaks](https://doc.wikimedia.org/Wikibase/master/php/md_docs_topics_json.html#json_snaks) (super important for implementing API calls)

## Example non-Wikidata Wikibase instances
- [Wikibase Registry](https://wikibase-registry.wmflabs.org/wiki/Main_Page) (a Wikibase of Wikibases)
- [Semantic Lab at Pratt](http://base.semlab.io/wiki/Main_Page) (houses Linked Jazz project)
    - Example item: [Apollo Theater](http://base.semlab.io/wiki/Item:Q22246)
    - Note that this has properties linking back to [same entity’s](https://www.wikidata.org/wiki/Q619124) representation on Wikidata ([Wikidata QID](http://base.semlab.io/wiki/Property:P8) and [Wikidata URI](http://base.semlab.io/wiki/Property:P9))
- [FactGrid database](https://database.factgrid.de/wiki/Main_Page)
    - Example item: [Johann Adam Weishaupt](https://database.factgrid.de/wiki/Item:Q1308)
        - Note how this is connecting to different Wikimedia projects via sitelinks  
- [Enslaved.org Wikibase](https://lod.enslaved.org/wiki/Meta:Main_Page) 

## Code
- Wikibase repository (mirror): https://github.com/wikimedia/Wikibase
- Wikibase release pipeline: https://github.com/wmde/wikibase-release-pipeline
- Pywikibot (mirror): https://github.com/wikimedia/pywikibot
    - Python library for calls to the MediaWiki API

