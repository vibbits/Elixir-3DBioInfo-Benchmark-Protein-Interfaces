<h2>Random forest classification</h2>

To investigate how effective the 221 unique raw features computed for the dimers of our benchmark dataset are in discriminating between the two categories of dimer,  we used a RF classifier [1], as implemented in the Scikit-learn package [2]. The classifier, subjected to a leave-one-out cross-validation, assigned to each homodimer an average probability to carry out a given label (physiological, or non-physiological) that was used to compute the ROC curve. RFs are protected against overfitting, since the computed probabilities are averaged over many random decision-trees, thereby reducing variance without increasing bias. 

<br>

<h2>Content of the folder</h2>

Files **rf_topkXX.out**: those files correspond to the probability for each entry to be a physiological dimer calculated using the random forest method on the features used by the teams (221 features in total). They contain three columns: 
- *entry id*: the pdb id of the entry.
- *label*: indicates if an entry is a physiological dimer (=1) or not (=0).
- *probability*: denotes the probability calculated with the random forest that the entry is a physiological dimer. 

There are 5 different files, using the top 5, 10, 20, 50 and 221 features of the dataset.

Files **correlations-topXX.csv**: these files show the correlation between the top 20, top 50 and top 221 features selected during the random forest analysis.

<br>

<h2>References</h2>

[1]	Hastie, T., Tibshirani, R., Friedman, J., The Elements of Statistical Learning, Springer New York, n.d.

[2]	Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., et al., Scikit-learn: Machine Learning in Python. arXiv [cs.LG] 2012, 2825–2830.
