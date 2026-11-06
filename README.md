# ReviewsPreprossing

An academic NLP mini project exploring text preprocessing and numerical text representation across product, restaurant, and movie reviews.

## Project notebook

Open [the executed Jupyter Notebook](7th_Mini_Project_NLP_Text_Preprocessing_Representation.ipynb) to view the implementation, output tables, visualizations, and discussion.

The project focuses on descriptive analysis. It does not train classifiers, neural networks, or prediction models.

## Dataset

The notebook downloads the [UCI Sentiment Labelled Sentences dataset](https://archive.ics.uci.edu/dataset/331/sentiment+labelled+sentences), contributed by Dimitrios Kotzias (2015).

| Domain | Reviews | Positive | Negative |
|---|---:|---:|---:|
| Amazon | 1,000 | 500 | 500 |
| Yelp | 1,000 | 500 | 500 |
| IMDb | 1,000 | 500 | 500 |
| **Total** | **3,000** | **1,500** | **1,500** |

These distributions are checked during execution. Original text and domain labels are preserved, and duplicate records are retained to analyse all released samples. No manual dataset upload is needed.

## What the project covers

- Dataset exploration: sample records, data types, missing values, duplicates, and class/domain distributions.
- Preprocessing: lowercasing, punctuation and special-character removal, NLTK tokenization, and stopword removal.
- Negation preservation: explicit `not`, `no`, and `never` tokens remain in the final text.
- Word-level one-hot encoding with an explicit vocabulary-to-index mapping.
- Document-level Bag of Words, bigrams, and TF-IDF representations.
- Domain comparisons using frequent terms, bigrams, and globally fitted TF-IDF weights.
- Interpretation of actual results, representation limitations, and a final validation checklist.

BoW, bigrams, and TF-IDF all use the same preprocessed documents. Individual-document TF-IDF rankings and domain-average TF-IDF rankings are reported separately.

## Running the notebook

Use Python 3.11 (the validated version) and Jupyter Notebook or JupyterLab.

```bash
git clone https://github.com/Haneenabdelghany/ReviewsPreprossing.git
cd ReviewsPreprossing
python -m pip install notebook
python -m notebook
```

Open `7th_Mini_Project_NLP_Text_Preprocessing_Representation.ipynb`, select a Python kernel, and choose **Restart Kernel and Run All Cells**.

The first code cell installs missing analysis dependencies into the active kernel: Pandas, NumPy, Matplotlib, Seaborn, NLTK, Scikit-learn, SciPy, and IPython. Internet access is required for initial package installation, the UCI dataset download, and missing NLTK stopwords. The notebook records package versions and the downloaded archive's SHA-256 checksum.

## Interpretation and limitations

TF-IDF supports weighted vocabulary analysis, while bigrams add local phrase information that unigram representations omit. Domain comparisons use one shared vocabulary and global IDF transformation; high domain concentration is not assumed to imply exclusivity.

These sparse lexical representations do not capture contextual meaning or full sentence structure. Removing punctuation can split contractions and lose contracted negation, numbers, and emphasis. Stopword removal may create bigram adjacency absent from the original sentence. Empty preprocessed reviews remain as zero rows, and retained duplicates affect frequencies.

The notebook includes saved outputs and assertions checking all 3,000 samples, class/domain balance, original-text preservation, feature alignment, and representation consistency.
