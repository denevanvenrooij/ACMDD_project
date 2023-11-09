# ACMDD_project
Our ACMDD project consisted of an investigation into finding a novel antagonist for the A3 receptor, using a QSAR machine-learning model for classification, virtual screening, and docking.

At first, we chose the A2a receptor, but after some discussion, we selected the A3 receptor. This receptor is found in the lungs, liver, heart, kidneys, and other tissues, and has been presented as a potential target for neurodegenerative diseases, asthma, cardiac ischemia, and various cancers. Yet, only a handful of antagonists for A3 have been published. Therefore it is important to continue to study the receptor and try to find novel candidate antagonists. 

First, we fetched compound data from ChEMBL selected for Ki values, afterwards, we also fetched a list of compounds based on ChEMBL values using Papyrus. The datasets contained 3944 and 3243 unique compounds, respectively. These datasets were not filtered. The pChEMBL dataset was selected because it comprised more relevant values for bioactivity. The pKi dataset was also used for model evaluation, though.

Using this dataset we created multiple QSAR models using machine learning algorithms and the pChEMBL dataset: Random Forests, Support Vector Machines, and Neural Networks algorithms were used. The RF algorithm produced the largest AUC and was therefore selected for creating the model for the purpose of virtual screening. Cross-validation was not performed during the development of the model used for virtual screening.

The list of SMILES used for virtual screening was compiled by Amine. This list is called smiles_selection.

Virtual screening was performed with a Random Forest QSAR classification model. The results of runs were used to tune the model into producing a short list of compounds to make a selection for docking. Run 10 and run 18 were used for this, and can be found in the results folder. A selection of candidate compounds was constructed manually since no selection for antagonists or agonists had been made previously. The goal was to find an antagonist for A3, so any ligands that were produced by way of virtual screening that contained a ribose group were excluded since these are known to be present in agonists. The list is called ligand_selection.

Docking was performed by Nicky. The structure of the A3 receptor was experimentally determined using AlphaFold, as the crystal structure is not yet known. The original selection for virtual screening contained compounds that were in the training data, and some duplicates. These had to be removed after being classified as potential candidates by the model. This list of compounds selected for docking resulted in 7 ligands, only 4 of which were antagonists. This list is called ligands_selection. The ligands were docked in all predicted conformations using AutoDock Vina (Code available on GitHub). Ligands 1-4 were docked in the predicted inactive structure of A3, as they are predicted to be antagonists. Although we are looking for antagonists, we also docked the potential agonist, as they showed promising results from the QSAR analysis. Therefore, ligands 5-7 were docked in the active predicted form of A3. They contain a ribose group and are therefore believed to be agonists. In conclusion, for the antagonists, ligand 3 conformer 1 shows the best results (lowest negative docking score and highest pCHEMBL value). For the agonists, ligand 6 is expected to be the best candidate, because ligand 5 shows unreliable results. However, AutoDock predicted negative pCHEMBL values, which we know is not possible. Therefore, the question is raised whether these scores and the docking method itself could be trusted. A detailed look into the results can be found in 'Overview A3 candidates.xlsx'.




















