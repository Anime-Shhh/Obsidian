[[Intro to DS]]
# IDF(inverse document frequency) matrix
## Use Case?
IDF matrices are made to see the frequency of words accross a collection of documents

## What is an IDF Matrix?
In practice, NLP uses matrices to represent text numerically.

You usually start with:
### Term-document matrix:

||word1|word2|word3|
|---|---|---|---|
|doc1|tf|tf|tf|
|doc2|tf|tf|tf|

Each row = document  
Each column = vocabulary word

---

### IDF matrix:

The IDF values are applied to the columns (terms). Conceptually:
- Each column gets scaled by its IDF weight.
- Rare words get larger weights.
Example:

| term    | IDF |
| ------- | --- |
| the     | 0.1 |
| cat     | 1.5 |
| quantum | 3.2 |
## How IDF is actually used (TF-IDF)

Most of the time you don't use IDF alone — you combine it with term frequency:

TF-IDF=TF×IDFTF\text{-}IDF = TF \times IDFTF-IDF=TF×IDF

This creates a **TF-IDF matrix**, which:

✅ highlights important words  
✅ downweights common words  
✅ converts text into numerical vectors for ML
## Simple intuition

Think:

TF = how often a word appears in THIS document  
IDF = how rare that word is across ALL documents


## Probabilistic Language Models

Given a sentence:
```
Apple's are ___.
```

You would compute:
	P(word_i = "brown"|word_1, ..., word_i-1) = ?
	P(word_i = "red"|word_1, ..., word_i-1) = ?
for all possibilities and determine the probability, choose the one with the highest probability. Then feed it back into the machine to determine the next word. 
