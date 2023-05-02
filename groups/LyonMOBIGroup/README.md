**Lyon MOBI team / Juliette Martin**   (juliette.martin@ibcp.fr)

We compute three descriptors for each interface (F_shape, F_hydro,F_tails), and one integrated score (I_shape_hydro_tails). Each is described below.

- F_shape
This quantity is obtained by fast shape-based docking. 
The two chains of a dimer are docked using the hex software with the same parameters as in (Martin J, Lavery R. Arbitrary protein-protein docking targets biologically relevant interfaces. BMC Biophysics. 2012). We compute, for each residue, the number of hits , i.e., frequency of each residue at the interface over the first 250 poses (interface defined by change in accessibility computed with NACCESS). 
F_shape is then defined as the fraction of number of hits that is captured by the residues of the interface core.
The rationale is that physiological interfaces should capture more hits than non-physiological ones.

- F_hydro
This quantity is obtained using the Kyte&Doolittle hydrophobicity scale.
Each residue is assigned a hydrophobicity score, defined by its hydrophobicity value or zero if the value is negative.Hydrophobicity score are summed over the surface residues and over the interface core residues.F_hydro is then defined as the fraction of surface hydrophobicity captured by the residues of the interface core.The rationale is that physiological interfaces should capture more hydrophobicity than non-physiological ones.

- F_tails
This quantity is obtained using the location of terminal residues with respect to protein-protein interface. It is a binary variable, equal to 0 if at least terminal residue is involved at the interface (rim and core), and 1 otherwise. The rationale is that tails are under-represented in physiological interfaces (Martin OMF, Etheve L, Launay G, Martin J. Implication of Terminal Residues at Protein-Protein and Protein-DNA Interfaces. PLOS ONE. 2016).

- I_shape_hydro_tails
The integrated score is defined by 
$$I=F<sub>shape</sub>+F_hydro(F_tails)$$
with F<sub>tails</sub>=1 if 
F<sub>tails</sub>=1, and 
F<sub>tails</sub>=0.5 if 
F<sub>tails</sub>=0.
Here we simply sum the contributions of shape and hydrophobicity, and penalize interfaces with tails by dividing their score by 2.
