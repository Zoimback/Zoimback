Natural Language Processing

Natural Language Processing

Inverse Document Frequency
 Definition
 Forms
 Fine-tuning
 IDF and Classification

Natural Language Processing

Inverse Document Frequency
- So far we know how to count words
- Counting words document by document doesnt say anything about how

relevant those words are in the corpus

Doc 1: hello hello plane
Doc 2: hello hello hello duck
Doc 3: hello hello rain

-> [2, 1, 0, 0]
-> [3, 0, 1, 0]
-> [2, 0, 0, 1]

Hello is always carrying a significant weight in the resulting vectorization and
barely contributes with any information

Natural Language Processing

Inverse Document Frequency
- Try to make words less relevant if they appear in too many documents

Doc 1: hello hello plane
Doc 2: hello hello hello duck
Doc 3: hello hello rain

hello appears in all 3 documents 3 / 3 = 1
the rest of the words appear in just one document each = 1 / 3

What if we use these new coefficients?

Natural Language Processing

Intuitively, this ratio is closer to 1 the more frequent a word is

Inverse Document Frequency
-
- So the inverses of these ratios will indeed penalize too frequent words!
Doc 1: hello hello plane
Doc 2: hello hello hello duck
Doc 3: hello hello rain

-> [0, log(3), 0, 0]
-> [0, 0, log(3), 0]
-> [ 0, 0, 0, log(3)]

IDF(hello) = log(3 / 3) = log(1)
IDF(plane) = IDF(duck) = IDF(rain) = log(3 / 1) = log(3)

The combination of frequencies and their IDFs is called TF-IDF
TF-IDF(word) = TF(word) * IDF(word)

Natural Language Processing

Why the logarithm?
-
- And it completely cancels out words that appear everywhere!

It prevents excessively rare words being excessively rewarded

Natural Language Processing

Fine tuning
- TF-IDF normally requires some tuning for it to be useful

- Getting rid of words that are too rare (setting a minimum doc freq)
- Conversely, ignoring words that are too frequent
- Keeping dimensionality in check (max features)
- Choosing the right TF (absolute, relative, logarithmic)
- And even adding smoothing to the IDF formula

Natural Language Processing

TF-IDF and classification
- This what our next exercise will be about!
- TF-IDF gives us vectorizations rewarding rare terms
-  so, in theory, if a bunch of documents share the same rare terms they

might be about the same!

- e.g. having 100 out of 1000 documents talking about birds might hint us

that those documents might belong to the same category

- Theres a notebook in the exercise explaining this in more detail ;