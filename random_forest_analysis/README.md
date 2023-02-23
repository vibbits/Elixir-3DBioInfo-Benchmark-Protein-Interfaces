Files **rf_topkXX.out**: those files correspond to the probability for each entry to be a physiological dimer calculated using the random forest method on the features used by the teams (221 features in total). They contain three columns: 
- *entry id*: the pdb id of the entry.
- *label*: indicates if an entry is a physiological dimer (=1) or not (=0).
- *probability*: denotes the probability calculated with the random forest that the entry is a physiological dimer. 

There are 5 different files, using the top 5, 10, 20, 50 and 221 features of the dataset.

Files **correlations-topXX.csv**: these files show the correlation between the top 20, top 50 and top 221 features selected during the random forest analysis.
