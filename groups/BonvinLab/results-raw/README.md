Bonvin Lab. University of Utrecht  Elixir NL (a.m.j.j.bonvin@uu.nl)

**PRODIGY-CRYSTAL**

The classification into physiological assemblies and crystal contacts is based on the contact-based PRODIGY-CRYSTAL method, described online (https://bianca.science.uu.nl/prodigy/method#heading_c_three) and published in:

* K. Elez, A.M.J.J. Bonvin* and A. Vangone. Distinguishing crystallographic from biological interfaces in protein complexes: Role of intermolecular contacts and energetics for classification https://doi.org/10.1186/s12859-018-2414-9. BMC Bioinformatics, 19 (Suppl 15), 438 (2018).

PRODIGY-CRYSTAL is available as a web server (https://bianca.science.uu.nl/prodigy/):

* B. Jiménez-García, K. Elez, P.I. Koukos, A.M.J.J. Bonvin and A. Vangone. PRODIGY-crystal: a web-tool for classification of biological interfaces in protein complexes (https://doi.org/10.1093/bioinformatics/btz437). Bioinformatics, 35, 4821–4823 (2019).
Source code is available from GitHub (https://github.com/haddocking/prodigy-cryst).

**Deeprank-GNN**

The Deeprank-GNN classification is based on a GraphNeural Network (GNN) that has been pre-trained on the MANY dataset (https://pubmed.ncbi.nlm.nih.gov/25326082/), which consists of 2828 biological interfaces and 2911 crystal ones, only using PSSM features. The MANY dataset was divided into a training (80%) and a validation set (20%), while maintaining the balance between positive and negative data. 
Each structure of the dataset has been refined using the HADDOCK short energy minimization protocol before applying the Deeprank classifier. 7 complexes have been discarded from the dataset classification due to :the lack of PSSM information 

*Manon Réau, Nicolas Renaud, Li C Xue, Alexandre M J J Bonvin, DeepRank-GNN: a graph neural network framework to learn patterns in protein–protein interfaces, Bioinformatics, Volume 39, Issue 1, January 2023, btac759, https://doi.org/10.1093/bioinformatics/btac759


Source code is available from GitHub (https://github.com/DeepRank/Deeprank-GNN)

**HADDOCK**

For each of the structures on the dataset, the HADDOCK score has been calculated after a short energy minimisation of the provided complexes. The HADDOCK score is based on a linear combination of intermolecular electrostatic and van der Waals energies and an empirical desolvation energy term.  Note that HADDOCK has not been trained/tested for classifying structures as physiological or non-physiological).

* G.C.P van Zundert, J.P.G.L.M. Rodrigues, M. Trellet, C. Schmitz, P.L. Kastritis, E. Karaca, A.S.J. Melquiond, M. van Dijk, S.J. de Vries and A.M.J.J. Bonvin. "The HADDOCK2.2 webserver: User-friendly integrative modeling of biomolecular complexes." J. Mol. Biol., 428, 720-725 (2015).

* C Dominguez, R Boelens, AMJJ Bonvin. "HADDOCK: a protein− protein docking approach based on biochemical or biophysical information". Journal of the American Chemical Society, 125, 1731-1737 (2003).
