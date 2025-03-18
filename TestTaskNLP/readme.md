# Sentiment Analysis using BERT

## Overview
This project implements a sentiment analysis model using **BERT** to classify text into three categories: *negative, neutral, positive*. The model was trained on a dataset of social media posts and fine-tuned using **BERT-base** and later improved with **BERT-large** for better accuracy.

## Features
- **Text Preprocessing:** Cleaning and tokenization of input text.
- **Model Training:** Fine-tuning BERT on labeled training data.
- **Evaluation:** Performance metrics including accuracy, loss, precision, recall, and F1-score.
- **Submission:** Generating predictions for Kaggle competition.

## Setup
### Prerequisites
Ensure you have Python 3.8+ installed along with the necessary libraries:
```bash
pip install torch transformers pandas scikit-learn
```

### Dataset
- **Train File:** `train.csv`
- **Test File:** `test.csv`

Place them in the `data/` directory.

## Training Process
```python
from transformers import AutoModelForSequenceClassification, AdamW

model_name = "bert-base-uncased"
model = AutoModelForSequenceClassification.from_pretrained(model_name, num_labels=3).to(device)

optimizer = AdamW(model.parameters(), lr=2e-5)
```

Run the training script:
```bash
python train.py
```

## Evaluation Metrics
| Metric      | Score |
|------------|-------|
| Accuracy   | 76.54% |
| F1-score   | 75.38% |

## Results
After fine-tuning **BERT-large**, we achieved a final public leaderboard score of **0.77504** on Kaggle.

## Next Steps
- Experimenting with **RoBERTa** for better contextual understanding.
- Hyperparameter tuning using **Optuna**.
- Implementing **multi-GPU training** for speed optimization.

## Author
Anton Babenko

