# Explainable deep-learning detection of microplastic fibers

This repository contains data and scripts required for reproducing the results presented in the paper **Explainable deep-learning detection of microplastic fibers via polarization-resolved holographic microscopy** by Jan Appel, Marika Valentino, Lisa Miccio, Vittorio Bianco, Raffaella Mossotti, Giulia Dalla Fontana, Miroslav Ježek, Pietro Ferraro, and Jaromír Běhal. The paper is available on arXiv: https://arxiv.org/pdf/2601.15769


## List of code files in this repository:
### Data_preprocesing.ipynb
Input data -feat_mat.mat- 8 statistical parameters and 9 polarization characteristics, representing a total of 72-dimensional feature vectors for each fiber. A total of 296 fibers: 47 MFFs of PA6, 51 of PET, 46 of PP, 47 of PA6.6, 47 of cotton, and 58 of wool.


For model training, the input data (see data folder - feat_mat.mat) is divided into training and validation sets. The data is then normalized by Z-transform and stored, along with the scaling factors. 
### Other_machine_learning_models.ipynb
To compare with other ML models, we trained several common ML classifiers on the loaded training and validation data. Training was performed both with and without feature selection (mRMR).
### Train_DNN.ipynb
load train and validation data, design of deep neural network, iterative training network, save best models (see data folder).
This code provides the design of our model - Full connected neural network with 72 neurons in input layer (corresponds to a 72-dimensional feature vector), 4 hidden layer with 256, 128, 64 and 32 nerurons and output layer with 6 neurons (corresponds to 6 classis of fiberes). All hidden layers in the network employ regularization techniques, specifically: batch normalization, dropout and additional regularization methods like L1,L2 regularization.
The model is trained on the loaded training and validation data. The best models are stored in the data folder.
### Evaluation_model_confusion_matrix.ipynb
To evaluate the trained model, we use the confusion matrix and the following metrics: precision, recall, and F1-score. The evaluation is performed on the validation dataset and on the entire dataset (i.e., validation and training data combined). 
### SHAP.ipynb
This file loads the saved training and validation data, which is then used to calculate the SHAP FI values. The results are presented using bar charts.

### data folder:
- feat_mat.mat:	input data - 8 statistical parameters and 9 polarization characteristics, representing a total of 72-dimensional feature vectors for each fiber. A total of 296 fibers: 47 MFFs of PA6, 51 of PET, 46 of PP, 47 of PA6.6, 47 of cotton, and 58 of wool
- x_train_Znorm.csv, x_val_Znorm.csv, y_train.npy, y_val.npy: split and normalization data for train of DNN, Other_machine_learning_models respectively (see Data_preprocesing.ipynb)
- scaler_Ztransform.save: scaler used for normalization (see Data_preprocesing.ipynb)
- best_model_v2_#.keras:	28 best models. Results of training our full-connected neural network (see Train_DNN.pynb)
- confusion_matrix_total.pdf, confusion_matrix_validation.pdf, plot_shap_ind_summ.pdf, plot_shap_summ_classes.pdf: pictures with main results results
- shap_array.npy:	calculate SHAP FI values (see SHAP.ipynb)

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
