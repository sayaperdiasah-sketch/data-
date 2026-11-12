ICBHI LUNG SOUND CLASSIFICATION — RESULT PACKAGE
==================================================
Generated: 2026-11-12T02:30:23.824915

Dataset     : ICBHI 2017 Respiratory Sound Database
              920 wav files, 126 patients, 7 classes (Asthma+LRTI merged -> Other)
Validation  : Stratified Group K-Fold (K=5), groups=patient_id
Models      : CatBoost, LightGBM, Logistic Regression, Random Forest
Features    : MFCC (52) + ZCR/Spectral (15) + Annotation (15) = 82

FILE MANIFEST
-------------
results/
├── icbhi_metadata.csv                  (raw metadata)
├── icbhi_metadata_final.csv            (with diagnosis_7)
├── icbhi_annotation_features.csv       (B1 output)
├── icbhi_audio_features.csv            (B3 output)
├── icbhi_features_final.csv            (B4 merged)
├── folds_patientwise.json              (C1)
├── folds_random.json                   (C1b)
├── results_patientwise.csv             (D1)
├── preds_patientwise.csv               (D1 raw preds)
├── results_baseline.csv                (D2)
├── results_random.csv                  (D3)
├── results_ablation.csv                (E1)
├── feature_importance.csv              (E2)
├── table1_model_comparison.csv
├── table2_accuracy.csv
├── table3_ablation_fixed.csv
├── table4_time.csv
├── table5_per_class.csv
├── figures/
│   ├── fig1_model_comparison.png
│   ├── fig2_ablation.png
│   ├── fig3_cm_lightgbm.png
│   ├── fig4_cm_catboost.png
│   ├── fig5_feature_importance.png
│   ├── fig6_annotation_by_class.png
│   └── fig7_per_fold_stability.png
└── tables_png/
    ├── table1_model_comparison.png
    ├── table2_accuracy.png
    ├── table3_ablation.png
    ├── table4_time.png
    └── table5_per_class.png

KEY RESULTS
-----------
LightGBM macro-F1 (patient-wise): 0.442 ± 0.065   <-- BEST
CatBoost macro-F1 (patient-wise): 0.438 ± 0.120
Random split inflation (LightGBM): +0.109 (0.442 -> 0.551)
Ablation: Spectral only (15 feat) = 0.421, nearly matches All (82 feat) = 0.442
Feature importance: MFCC 68.2%, Spectral 22.5%, Annotation 9.3%
Fit time: LightGBM 7.9 s/fold, CatBoost 63.0 s/fold (8x faster)
