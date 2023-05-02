**Casadio-Lab.**   University of Bologna, Italy   (rita.casadio@unibo.it)
Castrense Savojardo, Pier Luigi Martelli, Rita Casadio Biocomputing Group, University of Bologna, Italy

Here we describe the approach based on our ISPRED4 interaction site predictor for discriminating physiological from non-physiological dimers in the context of the ELIXIR 3DBioInfo Community Benchmark.
The ISPRED4 prediction method
ISPRED4 [1] (https://ispred4.biocomp.unibo.it) is an improved structure-based predictor of PPI sites on unbound monomer surfaces.



 ![casadio_fig1](https://user-images.githubusercontent.com/22592827/235601016-ce7835b1-9961-421c-9353-28cbd3aadc6d.png)


Figure 1. The ISPRED4 workflow. GRHCRF: Grammatical-Restrained Conditional Random Fields [2].
 
The ISPRED4 workflow is shown in Figure 1. ISPRED4 takes in input an unbound protein chain and identifies, on the protein surface, protein-protein interaction sites i.e., residues that are putatively involved in interactions with other proteins. ISPRED4 performs its prediction in a partner unspecific way: no prior knowledge of the putative interaction partner is required. The first step is the isolation of those residues placed in the protein surface. This is accomplished using Accessible Surface Area (ASA) values computed by DSSP [3] and transformed into Relative Solvent Accessibility (RSA) values using the Sander & Rost scale of residue maximal accessibility [4]. Protein surface is then defined as the collection of residues having RSA greater or equal to 20%.
Then, ISPRED4 relies on machine-learning methods (SVMs and GRHCRFs [2]) incorporating 46 features extracted from both protein sequence and structure. Residue descriptors used by ISPRED4 include:

- Sequence profile from Multiple Sequence Alignment (MSA), obtained running 3 iterations of PSI-BLAST against UniRef90 database with e-value threshold set to 0.001.

- Residue conservation score from the MSA: Normalized Shannon's entropy on sequence profile.

- Residue physico-chemical properties: 10 Kidera factors from dimension reduction of 188 physical properties [5].

- Intra-chain coevolution scores computed using PSICOV [6]. Two descriptors evaluating the overall coevolution score with respect to: i) residues within the local structural context and ii) the remaining surface residues (i.e., not part of the local context).

- Interface propensity, computed on the training set for each residue type R as the log-ratio of frequencies of R in interface and surface, respectively.

- Solvent exposure delta: difference between experimental and predicted RSA (using the SABLE [7] program from sequence). Rationale: sequence-based RSA predictors tend to provide RSA values as observed in protein complexes and the difference can be used as a fingerprint for PPI sites.

- Geometrical features, including depth index, as computed using the DPX algorithm [8], and protrusion index [9], both extracted using the Protein Structure And Interaction Analyzer (PSAIA) [10].

- Secondary structure, extracted with DSSP [3] and mapped in three classes: helix (H, G, I), strand (E, B) and coil (T, S, -).

- Residue B-factor, computed averaging B-factors of all atoms.

