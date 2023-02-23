The PDB folder consists of 1677 entries, the CIF folder contains 1673 entries because the same structure can generate multiple interfaces depending on symmetry operations.

Of the 1677 entries :
    • 700 were selected based on ProtCID
    • 977 were selected based on QSalign

Folder content:
**benchmark_pdb_format/** contains unedited PDB format for QSalign structures, PDB format generated by ProtCID for other structures.

**benchmark_mmcif_format/** contains unedited CIF format for QSalign structures, CIF format generated by ProtCID for other structures.

**benchmark_annotated.csv** is a table recapitulating the main features of the complexes of the dataset. The columns are organized as follow:

- ID: pdb identifier of the structure, followed by “_X” for the complexes from the QSalign dataset, with X denoting the number of the biological assembly.
- InterfaceID: The unique integer number for an interface in the crystal. Specific to complexes derived from ProtCID [1].
- AuthChain1: The author chain identifier of the first chain of the dimer. Specific to complexes derived from ProtCID [1].
- AuthChain2: The author chain identifier of the second chain of the dimer. Specific to complexes derived from ProtCID [1].
- SymmetryOp1: The symmetry operator used to rotate and translate the asymmetric chain to generate the first chain of a dimer. Crystallographic symmetry operators are used to build the crystal from an asymmetric unit, defined in PDB/mmCIF/XML files. Interfaces are identified from the crystal. Specific to complexes derived from ProtCID [1].
- SymmetryOp2: The symmetry operator used to rotate and translate the asymmetric chain to generate the second chain of a dimer. Specific to complexes derived from ProtCID [1].
- physio: True if the dimer is a physiological contact, False otherwise.
- contacts: The number of inter-residue contacts between the two subunits of the dimer.
- gene: the UniProt identifier of the protein.
- superfamily: The CATH [2,3] superfamily annotation of the protein.
- pfam: The Pfam domain annotation [4,5] of the protein. 
- bsa: the buried surface area of the dimer
- bsa_polar: The polar surface area of the dimer
- bsa_apolar: The apolar surface area of the dimer
- frac_polar: The polar fraction of the buried surface area of the dimer
- frac_apolar: The apolar fraction of the buried surface area of the dimer


References
[1]	Xu, Q., Dunbrack, R.L., Jr, ProtCID: a data resource for structural information on protein interactions. Nat. Commun. 2020, 11, 711.

[2]	Lewis, T.E., Sillitoe, I., Dawson, N., Lam, S.D., et al., Gene3D: Extensive prediction of globular domains in proteins. Nucleic Acids Res. 2018, 46, D435–D439.

[3]	Sillitoe, I., Bordin, N., Dawson, N., Waman, V.P., et al., CATH: increased structural coverage of functional space. Nucleic Acids Res. 2021, 49, D266–D273.

[4]	Mistry, J., Chuguransky, S., Williams, L., Qureshi, M., et al., Pfam: The protein families database in 2021. Nucleic Acids Res. 2021, 49, D412–D419.

[5]	Paysan-Lafosse, T., Blum, M., Chuguransky, S., Grego, T., et al., InterPro in 2022. Nucleic Acids Res. 2023, 51, D418–D427.
