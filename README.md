🧠 Data Citation Identification and Classification using SciBERT
📘 Overview

This project uses SciBERT to automatically identify and classify dataset mentions in scientific research papers.
The workflow combines Named Entity Recognition (NER) and text classification into a single pipeline that detects dataset mentions and classifies their citation types.

⚙️ Project Workflow
1. Exploratory Data Analysis (EDA)

Before training, an EDA notebook was created to:

Explore the dataset structure and class distribution

Visualize common dataset-related terms

Analyze token lengths and class imbalance

The EDA helped refine preprocessing and labeling strategies.

2. Fine-tuning SciBERT for NER

Base model: allenai/scibert_scivocab_uncased

Task: Identify dataset mentions in scientific text (BIO tagging)

Dataset prepared with custom entity spans for data mentions

Optimizer: AdamW

Learning rate: 2e-5

Evaluation metrics: F1, Precision, Recall

3. Fine-tuning SciBERT for Classification

Same base model (allenai/scibert_scivocab_uncased)

Task: Classify each detected mention as one of:

Explicit data citation

Implicit data mention

Generic dataset reference

Used the [CLS] token for classification

Fine-tuned using Hugging Face Trainer API

4. Pipeline Integration

A unified script/notebook was created to combine both fine-tuned models:

Run NER to extract dataset mentions


🧩 Tech Stack

Language: Python

Frameworks: PyTorch, Hugging Face Transformers

Libraries: pandas, numpy, scikit-learn, matplotlib, seaborn, tqdm

📈 Results
Model	Task	F1 Score
SciBERT	NER	0.91
SciBERT	Classification	0.9
