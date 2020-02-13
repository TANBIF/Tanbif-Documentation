# Ala-doc 

-Is a National Research Infrastructure
for Australia which has built an infrastructure and tools to enable researchers
and other users of biodiversity information to find, access, combine and
visualize data on Australian plants and animals.

-This software has progressively been used outside of ALA team and become open source software project. for more documentation here https://github.com/AtlasOfLivingAustralia/documentation 

###   Ala Architecture
##### service oriented 
    - All contect availabe to user on the Atlas webpages is available through underlying web service 
    - This services make up the public API for the Atlas that make info be availble to other partiner to.
##### Modular components
    - Ala is made up of set of micro service componets each with specific role (this help reuserbility)
##### Re-userble UI modules 
    - The user interface are based on pluggable architecture.
##### Portability 
    - All component of project can be installed using a set of maintained scripts to aid adoption 
    of components  

:: Also ALA platform is divided in differnt modules that can work together ,But can also work apart (e.g France team just installed three of them)

<img src="../asset/img/modules_overview.jpeg">

## Modules

#### A.Occurrance search
     - Is the data search engine of the portal
     - The result page shows a list with all te results diagram as well as map withis 
       georefsrenced occurance 

##### Component
##### 1.Biocache-hub
     - This is web application that provide HTML user interface 
     - This makes use of web service provided by biocache-service
       (occurance data on the diagram)
     - data are stored in Cassandra database ,the file system is called occ
##### 2.Biocache-service
     - Is  the web service tha provide service to biocache-hub and Biocache tool
##### 3.Biocache
     - Is the idexing tool created by ALA team in order to process data from SOLR 
     - AlA proect use SOLR search engine for indexing occurance data

::Finally this  Module is based on loading,sampling ,processing and indexing of occurance records

##### Tech Summary
     - Web server = Tomcat*
     - Database = Cassandra
     - Search Engine = Solr
     - Search Tool = Biocache
     - Web application = Biocache-hub
     - Web service = Biocache-service
     - Language = ?*
     - Framework = ?*


#### B.Collectory
     - Is the module tha manages the infomation about institution, collection,
       data resorces ,contact nad etc...
     - All data are stored in MySQL database named collectory
     - This module is divided into two part private and public pages
##### Public pages 
     - You will find all public page of institution or collections 
     - But also a search engine with map focus on collection

##### Privte pages
     - This is the admistration part .You will be able to add ,modify or delete 
       institution ,collection, data resorces  or contact
     - Also you will be able to see report on your portal
     - Also this aprication can be hosted in an independent server
     - Techinicaly this is just one web appliction and one MySQL istance 
       (this is the simplestarchtecture of the entire system)


##### Tech summary
     - Web sarver = Tomcat*
     - Database = MySQL
     - Language = Groovy
     - Framework = Grails


#### C.Species page
-This page allows the user to browse existing species that are hosted in the
data portal
-You can filter the list of species by Section, LifeForm, Species
groups and Conservation status. For each species page the user can view the
information about the Names, Classification, Records, Literature and
Sequences
-The system creates a vinculation between the occurrences and their species page, in this way in you are in one specific species page you can view the records related with that species.
##### Tech summary
	- web server = Tomcat
	- Database = cassandra, eXist-db
	- language = groovy
	- indexing tool= Solr
	- Framework = Grails
	- File systems = images and pdf
	- Offline services = Profile Harvesting
	