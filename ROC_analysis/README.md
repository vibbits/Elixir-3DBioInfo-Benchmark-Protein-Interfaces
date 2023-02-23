**classification_entries_allmethods.xlsx**: contains information concerning the classification of each entries of the benchmark by the three classifiers developped in this work: consensus score, random forest and dockQ score applied on AlphaFold models.

It contains two sheets, with the following columns:

**Sheet 1**: classification_entries_allmethods

- *pdb.id*: pdb identifier of the structure, followed by “_X” for the complexes from the QSalign dataset, with X denoting the number of the biological assembly.
- *physio*: 1 if the dimer is a physiological contact, 0 otherwise.
- *consensus.score*: classification according to the consensus score. TRUE if correctly classified, FALSE otherwise.
- *random.forest*: classification according to the random forest score. TRUE if correctly classified, FALSE otherwise.
- *AlphaFold2*: classification according to the AlphaFold score. TRUE if correctly classified, FALSE otherwise.
- *misclassified*: number of methods misclassifying the entry.

**Sheet 2**: misclassified_entries_analysis

The subset of entries misclassified by 2 or more methods. Columns 1-6 contain the same information as in Sheet 1, Column 7 and 8 are organized as follow:
- *reassignment*: lists misclassified entries that are likely misassigned  (‘1’ red), and misclassified entries that are likely not misassigned ( ‘0’ blue). 
- *protCID*: Comments supporting the re-assignments on the basis of ProtCID or ProtCAD.
