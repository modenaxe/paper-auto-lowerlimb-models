# Overview

This repository contains the data, models and the MATLAB scripts to inspect and reproduce the results of the following publication:

```bibtex
@article{Modenese2020auto,
  title={Automatic Generation of Personalized Models of the Lower Limb from Three-Dimensional Bone Geometries: A Validation Study},
  author={Modenese, Luca and Renault, Jean-Baptiste},
  journal={under review},
  year={2020},
  publisher={}
  doi={}
}
```
The paper will be open access and available from [from the Journal website](TBA).

Please cite the manuscript if you make use of these materials for your research or presentations.

## Brief summary of the publication
In our manuscript: 
* We presented a MATLAB toolbox called [STAPLE](TBA) for creating lower extremity models of the lower limb from three-dimensional bone geometries in a fully automatic way. 
* We described the algorithms for automatic processing of the lower limb bone geometries that are included in the STAPLE package.
* We validated a workflow equivalent to the codified approach of [Modenese et al. (2018)](https://doi.org/10.1016/j.jbiomech.2018.03.039) by comparing lower limb models created following that methodology with the equivalente automatic workflow implemented in STAPLE. 
* Finally, we presented some further functionality of STAPLE, including the extraction of articular surfaces and the possibility of streamlining the creation of skeletal models with the automatic technique for generating muscle anatomical models published by [Modenese and Kohout, 2020](http://link.springer.com/article/10.1007/s10439-020-02490-4).

![modelling_workflow](./images/workflow.png)

# Requirements
In order to use the content of this repository you will need to:
1. have MATLAB R2018b or more recent installed in your machine. The analyses of the paper were performed using version R2019b.
2. download [OpenSim 4.1](https://simtk.org/projects/opensim). You will use OpenSim to visualize the models. 
3. set up the OpenSim 4.1 API for MATLAB. Required to run the provided scripts. Please refer to the OpenSim [documentation](https://simtk-confluence.stanford.edu/display/OpenSim/Scripting+with+Matlab).
4. (optional) [OpenSim 3.3](https://simtk.org/projects/opensim). This can be used for visualising the manual models. To install OpenSim 3.3 go to the `Download` page of the provided link and click on `Previous releases`, as shown in [this screenshot](https://github.com/modenaxe/3d-muscles/blob/master/images/get_osim3.3.PNG). No API installation required for OpenSim 3.3.

# Contents
This repository includes:
1. bone geometries
2. STAPLE package as git submodule
3. manual models from previous research
4. automatically generated models
5. some gait simulations
5. MATLAB scripts to recreate the models and tables of the paper.

![modelling_workflow](./images/datasets.png)

# Visulizing the OpenSim models

## Manual models
Manual models can be visualised with OpenSim 3.3. 
The bone geometries are binary vtp files and are NOT visible in OpenSim 4.0
The muscles and virtual markers have been removed from the original models.
These models were generated using NMSBuilder v1.0. The NMSBuilder files are
not shared because of their size (they include medical images).
The complete OpenSim models and the NMSBuilder models can be obtained 
contacting the corresponding author of the publication.

## Automatic models
Automatic models can be visualised with OpenSim 4.1. 
The bone geometries are ASCII files in OBJ format. If they are not present 
in the repository, they will be generated by a_createOsimModels.m during 
the creation of the models from the matlab triangulations included in 
the ./bone_geometries folder.

# Running the MATLAB scripts
The provided MATLAB scripts produce the results described in the following table:
| Script name | Script action | Related item in the manuscript|
| --- | --- | --- |
| createAutomaticOsimModels.m | creates the automatic OpenSim model using the bone geometries from the `bone_geometries` folder | N/A |
| compare_osim_models.m | compares the joint coordinate systems of the automatically generated and the manual OpenSim models | Table 4 |
| compare_hip_fit.m | compares, in all datasets, the estimations of the centres of the femoral head provided by Kai-femur and GIBOC-tibia | Table 4 | 
| compare_pelvis_algorithms.m | compares, in all datasets, the joint coordinate systems estimated by `STAPLE-pelvis` and `Kai-pelvis` algorithms using the former as reference | Table 5 |
| compare_knee_algorithms.m | compares, in all datasets, the joint coordinate systems estimated by all `GIBOC-`, `Kai-` and `Miranda-` algorithms at the distal femur and proximal tibia, i.e. at tibiofemoral joint. `GIBOC-Cylinder` is used as reference | Table 5 |
| suppl_mat_tibiofemoral_alignment.m | compares, in all datasets, the joint coordinate systems estimated by all `GIBOC-tibia`, `Kai-tibia` and `Miranda-tibia` algorithms against the `GIBOC-Cylinder` algorithm for the femur to quantify the tibiofemoral alignment. | Table S1 (Supplementary Material) |
| suppl_mat_compare_PCA_vs_Inertial.m | compares, in all datasets, the vertical anatomical axis of the tibia when computed using principal component analysis as in `Kai-tibia` or principal inertial axes as in all `GIBOC` algorithms for the tibia | Table S2 (Supplementary Material) |

# Limitations and notes about reproducibility
* The presented workflow produced models in OpenSim format, but their structure is actually generic.
* These manual OpenSim models were generated using NMSBuilder v1.0. The NMSBuilder files are not shared because of their size (they include medical images).
The complete NMSBuilder models can be obtained contacting the corresponding author of the publication.
* The STAPLE pack is still in strong development, so documentation might be missing. Please refer to the main repository and to the examples included there.