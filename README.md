# FAQ Chatbot

A machine learning chatbot that answers frequently asked questions about ICTHub's courses, pricing, and services. The model classifies a user's question and returns the most relevant predefined response, served through a simple Gradio web interface.

## Overview

This chatbot was built by training a text classification model on a manually-collected FAQ dataset. User input is vectorized, classified, and mapped back to a human-readable answer. A word-validation step filters out meaningless input before prediction.

## Features

- Text classification model trained on a custom FAQ dataset
- Input validation using NLTK's English word corpus (plus custom domain words)
- Interactive web interface built with Gradio
- Serialized model pipeline (model, vectorizer, label encoder) for reproducible inference

## Tech Stack

- **Python**
- **scikit-learn** — model training & prediction
- **CountVectorizer** — text vectorization
- **NLTK** — word validation
- **joblib** — model serialization
- **Gradio** — web interface

## How It Works

1. The user types a question into the Gradio interface.
2. `is_meaningful_word()` checks the input against a combined English + domain-specific word set.
3. If valid, `CountVectorizer` transforms the text and the trained model predicts a class.
4. The `LabelEncoder` maps the predicted class back to a readable answer.

## Project Structure

```
├── best_model.joblib         # Trained classification model
├── count_vectorizer.joblib   # Fitted CountVectorizer
├── label_encoder.joblib      # Fitted LabelEncoder
├── chatbot.py                # Core chatbot logic
└── gui.py                    # Gradio interface
```

## Running the Project

```bash
pip install scikit-learn nltk gradio joblib
python gui.py
```

The Gradio interface will launch in your browser. Type `exit` to end a console session, or interact directly through the web UI.

## Note

This project was developed during an AI internship at ICTHub.
