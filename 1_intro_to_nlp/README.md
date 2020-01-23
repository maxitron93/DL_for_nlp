# Introduction to NLP

#### Basics of NLP 
Natural language processing is the machine-based processing of human communication. It aims to teach machines how to process and understand the language of humans.

The key thing to consider in NLP is that communication needs to occur in the natural language of humans. We've been communicating with machines for decades now by creating programs, but these programs are written in languages that are not natural languages; Java, Python, C, and C++, etc.

So far, for humans to communicate with a machine, we must learn a language that the machine is able to understand. The purpose of natural language processing is to enable the opposite of this. <strong>Rather than having humans conform to the ways of a machine and learn how to effectively communicate with them, natural language processing enables machines to conform to humans and learn their way of communication</strong>.

Machines work best with numerical data. So, natural language processing works with textual data and converts it into numerical data, enabling machine learning and deep learning models to be fitted on it. This, <strong>NLP bridges the communication gap between humans and machines</strong> by taking the spoken and written forms of language from humans and converting them into data that can be understood by machines.

Thanks to natural language processing, the machine is able to make sense of, answer questions based on, solve problems using, and communicate in a natural language, among other things.

#### Capabilities of NLP
NLP applications fall under three broad capabilities of natural language processing:

1. <strong>Speech Recognition</strong>: The machine is able to recognize a natural language in its spoken form and translate it into a textual form. e.g. you can enable dictation and speak to your phone, and it will convert whatever you are saying into text.
2. <strong>Natural Language Understanding</strong>: The machine is able to understand a natural language in both its spoken and written form. e.g. saying 'Hey Siri, call home' to Siri on your iPhone for Siri to automatically call 'home' for you.
3. <strong>Natural Language Generation</strong>: The machine is able to generate natural language itself. e.g. Asking 'Siri, what time is it?' and her replying with the time – 'It's 2:08pm'.

#### Applications of NLP
<em>Variety of Applications covered in this section - not exhaustive and the buckets don't seem mutually exclusive.</em>

#### Text preprocessing

Text preprocessing techniques involve prepping the corpora for proper analysis and for the machine learning and deep learning models. Each corpus requires different text preprocessing techniques depending on the task that needs to be executed. A number of the preprocessing techniques include:

- Lowercasing/uppercasing
- Noise removal: e.g, removing punctuation marks and HTML markup.
- Text normalization: Making the textual input is consistent.
- Stemming: Reduce words to their stem or root form.
- Lemmatization: Similar to stemming, but instead of removing letters, it often uses WordNet mappings to return words to their root form.
- Tokenization
- Removing stop words

## Word Embeddings

NLP models perform most efficiently when provided with numerical data as input, and thus a key role of natural language processing is to transform preprocessed textual data into representation of the numerical data.

This is what word embeddings are: they are numerical representations in the form of real-value vectors for text. <strong>Words that have similar meanings map to similar vectors and thus have similar representations.</strong> 

The beneficial aspect of word embeddings is that they are able to capture contextual, semantic, and syntactic similarities, and the relations of a word with other words, to effectively train the machine to comprehend natural language. <strong>This is the main aim of word embeddings – to form clusters of similar vectors that correspond to words with similar meanings</strong>.

This process of transforming words into their real-value vectors is known as vectorization. There are many word embedding techniques available, but the two main ones are Word2Vec and GloVe:

#### Word2Vec

A techniques used to generate vectors from words. Word2Vec is a shallow neural network – it has only two layers – and thus does not qualify as a deep learning model.

The aim of Word2Vec is to understand the probability of two or more words occurring together and thus to group words with similar meanings together to form a cluster in a vector space.

Like any other machine learning or deep learning model, Word2Vec becomes more and more efficient by learning from past data and past occurrences of words. Thus, if provided with enough data and context, it can accurately guess a word's meaning based on past occurrences and context.

Once Word2Vec has been given a corpus, it produces a vocabulary wherein each word has a vector of its own attached to it, which is known as its neural word embedding.

Word2Vec trains a word against words that neighbor the word in the input corpus, and there are two methods of doing so:

1. <strong>Continuous Bag of Words (CBOW)</strong>: This method predicts the current word based on the context. Thus, it takes the word's surrounding words as input to produce the word as output, and it chooses this word based on the probability that this is indeed the word that is a part of the sentence.

    For example, if the algorithm is provided with the words "the food was" and needs to predict the adjective after it, it is most likely to output the word "good" rather than output the word "delightful," since there would be more instances where the word "good" was used, and thus it has learned that "good" has a higher probability than "delightful." CBOW it said to be faster than skip-gram and has a higher accuracy with more frequent words.

2. <strong>Skip-gram</strong>: This method predicts the words surrounding a word by taking the word as input, understanding the meaning of the word, and assigning it to a context. For example, if the algorithm was given the word "delightful," it would have to understand its meaning and learn from past context to predict that the probability that the surrounding words are "the food was" is highest. Skip-gram is said to work best with a small corpus.

While both methods seem to be working in opposite manners, they are essentially predicting words based on the context of local (nearby) words; they are using a window of context to predict what word will come next. This <strong>window</strong> is a configurable parameter.

The decision of choosing which algorithm to use depends on the corpus at hand. CBOW works on the basis of probability and thus chooses the word that has the highest probability of occurring given a specific context. <strong>This means it will usually predict only common and frequent words since those have the highest probabilities, and rare and infrequent words will never be produced by CBOW</strong>.

Skip-gram, on the other hand, predicts context, and thus when given a word, it will take it as a new observation rather than comparing it to an existing word with a similar meaning. Due to this, rare words will not be avoided or looked over. However, this also means that a lot of training data will be required for skip-gram to work efficiently. 

#### GloVe
GloVe, an abbreviation of "global vectors," is a word embedding technique that has been developed by Stanford. It is an unsupervised learning algorithm that builds on Word2Vec. While Word2Vec is quite successful in generating word embeddings, <strong>the issue with Word2Vec is that is it has a small window through which it focuses on local words and local context to predict words</strong>. GloVe, as mentioned in its name, looks at all the words present in a corpus.

While Word2Vec is a predictive model as it learns vectors to improve its predictive abilities, <strong>GloVe is a count-based model. What this means is that GloVe learns its vectors by performing dimensionality reduction on a co-occurrence counts matrix.</strong> The connections that GloVe is able to make are along the lines of this:

king – man + woman = queen

This means it's able to understand that "king" and "queen" share a relationship that is similar to that between "man" and "woman".

When dealing with a corpus, there exist algorithms to construct matrices based on term frequencies. Basically, these matrices contain words that occur in a document as rows, and the columns are either paragraphs or separate documents. The elements of the matrices represent the frequency with which the words occur in the documents. Naturally, with a large corpus, this matrix will be huge. Processing such a large matrix will take a lot of time and memory, thus we perform dimensionality reduction. This is the process of reducing the size of the matrix so it is possible to perform further operations on it.

In the case of GloVe, the matrix is known as a co-occurrence counts matrix, which contains information on how many times a word has occurred in a particular context in a corpus. The rows are the words and the columns are the contexts. This matrix is then factorized in order to reduce the dimensions, and the new matrix has a vector representation for each word.




