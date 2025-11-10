# PERMUTATION LEARNING WITH ONLY N PARAMETERS: FROM SOFTSORT TO SELF-ORGANIZING GAUSSIANS

**Kai Uwe Barthel, HTW Berlin, Germany; Florian Barthel, Peter Eisert***
***Fraunhofer HHI / HU Berlin, Germany

### Abstract

Permutation learning is essential for organizing high-dimensional data in optimization and machine learning. Current methods like Gumbel-Sinkhorn require $\mathbf{N^2}$ parameters for $\mathbf{N}$ objects, operating on the full permutation matrix. While low-rank approximations offer some reduction to $\mathbf{2NM}$ (with $\mathbf{M \ll N}$), they still create a computational bottleneck for very large datasets. SoftSort, a continuous relaxation of the argsort operator, enables differentiable 1D sorting but struggles with multidimensional data and complex permutations. We introduce a novel method for learning permutations using only $\mathbf{N}$ parameters, dramatically reducing storage costs. Our method extends SoftSort by iteratively shuffling the $\mathbf{N}$ indices of the elements to be sorted and applying a few SoftSort optimization steps per iteration. This significantly improves sorting quality, especially for multidimensional data and complex criteria, outperforming pure SoftSort. Our method offers superior memory efficiency and scalability while maintaining high-quality permutation learning. Its drastically reduced memory requirements make it ideal for large-scale optimization tasks like "Self-Organizing Gaussians", where efficient and scalable permutation learning is critical.


## Release

- [2025/09/11]  [Permutation Learning with Only N Parameters: From SoftSort to Self-Organizing Gaussians](https://eurasip.org/Proceedings/Eusipco/Eusipco2025/pdfs/0001892.pdf).








