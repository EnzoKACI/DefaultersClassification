# IntroNotebooktoML

Intro notebook to Machine Learning (loan defaulters issue)

This notebook served as the final project of an introductory class in Artificial Intelligence applied to Business.

We tried to tackle the issue proposed on the Kaggle dataset linked here https://www.kaggle.com/datasets/yasserh/loan-default-dataset .

We describe the task as predicting the y label: default using the x features processed from the 34 columns available in the dataset.
The prediction will be made using classification algorithms such as Logistic Regression and (weighted) SVM.

The main problem we had to tackle was imbalanced characteristics of our datasets as there are fewer defaulters (1 class) than non-defaulters (0 class).
Thus, we used two methods to assess the best way to tackle this imbalanced dataset issue.

This notebook's purpose is to show the use of basic tools in Machine Learning: scikit-learn library, model evaluation using ROC/AUC curves, accuracy/recall/precision and F1-score metrics.

Here is a small glance at the conclusion from the notebook:

We found out that the most influential variable is the "south" category from the "Region" feature according to the coefficients so it means that changing this variable might have high impact on the SVM model's decision. We believe it is not very satisfactory for explanation, because it could mean there is another bias in the data: maybe bankers in the south accept more loans and get more defaulted. What we observe in the original dataset is that the "south" category is quite following the distribution of the dataset but is overrepresented: half of positive and half of negative values are from the south while other categories might be scattered for positive and negative status, so south has a high impact on the final decision.

So we can say our dataset is corrupted by its origin: it might have been gathered by a southern agency which mostly got local data and gathered less of national information.

If we drop the "region" feature then we might get a "region agnostic" model and that would be fine in term of explanatory analysis but actually we would also loose a lot of accuracy. Another way to address this issue would be to build a specific model for the south data, as it would be less corrupted but more specialized. Thus, we believe it is not an interesting study for a bank's scale and a software solution using Machine Learning and big data would be too expensive to put in place, maintain and update in a local area. Plus, for corporate meaning, having only one part of their agencies using these models could create even more bias: if they have a better prediction on who is more likely to default, they might have less and less data on defaulting clients in a particular region (which is the initial goal of the bank) though it would make this dataset impossible to gather with a nationally built one to be able to make national predictions, thus it is better to wait to be able to use a national dataset for nationwide predictions.