All the features are computed for each surface residue and then averaged over the local structural context comprising surface residues at a Cα-Cα distance below 12Å.
Training of ISPRED4 has been performed using a dataset of 314 unbound protein chains extracted from 151 high-resolution, functional protein-protein complexes derived from the Docking Benchmark dataset version 5 (DBv5) [11] (https://zlab.umassmed.edu/benchmark/). Complexes in this dataset comprise both bound and unbound forms.
 
![casadio_fig2](https://user-images.githubusercontent.com/22592827/235601033-bbdd8c3a-da92-48f3-91ac-f3af56564dff.png)

Figure 2. Calculation of experimental interaction sites and features in the ISPRED4 training dataset
 
Experimental interaction sites for training were taken from the bound complexes whereas features were extracted from unbound chains (Figure 2). This allows to avoid biases in the computation of features due to possible conformational changes of interface regions upon binding. Protein-protein interfaces were defined as the set of all surface residues undergoing a change in ASA upon binding. In practice, this is performed by applying DSSP to both the bound and the unbound structures and then identifying those surface residues for which bound and unbound ASA differ (specifically, unbound ASA is higher than the bound one). Surface is defined as detailed above i.e., using a threshold of 20% on the residue RSA as computed in the unbound structure.
 
Two different machine-learning methods are employed in ISPRED4. In a first step, a Support Vector Machine (SVM) is used to process the above 46 features and perform a preliminary discrimination of interaction sites in the protein surface. Then, a Grammatical-Restrained Hidden Conditional Random Field (GRHCRF) [2] model is adopted for refining and correcting SVM predictions by means of a regular grammar, which models the proximity relationships of interface residues along the surface sequence. The GRHCRF introduces correlations among the different SVM predictions by filtering out single isolated spots and by reinforcing locally coherent predictions.
ISPRED4 for discrimination of physiological from non-physiological dimers
The discrimination problem can be stated as follows: given a query protein assembly, we want to compute a score proportional to the likelihood that the interface represented in the assembly is the functional one i.e., the one assumed by the protein in physiological conditions. We propose to adopt ISPRED4 as a proxy for distinguishing physiological from non-physiological assemblies. Currently, only homodimers are included in the benchmark dataset. However, the procedure described here can be easily adapted to classify any kind of protein assembly (homo and hetero multimers).

ISPRED4 has been trained on functional complexes extracted from the Docking Benchmark dataset [1, 11].  We can derive a global score for a given complex to be physiological by assessing the overlap between expected and predicted interfaces. This strategy is based on the hypothesis that the larger the overlap the higher is the probability that the complex is functional.

Different scoring schemes have been evaluated during experiments.
Overall, the procedure can be outlined as follows:
 
Residues belonging to the protein-protein interface are extracted from the input protein assembly. In particular, we use the ASA difference definition as detailed above.
We apply ISPRED4 to a single subunit in the complex.
We compare PPI sites identified by ISPRED4 to those extracted from the target assembly, classifying surface residues in four categories:
True Positives (TPs) i.e., surface residues belonging to the protein-protein interface and classified by ISPRED4 as PPI sites.
False Negatives (FNs) i.e., surface residues belonging to the protein-protein interface and not recognized by ISPRED4 as PPI sites.
False Positives (FPs) i.e., surface residues not belonging to the protein-protein interface but classified by ISPRED4 as PPI sites.
True Negatives (TNs) i.e., surface residues not belonging to the protein-protein interface and not recognized by ISPRED4 as PPI sites.
Using TPs, FNs, FPs and TNs we can score the ISPRED4 prediction using the Matthews Correlation Coefficient:
 
The MCC index can be directly interpreted as a score for the input assembly to be functional. The value goes from -1 to 1, the higher it is the higher is the likelihood that the input assembly is functional.

In Figure 1 we summarize the procedure for assemblies that are symmetric homodimers. In Figure 2, the procedure is described for asymmetric homodimers. In the latter case, interface regions can be different in the two subunits. In order to avoid any bias and to make our procedure independent from the symmetry properties of the input assembly, ISPRED4 predictions are performed on single subunits and compared with all interface residues remapped in the processed subunit. This allows us to adequately compute scoring indexes.


![casadio_fig3](https://user-images.githubusercontent.com/22592827/235601048-141cf3c1-247c-4431-902f-97ae5dfbd507.png)


Figure 3. Computation MCC-based scoring function for symmetric homodimers!

 
![casadio_fig4](https://user-images.githubusercontent.com/22592827/235601059-e3653d1f-0530-4d16-913a-2dee4825be1a.png)

Figure 4. Computation MCC-based scoring function for asymmetric homodimers


Self-evaluation on the benchmark_v3
The above procedure has been self-evaluated on the current version of the benchmark (v2) comprising 1677 homodimeric assemblies classified into 836 and 841 physiological and non-physiological complexes, respectively.
Firstly, we evaluated the distribution of the scoring function in physiological and non-physiological complexes. Distribution plots are shown in Figure 5.

![casadio_fig5](https://user-images.githubusercontent.com/22592827/235597886-7d55e899-9ea0-4ff6-9a26-bc9105937bf6.png)


Figure 5. Distribution of MCC-based scores assigned to 836 and 841 physiological and non-physiological complexes, respectively.
 
As can be seen, the distributions are different for physiological and non-physiological complexes, providing some separation of the two classes. Area Under the ROC Curve (AUC) is 0.76.
References
1. Savojardo C, Fariselli P, Martelli PL, Casadio R. ISPRED4: interaction sites PREDiction in protein structures with a refining grammar model. Bioinformatics. 2017;33:1656–63.
2. Fariselli P, Savojardo C, Martelli PL, Casadio R. Grammatical-Restrained Hidden Conditional Random Fields for Bioinformatics applications. Algorithms Mol Biol. 2009;4:13.
3. Kabsch W, Sander C. Dictionary of protein secondary structure: pattern recognition of hydrogen-bonded and geometrical features. Biopolymers. 1983;22:2577–637.
4. Rost B, Sander C. Conservation and prediction of solvent accessibility in protein families. Proteins. 1994;20:216–26.
5. Kidera A, Konishi Y, Oka M, Ooi T, Scheraga HA. Statistical analysis of the physical properties of the 20 naturally occurring amino acids. J Protein Chem. 1985;4:23–55.
6. Jones DT, Buchan DWA, Cozzetto D, Pontil M. PSICOV: precise structural contact prediction using sparse inverse covariance estimation on large multiple sequence alignments. Bioinformatics. 2012;28:184–90.
7. Adamczak R, Porollo A, Meller J. Combining prediction of secondary structure and solvent accessibility in proteins. Proteins. 2005;59:467–75.
8. Pintar A, Carugo O, Pongor S. Atom Depth as a Descriptor of the Protein Interior. Biophys J. 2003;84:2553–61.
9. Pintar A, Carugo O, Pongor S. CX, an algorithm that identifies protruding atoms in proteins. Bioinformatics. 2002;18:980–4.
10. Mihel J, Šikić M, Tomić S, Jeren B, Vlahoviček K. PSAIA – Protein Structure and Interaction Analyzer. BMC Structural Biology. 2008;8:21.
11. Vreven T, Moal IH, Vangone A, Pierce BG, Kastritis PL, Torchala M, et al. Updates to the Integrated Protein-Protein Interaction Benchmarks: Docking Benchmark Version 5 and Affinity Benchmark Version 2. J Mol Biol. 2015;427:3031–41.
 
 
