# Explainable deep-learning detection of microplastic fibers

This repository contains data and scripts required for reproducing the results presented in the paper **Explainable deep-learning detection of microplastic fibers via polarization-resolved holographic microscopy** by Jan Appel, Marika Valentino, Lisa Miccio, Vittorio Bianco, Raffaella Mossotti, Giulia Dalla Fontana, Miroslav Ježek, Pietro Ferraro, and Jaromír Běhal. The paper is available on arXiv: https://arxiv.org/pdf/2601.15769


## List of code files in this repository:
### Data_preprocesing.ipynb
load input data (see data folder), split input data to train and validation data, normalization of data, save train and validation data, save scaler used for normalization.
### Other_machine_learning_models.ipynb
load train and validation data, classification without feature selection, classification with feature selection (mRMR)
### Train_DNN.ipynb
load train and validation data, design of deep neural network, iterative training network, save best models (see data folder)
### Evaluation_model_confusion_matrix.ipynb
load train and validation data, load best model, evaluation confusion matrix, precision, recall and f1-score for validation data and whole dataset.
### SHAP.ipynb
load train and validation data, calculate SHAP FI values, create SHAP FI plots

### data folder:
- best_model_v2_#.keras:	28 best models
- feat_mat.mat:	input data
- x_train_Znorm.csv, x_val_Znorm.csv, y_train.npy, y_val.npy: split and normalization data for train of DNN, Other_machine_learning_models respectively (see Data_preprocesing.ipynb)
- scaler_Ztransform.save: scaler used for normalization (see Data_preprocesing.ipynb)
- shap_array.npy:	calculate SHAP FI values (see SHAP.ipynb)
- confusion_matrix_total.pdf, confusion_matrix_validation.pdf, plot_shap_ind_summ.pdf, plot_shap_summ_classes.pdf: pictures with main results results

## Pip request
piprequest:

- Data_preprocesing.ipynb:
joblib : 1.5.3
keras  : 3.13.1
numpy  : 2.3.5
pandas : 2.3.3
scipy  : 1.17.0
sklearn: 1.8.0

- Other_machine_learning_models.ipynb:
matplotlib: 3.10.8
mrmr      : 0.2.8
numpy     : 2.3.5
pandas    : 2.3.3
sklearn   : 1.8.0
tensorflow: 2.20.0

- Train_DNN.ipynb:
keras : 3.13.1
numpy : 2.3.5
pandas: 2.3.3

- Evaluation_model_confusion_matrix.ipynb:
keras     : 3.13.1
matplotlib: 3.10.8
numpy     : 2.3.5
pandas    : 2.3.3
seaborn   : 0.13.2
sklearn   : 1.8.0
tabulate  : 0.9.0
tensorflow: 2.20.0

- SHAP.ipynb:
keras : 3.12.0
numpy : 1.26.4
pandas: 2.3.3
shap  : 0.49.1
