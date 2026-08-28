# NLP_THEORY_ASSIGNMENT_1_057
# UCS3564 – Natural Language Processing

## Comprehensive NLP Pipeline

### Course Information

* **Course Code:** UCS3564
* **Course:** Natural Language Processing
* **Batch:** 2024–2028
* **Academic Year:** 2026–2027
* **Branch:** B.E. Computer Science and Engineering

---

## 1. Project Overview

This project implements a complete Natural Language Processing pipeline using a text review dataset.

The project covers multiple levels of NLP, including:

* Text preprocessing and normalization
* Vocabulary construction and unknown-word handling
* N-gram language modeling
* Smoothing techniques and perplexity evaluation
* Part-of-Speech tagging
* Hidden Markov Model (HMM) with Viterbi decoding
* Most Frequent Tag (MFT) baseline
* POS tagging comparison with spaCy
* Context-Free Grammar (CFG)
* Chomsky Normal Form (CNF)
* CKY parsing
* Dependency parsing
* WordNet lexical semantics
* Simplified Lesk Word Sense Disambiguation
* TF-IDF
* Word-word co-occurrence matrix
* Positive Pointwise Mutual Information (PPMI)
* Word2Vec Skip-Gram
* Vector semantic comparison

The implementation is organized as a sequence of modular notebook cells, with intermediate outputs and evaluation results.

---

## 2. Objectives

The main objectives of this project are to:

1. Apply fundamental text preprocessing techniques.
2. Build and evaluate unigram, bigram and trigram language models.
3. Implement different smoothing methods and compare their perplexity.
4. Implement POS tagging using an HMM and the Viterbi algorithm.
5. Compare the HMM tagger with an MFT baseline and spaCy.
6. Perform syntactic parsing using CFG, CNF and CKY.
7. Generate dependency parses and extract subject–verb–object relations.
8. Explore lexical semantics using WordNet.
9. Implement simplified Lesk word sense disambiguation.
10. Construct TF-IDF and PPMI vector representations.
11. Train a Word2Vec Skip-Gram model.
12. Compare different vector representations using cosine similarity.
13. Handle common NLP edge cases throughout the pipeline.

---

## 3. Dataset

The project uses a text review dataset divided into:

* Training set
* Validation set
* Test set

The training data is used for learning vocabulary, language models, POS-related statistics and vector representations.

The validation set is used where required for parameter tuning, while the test set is used for final evaluation.

---

## 4. NLP Pipeline

### Part 1 – Text Preprocessing

The preprocessing pipeline includes:

* Lowercase conversion
* Tokenization
* Stopword removal
* Porter stemming
* WordNet lemmatization
* Vocabulary construction
* Vocabulary cutoff
* `<UNK>` handling
* Type-token ratio calculation

The normalized corpus is used by subsequent language modeling and semantic tasks.

---

### Part 2 – N-gram Language Models

The project implements:

* Unigram language model
* Bigram language model
* Trigram language model

Sentence boundary markers are used during language-model construction.

The following smoothing techniques are implemented:

* Laplace / Add-One smoothing
* Add-k smoothing
* Kneser-Ney smoothing

Models are evaluated using perplexity on the test set, and sample sentences are generated from the language models.

---

### Part 3 – POS Tagging

POS tagging is implemented using:

* Most Frequent Tag (MFT) baseline
* Hidden Markov Model (HMM)
* Viterbi decoding
* Unknown-word handling
* spaCy POS tagging for comparison

Transition and emission probabilities are estimated from the tagged corpus.

The performance of the HMM tagger is compared against the MFT baseline and spaCy.

The five most frequent HMM confusion pairs are also reported.

---

### Part 4 – Syntactic Parsing

A Context-Free Grammar (CFG) is constructed for ten sentences from the dataset.

The grammar is converted into Chomsky Normal Form (CNF), followed by CKY/chart parsing.

The project reports:

* Number of CFG productions
* Number of terminals and non-terminals
* CNF grammar
* Number of parse trees for each sentence
* First parse tree for each successfully parsed sentence
* Ambiguity analysis

Ambiguous sentences are identified by checking whether more than one parse tree exists.

Dependency parsing is also performed using spaCy, with dependency relations and subject–verb–object triples extracted from the parsed sentences.

---

### Part 5 – Lexical Semantics and Word Sense Disambiguation

WordNet is used to investigate multiple senses of selected polysemous words.

For selected words, the project examines:

* WordNet senses
* Definitions
* Hypernyms
* Hyponyms
* Antonyms

A simplified Lesk algorithm is implemented for word sense disambiguation.

The algorithm is evaluated on 20 hand-labelled sentences, and the following are reported:

* Total sentences
* Correct predictions
* Incorrect predictions
* Accuracy

---

### Part 6 – Vector Semantics

Three different vector representations are constructed and compared.

