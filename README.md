[![CI](https://github.com/fair-data-collective/zonmw-generic-vocabulary/workflows/Sheet2RDF/badge.svg)](https://github.com/fair-data-collective/zonmw-generic-vocabulary/actions?query=workflow%3ASheet2RDF)

# [ZonMw Generic Controlled Vocabulary](http://purl.org/zonmw/generic)
Controlled vocabularies allow an accurate and controlled approach in describing physical and digital assets (e.g., data). One of such controlled vocabulary is **ZonMw Generic Controlled Vocabulary**. This controlled vocabulary is a result of series of [Metadata 4 Machine (M4M) Workshops](https://www.go-fair.org/zonmw-clusters-m4m-workshop-dates/) that run from October 2020 to July 2021 under Dutch COVID19 program, which is funded by ZonMw. 

`sheet2rdf` and `OntoStack`, developed by [FAIR Data Collective](https://dk.linkedin.com/company/fair-data-collective), are used to build and serve **ZonMw Generic Controlled Vocabulary**, while [PURL](https://archive.org/services/purl/) is used to persist identifiers for the vocabulary terms and properties:

   http://purl.org/zonmw/generic


# Tooling
## [sheet2rdf](https://github.com/fair-data-collective/sheet2rdf)

This repository hosts automatic workflow, executed by means of Github actions, and underlying shell and python scripts which:

- [Fetches Google Sheet](https://docs.google.com/spreadsheets/d/1g6pfXRYA-4LjRj2ZS74jcs9R5vs5dOCoBdwAQW8opcY/edit#gid=1316280843), containing the taxonomy terms and their defitions, from Google Drive and stores is as `xlsx` and `csv` files
- Converts fetched sheet to machine-actionable and FAIR RDF vocabulary using [xls2rdf](https://github.com/sparna-git/xls2rdf)
- Tests the resulting RDF vocabulary using [qSKOS](https://github.com/cmader/qSKOS/)
- Commits conversion results and tests logs to this repository
- and deploy RDF vocabulary to OntoStack to be served to humans and machines

## [OntoStack](http://vocab.fairdatacollective.org)

OntoStack is a set of orchestrated micro-services configured and interfaced such that they can intake vocabularies and resolve their terms and RDF properties upon requests either by humans or machines.

Some of OntoStack micro-services are:

- [Jena Fuseki](https://jena.apache.org/documentation/fuseki2/) a graph database
- [SKOSMOS](http://www.skosmos.org/) a web-based SKOS browser acting as a front-end for the vocabularies persisted by the graph database
- [Træfik](https://doc.traefik.io/traefik/) an edge router responsible for proper serving of URL requests

**ZonMw Generic Controlled Vocabulary** is served by FAIR Data Collective instance of `OntoStack`:
http://vocab.fairdatacollective.org/
