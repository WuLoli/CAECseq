# CAECseq: A Convolutional Auto-Encoder for Haplotype Assembly and Viral Quasispecies Reconstruction
Haplotype assembly and viral quasispecies reconstruction are challenging tasks concerned with analysis of genomic mixtures using sequencing data. High-throughput sequencing technologies generate enormous amounts of short fragments (reads) which essentially oversample components of a mixture; the representation redundancy enables reconstruction of the components (haplotypes, viral strains). The reconstruction problem, known to be NP-hard, boils down to grouping together reads originating from the same component in a mixture. Existing methods struggle to solve this problem with required level of accuracy and low runtimes; the problem is becoming increasingly more challenging as the number and length of the components increase. This paper proposes a read clustering method based on a convolutional auto-encoder designed to first project sequenced fragments to a low-dimensional space and then estimate the probability of the read origin using learned embedded features. The components are reconstructed by finding consensus sequences that agglomerate reads from the same origin. Mini-batch stochastic gradient descent and dimension reduction of reads allow the proposed method to efficiently deal with massive numbers of long reads. Experiments on simulated, semi-experimental and experimental data demonstrate the ability of the proposed method to accurately reconstruct haplotypes and viral quasispecies, often demonstrating superior performance compared to state-of-the-art methods.

Software requirement:
-----------------
1. Python 3.6 or higher (https://www.python.org/)
2. Tensorflow package (Initial experiment uses version 1.14) (https://www.tensorflow.org/)
3. Biopython package (https://biopython.org/)
4. Numpy package (http://www.numpy.org/)
5. C++ (http://www.cplusplus.com/)

Reference:
-----------------
Ziqi Ke and Haris Vikalo. "A convolutional auto-encoder for haplotype assembly and viral quasispecies reconstruction," Thirty-fourth Conference on Neural Information Processing Systems (NeurIPS), December 6-12, 2020.<br/>

Pre-trained models and data:
-----------------
The pre-trained models and data could be downloaded from the Supplemental section at https://proceedings.neurips.cc/paper/2020/hash/9c449771d0edc923c2713a7462cefa3b-Abstract.html
1. Please follow the Readme.txt file
2. The pre-trained models for HIV-1 data are the .h5 files in the HIV-1 folder
