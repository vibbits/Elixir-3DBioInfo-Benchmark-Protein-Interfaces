**Ora Schueler-Furman HUJI**, Elixir IL (ora.furman-schueler@mail.huji.ac.il)

PDB files were cleaned with a python script (based on Rosetta's clean_pdb.py). We ran Rosetta (v2020.28.61328) InterfaceAnalyzer (Stranges & Kuhlman, 2013), on the cleaned PDB structures, then performed docking with local refinement using the RosettaDock [1] protocol, with the best structures by interface score subsequently analyzed with InterfaceAnalyzer. To evaluate dimers with disulfide bridges in the interaction surface, we used the flag `'-detect_disulf false'` to load structures into Rosetta.
AUC values were calculated using pROC (v.1.16.2) package of R (v3.5.2).

* Stranges PB, Kuhlman B: A comparison of successful and failed protein interface designs highlights the challenges of designing buried hydrogen bonds. Protein Sci 2013, 22:74–82.

Brief description of individual scores

- I_sc: interface score, the energies of the two monomer subtracted from the total energy of the complex

- dG_cross/dSASA*: binding energy per unit interface area  calculated using only cross-interface energy terms  

- sc_value: shape complementarity value

- fa_intra_sol_xover4: intra-residue LK solvation, counted for the atom-pairs beyond torsion-relationship.

- dG_separated/dSASA* binding energy of separate components per unit interface area.

- fa_dun: Internal energy of sidechain rotamers as derived from Dunbrack's statistics (2010 Rotamer Library used in Talaris2013).  Supports any residue type for which a rotamer library is available.

- dSASA_polar: polar components of dSASA (measures hydrophilicity of interface)

- fa_intra_rep: Lennard-Jones repulsive between atoms in the same residue


Note: ‘*’ indicates that the corresponding quantities were multiplied by 100 to  fit the units in the score file. See:https://www.rosettacommons.org/docs/latest/application_documentation/analysis/interface-analyzer

[1] Gray JJ, Moughon S, Wang C, Schueler-Furman O, Kuhlman B, Rohl CA, Baker D. Protein-protein docking with simultaneous optimization of rigid-body displacement and side-chain conformations. J Mol Biol. 2003 Aug 1;331(1):281-99. doi: 10.1016/s0022-2836(03)00670-3.
