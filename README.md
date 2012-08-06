Hands On Lab
============

Description
-----------

This repository contains project models for hands on lab sessions about elasticsearch.


How to use it
-------------

### Optional

First, you can download a full packaged version of Elasticsearch with:

* Elasticsearch 0.19.8 (Non modified distribution is [here](https://github.com/downloads/elasticsearch/elasticsearch/elasticsearch-0.19.8.zip) )
* elasticsearch.yml file modified to disable multicast and use handson as a cluster name
* [MOBZ Head Plugin](https://github.com/mobz/elasticsearch-head/zipball/master)
* [Bigdesk Plugin](https://github.com/lukas-vlcek/bigdesk/zipball/master)

### Download the project

     git clone https://github.com/dadoonet/hands-on.git

### Compile the project

     mvn compile

### Run tests

     mvn test

Tests should fail as you have to fill blanks!

Use cases
---------

### Test 0: just start a node

When running [NodeTest](https://github.com/elasticsearchfr/hands-on/blob/master/src/test/java/org/elasticsearchfr/handson/ex0/NodeTest.java),
you should bring to live an Elasticsearch node.

When successful, launch an external Elasticsearch node, using the optional download above and look at logs.
You should see that when running test, both nodes see each other.

You can add the following line at the end of NodeTest:

     Thread.sleep(120000);
     
And open in your browser: http://localhost:9200/_plugin/head/ to see one node, then both nodes and then only one node.
Have a look also at http://localhost:9200/_plugin/bigdesk/


### Test 1: Index/Get and Delete some documents

We index one beer in index meal, type beer: Heineken, PALE, 0.33 L, 3 EUROS.
We have defined a Javabean to handle [Beer](https://github.com/elasticsearchfr/hands-on/blob/master/src/test/java/org/elasticsearchfr/handson/beans/Beer.java) documents.

We will:
* use Jackson to generate JSon from object
* index the beer
* get back the generated ID for this document
* ask Elasticsearch to get the document back
* deserialize it from JSon to javabean Beer
* check that sent and indexed objects are equals
* remove the beer document and check that it does not exist anymore

See [IndexTest.java](https://github.com/elasticsearchfr/hands-on/blob/master/src/test/java/org/elasticsearchfr/handson/ex1/IndexTest.java).

We index 1 000 beers with the Elasticsearch bulk feature.

We will:
* index all beers
* check that there is no failure
* remove all beers

See [IndexTest.java](https://github.com/elasticsearchfr/hands-on/blob/master/src/test/java/org/elasticsearchfr/handson/ex1/IndexTest.java).

You can increase the number of beer to see how fast is it on your personal computer.


### Test 2: Searching for documents

TO BE COMPLETED