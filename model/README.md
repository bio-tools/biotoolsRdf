# Introduction

**CAUTION: biotoolsRDF is under construction; please contribute via the [tracker](https://github.com/bio-tools/biotoolsRdf/issues).  New classes and properies are yet to be formally defined.  Refer to [biotoolsSchema](http://github.com/bio-tools/biotoolsschema) and the [EDAM ontology](https://github.com/edamontology/edamontology/) upon which much of biotoolsRDF is based.**

The biotools ontology (biotoolsRDF) defines the OWL2 Web Ontology Language encoding of [biotoolsSchema](https://github.com/bio-tools/biotoolsschema); the resource description model for bioinformatics software.  This document describes the set of classes, properties and restrictions that can be used to represent and interchange information about software provided in different systems and contexts.

biotoolsRDF is fully compatible with biotoolsSchema and thus [bio.tools](https://github.com/bio-tools/biotoolsregistry/); the registry of bioinformatics software resources (https//:bio.tools) provided by [ELIXIR](https://www.elixir-europe.org/).

biotoolsRDF is an *application ontology* and re-uses other well established vocabularies wherever possible, adhering to the [MIREOT guidelines](http://precedings.nature.com/documents/3574/version/1) for concept imports.

# Namespaces
biotoolsRDF uses classes and properties from the following vocabularies:

prefix   | namespace IRI                               | definition
-------- | ------------------------------------------- | ----------
xsd      | http://www.w3.org/2000/10/XMLSchema#        | [XML Schema Namespace](https://www.w3.org/TR/2012/REC-xmlschema11-2-20120405/)
rdfs     | http://www.w3.org/2000/01/rdf-schema#       | [RDF Schema 1.1 namespace](https://www.w3.org/TR/2014/REC-rdf-schema-20140225/)
dcterms  | http://purl.org/dc/terms/                   | [DCMI terms namespace](http://dublincore.org/documents/dcmi-terms/) of Dublin Core Metadata Initiative
foaf     | http://xmlns.com/foaf/0.1/#                 | [FOAF namespace](http://xmlns.com/foaf/spec/)
edam     | http://edamontology.org#                    | [EDAM namespace](https://github.com/edamontology/edamontology)



The following vocabularies are used for housekeeping (internal aspects of biotoolsRDF not documented below):

prefix   | namespace IRI                                 | definition
-------- | --------------------------------------------- | ----------
rdf      | http://www.w3.org/1999/02/22-rdf-syntax-ns#   | [RDF namespace](https://www.w3.org/TR/rdf-schema/)
dc       | http://purl.org/dc/elements/1.1/              | [Dublin Core Metadata Element Set](http://dublincore.org/documents/dces/), Version 1.1 (original 15 elements)
owl      | http://www.w3.org/2002/07/owl#                | [OWL Web Ontology Language](https://www.w3.org/TR/owl-guide/)
doap     | http://usefulinc.com/ns/doap#                 | [DOAP vocabulary](https://github.com/ewilderj/doap/wiki)
oboInOwl | http://www.geneontology.org/formats/oboInOwl# | [oboInOwl vocabulary](https://www.bioontology.org/wiki/OboInOwl:Main_Page)
obo      | http://purl.obolibrary.org/obo/               | [OBO vocabulary](https://owlcollab.github.io/oboformat/doc/obo-syntax.html)


     
# Classes
biotoolsRDF uses the following classes:

class                        | description                     | biotoolsSchema
---------------------------- | ------------------------        | --------------
biotools:Tool                | Bioinformatics software         | ```<tool>```
biotools:ToolType            | Type of software                | ```<toolType>```
biotools:Accessibility       | Software accessibility          | ```<accessibility>```
biotools:OperatingSystem     | Supported operating system      | ```<operatingSystem>```
biotools:Language            | Programming language            | ```<language>```
biotools:License             | Software or data usage license  | ```<license>```
biotools:Maturity            | Software development stage      | ```<maturity>```
biotools:OtherId             | Software unique identifier      | ```<otherID>```
biotools:OtherIdType         | Type of software identifier     | ```<otherID><type>```
biotools:Function            | Software function / mode        | ```<function>```
biotools:IOData              | Input or output data            | ```<function><input>\|<output>```
edam:Data                    | Type of data                    | ```<function><input>\|<output><data>```
edam:Format                  | Format of data                  | ```<function><input>\|<output><format>```
edam:Operation               | Basic operation / method        | ```<function><operation>```
biotools:RelatedResource     | Link, download or documentation | ```<link>\|<download>\|<documentation>```
biotools:RelatedResourceType | Type of related resource        | *see below*
biotools:Credit              | Credit of the software          | ```<credit>```
biotools:CreditType          | Type of credit                  | *see below*
biotools:ElixirCredit        | ELIXIR credit                   | *see below*
biotools:Publication         | Publication about the software  | ```<publication>```
biotools:PublicationType     | Type of publication             | ```<publication><type>```
xsd:token                    | String (with restrictions)      | - 
xsd:anyURI                   | URI                             | - 


NB:  biotools:Tool is equivalent to the Software class (http://purl.org/dc/dcmitype/Software) from the [DCMI Type Vocabulary](http://dublincore.org/documents/dcmi-type-vocabulary/).

## Subclasses of biotools:RelatedResourceType

class                        | description           | biotoolsSchema
---------------------------- | --------------------- | --------------
biotools:LinkType            | Type of link          | ```<link><type>```
biotools:DownloadType        | Type of download      | ```<download><type>```
biotools:DocumentationType   | Type of documentation | ```<documentation><type>```


## Subclasses of biotools:CreditType

class                        | description             | biotoolsSchema
---------------------------- | ----------------------- | --------------
biotools:CreditTypeEntity    | Type of credited entity | ```<credit><typeEntity>```
biotools:CreditTypeRole      | Role of credited entity | ```<credit><typeRole>```

## Subclasses of biotools:ElixirCredit

class                        | description               | biotoolsSchema
---------------------------- | ------------------------- | --------------
biotools:ElixirNode          | ELIXIR national node      | ```<elixirNode>```
biotools:ElixirPlatform      | ELIXIR technical platform | ```<elixirPlatform>```
biotools:ElixirCommunity     | ELIXIR community          | ```<elixirCommunity>```


# Properties
biotoolsRDF uses the following properties:

property                    | note
---------------------       | --------------   
biotools:hasAccessibility   | Tool has an accessibility tag
biotools:collectionId       | Tool has assignment to some collection in bio.tools
biotools:hasCost            | Tool has a monetary cost
biotools:hasElixirCredit    | Tool has a credited ELIXIR entity
biotools:hasFunction        | Tool has a function/mode of operating
biotools:hasInput           | Tool function/mode has an input
biotools:hasOperation       | Tool function/mode performs some specific operation 
biotools:hasOtherId         | Tool has an identifier (typically in addition to bio.tools toolID)
biotools:hasOutput          | Tool function/mode has an output
biotools:hasRelatedResource | Tool has a related resource (link, download or documentation)
biotools:hasMaturity        | Tool has associated product maturity level
biotools:hasOperatingSystem | Tool has supported operating system
biotools:cmd                | Tool function/mode has pertinent command-line fragment
biotools:hasDataType        | Input or output is of a certain data type
biotools:hasDataFormat      | Input or output supported in a certain data format
dcterms:description         | Tool has a textual description
dcterms:identifier          | Misc entity has an identifier
dcterms:language            | Tool has a relevant programming languages(s)
dcterms:license             | Tool has a software or data usage license
dcterms:subject             | Tool has a relevant EDAM topic
dcterms:title               | Tool has a name
dcterms:type                | Misc entity has tags from controlled vocabulary
foaf:name                   | Credited entity has a name
foaf:mbox                   | Credited entity has an email address
foaf:page                   | Misc. entity has a URL
dcterms:hasVersion          | Misc. entity has associated version information
rdfs:comment                | Misc. entity has an associated note









# Data model

## biotools:Tool

![biotools:Tool](images/Tool.PNG)


property                        | value                     | biotoolsSchema
---------------------           | --------------            | ---------------------
dcterms:title (1)               | xsd:token                 | ```<name>```
dcterms:description             | xsd:token                 | ```<description>```
foaf:page                       | xsd:anyURI                | ```<homepage>```
dcterms:identifier              | xsd:token                 | ```<biotoolsID>```
dcterms:identifier              | xsd:token                 | ```<biotoolsCURIE>```
dcterms:hasVersion              | xsd:token                 | ```<version>```
dcterms:type                    | biotools:ToolType         | ```<toolType>```
dcterms:subject (2)             | edam:Topic                | ```<topic>```
biotools:hasOperatingSystem     | biotools:OperatingSystem  | ```<operatingSystem>```
dcterms:language                | biotools:Language         | ```<language>```
dcterms:license                 | biotools:License          | ```<license>```
biotools:collectionId           | xsd:token                 | ```<collectionID>```
biotools:hasMaturity            | biotools:Maturity         | ```<maturity>```
biotools:hasCost                | biotools:Cost             | ```<cost>```
biotools:hasAccessibility       | biotools:Accessibility    | ```<accessibility>```
biotools:hasElixirCredit        | biotools:ElixirCredit     | ```<elixirNode>\|<elixirPlatform>\|<elixirCommunity>```
biotools:hasOtherId             | biotools:OtherId          | ```<otherID>```
biotools:hasFunction            | biotools:Function         | ```<function>```
biotools:hasRelatedResource (3) | biotools:RelatedResource  | ```<link>\|<download>\|<documentation>```



(1) foaf:name also applicable
(2) foaf:topic also applicable
(3) dcterms:relation also applicable?


## biotools:OtherId

![biotools:OtherId](images/OtherId.PNG)

property                     | value                        | biotoolsSchema
---------------------------- | --------------               | ---------------------
dcterms:identifier           | xsd:token                    | ```<otherid><value>```
dcterms:type                 | biotools:OtherIdType         | ```<otherid<type>```
dcterms:hasVersion           | xsd:token                    | ```<otherid><version>```



## biotools:Function

![biotools:Function](images/Function.PNG)


property              | value           | biotoolsSchema
--------------------- | --------------- | ---------------------
biotools:hasInput     | biotools:IOData | ```<function><input>```
biotools:hasOperation | edam:Operation  | ```<function><operation>```
biotools:hasOutput    | biotools:IOData | ```<function><output>```
biotools:cmd          | xsd:token       | ```<function><cmd>```
rdfs:comment          | xsd:token       | ```<function><note>```

## biotools:IOData

property               | value       | biotoolsSchema
---------------------- | ----------- | ----------------------------------
biotools:hasDataType   | edam:Data   | ```<function><input>\|<output><Data>```
biotools:hasDataFormat | edam:Format | ```<function><input>\|<output><Format>```



## biotools:RelatedResource

![biotools:RelatedResource](images/RelatedResource.PNG)

property                     | value                        | biotoolsSchema
---------------------------- | --------------               | ---------------------
foaf:page                    | xsd:anyURI                   | ```<link>\|<download>\|<documentation><uri>```
rdfs:comment                 | xsd:token                    | ```<link>\|<download>\|<documentation><note>```
dcterms:hasVersion           | xsd:token                    | ```<link>\|<download>\|<documentation><version>```
dcterms:type                 | biotools:RelatedResourceType | ```<link>\|<download>\|<documentation><type>```



## biotools:Credit

![biotools:Credit](images/Credit.PNG)

property                     | value                        | biotoolsSchema
---------------------------- | --------------               | ---------------------
foaf:name                    | xsd:token                    | ```<credit><name>```
foaf:mbox                    | xsd:token                    | ```<credit><email>```
foaf:page                    | xsd:anyURI                   | ```<credit><url>```
dcterms:identifier           | xsd:token                    | ```<credit><orcidid>```
dcterms:identifier           | xsd:token                    | ```<credit><gridid>```
dcterms:identifier           | xsd:token                    | ```<credit><rorid>```
dcterms:identifier           | xsd:token                    | ```<credit><fundrefid>```
rdfs:comment                 | xsd:token                    | ```<credit><note>```
dcterms:type                 | biotools:CreditType          | ```<credit><typeEntity>\|<typeRole>```



## biotools:Publication

![biotools:Publication](images/Publication.PNG)

property                     | value                        | biotoolsSchema
---------------------------- | --------------               | ---------------------
dcterms:identifier           | xsd:token                    | ```<publication><doi>```
dcterms:identifier           | xsd:token                    | ```<publication><pmid>```
dcterms:identifier           | xsd:token                    | ```<publication><pmcid>```
dcterms:type                 | biotools:PublicationType     | ```<publication><type>```
dcterms:hasVersion           | xsd:token                    | ```<publication><version>```
rdfs:comment                 | xsd:token                    | ```<publication><note>```


