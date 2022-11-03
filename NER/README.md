# Named Entity Recognition

NER refers to the IE task of identifying the entities in a document. Entities are typically names of persons, locations, and organizations, and other specialized strings, such as money expressions, dates, products, names/numbers of laws or articles, and so on. NER is an important step in the pipeline of several NLP applications involving information extraction.

A simple approach to building an NER system is to maintain a large collection of person/organization/location names that are the most relevant to our company (e.g., names of all clients, cities in their addresses, etc.); this is typically referred to as a gazetteer. To check whether a given word is a named entity or not, just do a lookup in the gazetteer. If a large number of entities present in our data are covered by a gazetteer, then it’s a great way to start, especially when we don’t have an existing NER system available. There are a few questions to consider with such an approach. How does it deal with new names? How do we periodically update this database? How does it keep track of aliases, i.e., different variations of a given name (e.g., USA, United
States, etc.)?


- Rule-Based Ner : based on a compiled list of patterns based on word tokens and POS tags. For example, a pattern “NNP was born,” where “NNP” is the POS tag for a proper noun, indicates that the word that was tagged “NNP” refers to a person. Such rules can be programmed to cover as many cases as possible to build a rule-based NER system. Stanford NLP’s RegexNER  and spaCy’s EntityRuler provide functionalities to implement your own rule-based NER.

- ML model: predict the named entities in unseen text. For each word, a decision has to be made whether or not that word is an entity, and if it is, what type of the entity it is. In many ways, similar to the classification problems.


NER is traditionally modeled as sequence classification problem, where entity prediction of current word also depends on the context. For example, if the previous word was a person name, there's a probability that the current word is also a person name if it's a noun (e.g., first and last names).