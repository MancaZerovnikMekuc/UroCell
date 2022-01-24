# The UroCell Dataset
The repository contains the UroCell dataset - an **annotated volumetric dataset of intracellular compartments** obtained with focused ion beam and scanning electron microscopy (FIB-SEM). 
<p align="center">
<img src="https://github.com/MancaZerovnikMekuc/UroCell/blob/master/compartments.png" alt="alt text" width="500">
</p>

### Procedure
We obtained tissue samples from urinary bladders of 6-8 weeks old healthy male C57BL/6J mice in accordance with European guidelines and Slovenian legislation. The experiments were approved by the Veterinary Administration of the Slovenian Ministry of Agriculture and Forestry (permit no. U34401-6/2015/4) in compliance with the Animal Health Protection Act and the Instructions for Granting Permits for Animal Experimentation for Scientific Purposes. 
The volumetric data was obtained from the tissue with a FIB-SEM dual-beam electron microscope. Briefly, urinary bladders were isolated and immediately cryo-fixed with a CPC device (Leica), freeze-substituted in AFS (Leica) with 2% OsO4 in acetone, and embedded in Epon. To locate the region of interest, which were terminally differentiated cells of the bladder epithelium (umbrella cells), Epon ultrathin sections were inspected with the Philips CM100 transmission electron microscope and the location of cells was correlated with their location in the epon block. The epon block was then taken into a dual-beam Helios NanoLab 650 microscope (FEI) and the umbrella cell was sectioned with the FIB. 

The dimensions of each pixel were x=5.49 nm, y=5.49 nm, z=15.0 nm. We binned x and y pixels by 3 to obtain an almost isotropic resolution in all three directions which resulted in 1056 serial sections of 1366x1180 pixels. The voxel dimensions in the dataset are thus approximately x=16 nm, y=16 nm, z=15 nm. 

### Annotations

The dataset contains eight sub-volumes of 256x256x256 voxels. Currently, four intracellular compartment types are annotated: mitochondria, endolysosomes, Golgi apparatus, and fusiform vesicles. 

Mitochondria and endolysosomes are annotated in five sub-volumes, fusiform vesicles are annotated in four sub-volumes, Golgi apparatus is annotated in all eight sub-volumes. 

Mitochondria, endolysosome and fusiform vesicles labels are precise while the annotations of Golgi apparatus are approximate. They are defining regions of Golgi apparatus but they are not following the exact border of the compartment, except for the two sub-volumes for which we also provide the precise labels. 

For the class of mitochondria and fusiform vesicles, we also provide labels for instance segmentation, where each instance of the compartment in the target class has its own label.

For the class of mitochondria, we also provide labels indicating the shape of each instance: we define if the object is forked or narrowed (an instance can be both - forked and narrowed).

All annotations were revised by biomedical experts.

### Dataset structure

The dataset is structured into four folders, each containing 256x256x256 sub-volumes. The files are stored in the gzipped Neuroimaging Informatics Technology Initiative (NIfTI) volumetric file format.

* *data*: contains the original FIB-SEM scanned data
* *mito*: contains four sub-folders:
    * *binary:* contains manual annotations of mitochondria (label 0: background, label 1: mitochondria)
    * *instance:* contains manual annotations of mitochondria where each instance of a mitochondrion is labeled with a different integer number (label 0: background, label > 0: mitochondria)
    * *forked:* contains manual annotations of mitochondria with information if an object is forked or not (label 0: background, label 1: forked mitochondria objects, label 2: non-forked mitochondria)
    * *narrowed:* contains manual annotations of mitochondria with information if an object is narrowed or not (label 0: background, label 1: non-narrowed mitochondria objects, label 2: narrowed mitochondria)
* *lyso*: contains manual annotations of endolysosomes (label 0: background, label 1: endolysosome)
* *golgi*: contains two sub-folders:
    * *approximate:* contains approximate manual annotations of Golgi apparatus (label 0: background, label 1: Golgi apparatus)
    * *precise:* contains precise manual annotations of Golgi apparatus (label 0: background, label 1: Golgi apparatus)
* *fv*: contains two sub-folders:
    * *binary:* contains manual annotations of fusiform vesicles (label 0: background, label 1: fusiform vesicle)
    * *instance:* contains manual annotations of fusiform vesicles where each instance of a fusiform vesicle is labeled with a different integer number (label 0: background, label > 0: fusiform vesicle)

### Cite us
Please cite our [paper](https://doi.org/10.1016/j.compbiomed.2020.103693) if you use this dataset. 

### Acknowledgements
The dataset is published under the [CC-BY-NC-SA 4.0 license](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode). Feel free to use it for your research with necessary attributions. 
