# Elixir-3DBioInfo-Benchmark-Protein-Interfaces

The content is provided under the license https://creativecommons.org/licenses/by/4.0/.

**Introduction**

The benchmark dataset set itself contains a few hundred homodimers that are predicted to be “physiological or non-physiological” (folder **benchmark**). Those predictions are based on the methods from the groups of Dunbrack and Levy. These methods rely on the conservation of interaction geometry (i.e., not of the residues at the interface, but of the structure of the interface), across crystal forms (Roland’s method), across homologs (QSalign), or across methods (QSbio, itself integrating PISA + EPPIC). 

The key points of this dataset are: 
 
(i) it is relatively large

(ii) it is accurate

(iii) it is expected to yield difficult predictions because the distribution of interface sizes is comparable among physiological and non-physiological complexes.

13 groups applied different scores to discriminate between the physiological and non-physiological interfaces of this benchmark.


**Content of the repository**

This repository contains 14 folders. 13 folders correspond to the results of each participants, one folder corresponds to the benchmark set of protein structures.

The folder **benchmark** is organized as follow:

   - **01_PDB_legacy_3dcomplex** contains PDB format edited by 3Dcomplex for QSalign structures, PDB format generated by ProtCID for other structures.

   - **02_PDB_legacy_original** contains unedited PDB format for QSalign structures, PDB format generated by ProtCID for other structures.

   - **03_PDB_mmcif** contains unedited CIF format for QSalign structures, CIF format generated by ProtCID for other structures.

 Each folder consists of 1677 entries (note: the CIF folder contains 1673 entries because the same structure can generate multiple interfaces depending on symmetry operations).

 Of the 1677 entries :
 
     • 700 were selected based on ProtCID
     
     • 977 were selected based on QSalign
     
     
     
These folders of the participants are organized as follow:

  - **results-raw** contains a csv file with the different raw scores of the participants applied on the benchmark.

  - **results-classifier** contains a csv file with the different integrated scores of the participants applied on the benchmark.
  
  Rk: not all groups applied integrated scores on the benchmark, therefore the folder results-classifier can be absent for some groups.

Each folder also contains a documentation made by the participants describing the raw and integrated scores they applied on the benchmark.

