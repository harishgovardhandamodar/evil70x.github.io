Graph distance combining local and global distances. 

The local metric H is the Hamming distance, corresponding to the difference for the edges in both networks. 

The global (spectral) metric IM is the Ipsen-Mikailov distance, corresponding to the square-root of the squared difference of the Laplacian spectrum for each network. 

The Hamming-Ipsen-Mikhailov (HIM) distance is an Euclidean metric on the space created by the Cartesian product of the metric space associated with H and IM. The trade-off between global and local information is governed by a combination factor: when this is one, local and global information are balanced; when it is zero, it reduces to the (local) Hamming distance; and as it approaches infinity it becomes the (global) Ipsen-Mikhailov distance. 


The results dictionary also stores a 2-tuple of the underlying adjacency matrices in the key `'adjacency_matrices'`, the Hamming distance in `'hamming_dist'`, the Ipsen-Mikhailov distance in `'ipsen_mikhailov_dist'`, and the Lorentzian half-width at half-maximum in `'hwhm'`. If the networks being compared are directed, the augmented adjacency matrices are calculated and stored in `'augmented_adjacency_matrices'`. 

#### Parameters 
---------- 
G1, G2 (nx.Graph) two networkx graphs to be compared. 
combination_factor (float) positive factor in front of the IM metric. 

#### Returns
------- 
dist (float) the distance between G1 and G2. 

#### Notes
----- 
Requires networks with the same number of nodes.
The networks can be directed and weighted (with weights in the range :math:`[0,1]`). Both (H and IM) are also saved in the results dictionary. 

#### References 
---------- 
[1] https://ieeexplore.ieee.org/abstract/document/7344816 """