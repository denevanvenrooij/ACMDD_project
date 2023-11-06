# ACMDD_project
Our ACMDD project consisted of an investigation into finding a novel antagonist for the A3 receptor, using a QSAR machine learning model for classification, virtual screening, and docking.

We selected the A3 receptor because ..

First, we fetched compound data from ChEMBL selected for Ki values, afterwards, we also fetched a list of compounds based on ChEMBL values using Papyrus. The datasets contained 3944 and 3243 unique compounds, respectively. These datasets were not filtered. The pChEMBL dataset was selected because it comprised more relevant values for bioactivity. The pKi dataset was also used for model evaluation, though.

Using this dataset we created multiple QSAR models using machine learning algorithms and the pChEMBL dataset: Random Forests, Support Vector Machines, and Neural Networks algorithms were used. The RF algorithm produced the largest AUC and was therefore selected for creating the model for the purpose of virtual screening. Cross-validation was not performed during the development of the model used for virtual screening.

The list of SMILES used for virtual screening was compiled by Amine

Virtual screening was performed with a Random Forest QSAR classification model
