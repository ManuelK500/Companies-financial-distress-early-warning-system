<p align="left">
  <img src="https://img.shields.io/badge/Python-3.10-blue" />
  <img src="https://img.shields.io/github/license/ManuelK500/Companies-financial-distress-early-warning-system" />
  <img src="https://img.shields.io/github/last-commit/ManuelK500/Companies-financial-distress-early-warning-system" />
  <img src="https://img.shields.io/github/repo-size/ManuelK500/Companies-financial-distress-early-warning-system" />
  <img src="https://img.shields.io/github/issues/ManuelK500/Companies-financial-distress-early-warning-system" />
  <img src="https://img.shields.io/badge/Code%20Style-Black-black" />
</p>


# Companies-financial-distress-early-warning-system
End-to-end financial distress early-warning system for U.S. companies (Python + ML + Power BI)
Financial Distress Early‑Warning System for U.S. Companies

A production‑minded analytics system that predicts the likelihood of financial distress for U.S. companies using financial statement data, machine learning, and explainable AI.
Designed for executive audiences, risk teams, and data‑driven decision‑makers.

Project Overview

Financial distress can lead to bankruptcy, layoffs, credit downgrades, and major operational disruptions.
This system provides an early‑warning signal by analyzing company‑level financials and generating a distress probability score supported by explainable AI.

The system includes:

    Automated data ingestion

    Feature engineering based on financial ratios

    Machine learning classification models

    SHAP explainability for transparency

    Model performance metrics

    Dashboard‑ready outputs

    A modular, production‑ready codebase

    Business Problem

Executives and risk analysts need to identify companies at risk of financial distress before the event occurs.
Traditional financial ratios alone are insufficient — they lack predictive power and interpretability.

This project solves that by combining:

    Historical financial data

    Machine learning models

    Explainable AI (SHAP)

    Automated pipelines

The result is a system that provides actionable, interpretable, and timely insights

Project Architecture

High‑level flow:

    Data Ingestion → Load raw financial data

    Feature Engineering → Create ratios, transformations, and derived metrics

    Model Training → Train ML models (Random Forest, XGBoost, etc.)

    Model Evaluation → ROC, confusion matrix, precision/recall

    Explainability → SHAP summary and force plots

    Outputs → Predictions, visuals, dashboard artifacts

financial-distress-early-warning-system/
│
├── data/
│   ├── raw/
│   ├── processed/
│   ├── external/
│   └── interim/
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_model_training.ipynb
│   └── 04_model_evaluation.ipynb
│
├── src/
│   ├── data_ingestion.py
│   ├── feature_engineering.py
│   ├── model_training.py
│   ├── model_evaluation.py
│   ├── shap_explainability.py
│   └── utils/
│       ├── io_utils.py
│       ├── preprocessing_utils.py
│       └── visualization_utils.py
│
├── automation/
│   ├── daily_update_pipeline.py
│   ├── scheduled_tasks.md
│   └── logs/
│
├── dashboards/
│   ├── powerbi/
│   └── streamlit/
│       ├── app.py
│       └── components/
│
├── visuals/
│
└── docs/
    ├── data_dictionary.md
    ├── model_card.md
    └── api_documentation.md


How to Run the Project

1. Clone the Repository
python -m venv venv
venv\Scripts\activate

2. Create and Activate a Virtual Environment
python -m venv venv
venv\Scripts\activate

3. Install Dependencies
pip install -r requirements.txt

4. Run the Pipeline
python src/data_ingestion.py
python src/feature_engineering.py
python src/model_training.py
python src/model_evaluation.py


Model Performance 

This section will include:

    Confusion matrix

    ROC curve

    Precision, recall, F1

    Feature importance

    SHAP summary plot


    Explainability (SHAP)

The system includes full SHAP explainability:

    Global feature importance

    Local explanations for individual companies

    Force plots

    Summary plots


    Dashboard Integration

The project includes scaffolding for:

    Power BI dashboard


These will visualize:

    Distress probability

    Key drivers

    Trends

    Company‑level insights

    Author

Emmanuel Ahiekpor
Senior Data Scientist & Business Analyst


Project Architecture

Architecture Diagram
```mermaid
flowchart TD

    %% Data Layer
    A[Raw Financial Data<br/>CSV, Excel, External Sources] --> B[Data Ingestion<br/>src/data_ingestion.py]

    %% Feature Engineering
    B --> C[Feature Engineering<br/>src/feature_engineering.py]

    %% Modeling
    C --> D[Model Training<br/>src/model_training.py]
    D --> E[Model Evaluation<br/>src/model_evaluation.py]

    %% Explainability
    D --> F[SHAP Explainability<br/>src/shap_explainability.py]

    %% Outputs
    E --> G[Model Outputs<br/>Predictions, Metrics]
    F --> H[Explainability Visuals<br/>SHAP Summary, Force Plots]

    %% Dashboards
    G --> I[Power BI Dashboard<br/>dashboards/powerbi]
    H --> I
    G --> J[Streamlit App<br/>dashboards/streamlit/app.py]
    H --> J

    %% Storage
    B --> K[Processed Data<br/>data/processed]
    C --> K
    D --> L[Models & Artifacts<br/>models/]
    E --> M[Visuals<br/>visuals/]
    F --> M

 
Layered Architecture Diagram
```mermaid
flowchart LR

    %% -------------------------
    %% Data Layer
    %% -------------------------
    subgraph Data_Layer [Data Layer]
        A[Raw Financial Data<br/>CSV, Excel, External Sources]
        B[Data Ingestion<br/>src/data_ingestion.py]
    end

    %% -------------------------
    %% Feature Engineering Layer
    %% -------------------------
    subgraph Feature_Layer [Feature Engineering Layer]
        C[Feature Engineering<br/>src/feature_engineering.py]
    end

    %% -------------------------
    %% Modeling Layer
    %% -------------------------
    subgraph Modeling_Layer [Modeling Layer]
        D[Model Training<br/>src/model_training.py]
        E[Model Evaluation<br/>src/model_evaluation.py]
    end

    %% -------------------------
    %% Explainability Layer
    %% -------------------------
    subgraph Explainability_Layer [Explainability Layer]
        F[SHAP Explainability<br/>src/shap_explainability.py]
    end

    %% -------------------------
    %% Output Layer
    %% -------------------------
    subgraph Output_Layer [Output Layer]
        G[Predictions & Metrics]
        H[Visuals<br/>visuals/]
        I[Models & Artifacts<br/>models/]
    end

    %% -------------------------
    %% Dashboard Layer
    %% -------------------------
    subgraph Dashboard_Layer [Dashboard Layer]
        J[Power BI Dashboard<br/>dashboards/powerbi]
        K[Streamlit App<br/>dashboards/streamlit/app.py]
    end

    %% -------------------------
    %% Flow Connections
    %% -------------------------
    A --> B --> C --> D --> E --> F
    D --> I
    E --> G --> J
    F --> H --> J
    G --> K
    H --> K
