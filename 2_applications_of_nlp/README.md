# Applications of NLP

## POS Tagging

#### Parts of Speech

Parts of speech are categories assigned to words based on their syntactic or grammatical functions. The English language has nine main parts of speech:

1. <strong>Nouns</strong>: Things or people (table, dog, piano, London, towel)
2. <strong>Pronouns</strong>: Words that replace nouns (I, you, he, she, it)
3. <strong>Adjectives</strong>: Words that describe nouns (intelligent, small, silly, intriguing, blue)
4. <strong>Determiners</strong>: Words that limit nouns (a few, many, some, three)
5. <strong>Prepositions</strong>: Words that link nouns to other words (to, on, in, under, beside)
6. <strong>Verbs</strong>: Action words (to be, to have, to study, to learn, to play)
7. <strong>Adverbs</strong>: Words that describe verbs, adjectives, or adverbs themselves (quickly, shortly, very, really, drastically)
8. <strong>Conjunctions</strong>: Words that join two sentences or words (and, but, yet)
9. <strong>Interjections</strong>: Words that are exclamations (ouch! Ow! Wow!)

#### POS Tagger

POS tagging is the process of assigning a tag to a word. Most POS taggers are supervised learning algorithms. Thus, POS taggers hone their predictive abilities by learning from previously labeled datasets.

The datasets can consist of a variety of features, including the word itself, the definition of the word, the relationships of the word with its preceding, proceeding, and other related word(s) that are present within the same sentence, phrase, or paragraph. These features together help the tagger predict what POS tag should be assigned to a word.

The corpus used to train a supervised POS tagger is known as a pre-tagged corpus. Such corpora serve as the basis for the creation of a system for the POS tagger to tag untagged words.

Pre-tagged corpora, however, are not always readily available, and to accurately train a tagger, the corpus must be large. Thus, recently there have been iterations of the POS tagger that can be considered as unsupervised learning algorithms. The drawback of unsupervised learning methods is that the cluster of POS tags generated automatically may not always be as accurate as those found in the pre-tagged corpora used to train supervised methods.

An important thing to remember is that since a POS tagger assigns a POS tag to each word in the given corpus, the input needs to be in the form of word tokens. Therefore, before performing POS tagging, tokenization needs to be carried out on the corpus. For example:

