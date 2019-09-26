# The UroCell Dataset
The repository contains the UroCell dataset - an **annotated volumetric dataset of intracellular compartments** obtained with focus ion beam and scaning electron microscopy (FIB-SEM). 

### Procedure
We obtained tissue samples from urinary bladders of 6-8 weeks old male C57B6 mice. The volumetric data were obtained from the tissue with focused ion beam scanning electron microscopy. Bladders were cryo-fixed with a CPC device (Leica), freeze-substituted in AFS (Leica) with 2% OsO4 in acetone, and embedded in epon. To locate the region of interest - terminally differentiated cells of the bladder epithelium (umbrella cells), epon ultrathin sections were inspected with the Philips CM100 transmission electron microscope and the location of cells was correlated with their location in the epon block. The epon block was then taken into a dual beam Helios NanoLab 650 microscope (FEI) and sectioned with the focused ion beam. 

The dimensions of of each pixel were x=5.49 nm, y=5.49 nm, z=15.0 nm. We binned x and y pixels by 3 to obtain an almost isotropic resolution in all three directions which resulted in 1056 serial sections of 1366x1180 pixels. The voxel dimensions in the dataset are thus approximately x=16 nm, y=16 nm, z=15 nm. 

### Annotations

The dataset contains 5 annotated sub-volumes of 256x256x256 voxels. Currently, two intracellular compartment types are annotated: mitochondria and compartments of the lysosomal pathway. All annotations were revised by biomedical experts. We will add other compartment types in the future.

### Dataset structure

The dataset is structured into three folders, each containing five 256x256x256 sub-volumes. The files are stored in the gzipped Neuroimaging Informatics Technology Initiative (NIfTI) volumetric file format.

* *data*: contains the original FIB-SEM scanned data
* *mito*: contains manual annotations of mitochondria
* *lyso*: contains manual annotations of compartments of the lysosomal pathway

### Acknowledgements
The dataset is published under the [CC-BY-NC-SA 4.0 licence](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode). Feel free to use it for your research with necessary attributions. 
