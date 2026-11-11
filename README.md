# Pokémon Battle Prediction – FDS 2026/27

Repository del gruppo per la riproducibilità delle tre submission della competizione Kaggle.

## File

- `pokemon_models_fixed.ipynb`: codice dei modelli, validazione a 5 fold e generazione di `submission_baseline.csv`, `submission_lightgbm.csv` e `submission_ensemble.csv`.

## Esecuzione

1. Su Kaggle, collegare `train.jsonl`, `test.jsonl` e `sample_submission.csv` dalla competizione `fds-pokemon-battles-prediction-2026`.
2. Abilitare Internet nelle opzioni della sessione Kaggle, se consentito dalle regole della competizione.
3. Aprire il notebook finale del gruppo, che clona questo repository.
4. Eseguire il notebook completo e controllare i tre CSV in `/kaggle/working`.

## Metodologia sintetica

- Baseline ampliata: LogisticRegression con 15 feature numeriche.
- LightGBM: 23 feature numeriche, indicatori delle mosse e dei Pokémon osservati.
- Ensemble: media 50/50 delle probabilità di LightGBM e LogisticRegression avanzata.
- Validazione: StratifiedKFold, 5 fold, seed 42; accuracy.

Il modello usa solo i dati della competizione. Le osservazioni riguardano i primi 30 turni.

## Responsabilità e tracciabilità

Inserire qui i nomi dei membri del gruppo, l'elenco delle submission effettivamente selezionate entro il termine, la versione/commit del codice e una nota sull'eventuale assistenza AI nella preparazione tecnica/documentazione.
