## Semantic Natural Language Understanding with Spark Streaming, UIMA, and Machine-learned Ontologies, David Talby CTO at Atigeo ##

[Notebook link](github.com/atigeo/nlp_demo)

Semantic Search

* Dictionary based attribute extracted
* Machine Learning attribute extraction
* Lots of work on grammar - gets specific to domain
* NLTK text does not reflect doctor recommendations well - usually lacks grammar
* For eg: Patient denies alcohol abuse - doctor implies there may be alcohol abuse - but the sentence does not imply speculation
* For eg: Allergies: Penicillin, Dust, Sneezing - hard for even humans to make sense.

Unstructured Information Management Architecture(UIMA)

* Used to extract annotations over text.

Machine Learned Annnotators

* Sometimes its easier to code an annotations business logic
* Other times its easier to learn from examples.
* Build annotations pipeline + logic for annotations generation
* Build ontologies and dictionaries
* UMLS - Unified Medical Language System used for Medical/Biological NLP applications. Has 2.7 millions terms but the term AIDS is not there(has terms like HIV instead). 
* Word2Vec
* UMLS - ontology - Spark MLLIB - MIMIC

3 things you need to know NLP for 

* Almost never  assume you can use the text as is.
* Start with annotations pipeline.
* Use both static and ML based annotators as it is domain specific.
* How to build the ontology(eg: word2vec)
* Turns into a supervised classification problem.


