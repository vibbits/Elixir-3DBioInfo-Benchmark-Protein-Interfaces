# Elixir-3DBioInfo-Benchmark-Protein-Interfaces

The content is provided under the license https://creativecommons.org/licenses/by/4.0/.



This repository contains 14 folders. 13 folders correspond to the results of each participants, one folder corresponds to the benchmark set of protein structures. 



- These folders of the participants are organized as follow:

  **results-raw**

  **results-classifier**



- The folder **benchmark** is organized as follow:

Folder content:

  **01_PDB_legacy_3dcomplex** contains PDB format edited by 3Dcomplex for QSalign structures, PDB format generated by ProtCID for other structures.
  
  **02_PDB_legacy_original** contains unedited PDB format for QSalign structures, PDB format generated by ProtCID for other structures.
  
  **03_PDB_mmcif** contains unedited CIF format for QSalign structures, CIF format generated by ProtCID for other structures.

Each folder consists of 1677 entries (note: the CIF folder contains 1673 entries because the same structure can generate multiple interfaces depending on symmetry operations).

Of the 1677 entries :
    • 700 were selected based on ProtCID
    • 977 were selected based on QSalign
