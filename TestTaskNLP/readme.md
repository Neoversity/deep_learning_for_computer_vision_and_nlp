# Sentiment Analysis using BERT

## Overview
This project implements a sentiment analysis model using **BERT** to classify text into three categories: *negative, neutral, positive*. The model was trained on a dataset of social media posts and fine-tuned using **BERT-base** and later improved with **BERT-large** for better accuracy.

## Features
- **Text Preprocessing:** Cleaning and tokenization of input text.
- **Model Training:** Fine-tuning BERT on labeled training data.
- **Evaluation:** Performance metrics including accuracy, loss, precision, recall, and F1-score.
- **Submission:** Generating predictions for the Kaggle competition.

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

# Comparison of BERT and DistilBERT for NLP Task

## Overview
This project compares the efficiency of **BERT-Large** and **DistilBERT** for text classification. Different architectures were tested to find the best balance between training speed and prediction accuracy.

## Results

| Epoch | Train Loss | Train Acc | Val Loss | Val Acc |
|--------|------------|-----------|-----------|-----------|
| 1      | 0.6872     | 71.62%    | 0.5974    | 76.41%    |
| 2      | 0.5313     | 79.34%    | 0.6033    | 76.31%    |
| 3      | 0.3738     | 85.99%    | 0.7209    | 74.31%    |

✅ **DistilBERT** is faster and lighter, but **Val Accuracy** starts to drop after the 2nd epoch.
✅ **Overfitting** — the model learns well (**85.99%**), but degrades on validation.
❌ **Lower Val Accuracy** (**74.31%**) compared to BERT.

---

| Epoch | Train Loss | Train Acc | Val Loss | Val Acc |
|--------|------------|-----------|-----------|-----------|
| 1      | 0.6820     | 71.80%    | 0.6113    | 75.04%    |
| 2      | 0.5405     | 79.08%    | 0.6298    | 75.77%    |
| 3      | 0.4183     | 84.17%    | 0.6372    | 75.38%    |

✅ **BERT-Large** achieves **higher Val Accuracy** (**75.77%**) with longer training.

## Conclusions
1. **DistilBERT** is suitable for fast computations but has limitations in accuracy.
2. **BERT-Large** provides more stable results but requires more resources.
3. **Potential improvements:** Using **RoBERTa**, **optimizing learning rate**, and experimenting with **regularization**.

🚀 **Recommendation:** Use **BERT-Large** for maximum accuracy or **DistilBERT** for fast computations at a lower cost.

## Results
After fine-tuning **BERT-large**, we achieved a final public leaderboard score of **0.77504** on Kaggle.

## Next Steps
- Experimenting with **RoBERTa** for better contextual understanding.
- Hyperparameter tuning using **Optuna**.
- Implementing **multi-GPU training** for speed optimization.

## Author
Anton Babenko
