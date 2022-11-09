# The UroCell Dataset

Manca Žerovnik Mekuč<sup>1</sup>, Ciril Bohak<sup>1,2</sup>, Samo Hudoklin<sup>3</sup>, Eva Boneš<sup>1</sup>, Byeong Hak Kim<sup>4</sup>, Rok Romih<sup>3</sup>, Min Young Kim<sup>4</sup>, and Matija Marolt<sup>1</sup>

<sup>1</sup> Laboratory for Coumputer Graphics and Multimedia, Faculty of Computer and Information Science, University of Ljubljana

<sup>2</sup> Visual Computing Center, King Abdullah University of Science and Technology

<sup>3</sup> Institute of Cell Biology, Faculty of Medicine, University of Ljubljana

<sup>4</sup> School of Electronics Engineering and Research Center for Neurosurgical Robotic System, Kyungpook National University

<sup>5</sup> Hanwha Systems Corporation, Optronics Team

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

For the class of mitochondria, we also provide labels indicating the shape of each instance: we define if the object is branched or contacting (an instance can be both - branched and contacting).

All annotations were revised by biomedical experts.

### Dataset structure

The dataset is structured into four folders, each containing 256x256x256 sub-volumes. The files are stored in the gzipped Neuroimaging Informatics Technology Initiative (NIfTI) volumetric file format.

* *data*: contains the original FIB-SEM scanned data
* *mito*: contains four sub-folders:
    * *binary:* contains manual annotations of mitochondria (label 0: background, label 1: mitochondria)
    * *instance:* contains manual annotations of mitochondria where each instance of a mitochondrion is labeled with a different integer number (label 0: background, label > 0: mitochondria)
    * *branched:* contains manual annotations of mitochondria with information if an object is branched or not (label 0: background, label 1: branched mitochondria objects, label 2: non-branched mitochondria)
    * *contacting:* contains manual annotations of mitochondria with information if an object is contacting or not (label 0: background, label 1: non-contacting mitochondria objects, label 2: contacting mitochondria)
    * *mesh:* contains mesh representations of mitochondria in OBJ format
* *lyso*: 
    * *binary:* contains manual annotations of endolysosomes (label 0: background, label 1: endolysosome)
    * *mesh:* contains mesh representations of endolysosomes in OBJ format
* *golgi*: contains two sub-folders:
    * *approximate:*
        * *binary:* contains approximate manual annotations of Golgi apparatus (label 0: background, label 1: Golgi apparatus)
        * *mesh:* contains mesh representations of Golgi apparatus in OBJ format
    * *precise:*
        * *binary:* contains precise manual annotations of Golgi apparatus (label 0: background, label 1: Golgi apparatus)
        * *mesh:* contains mesh representations of Golgi apparatus in OBJ format
* *fv*: contains two sub-folders:
    * *binary:* contains manual annotations of fusiform vesicles (label 0: background, label 1: fusiform vesicle)
    * *instance:* contains manual annotations of fusiform vesicles where each instance of a fusiform vesicle is labeled with a different integer number (label 0: background, label > 0: fusiform vesicle)
    * *mesh:* contains mesh representations of fusiform vesicles in OBJ format

### Cite us
Please cite our papers [(Žerovnik Mekuč et al. 2020)](https://doi.org/10.1016/j.compbiomed.2020.103693) or [(Žerovnik Mekuč et al. 2022)](https://doi.org/10.1016/j.cmpb.2022.106959) if you use this dataset.

BibTex:
```
@article{ZerovnikMekuc2020,
    author = {Manca {Žerovnik Mekuč} and Ciril Bohak and Samo Hudoklin and Byeong Hak Kim and Rok Romih and Min Young Kim and Matija Marolt},
    title = {Automatic segmentation of mitochondria and endolysosomes in volumetric electron microscopy data},
    journal = {Computers in Biology and Medicine},
    volume = {119},
    pages = {103693},
    year = {2020},
    issn = {0010-4825},
    doi = {https://doi.org/10.1016/j.compbiomed.2020.103693},
    url = {https://www.sciencedirect.com/science/article/pii/S0010482520300792}
}
``` 
and

```
@article{ZerovnikMekuc2022,
    author = {Manca {Žerovnik Mekuč} and Ciril Bohak and Eva Boneš and Samo Hudoklin and Rok Romih and Matija Marolt},
    title = {Automatic segmentation and reconstruction of intracellular compartments in volumetric electron microscopy data},
    journal = {Computer Methods and Programs in Biomedicine},
    volume = {223},
    pages = {106959},
    year = {2022},
    issn = {0169-2607},
    doi = {https://doi.org/10.1016/j.cmpb.2022.106959},
    url = {https://www.sciencedirect.com/science/article/pii/S0169260722003418}
}
```

### Acknowledgements
The dataset is published under the [CC-BY-NC-SA 4.0 license](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode). Feel free to use it for your research with necessary attributions. 
