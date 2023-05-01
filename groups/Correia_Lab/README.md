**Correia Lab.** EPFL Lausanne Switzerland (bruno.correia@epfl.ch)

We use our deep-learning algorithm MaSIF ( Molecular Surface Interaction Fingerprinting) designed for predicting protein-protein interactions (PPI). MaSIF learns and compute the chemical (electrostatics, H-bonds, hydrophobicity) and geometrical (shape and curvature) surface features of PPI in order to draw a surface "fingerprint". This latter is vectorized in a so-called "descriptor", a vector that describes the surface features.
In order to search for a complementary interaction interface, MaSIF computes the descriptor of one interface and then searches for the invert of this descriptor (e.g. a positive charge of one side should be complemented by a negative charge on the other, etc...).  In short, small descriptor distance between interacting patches indicate high surface complementarity.

Among the different output of MaSIF, two scores are relevant :

Descriptor distance score is a score that evaluates the complementary of two interacting patches. The function is :

score = $$\sum_{k=1}^n a_k b_k$$

$$\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)$$

where i is a pair of interacting points of the interface and d the descriptor distance between these points. The smaller is the distance between complementary descriptors, the more complementarity and the higher is the score.

Neural network alignment score is a complex function that computes a score between 0 (bad alignment between patches) and 1 (good alignment). This function is computed based on the 3D Euclidean distance, the MaSIF fingerprint/descriptor distance and the product of the normals between correspondences.nn12 and nn0129 stands for two different neural networks.


Reference : Gainza, P., Sverrisson, F., Monti, F. et al. Deciphering interaction fingerprints from protein molecular surfaces using geometric deep learning. Nat Methods 17, 184–192 (2020). https://doi.org/10.1038/s41592-019-0666-6
