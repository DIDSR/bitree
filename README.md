# bitree
This repository contains the source code for a standalone application that reads a computational phantom described with uniform voxels, and creats an equivalent version of the phantom using a binary tree data structure. 
The binary tree reduces the size of the data by eliminating redundancy in uniform parts of the phantom, while enabling an efficient random access to the data that can be used at run-time during computer simulations (unlike standard compression algorithms).

The implemented binary tree algorithm was introduced at the [6th International Workshop on Computational Human Phantoms](http://www.cpworkshop.org/) (August 30, 2017; Annapolis MD, USA).
The following manuscript describing the method is under consideration for a special issue of the IEEE Transactions on Radiation and Plasma Medical Sciences journal:

**TITLE:**
Reducing the memory requirements of high resolution voxel phantoms by means of a binary tree data structure

**AUTHORS:**
Andreu Badal and Aldo Badano

        Division of Imaging, Diagnostics, and Software Reliability
        Office of Science and Engineering Laboratories
        Center for Devices and Radiological Health
        U.S. Food and Drug Administration

**ABSTRACT**
Computational human phantoms are a well-established tool used to simulate the performance of medical imaging devices. The maximum resolution of voxelized phantoms is bounded in practice by the available computer memory, which is especially limited for GPU-based simulations. For phantoms that have been segmented into a small number of tissue types, the use of a uniform grid is inefficient because large numbers of adjacent voxels are composed of the same tissue. The computer files used to store these phantoms can be compressed into a small fraction of their original size using standard lossless compression algorithms. Compression is used for storage and distribution, but not during the simulations because compression algorithms compress the data incrementally from the first byte to the last. This approach intrinsically prevents access to random locations along the data stream, which is an essential requirement of the majority of simulation algorithms. In this work we propose to store voxelized phantoms in memory using a binary tree structure, as a way to accomplish both data compression and fast random access. The composition of a particular voxel can be efficiently retrieved by traversing the binary tree down from the root node to the corresponding leaf node. As a drawback, the memory savings come at the cost of more frequent memory access, which might slow down simulations in which memory access constitutes a substantial fraction of the execution time. Methods to generate and efficiently store in memory a binary tree geometry, and an example implementation in a GPU-accelerated Monte Carlo code for x-ray imaging virtual clinical trials (MC-GPU), are presented. Results of a simulation of mammography and tomosynthesis imaging with a computational breast phantom voxelized at 50 micron show that the implemented binary tree geometry can achieve a 50-fold reduction of memory use, with a 4.7% increase in simulation time.
