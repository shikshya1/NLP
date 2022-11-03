# Text Representation

Maps each word in the vocabulary(V) of the text corpus to a unique ID (integer value), then represent each sentence or document in the corpus as a V-dimensional vector.

### One-Hot encoding:

In one-hot encoding, each word w in the corpus vocabulary is given a unique integer ID w id that is between 1 and |V|, where V is the set of the corpus vocabulary. Each word is then represented by a V-dimensional binary vector of 0s and 1s.

### Bag of Words:
Represents the text under consideration as a bag (collection) of words while ignoring the order and context.

Advantages:

- Simple to understand and implement.
- With this representation, documents having the same words will have their vector representations closer to each other in Euclidean space as compared to documents with completely different words.

Disadvantages:

-The size of the vector increases with the size of the vocabulary. Thus, sparsity continues to be a problem. One way to control it is by limiting the vocabulary to n number of the most frequent words.
- It does not capture the similarity between different words that mean the same thing. Say we have three documents: “I run”, “I ran”, and “I ate”. BoW vectors of all three documents will be equally apart.
- This representation does not have any way to handle out of vocabulary words (i.e., new words that were not seen in the corpus that was used to build the vectorizer).
- As the name indicates, it is a “bag” of words—word order information is lost in this representation. 

### Bag of N-Grams:
 
Breaks text into chunks of n contiguous words (or tokens). This can help us capture some context, which earlier approaches could not do. Each chunk is called an n-gram. The corpus vocabulary, V, is then nothing but a collection of all unique n-grams across the text corpus. Then, each document in the
corpus is represented by a vector of length |V|. This vector simply contains the frequency counts of n-grams present in the document and zero for the n-grams that are not present.

Pros and Cons:

- It captures some context and word-order information in the form of n-grams.
- Thus, resulting vector space is able to capture some semantic similarity. Documents having the same n-grams will have their vectors closer to each other in Euclidean space as compared to documents with completely different n-grams.
- As n increases, dimensionality (and therefore sparsity) only increases rapidly.
- It still provides no way to address the OOV problem.

### TF-IDF:

The intuition behind TF-IDF is as follows: if a word w appears many times in a document d<sub>i</sub> but does not occur much in the rest of the documents d<sub>j</sub> in the corpus, then the word w must be of great importance to the document d i . The importance of w should increase in proportion to its frequency in d<sub>i</sub> , but at the same time, its importance should decrease in proportion to the word’s frequency in other documents d<sub>j</sub> in the corpus. Mathematically, this is captured using two quantities: TF and IDF. The two are then combined to arrive at the TF-IDF score.

Disadvantages :

• These are discrete representations- i.e: they treat language units (words, n-grams) as atomic units. This discreteness hampers the ability to capture relationship between words.
• The feature vectors are sparse and high-dimensional representations. The dimensionality increases with the size of the vocabulary, with most values being zero for any vector. This hampers learning capability. Further, high-dimensionality representation makes them computationally inefficient.
• They cannot handle OOV words.

### Word Embeddings (Word2Vec):

Word2vec ensures that the learned word representations are low dimensional  and dense (that is, most values in these vectors are non-zero). Such representations make ML tasks more tractable and efficient. Word2vec led to a lot of work (both pure and applied) in the direction of learning text representations using neural networks. These representations are also called “embeddings.” 

Given a text corpus, the aim is to learn embeddings for every word in the corpus such that the word vector in the embedding space best captures the meaning of the word. To “derive” the meaning of the word, Word2vec uses distributional similarity and distributional hypothesis. That is, it derives the meaning of a word from its context: words that appear in its neighborhood in the text. So, if two different words (often) occur in similar context, then it’s highly likely that their meanings are also similar. Word2vec operationalizes this by projecting the meaning of the words in a vector space where words with similar meanings will tend to cluster together, and words with very different meanings are far from one another.

Architectural variants proposed in Word2Vec approach:

1) Continuous bag of words (CBOW): In CBOW, the primary task is to build a language model that correctly predicts the center word given the context words in which the center word appears. What is a language model? It is a (statistical) model that tries to give a probability distribution over sequences of words. Given a sentence of, say, m words, it assigns a probability Pr(w 1 , w 2 , ….., w n ) to the whole sentence. The objective of a language
model is to assign probabilities in such a way that it gives high probability to “good” sentences and low probabilities to “bad” sentences. By good, we mean sentences that are semantically and syntactically correct. By bad, we mean sentences that are incorrect—semantically or syntactically or both. So, for a sentence like “The cat jumped over the dog,” it will try to assign a probability close to 1.0, whereas for a sentence like “jumped over the the cat dog,” it tries to assign a probability close to 0.0.


2) SkipGram: SkipGram is very similar to CBOW, with some minor changes. In SkipGram, the task is to predict the context words from the center word. 