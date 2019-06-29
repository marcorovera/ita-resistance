ita-resistance
================
### General Info
This repository provides data, scripts and output files related to my PhD dissertation "Event based-access to historical textual collections".
#### data
- argStructs: argument structures of event-denoting lexical units, extracted from the three subcorpora and tagged with semantic types (sorted by POS: v=verbs, n=nouns, mw=multiword verbal expressions). Input for `eventExtractor.ipynb`.
- gazetteers: lists of Persons, Locations and Organizations used for entity extraction and disambiguation in Chapter 3. Input for `buildNEPatterns.py`
- resource: lexico-semantic resource describing argument structure of target event-denoting Lexical Units. Input for `eventExtractor.ipynb`
- semTypesTrain: seed words used for creating semantic type centroids in `semanticTagger.py`
#### scripts
- `buildNEPatterns.py`: takes as input the gazetteers and creates surface forms for textual lookup by combining name, surname and nickname (see Chapter 3.1). Additionally, creates dictionaries of surface forms of locations and organizations. Outputs three dictionaries, ready for textual lookup.
- `eventExtractor.ipynb`: given the sentences represented as tagged argument structures and the lexico-semantic resource, extracts and classifies events from the corpus.
- `semanticTagger.ipynb`: given a word, classifies it into one of the Semantic Types listed in `semTypesSeedWords.json`. It uses a treshold (default set to 0) for excluding "out-of-domain" words.
#### output
- events_data: output data of extracted events and semantic roles from the memoirs corpus, sorted by high/low confidence and by POS (Chapter 5).
- `memoirsEventsEntityGraph.gephi`: Gephi formatted event-entity graph describing events and entities extracted from the Memoirs corpus (Chapter 6). 
Nodes have the following attributes. 
    - *id*: the ID of the node; 
    - *text*: the portion of text corresponding to that entity in the documents; 
    - *gen_type*: it only has two possible values "EVENT" or "ENTITY"; 
    - *spec_type*: for EVENT Nodes, it corresponds to the Event Class, while for ENTITY Nodes, it corresponds to the Semantic Type of the Entity.

    Edges have the following attributes:
	- *id*: the ID of the edge;
	- *sent*: id of the sentence where the event is mentioned;
	- *role*: the Semantic Role of the Entity in the related Event.
	- *doc*: the label of the document the event mention has been extracted from.
