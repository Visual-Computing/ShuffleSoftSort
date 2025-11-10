## ShuffleSoftSort: Scalable Permutation Learning with Only $N$ Parameters

[![Paper](https://img.shields.io/badge/Paper-EUSIPCO%202025-blue.svg)](https://eurasip.org/Proceedings/Eusipco/Eusipco2025/pdfs/0001892.pdf)
[![Code Status](https://img.shields.io/badge/Status-Active-brightgreen)](https://github.com/Visual-Computing/ShuffleSoftSort)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub Stars](https://img.shields.io/github/stars/Visual-Computing/ShuffleSoftSort?style=social)](https://github.com/Visual-Computing/ShuffleSoftSort/stargazers)

This is the official repository for the EUSIPCO 2025 paper: 
**"Permutation Learning with Only N Parameters: From SoftSort to Self-Organizing Gaussians"**.

**Kai Uwe Barthel (1), Florian Barthel (2), Peter Eisert (2)**
*(1: HTW Berlin, Germany, 2: Fraunhofer HHI / HU Berlin, Germany)*

---

### 💡 The Problem: Scalability in Permutation Learning

* While Gumbel-Sinkhorn is powerful, its O(N2) parameter complexity makes it impractical for large datasets. 
* Conversely, SoftSort is memory-efficient but its one-dimensional nature makes it unsuitable for complex, multidimensional data.


### 🚀 Our Solution: ShuffleSoftSort

We propose **ShuffleSoftSort**, a novel permutation learning method that achieves both **significantly improved efficiency** and high sorting quality:

* **Efficiency:** ShuffleSoftSort requires only **$N$ parameters**, a dramatic, linear reduction from prior $N^2$ methods.
* ShuffleSoftSort: **Improves permutation** learning by iteratively applying SoftSort to randomly shuffled elements.

This makes the method **ideal for large-scale tasks** requiring efficient permutation learning, such as the *Self-Organizing Gaussians* application.

---

### 🔬 Principle and Properties
#### Permutation Learning Overview
The core task of permutation learning is to find a permutation matrix $\mathbf{P}$ that maps an input $\mathbf{X}$ to a desired ordered output $\mathbf{X_{sort}}$.<p align="center"><img src="https://github.com/Visual-Computing/ShuffleSoftSort/raw/main/images/permutation_learning.png" width="80%" alt="Diagram showing the general permutation learning process where an input vector X is permuted by P to result in Y."></p>

#### The ShuffleSoftSort Mechanism
ShuffleSoftSort leverages the efficiency of SoftSort while extending its capabilities to multidimensional data. The image below illustrates the core idea: colors (data points) are sorted in 1D space. By calculating the loss on the reverse-shuffled output, the network is forced to learn a better global permutation that effectively refines the sorting and overcomes the local constraints of SoftSort.

<p align="center"><img src="https://github.com/Visual-Computing/ShuffleSoftSort/raw/main/images/indices_swap.png" width="70%" alt="A toy example demonstrating the reverse-shuffling mechanism for refining the permutation."></p>

#### Algorithm
The full iterative algorithm for ShuffleSoftSort is detailed below:
<p> <img src="https://github.com/Visual-Computing/ShuffleSoftSort/raw/main/images/ShuffleSoftSort.png" width="80%" alt="Flowchart of the ShuffleSoftSort algorithm, detailing the steps of permutation, soft sorting, and loss calculation."> </p>

#### 📊 Comparison of Properties

| Property | Gumbel-Sinkhorn | Low-Rank Permutation | SoftSort (1D) | **ShuffleSoftSort** |
| :--- | :---: | :---: | :---: | :---: |
| Number of Parameters | $N^2$ | $2 \cdot N \cdot M$ | **$N$** | **$N$** |
| Non-Iterative Normalization | no | **yes** | **yes** | **yes** |
| Achievable HD Sorting Quality | **++** | o | $-$ | **++** |
| Permutation Validity | + | o | **++** | **++** |

#### 📚 Paper and Citation
For complete details on the method, derivation, and experimental results, please refer to our paper:

[2025/09/11] Kai Uwe Barthel, Florian Barthel, Peter Eisert 
[Permutation Learning with Only N Parameters: From SoftSort to Self-Organizing Gaussians](https://eurasip.org/Proceedings/Eusipco/Eusipco2025/pdfs/0001892.pdf)

#### 🛠️ Installation and Setup

Example Pytorch notebooks can be found [here](https://github.com/Visual-Computing/ShuffleSoftSort/tree/main/python).

This project is implemented in PyTorch. You can install the necessary dependencies using `pip`:


```bash
# Clone the repository
git clone [https://github.com/Visual-Computing/ShuffleSoftSort.git](https://github.com/Visual-Computing/ShuffleSoftSort.git)
cd ShuffleSoftSort

# Install required packages (assuming a standard requirements.txt for PyTorch)
pip install -r requirements.txt
```