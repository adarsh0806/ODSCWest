## Natural Language Processing with Graphs and Neo4j, William Lyon Developer Relations Engineer at Neo4j ##

Agenda

* Brief intro to graph db
* Representing text as graph
* NLP tasks - mining word associations, graph based summarization and keyword extraction, content recommendation

Whats a graph?

* Data structure with connected data - nodes are entities - relationships connect them
* Relational vs Graph models - graph nodes have index free adjacency - every node has a direct pointer to every other node it is connected to - performance is not dependent on overall size of data. Relational models' join is dependent on the overall size of the data - therefore traversals are slower
* Property graph model - Nodes can have labels, name-value properties. Relationships - relate nodes by type and direction, can have name-value properties. Relationships can be treated as undirected as well.

Query Language

* Cypher - CREATE(:Person{name:"Dan"}) - [:LOVES:] -> (:Person{name:"Ann"}))
* Nodes - (), Relationships - [], Properties - {}

Neo4j

* Uses Cypher
* Property graph data model - nodes and relationships
* Native graph processing

Neo4j browser

* Workbench that ships with neo4j to visualize the results

Representing text as graph

* Most common way - word2vec
* Represent text as a Text adjacency graph
* [Article Link](http://www.lyonwj.com/2015/06/16/nlp-with-neo4j/)
* [All notebook Code](https://github.com/adarsh0806/nlp-graph-notebooks)

Paradigmatic Similarity

* Represent each word by its context
* Compute context similarity
* Words with high context similarity likely have paradigmatic assocition
* [Notebook](https://github.com/johnymontana/nlp-graph-notebooks/blob/master/paradigmatic-relations.ipynb)
* Similarity metric - Jaccard(size of intersection between two sets/size of union between two sets), Dice similarity - similarities based on sets


[Game of Thrones graph](https://github.com/johnymontana/graph-of-thrones)

TextRank

* [Code](github.com/summanlp/textrank)
* [pip install summa](http://summanlp.github.io/textrank/)
* Keyword extraction is done without training the model

Summarization

* Opinion mining
* Summarize major opinions
* [Code](kavita-ganesan.com/opinosis)
* [Notebook](https://github.com/johnymontana/nlp-graph-notebooks/blob/master/opinion_mining.ipynb)

Content Recommendation

* Content based - recommending items based on what users have liked in the past
* Collaberative filtering - similar users are interested in similar things, so recommend items based on other similar users
* [Incomplete Notebook](https://github.com/johnymontana/nlp-graph-notebooks/blob/master/Content%20Recommendation.ipynb)
* [Live Demo use case - Date night movies](datenightmovies.com)

Concept Networks

* [ConceptNet](http://conceptnet.io/)
* Microsoft Concept Graph