#### TF-IDF

A term-document matrix is created using TF-IDF weighting.

The implementation uses the training corpus and reports:

* Number of documents
* Number of terms
* TF-IDF matrix shape

#### Word-Word Co-occurrence Matrix

A word-word co-occurrence matrix is constructed using a context window of:

**Window size = 2**

The matrix records how frequently words occur within the specified context window.

#### PPMI

Positive Pointwise Mutual Information is calculated from the co-occurrence matrix.

PPMI values are used to represent the strength of association between words.

#### Word2Vec Skip-Gram

A Word2Vec Skip-Gram model is trained using Gensim with:

* Vector size: 100
* Window size: 2
* Minimum count: 2
* Epochs: 10

Nearest neighbours are obtained for five query words.

The three representations are compared using cosine similarity.

---

## 5. Vector Semantics Comparison

Five query words are used for comparison:

* `card`
* `memory`
* `phone`
* `work`
* `battery`

For each query word, the project reports the top five nearest neighbours according to:

1. TF-IDF
2. PPMI
3. Word2Vec Skip-Gram

The results are used to compare the ability of each representation to capture semantic relationships in the dataset.

---

## 6. Edge Case Handling

The implementation considers common NLP edge cases, including:

* Empty input
* Single-token input
* Out-of-vocabulary words
* Ambiguous POS words
* Punctuation
* Special characters
* Mixed-case text
* Duplicate entries
* Very long input
* Non-ASCII characters

Functions are designed to avoid failures when possible and provide appropriate fallback behaviour.

---

## 7. Technologies and Libraries

### Programming Language

* Python

### Main Libraries

* NLTK
* NumPy
* Pandas
* scikit-learn
* spaCy
* Gensim
* Matplotlib
* Seaborn

### NLP Resources

* NLTK Treebank
* WordNet
* NLTK Stopwords
* spaCy language model

---

## 8. Project Structure

```text
NLP-Assignment/
│
├── NLP_Assignment.ipynb
├── README.md
├── requirements.txt
│
├── data/
│   └── dataset.csv
│
├── outputs/
│   ├── plots/
│   ├── parse_trees/
│   └── results/
│
└── report/
    └── NLP_Assignment_Report.pdf
```

The exact folder structure may vary depending on the final submission format.

---

## 9. Installation

Clone or download the project repository and install the required Python packages.

```bash
pip install -r requirements.txt
```

Additional NLTK resources may be required:

```python
import nltk

nltk.download("punkt")
nltk.download("stopwords")
nltk.download("wordnet")
nltk.download("omw-1.4")
nltk.download("treebank")
```

If spaCy is used:

```bash
python -m spacy download en_core_web_sm
```

---

## 10. Running the Project

1. Open `NLP_Assignment.ipynb`.
2. Install the required dependencies.
3. Ensure the dataset is available at the expected location.
4. Run the notebook cells sequentially from beginning to end.
5. Check the generated tables, metrics, parse trees and semantic results.
6. The final notebook should be submitted in executed form with all outputs visible.

---

## 11. Important Results

The project reports quantitative results for the major NLP components.

### POS Tagging

| Method       | Accuracy |
| ------------ | -------: |
| MFT Baseline |   0.9266 |
| HMM Viterbi  |   0.9184 |
| spaCy        |   0.9236 |

### HMM Confusion Pairs

The five most frequent confusion pairs are reported in the notebook, including:

* NOUN → VERB
* NOUN → ADJ
* . → NUM
* ADJ → NOUN
* ADJ → VERB

### Word Sense Disambiguation

The simplified Lesk evaluation reports:

* **Total sentences:** 20
* **Correct:** 11
* **Incorrect:** 9
* **Accuracy:** 55.00%

### Word2Vec

The Skip-Gram model uses 100-dimensional word vectors and a context window of 2.

Detailed nearest-neighbour results for the five query words are provided in the notebook.

---

## 12. Output

The executed notebook contains:

* Preprocessing outputs
* Vocabulary statistics
* Language-model statistics
* Perplexity results
* Generated sentences
* POS tagging results
* Confusion pairs
* CFG and CNF grammars
* CKY parse results
* Parse trees
* Dependency relations
* WordNet senses
* Lesk predictions and evaluation
* TF-IDF matrix
* Co-occurrence matrix
* PPMI matrix
* Word2Vec nearest neighbours
* Vector semantic comparison

---

## 13. Conclusion

This project demonstrates an end-to-end NLP pipeline covering preprocessing, statistical language modeling, syntactic analysis, lexical semantics and vector semantics.

Different NLP representations and algorithms are evaluated on the same dataset, allowing their strengths and limitations to be compared.

The final results show how traditional count-based representations such as TF-IDF and PPMI differ from distributed representations such as Word2Vec in capturing relationships between words.
