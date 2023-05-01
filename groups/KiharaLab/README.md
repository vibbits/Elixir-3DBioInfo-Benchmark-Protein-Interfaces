**Daisuke Kihara Lab.** Purdue University, USA (dkihara@purdue.edu)

Classifier description

Protein Interaction Combined Score of different labs

Xiao Wang<sup>2</sup>, Genki Terashi<sup>1</sup>, Daipayan Sarkar<sup>1</sup>, Charles Christoffer<sup>2</sup>, Tunde Aderinwale<sup>2</sup>, Jacob Verburgt<sup>1</sup>, & Daisuke Kihara<sup>1,2</sup>

1.	Department of Biological Sciences, Purdue University, West Lafayette, IN 47907, USA

2.	Department of Computer Science, Purdue University, West Lafayette, IN 47907, USA

Email: dkihara@purdue.edu

To benefit from different methods, we designed an overall score (OScore2) which is a simple linear regression of Phase1 raw scores from different labs. Our methods are based on the "V1+V2+V3 dataset" and 1677 proteins are studied from  07/20/2021 downloaded version.To get OScore2, we did the following steps.

1) Score Correlation Analysis: For different feature/raw scores from different labs (including Kiharalab, BolognaBiocomputingGroup, BonvinLab, FurmanLab, LyonMOBIGroup, Oliva_group and VenclovasLab), we analyzed their correlation and saved them into "correlation_analyze.csv". The correlation of any two features/scores can be easily checked in this table. In total, we collected 122 scores/features from different groups.

2) Group Independent Features/Scores: Based on the correlation analysis before, we used 0.8 as a threshold to group methods/features with correlation>=0.8 or correlation<=-0.8 together into a group. Then we grouped 122 scores/features into 46 relative independent scores/features, which was saved in 'group_correlation0.8.txt' file. In the next step, we used the 1st score/feature of each group as our final feature input for OScore2.

3) 4-Fold testing. We randomly divided the dataset into 4 folds, where 3 fold served as training and 1 fold used for testing. This process was repeated 4 times and we only reported the performance on the testing fold. We sampled from the 3-fold training data to make a balanced dataset, then a Ridge regression classifier was trained using the sampled balanced data. Then we applied the classifier on the testing fold. Here we also tried regular logistic regression and shallow neural network but reporting here just ridge regression results, because it performed the best and stable. All the fold outputs were saved in "final_output.txt" and the relative accuracy and confusion matrix results of each testing fold were saved in "final_record.txt". Meanwhile, the overall accuracy and confusion matrix combining all 4 testing folds were also saved in "final_output.txt". 

4) Confidence score in "final_output.txt".  To measure the confidence of our prediction for different targets, we also reported the "confidence" score for each target, which denotes the distance to the hyperplane for classification. The larger distance suggested more confident compared to the smaller confidences values. For the negative predictions, please consider its absolute value for the distance measurement.
-------
Feature description:
Protein interaction scores of the Version 3 dataset
Genki Terashi1, Xiao Wang2, Daipayan Sarkar1, Charles Christoffer2, Tunde Aderinwale2, Jacob Verburgt1, & Daisuke Kihara1,2
1.  Department of Biological Sciences, Purdue University, West Lafayette, IN 47907, USA
2.  Department of Computer Science, Purdue University, West Lafayette, IN 47907, USA
Email: dkihara@purdue.edu
We computed 8 different scores that evaluate interaction of two chains. Reference of the scores are followings:
DFIRE : Zhou, Hongyi, and Jeffrey Skolnick. "GOAP: a generalized orientation-dependent, all-atom statistical potential for protein structure prediction." Biophysical journal 101.8 (2011): 2043-2052.

GOAP :  Zhou, Hongyi, and Jeffrey Skolnick. "GOAP: a generalized orientation-dependent, all-atom statistical potential for protein structure prediction." Biophysical journal 101.8 (2011): 2043-2052.

DOVE:  Wang, Xiao, Genki Terashi, Charles Christoffer, Mengmeng Zhu, and Daisuke Kihara. "Protein docking model evaluation by 3D deep convolutional neural networks." Bioinformatics 36.7 (2020): 2113-2118.

GNN-DOVE : Wang, Xiao, Sean T. Flannery, and Daisuke Kihara. "Protein Docking Model Evaluation by Graph Neural Networks." bioRxiv (2020).

ITScore : Huang, Sheng‐You, and Xiaoqin Zou. "An iterative knowledge‐based scoring function for protein–protein recognition." Proteins: Structure, Function, and Bioinformatics 72.2 (2008): 557-579.

PhysicsScore: physics-based score in Multi-LZerd. Esquivel‐Rodríguez, Juan, Yifeng David Yang, and Daisuke Kihara. "Multi‐LZerD: multiple protein docking for asymmetric complexes." Proteins: Structure, Function, and Bioinformatics 80.7 (2012): 1818-1833.

RosettaInterfaceEnergy : Interface Enegy of Rosetta Energy Function (ref2015). Marze, Nicholas A., et al. "Efficient flexible backbone protein–protein docking for challenging targets." Bioinformatics 34.20 (2018): 3461-3469.

VoroMQA : Olechnovič, Kliment, and Česlovas Venclovas. "VoroMQA: Assessment of protein structure quality using interatomic contact areas." Proteins: Structure, Function, and Bioinformatics 85.6 (2017): 1131-1145.
