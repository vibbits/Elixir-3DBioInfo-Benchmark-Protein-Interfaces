**Haim Wolfson Lab.** Tel-Aviv University, IL (wolfson@post.tau.ac.il)

Jérôme Tubiana, Dina Schneidman, Haim Wolfson

Our submitted file consists of several energy scores (lower is better) and one metascore:

- Two all-atom potentials: the SOAP-pp interaction score [1] (F_SOAP) and the FireDock energy score [2] (F_FireDockScore).

-  A binding site score (F_Network_binding_0 and F_Network_binding_1). We predict for each amino acid of each chain a probability of being a protein-protein binding site, in a partner-independent fashion akin to SPPIDER [3] or Masif-site [4]). The probability is computed by ScanNet, a geometric deep learning neural network (manuscript in preparation). Then, agreement between the predictions and the interface is quantified.

- An interaction score (F_Network_full). We predict for each pair of amino acid of each chain of probability of being in contact. The probability is computed by ScanNet, a geometric deep learning neural network (manuscript in preparation). Then, agreement between the predictions and the interfaces is quantified.

-  A metapredictor score (I_Proba_Consensus) integrates the above scores and predicts a probability that the pose is an acceptable docking solution. It is calibrated on the Benchmark v5.0 dataset assuming a regular docking pipeline consisting of Rigid docking + refinement. Note that the probabilities are not calibrated for crystal vs biological interface classification.


[1] Dong, G. Q., Fan, H., Schneidman-Duhovny, D., Webb, B., & Sali, A. (2013). Optimized atomic statistical potentials: assessment of protein interfaces and loops. Bioinformatics, 29(24), 3158-3166.

[2] Andrusier, N., Nussinov, R., & Wolfson, H. J. (2007). FireDock: fast interaction refinement in molecular docking. Proteins: Structure, Function, and Bioinformatics, 69(1), 139-159.
