# Elixir-3DBioInfo-Benchmark-Protein-Interfaces

The content is provided under the license https://creativecommons.org/licenses/by/4.0/.

<br>

For more details about the work presented here, please refer to the preprint version of the article:
https://doi.org/10.22541/au.167569565.51141128/v1

<br>


<h2>Introduction</h2>

Reliably scoring and ranking candidate models of protein complexes and assigning their oligomeric state from the structure of the crystal lattice represent outstanding challenges. A community-wide effort was launched to tackle these challenges. The latest resources on protein complexes and interfaces were exploited to derive a benchmark dataset consisting of 1677 homodimer protein crystal structures, including a balanced mix of physiological and non-physiological complexes. The non-physiological complexes in the benchmark were selected to bury a similar or larger interface area than their physiological counterparts, making it more difficult for scoring functions to differentiate between them. Next, 252 functions for scoring protein-protein interfaces previously developed by 13 groups were collected and evaluated for their ability to discriminate between physiological and non-physiological complexes. A simple consensus score generated using the best performing score of each of the 13 groups, and a cross-validated Random Forest (RF) classifier were created. Both approaches showed excellent performance, with an area under the Receiver Operating Characteristic (ROC) curve of 0.93 and 0.94 respectively, outperforming individual scores developed by different groups. Additionally, AlphaFold2 [1] engines recalled the physiological dimers with significantly higher accuracy than the non-physiological set, lending support to the reliability of our benchmark dataset annotations. Optimizing the combined power of interface scoring functions and evaluating it on challenging benchmark datasets appears to be a promising strategy.

<br>

<h2>The benchmark</h2>

The benchmark dataset set contains 1677 homodimers that are predicted to be physiological or non-physiological (folder **benchmark**). Those predictions are based on the methods from the groups of Roland Dunbrack and Emmanuel Levy. These methods rely on the conservation of interaction geometry (i.e., not of the residues at the interface, but of the structure of the interface), across crystal forms (protCID [2]), across homologs (QSalign [3]), or across methods (QSbio, itself integrating PISA + EPPIC). Of the 1677 entries of the benchmark, 977 were selected based on QSalign and 700 were selected based on ProtCID.

The benchmark is composed of 836 physiological homodimers and 841 non-physiological ones.

The key points of this dataset are: 
 
(i) it is relatively large

(ii) it is accurate

(iii) it is expected to yield difficult predictions because the distribution of interface sizes is comparable among physiological and non-physiological complexes.

<br>

<h2>Content of the repository</h2>

This repository contains 17 folders. 13 folders correspond to the results of each participants, one folder corresponds to the benchmark set of protein structures, one to the AlphaFold models generated during the study, one to the random forest analysis and one to the ROC analysis.



<h3>benchmark</h3> 

Contains the pdb and mmcif files of the benchmark:

- **benchmark_pdb_format** contains unedited PDB format for QSalign structures, PDB format generated by ProtCID for other structures.

- **benchmark_mmcif_format** contains unedited CIF format for QSalign structures, CIF format generated by ProtCID for other structures.

Each folder consists of 1677 entries (note: the CIF folder contains 1673 entries because the same structure can generate multiple interfaces depending on symmetry operations).



<h3>AlphaFold_models</h3>

Contain the models computed by AlphaFold-multimer. It also contains a csv files recapitulating the dockQ score of each AlphaFold model. Please note that the folder contains only one AlphaFold model per entry, the one with the best DockQ score.



<h3>Random_Forest_analysis</h3>

Contains files from the random forest analysis:

Files **rf_topkXX.out**: those files correspond to the probability for each entry to be a physiological dimer calculated using the random forest method on the features used by the teams (221 features in total). They contain three columns: 
- *entry id*: the pdb id of the entry.
- *label*: indicates if an entry is a physiological dimer (=1) or not (=0).
- *probability*: denotes the probability calculated with the random forest that the entry is a physiological dimer. 

There are 5 different files, using the top 5, 10, 20, 50 and 221 features of the dataset.

Files **correlations-topXX.csv**: these files show the correlation between the top 20, top 50 and top 221 features selected during the random forest analysis.



<h3>ROC_analysis</h3>

Contains all the files related to the ROC analysis.     


<h3>groups</h3>

Contains the folders of all the participating groups, as well as the results from AlphaFold calculations.

The folders of the participants are organized as follow:

  - **results-raw** contains a csv file with the different raw scores of the participants applied on the benchmark.

  - **results-classifier** contains a csv file with the different integrated scores of the participants applied on the benchmark.
  
  Remark: not all groups applied integrated scores on the benchmark, therefore the folder results-classifier can be absent for some groups.

Each folder also contains a documentation made by the participants describing the raw and integrated scores they applied on the benchmark.

<br>

<h2>References</h2>

[1]	Jumper, J., Evans, R., Pritzel, A., Green, T., et al., Highly accurate protein structure prediction with AlphaFold. Nature 2021, 596, 583–589.

[2] Xu, Q., Dunbrack, R.L., Jr, ProtCID: a data resource for structural information on protein interactions. Nat. Commun. 2020, 11, 711.

[3] Dey, S., Ritchie, D.W., Levy, E.D., PDB-wide identification of biological assemblies from conserved quaternary structure geometry. Nat. Methods 2018, 15, 67–72.


