Related to https://docs.google.com/document/d/11XxFre4Oqe3WOo_usQqjJo6Q4YLVTm6w/

---------------------------------
collected_models_top_DockQ.csv
---------------------------------
Extradata for collected_models_top_DockQ.tar.gz. Contains a row for each target (incl. 4 which could not be modelled in AF-Multimer and 2 which failed in DockQ) with following columns:
- pdb_id: identifies dimer target
- is_levy: distinguishes between QSalign set (True) and ProtCID set (False)
- is_physio: True/False if phys./non-phys.
- len_seq: length of sequence for dimer
- model_id: ID of selected model (matches AF-paramaters used for model with highest DockQ)
- DockQ: DockQ score for selected model
- iptm: ipTM value predicted by AF-Multimer for selected model
---------------------------------
collected_models_top_DockQ.tar.gz
---------------------------------
Contains unrelaxed AF-Multimer model with highest DockQ score for each dimer-target. Files are named as "[PDB-ID].pdb".

---------------------------------
QS_DQ_iptm_phys-scatter:
---------------------------------
Alternative to Figure AF2 in manuscript. Here data shown for 4175 models generated for 835 phys. dimers. Correlations (Pearson) are 0.856 between QS and DockQ, 0.784 between ipTM and DockQ and 0.735 between ipTM and QS. Plot is similar to Fig. 3 in https://doi.org/10.1101/2021.10.04.463034 (AF-Multimer paper) and shows ipTM does reasonable predictions for DockQ (and QS) but has plenty of cases where ipTM overestimates the actual accuracy.

---------------------------------
collected_models_max_iptm:
---------------------------------
Contains unrelaxed AF-Multimer model with highest ipTM value for each dimer-target. Files are named as "[PDB-ID].pdb".

---------------------------------
main_af_multimer_dimer_results:
---------------------------------
Main results from unrelaxed AF-Multimer models. Columns:
- pdb_id: identifies dimer target
- is_levy: distinguishes between QSalign set (True) and ProtCID set (False)
- is_physio: True/False if phys./non-phys.
- len_seq: length of sequence for dimer
- max_template_date: cutoff date for templates considered in modelling with AF-Multimer (set before release date of pdb_id)
- max_QSscore/max_DockQ: max. QS/DockQ-score between any of the 5 generated models and dimer target structure
- max_iptm: max. ipTM value predicted by AF-Multimer
- QSscore_max_iptm/DockQ_max_iptm: QS/DockQ-score between generated model with max. ipTM and dimer target structure (i.e. between model in collected_models_max_iptm and given structure of dimer target)

-------------------------------------
Checking high-ipTM non-phys. dimers:
-------------------------------------
- There are 248 models for non-phys. dimers with max_iptm > 0.7 (trivial to extract from main_af_multimer_dimer_results). Those would be worth checking...
- For 3 non-phys. targets (3dcj_1, 1s9p_5, 1y6h_3), the same sequence existed also as phys. target (3da8_1, 1s9p_1, 1vez_2). For all 3 cases, AF-Multimer produced a prediction with high ipTM (>0.85) and high similarity to the phys. structure (QS-score > 0.8).
- Could QSalign be used to check whether the models would be expected to be phys.? Tested with two high-ipTM examples with QSalign web interface:
-> 1fp3_2 (https://qsalign.weizmann.ac.il/qsab/detp/dcd7f1c62c4e76fbde5f709c1b7b2519) was predicted as "likely to be correct" even though it is almost identical to the provided dimer-structure which is labeled as non-phys
-> 8jdw_1 (https://qsalign.weizmann.ac.il/qsab/detp/6e5292627de210f9b7f6559b5432abcb) was "Inconclusive because no homologous structure was found"
=> it is unclear if this can be reliably automated to provide some meaningful output for the 248 high-ipTM cases
