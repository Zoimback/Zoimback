Natural Language Processing

Natural Language Processing

More on Preprocessing
 Word Stemming
 Part of Speech Analysis

 Pos Tagging
 Named Entity Recognition
 Lemmatization
 Correcting mistakes

 Fuzzy search & Levenshtein distance

 Text canonicalization: normalization and expanding contractions

Natural Language Processing

Word Stemming
- Takes advantage of the fact that words have roots

[danced, dancer] -> dance

- Theres many Stemmers out there: snowball, Porter, Lancaster
- They all follow their own rules, but they all have the same goal

Natural Language Processing

Its just one of the many available Stemmers

Porter Stemmer
-
- Available in nltk
-

It works on a fixed ruleset for suffixes (e.g. emptiness -> empti)

Natural Language Processing

Stemming: Pros and Cons
-
-
-
- Some stemmings result in non-existent words (emptiness -> empti)

Its very efficient
It effectively reduces our vocabulary
Its word based (doesnt take into account any context at all)

Natural Language Processing

Part-of-speech (POS) tagging
- Kinda what you did back in school with sentences
-

I love coding -> [(I, PRP), (love, VBP), (coding, VBG)]
- PRP: Personal pronoun
- VBP: Verb
- VBG: Verb, gerund

- Theres many ways to perform POS Tagging (what you saw above)

- Statistic tagging
- Pre-trained models

- NLTK uses the later for POS Tagging

Natural Language Processing

Named Entity Recognition (NER)
-
- Becomes easier once we POS-tagged a sentence ;)

Identify names, dates, locations etc within a sentence

[(My, PRP$), (name, NN), (is, VBZ), (Sergio, NNP)]

=>                      (Sentence) My name is

        ||
                                           V

      (Person) Sergio

Natural Language Processing

Named Entity Recognition (NER)
- NLTK provides pre-trained models that infer what parts of a sentence are

actually Named Entities

- NLTKs MaxEnt NE Chunker accepts a tagged sentence and qualifies

each token as one of

{LOCATION, ORGANIZATION, PERSON, DURATION, DATE, CARDINAL, PERCENT, MONEY, MEASURE, FACILITY, GPE}

Natural Language Processing

Lemmatization
- Kinda the result of combining stemming and POS Tagging (although theyre not

exactly the same)

- Lemmatization tries to reduce or vocabulary by converting every word to their

base form

- Unlike stemming, the result will always be a valid word in the target language

wolves -> wolf

emptiness -> emptiness !!! (emptiness is a noun, empty is an adjective)

Natural Language Processing

Correcting mistakes
- Some inputs are highly unreliable (e.g. text messages, tweets)

Id lik an appple -> Id like an apple

One common strategy consists of having a dictionary, comparing our
current word with them and getting the closest match

Natural Language Processing

Levenshtein distance
-

Its the minimum number of insertions, edits, and deletions we need to
perform in a word to convert it to some other word

lieek -> likek -> like (one substitution, one deletion)

- Pythons Levenhstein.distance function can do that for you

Levenshtein.distance("lieek", "like") -> 2

Getting the argmin distance between your word and a whole dictionary will
allow you to fix a lot of mistakes

Natural Language Processing

Text canonicalization
- Having all the input texts using the same words to refer to the same

concept can be useful (or not!)

What ure doing -> What are you doing?

Notice that we changed u for you and we expanded the contraction
youre to you are

I just wanted to mention this concept, but well not work with it for now