## Problem 0: Setup your Pig Cluster

1. Follow these [instructions](https://class.coursera.org/datasci-002/wiki/view?page=awssetup) to setup the cluster and . NOTE: It will take you a good 60 minutes to go through all these instructions without even trying to run example.pig at the end. But they are worth it. You are learning how to use the Amazon cloud, which is by far the most popular cloud today! At the end, the instructions will refer to example.pig. This is the name of the sample program that we will run in the next step.

2. You will find example.pig in the [course materials repo](https://github.com/uwescience/datasci_course_materials). example.pig is a Pig Latin script that loads and parses the billion triple dataset that we will use in this assignment into triples: (subject, predicate, object). Then it groups the triples by their object attribute and sorts them in descending order based on the count of tuple in each group.

3. Follow the README.txt: it provides more information on how to run the sample program called example.pig.

4. There is nothing to turn in for Problem 0

### Useful Links

[Pig Latin reference](http://pig.apache.org/docs/r0.7.0/piglatin_ref2.html)

[Counting rows in an alias](http://stackoverflow.com/questions/9900761/pig-how-to-count-a-number-of-rows-in-alias)

### Quiz Description

As we discussed in class, we live in a "big data" era: our society is generating data at an unprecedented scale and rate. In fact, we are generating so much data that we are unable to take advantage of most of that data. This is quite unfortunate.

A large fraction of this data takes the form of gigantic graphs: A social network is a graph where vertices represent people and edges represent friendships. The Web is a graph where vertices represent pages and edges represent hyperlinks between pages. These graphs are very large and are difficult to study. One of the key challenges is that many graph algorithms are difficult to parallelize.

In this assignment, we will perform some basic analysis over one such graph. This graph is representative of other important graphs. The graph that we will study comes from the [billion triple dataset](http://km.aifb.kit.edu/projects/btc-2010/). This is an RDF dataset that contains a billion (add or take a few) triples from the Semantic Web. Some Webpages on the Web have a machine-readable description of their semantics stored as RDF triples: our dataset was obtained by a crawler that extracted all RDF triples from the Web.

RDF data is represented in triples of the form:
```
		subject  predicate  object  [context]
```
The [context] is not part of the triple, but is sometimes added to tell where the data is coming from. For example, file ```btc-2010-chunk-200``` contains the two "triples" (they are actually "quads" because they have the context too):
```
<http://www.last.fm/user/ForgottenSound> <http://xmlns.com/foaf/0.1/nick> "ForgottenSound" <http://rdf.opiumfield.com/lastfm/friends/life-exe> .
<http://dblp.l3s.de/d2r/resource/publications/journals/cg/WestermannH96> <http://xmlns.com/foaf/0.1/maker> <http://dblp.l3s.de/d2r/resource/authors/Birgit_Westermann> <http://dblp.l3s.de/d2r/data/publications/journals/cg/WestermannH96>
```
The first says that Webpage <http://www.last.fm/user/ForgottenSound> has the nickname "ForgottenSound"; the second describes the maker of another webpage. ```foaf``` stands for Friend of a Friend. Confused ? You don't need to know what they mean; some of the many triples refer to music, http://dbtune.org, others refer to company relationships, etc. For our purpose, these triples are just a large collection of triples. There were 317 2GB files in the [billion triple dataset](http://km.aifb.kit.edu/projects/btc-2010/) when we downloaded it. We uploaded them to Amazon's Web Services in S3: there were some errors, and only 251 uploaded correctly, for a total of about 550 GB of data.

This graph is similar in size to the [web graph](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.33.44&rep=rep1&type=pdf). As part of this assignment, we will compute the out-degree of each node in the graph. The out-degree of a node is the number of edges coming out of the node. This is an important property. If a graph is random, the out-degree of nodes will follow an exponential distribution (i.e., the number of nodes with degree d should be exp(- c*d) for some constant c). We will write the script in Problem 2, where we will run it on a small data sample. We will run the script on the big graph in Problem 4. What is very interesting is that we will find the distribution of node out-degrees to follow a power law (1/d^k for some constant k and it will look roughly like a straight-line on a graph with logarithmic scales on both the x and y axes) instead of an exponential distribution. If you look at Figures 2 and 3 in [this paper](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.33.44&rep=rep1&type=pdf), you will find that the degrees of web pages on the web, in general, follow a similar power law distribution. This is very interesting because it means that the Web and the semantic Web cannot be modeled as random graphs. They need a different theoretical model.

In Problem 3, we will look for paths of length 2 in a sub-graph of our big graph. This is a simple version of more complex algorithms that try to measure the diameter of a graph or try to extract other related properties. We will do all this on a very real 0.5TB graph! How cool will that look on your resume: "Analyzed properties of a 0.5TB (a billion vertices) graph using Pig/Hadoop".

You will access the following datasets in S3, throught pig (using the LOAD command -- see example.pig)

s3n://uw-cse-344-oregon.aws.amazon.com/cse344-test-file -- 250KB. This is used in example.pig. Always use this file for debugging your scripts first!

s3n://uw-cse-344-oregon.aws.amazon.com/btc-2010-chunk-000 -- 2GB. You will use this dataset in questions 1, 2, 3..

s3n://uw-cse-344-oregon.aws.amazon.com -- 0.5TB. This directory contains 251 files btc-2010-chunk-000 to btc-2010-chunk-317 (since only 251 of the original 318 files uploaded correctly). You will use this in problem 4.

It is not necessary for the assignment, but if you want to inspect the files directly, you can access them over the Internet using urls of the following form (Note that accessing the 0.5TB file in this way is not recommended!):
```
http://uw-cse-344-oregon.aws.amazon.com.s3.amazonaws.com/btc-2010-chunk-000
```
```
http://uw-cse-344-oregon.aws.amazon.com.s3.amazonaws.com/cse344-test-file
```
