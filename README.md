
# Pokémon Battle Outcome Prediction

**Foundations of Data Science — Sapienza University of Rome**  
Academic Year 2026/2027

## Project Overview

This project addresses a supervised binary classification task in the Pokémon Battle Prediction Kaggle competition.

The objective is to predict the final outcome of Generation 2 OU Pokémon battles using information available from the first 30 observed turns.

The target variable is `player_won`:
- `1`: Player 1 wins.
- `0`: Player 1 loses.

## Dataset

The competition provides:
- `train.jsonl`: 10,000 labeled battles.
- `test.jsonl`: 5,000 unlabeled battles.
- `sample_submission.csv`: official submission format.

The dataset contains team characteristics, Pokémon statistics, observed battle states, and move information.

Only competition-provided data is used for model training and prediction.

## Feature Engineering

Numerical features are extracted from team statistics and observed battle states.

The baseline uses 15 numerical features, while the advanced models use 23 numerical features.

Additional sparse features represent observed Pokémon and moves.

Feature transformations are fitted exclusively on training data within each cross-validation fold to prevent validation data leakage.

## Machine Learning Models

Three prediction approaches are evaluated.

### 1. Logistic Regression Baseline

A Logistic Regression classifier is trained using 15 numerical features with standard scaling.

### 2. LightGBM

A gradient boosting classifier combines 23 numerical features with additional indicators derived from observed moves and Pokémon.

### 3. Ensemble Model

The ensemble combines LightGBM and an advanced Logistic Regression classifier.

Final probabilities are computed using equal weights for the two models.

## Validation Strategy

Model performance is evaluated using Stratified 5-Fold Cross-Validation with random seed 42.

Accuracy is used as the primary evaluation metric.

The same cross-validation splits are used for all three approaches.

## Cross-Validation Results

| Model | Mean Accuracy |
|---|---:|
| Logistic Regression Baseline | 65.85% |
| LightGBM | 68.05% |
| Ensemble | 68.22% |

These results refer to local cross-validation and not to the Kaggle private leaderboard.

## Reproducibility

The project code is contained in `pokemon_models_fixed.ipynb`.

The final Kaggle notebook clones this GitHub repository, executes the model notebook using the official competition dataset, and reproduces the three prediction files.

All model implementations, feature transformations, and validation procedures are included in the notebook.

## Generated Submissions

The execution generates:

- `submission_baseline.csv`
- `submission_lightgbm.csv`
- `submission_ensemble.csv`

Each submission contains 5,000 binary predictions aligned with the official sample submission by `battle_id`.

## Limitations

Predictions are based on incomplete battle observations. Information beyond the first 30 turns is unavailable.

The opponent's team is partially unknown, and some features rely on approximations.

The ensemble achieves the highest mean cross-validation accuracy, although its improvement over LightGBM is relatively small.
