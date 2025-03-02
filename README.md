# Text Summarization NLP Project

## Project Overview
This project focuses on **text summarization** using **Natural Language Processing (NLP)** techniques. It leverages **Google Pegasus** for abstractive text summarization and follows a modular workflow to ensure smooth execution, training, evaluation, and deployment of the model.

## Workflows
The project follows a structured workflow to ensure reproducibility and maintainability:

1. **Update `config.yaml`** - Define high-level configurations such as model checkpoints and data sources.
2. **Update `params.yaml`** - Specify hyperparameters for training and evaluation.
3. **Update entity** - Define and manage structured data entities used in the pipeline.
4. **Update the configuration manager in `src/config`** - Manage the configurations dynamically.
5. **Update the components** - Implement core functionalities for data ingestion, transformation, training, and evaluation.
6. **Update the pipeline** - Connect various components into a streamlined workflow.
7. **Update `main.py`** - Implement the execution pipeline.
8. **Update `app.py`** - Deploy the model using **FastAPI** for real-time inference.

## Requirements
The project requires the following dependencies:

```plaintext
transformers
keras==2.15.0
transformers[sentencepiece]
datasets
sacrebleu
rouge_score
py7zr
pandas
nltk
tqdm
PyYAML
matplotlib
torch
notebook
boto3
mypy-boto3-s3
python-box
ensure
fastapi
uvicorn
Jinja2
evaluate
-e .
```

## Data Processing
### Data Ingestion
- The dataset is sourced from: [Summarizer Data](https://github.com/entbappy/Branching-tutorial/raw/master/summarizer-data.zip).
- Data is downloaded, extracted, and stored in `artifacts/data_ingestion/`.

### Data Transformation
- Tokenization is performed using `google/pegasus-cnn_dailymail`.
- Data is processed and prepared for model training.

## Model Training
- The model is trained using **Google Pegasus**.
- Training data is stored in `artifacts/model_trainer/`.
- The trained model is saved and used for inference.

## Model Evaluation
- The evaluation process calculates metrics such as **ROUGE Score** and **BLEU Score**.
- Metrics are logged in `artifacts/model_evaluation/metrics.csv`.

## Deployment
The trained model is deployed using **FastAPI** with the following endpoints:

- **`/train`** - Triggers model training.
- **`/predict`** - Generates a summary for the provided text input.
- **`/docs`** - Provides an interactive Swagger UI for testing the API.

## Example Summarization

**Reference Summary:**
> Hannah needs Betty's number, but Amanda doesn't have it. She needs to contact Larry.

**Model Summary:**
> Amanda can't find Betty's number. Larry called Betty last time they were at the park together. Hannah wants Amanda to text Larry. Amanda will text Larry.

## Running the Application
To run the FastAPI server:
```bash
uvicorn app:app --host 0.0.0.0 --port 8080
```

## Conclusion
This project demonstrates the application of **deep learning-based text summarization** using **Google Pegasus**. It follows a structured pipeline for data processing, model training, evaluation, and deployment via FastAPI.

