# Forest-type-classification

This is a multiclass classification task to predict the typologies of different forest sites in Czechia based on various soil properties, using statistical machine learning tools in Scikit-learn. The dataset used was originally uploaded on the Zenodo website by Hellebrandová (2023). It was the outcome of a project, carried out by a group of researchers in the Research Institute of Forestry and Hunting founded by the Ministry of Agriculture in the Czech Republic, with a view to developing and verifying spatial models of various forest soil properties in this country (Šrámek et al. 2020, p.7). As an aggregate product accumulated from multiple data sources with a certain degree of homogeneity, the dataset contains a total of 17187 records, each of which represents a soil sample, and 47 variables, which provide relevant information, including their sampling sites, vegetation forms, the contents of some chemical substances, and the measurement methods.

The project was not focused on building prediction models. Rather, the emphasis was put on data preprocessing and model selection with a wide range of techniques, as acquired from what I have learnt at university. The data-preprocessing steps used in the project are listed below:
- Imputing missing values with different techniques for quantitative and categorical features
- Removing predictors with zero variance and low variance
- Removing strongly correlated quantitative predictors
- Removing strongly correlated categorical predictors
- Lumping infrequently occurring classes in categorical predictors
- Oversampling the training data on the target variable
- Performing a Yeo-Johnson transformation with standardisation on quantitative predictors
- Converting categorical features to dummy variables

Also, I attempted to adhere to the standard machine learning workflow, from data cleaning and exploratory analysis to data preprocessing, model selection, and final evaluation of the chosen model. In particular, by using pipelines, the validation data and testing data were kept completely independent of any model-training and model-comparison procedures, even all data-preprocessing steps were only performed on the training splits in cross-validation for hyperparameter tuning and for model selection. The evaluation metric chosen was ROC-AUC.

The results showed that the Random Forest model returned the best performances, not only with the highest mean validation ROC-AUC score in cross-validation but also the ROC-AUC scores in each cross-validation run as well as in each class of the target variable. In the final evaluation stage, when the Random Forest model was experimented on the testing dataset, it returned impressive overall scores of precision, recall and accuracy of all nearly 90%. However, a deeper investigation revealed that for the 'Mixed' forest type, the model might perform worse than expectation, so further improvements could be made on this class.

In addition, the importance that each feature had on the model-training was also assessed with both permutation-based and impurity-based importance scores. This feature importance analysis demonstrated that the proportion of vegation types 1, 3, and 6 have the greatest impacts on the typology of a forest site, which suggest that humanity can have a direct influence on forest typologies by implementing different vegetation structures.
