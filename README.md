# ONC-RCC

Dataset of radiomic features extracted from renal masses. Two tumor types are included: oncocytomas (bening) an renal cell carcinoma (malignant). 

## Description
A total of 164 solid, enhancing lipid poor tumors from 159 patients are included (106 RCC and 58 ONC). The dataset presented here does not contain images, it contains only numerical features extracted from contrast-enhanced computed tomography scans. No patient identification information is given.  

## Volumetric masks 
A group of experienced radiologists performed manual volumetric segmentation of all masses on the nephrographic-phase scan, using 3D Slicer free software [1]. The binary volumetric masks for the remaining contrast-phases were obtained by transforming coordinate systems with the Nibabel package [2]. We obtained one binary mask of the mass volume for each available phase of contrast-enhanced computed tomography, resulting in multiple masks for one renal mass. The contrast phases included are unenhanced, corticomedullary, nephrographic, and excretory phases. 

## Radiomic extraction
We extracted 70 radiomic features from each tumor mask, obtaining a total of 280 features per mass. We performed feature extraction with the PyRadiomics open-source package [3], using the original images with no filter configuration. We applied image resampling obtaining a voxel spacing of 1 mm in the three spatial directions, using B-Spline interpolation of order 3 and tumor volume pad distance of 10 voxels. We included three groups of radiomic features: 
- *First order features*: obtained from histogram analysis of gray-level intensities (corresponding to Hounsfield Units distribution in the renal mass), with no regard for the spatial location of the intensities.
- *Shape features*: obtained from 2D and 3D analysis of the mass morphology, with no regard for gray-level intensities. 
- *Texture features*: obtained from second-order statistical texture analysis. Eleven features are calculated from the gray-level co-occurrence matrix and thirteen from the gray-level difference matrix.

The calculation formula of each feature can be found online in Pyradiomics documentation [4].

## References
[1] Fedorov A, Beichel R, Kalpathy-Cramer J, Finet J, Fillion-Robin J-C, Pujol S, et al. 3D Slicer as an Image Computing Platform for the Quantitative Imaging Network. Magnetic Resonance Imaging. 2012;30(9):1323-41. PMID: 22770690.

[2] Brett M, Hanke M, Markiewicz C, Côté M-A, McCarthy P, Cheng C, et al. nipy/nibabel: 3.0.0. Zenodo; 2019. doi: 10.5281/zenodo.3583002.

[3] van Griethuysen JJM, Fedorov A, Parmar C, Hosny A, Aucoin N, Narayan V, et al. Computational Radiomics System to Decode the Radiographic Phenotype. Cancer Res. 2017;77: e104–e107. doi: 10.1158/0008-5472.CAN-17-0339.

[4]	PyRadiomics Documentation. Accesed 13 Nov 2020. https://pyradiomics.readthedocs.io/

