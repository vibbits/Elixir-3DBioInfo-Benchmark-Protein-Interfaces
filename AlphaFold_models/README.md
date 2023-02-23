
<h3>collected_models_top_DockQ.csv<h3\>

Data file for collected_models_top_DockQ. Contains a row for each target (incl. 4 which could not be modelled in AF-Multimer and 2 which failed in DockQ) with following columns:
- *pdb_id*: identifies dimer target
- *is_levy*: distinguishes between QSalign set (True) and ProtCID set (False)
- *is_physio*: True/False if phys./non-phys.
- *len_seq*: length of sequence for dimer
- *model_id*: ID of selected model (matches AF-paramaters used for model with highest DockQ)
- *DockQ*: DockQ score for selected model
- *iptm*: ipTM value predicted by AF-Multimer for selected model


<h3>collected_models_top_DockQ<h3\>

Contains unrelaxed AF-Multimer model with highest DockQ score for each dimer-target. Files are named as "[PDB-ID].pdb".