- <strong>Input</strong>: ['I', 'enjoy', 'playing', 'the', 'piano']
- <strong>Output</strong>: ['I_PRO', 'enjoy_V', 'playing_V', 'the_DT', piano_N']

<strong>Note</strong>: The aforementioned parts of speech are very basic tags, and to ease the process of understanding natural language, POS algorithms create much more complicated tags that are variations of these basic ones. A popular [tagset](https://www.ling.upenn.edu/courses/Fall_2003/ling001/penn_treebank_pos.html) is the Treebank tagset. A majority of the pre-trained taggers for the English language are trained on this tagset, including NLTK's POS tagger.

#### Applications of POS tagging

Just like text pre-processing techniques help the machine understand natural language better by encouraging it to focus on only the important details, POS tagging helps the machine actually interpret the context of text and thus make sense of it.

Understanding what words correspond to which parts of speech can be beneficial in processing natural language in several ways for a machine:

- Differentiating between homonyms – words that have the same spelling but mean different things.
- Builds on the need for sentence and word segmentation – one of the basic tasks of natural language processing.
- Used in performing higher-level tasks by other algorithms (e.g. named entity recognition, sentiment analysis, question answering, etc)

<strong>Thus, POS tagging is an important step in the process of understanding natural language because it contributes to other tasks.</strong>


#### Rule-Based POS Taggers

These POS taggers work by rules. The purpose for giving the taggers sets of rules is to ensure that they tag an ambiguous/unknown word accurately most of the times, thus most of the rules are applied only when the taggers come across an ambiguous/unknown word.

These rules are often known as context frame rules and provide the taggers with contextual information to understand what tag to give an ambiguous word. <strong>An example of a rule is as follows: If an ambiguous/unknown word, x, is preceded by a determiner and followed by a noun, then assign it the tag of an adjective</strong>.

The rules depend on your theory of grammar. Additionally, they also often include rules such as capitalization and punctuation. This can help you recognize pronouns and differentiate them from words found at the start of a sentence (following a full stop).

Recently, there have been experiments with training these taggers the unsupervised way. Untagged text is given to the tagger to tag, and humans go through the output tags, correcting whatever tags are inaccurate. This correctly tagged text is then given to the tagger so that it can develop correction rules between the two different tagsets and learn how to accurately tag words. An example of this correction rule-based POS tagger is Brill's tagger. 

## Stochastic POS Taggers

Stochastic POS taggers are taggers that use any method other than rule-based methods to assign tags to words. Thus, there are a large number of approaches that fall into the stochastic category. All models that incorporate statistical methods, such as probability and frequency, when determining the POS tags for words are stochastic models. This section will discuss three models:

1. The Unigram or Word Frequency Approach
2. The n–gram approach
3. The hidden Markov Model

#### The Unigram or Word Frequency Approach

The simplest stochastic POS taggers assign POS tags to ambiguous words solely based on the probability that a word occurs with a tag. This basically means that whatever tag the tagger found linked with a word most often in the training set is the tag that it will assign to an ambiguous instance of the same word. For example, let's say the training set has the word "beautiful" tagged as an adjective a majority of the time. When the POS tagger encounters "beaut", it won't be able to tag this directly because it isn't a proper word. This will be an ambiguous word, and so it will calculate the probability of it being each of the POS tags, based on how many times different instances of this word have been tagged with each of those POS tags. "beaut" can be seen as an ambiguous form of "beautiful", and since "beautiful" has been tagged as an adjective a majority of the time, the POS tagger will tag "beaut" as an adjective too. This is called the word frequency approach because the tagger is checking the frequency of the POS tags assigned to words.

#### The n – gram Approach

This builds on the previous approach. The n in the name stands for how many words are considered when determining the probability of a word belonging to a particular POS tag. When assigning a tag to a word, these POS taggers create a context of the word by factoring in the type of token it is, along with the POS tags of the n preceding words. Based on the context, the taggers select the tag that is most likely to be in sequence with the tags of the preceding words and assigns this to the word in question. The most popular n – gram tagger is known as the Viterbi algorithm.

#### Hidden Markov Model

The hidden Markov model combines both the word frequency approach and the n – gram approach. A Markov model is one that describes a sequence of events or states. The probability of each state occurring depends solely on the state attained by the previous event. These events are based on observations. The "hidden" aspect of the hidden Markov model is that the set of states that an event could possibly be is hidden.

In the case of POS tagging, the observations are the word tokens, and the hidden set of states are the POS tags. The way this works is that the model calculates the probability of a word having a particular tag based on what the tag of the previous word was. For example, P (V | NN) is the probability of the current word being a verb given that the previous word is a noun.

## Chunking

Chunking is an algorithm that takes words and their POS tags as input. It processes these individual tokens and their tags to see whether they can be combined. The combination of one or more individual tokens is known as a chunk, and the POS tag assigned to such a chunk is known as a chunk tag.

These combinations of POS tags are phrases by and are more efficient than simple POS tags. These phrases are chunks. There will be instances where a single word is considered a chunk and assigned a chunk tag too. There are five major chunk tags:

1. <strong>Noun Phrase (NP)</strong>: These are phrases that have nouns as the head word. They act as a subject or an object to the verb or verb phrase.
2. <strong>Verb Phrase (VP)</strong>: These are phrases that have verbs as the head word.
3. <strong>Adjective Phrase (ADJP)</strong>: These are phrases that have adjectives as the head word. Describing and qualifying nouns or pronouns is the main function of adjective phrases. They are found either directly before or after the noun or pronoun.
4. <strong>Adverb Phrase (ADVP)</strong>: These are phrases that have adverbs as the head word. They're used as modifiers for nouns and verbs by providing details that describe and qualify them.
5. <strong>Prepositional Phrase (PP)</strong>: These are phrases that have prepositions as the head word. They position an action or an entity in time or space.

Thus, chunking is performed after POS tagging has been applied on a corpus. This allows the text to be broken down into its simplest form (tokens of words), have its structure analyzed, and then be grouped back together into meaningful higher-level chunks. Chunking also benefits higher-level process like named entity recognition.

## Chinking

Chinking is an extension of chunking, as you've probably guessed already from its name. It's not a mandatory for step but it can be beneficial.

Chinking is performed after chunking. Post chunking, you have chunks with their chunk tags, along with individual words with their POS tags. Often, these extra words are unnecessary. They don't contribute to the final result or the entire process of understanding natural language and thus are a nuisance. The process of chinking helps us deal with this issue by extracting the chunks, and their chunk tags form the tagged corpus, thus getting rid of the unnecessary bits. These useful chunks are called chinks once they have been extracted from the tagged corpus.

For example, if you need only the nouns or noun phrases from a corpus to answer questions such as "what is this corpus talking about?", you would apply chinking because it would extract just what you want and present it in front of your eyes. Let's check this out with an exercise.



