# Automatic Question Classification in Portuguese: A Large-Scale Dataset

This repository contains the dataset and the official implementation for the paper **"Automatic Question classification in Portuguese: A Large-Scale Dataset and Comparative Evaluation of Classification Strategies"** by Murilo Boccardo and Valéria D. Feltrim.

A central contribution of this project is the creation and curation of a large-scale Portuguese-language dataset comprising approximately 17,000 Brazilian university entrance exam questions collected from the Agatha.edu platform. The project evaluates two classification strategies: a single-step approach for direct fine-grained topic prediction, and a two-stage hierarchical approach (predicting the subject first, then the topic).

## 📊 Dataset Usage & Structure

The dataset is provided in `.parquet` format and is divided into different stages of processing to facilitate both reproducibility and custom usage.

Here is the difference between the available dataset files located in the `datasets/` folder:

* **`questoes_bruto.parquet`**: Contains the raw questions exactly as they were collected from the platform, prior to any modification.


* **`questoes_unificadas.parquet`**: Contains the dataset after the initial cleaning, normalization, and topic consolidation process. This step reduced the extreme granularity of the raw taxonomy (from 1,689 topics to 125) and unified semantically overlapping or redundant topics. Generated via `questoes_unificacao.ipynb`.


* **`questoes_tratadas.parquet`**: The final unified questions after the complete NLP preprocessing pipeline, which includes the standardization of text, handling of mathematical symbols, and removal of formatting artifacts. Generated via `pre_processamento.ipynb`.



### Pre-split Datasets

Inside the `datasets/divided/` directory, you will find the train, validation, and test splits used for the experiments, including the tokenized versions (`_tokenized.parquet`) specifically formatted for the Transformer models evaluated in the study.

## 💻 Code Structure

The codebase is organized through Jupyter Notebooks that document the entire experimental pipeline:

* **`questoes_unificacao.ipynb`**: Script responsible for the topic consolidation and reduction of label granularity.


* **`pre_processamento.ipynb`**: Script containing the data cleaning and NLP text normalization pipeline.


* **`main.ipynb`**: Contains the core code for training the models (Support Vector Machines, Naive Bayes, Random Forest, Logistic Regression, BERT, and DistilBERT) and implementing both the direct and two-stage hierarchical classification architectures.


* **`analysis.ipynb`**: Includes the scripts used to generate the performance metrics, confusion matrices, and overall analysis of the results found in the `results/` folder.



## ⚙️ Requirements

To install the necessary dependencies and reproduce the experiments, make sure you have Python installed and run the following commands in your terminal:

```bash
# Clone the repository
git clone https://github.com/murilob03/automatic-question-classification-pt.git
cd automatic-question-classification-pt

# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

# Install the required libraries
pip install -r requirements.txt
```

(Note: Be sure to download the specific spaCy Portuguese language model used for lemmatization and stopword removal  by running `python -m spacy download pt_core_news_sm`).

## 📝 Reference

If you use this dataset or code in your research, please cite our paper:

```bibtex
@article{boccardo-2026,
  title={Automatic Question classification in Portuguese: A Large-Scale Dataset and Comparative Evaluation of Classification Strategies},
  author={Boccardo, Murilo and Feltrim, Val{\'e}ria D.},
  journal={PROPOR},
  year={2026}
}
```