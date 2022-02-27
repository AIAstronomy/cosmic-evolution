# Cosmic evolution in galaxies with active nucleus 

Determine and underlying trend in Type I Active nucleai Galaxies using a novel algorithm that detects one-dimensional sequences in complex datasets.

[Document of the Master Thesis](https://1drv.ms/w/s!AhVCX2iWzgmbhQgoTzNTDx9adnzd?e=Y8L41l)

## Table of Contents

- [Overview](#overview)
- [Authors](#Authors)
- [Requirements](#requirements)
- [How it works](#requirements2)
- [Example Directory](#directory)
- [Selected Results](#acknowledgement)
- [References](#references)

## Overview

The Sequencer (Dalya Baron, https://arxiv.org/abs/2006.13948) is an algorithm that attempts to reveal the main sequence in a dataset, if it exists. To do so, it reorders objects within a set to produce the most elongated manifold describing their similarities which are measured in a multi-scale manner and using a collection of metrics. To be generic, it combines information from four different metrics: the Euclidean Distance, the Kullback-Leibler Divergence, the Monge-Wasserstein or Earth Mover Distance, and the Energy Distance. It considers different scales of the data by dividing each object in the input data into separate parts (chunks), and estimating pair-wise similarities between the chunks. It then aggregates the information in each of the chunks into a single estimator for each metric+scale.

The Sequencer is essentially an Unsupervised Dimensionality Reduction algorithm, since a sequence is a one-dimensional embedding of the input dataset.

Our goal is to explore the information content of AGN spectra, in particular the shape of some of the most important emission lines such as the hydrogen Balmer lines. To do
so, we use spectroscopic data from the QSOfit catalog created and analyzed Calderone et al. 2017 (MNRAS, 72,4), which includes 71252 Type I QSOs between redshifts of 0 < z < 2 (https://arxiv.org/abs/1612.01580)

This work also allows the creation of any dataset from a SDSS catalog, by automatically downloading the spectra files from any object based on its redshift, and implementing the data engineering neeed to create a dataset that can be used with the sequencer algorithm. This will allow for researchers to investigate trends in multiple emission lines and redshift interval for any objects needed.

For the initial work, we select systems with z < 0.3 so that the observed Hα emission line stays at wavelengths shorter than 8500˚ A, This reduces the sample size to 1937 AGN. 

Calderone et al. 2017 present a catalogue of measured properties for these AGN which includes continuum and emission lines measurements around the Hα, Hβ, MgII, and CIV emission lines. 

In order to estimate the continuum flux, we shift the spectra to rest-frame wavelength and then interpolate them to a common wavelength grid from 4000˚ A to 7000˚ A with 1A resolution. This dataset is analyzed by the novel algorithm to find the underlying trend of created dataset.


## Authors

- Moras Acosta, Manuel David (manomoras@gmail.com)
- Guzmán-Álvarez, César Augusto (Universidad Internacional de Valencia)

## Requirements

This work is implemented in python and for both the Dataset engineering and the Sequencer algorithm, requires the following:

- python 3.7.1
- numpy 1.18.1
- scipy 1.3.1
- matplotlib 3.5.1
- astropy 5.0.1
- requests 2.27.1
- networkx 2.4

## How it works

All code used in this project is available inside [`src/`](src) directory. It is written in Python.

Step 1: Download catalog and spectra data per AGN
Step 2: Normaliza spectra to rest frame wavelength
Step 3: Interpolated to a 4000 to 7000 common wavelength
Step 4: Cubic Spline interpolation to estimate flux distribution
Step 5: Remove continuum estimates
Step 6: define Sequencer object (metrics and scales and seq function)
Step 7: Execute sequencer object
Step 8: Final output of secuence: final elongation of the dataset

For more information see: [src/README.md](src/README.md)

## Example Directory

The [dataset directory](https://github.com/br0ly23/cosmic-evolution/tree/main/dataset) contains several Jupyter notebooks that illustrate different aspects of the Sequencer algorithm. Users who are not familiar with the Sequencer are encouraged to go through the examples in the following order:
1. `basic_sequencer_functionalities.ipynb`: this notebook shows the basic functionalities of the algorithm. It shows how to apply the Sequencer to a simple simulated dataset with default settings. It shows how to extract various interesting properties of the algorithm, such as the intermediate elongations obtained during the calculation. It then shows some non-default settings that the user should be aware of (parallelization, varying scales, output options). 
2. `comparison_with_tsne_and_umap.ipynb`: this notebook compares the Sequencer output to the one-dimensional embedding by tSNE and UMAP for a simulated dataset. Importantly, this notebook presents a method to define a general figure of merit for Dimensionality Reduction algorithms that can be used to optimize their hyper-parameters. Using this figure of merit, we can optimize the hyper-parameters of tSNE and UMAP and compare their resulting sequence to the one obtained with the Sequencer.
3. `visualizing_the_MST.ipynb`: this notebook shows how to extract the resulting final Minimum Spanning Tree and how to visualize it with the `networkx` package.
4. `examples_with_natural_images.ipynb`: this notebook shows examples with scrambled natural images. In this notebook, the rows of different natural images are shuffled, and then the Sequencer is applied to the shuffled dataset with the goal of recovering the original image. Finally, the notebook shows the application of tSNE and UMAP to the shuffled images, while varying their hyper-parameters. It illustrates the importance of defining a figure of merit to optimize the hyper-parameters of dimensionality reduction algorithms (the user should go over the notebook `comparison_with_tsne_and_umap.ipynb` before going over this notebook).
5. `importance_of_multi_scale_approach.ipynb`: this notebook applies the Sequencer to stellar spectra, which are 1D objects with relevant information on many different scales (both small scales and large scales). The notebook shows how to extract the intermediate elongations of different chunks of data, and using these, illustrates the importance of the multi-scale approach of the Sequencer.
6. `beyond_1D_sequence.ipynb`: the Sequencer provides a one-dimensional embedding of the input dataset. This notebook shows how we can go beyond a 1D sequence using a method somewhat similar to PCA: once the main trend in the data is detected, we can 'strip' it from the data, and apply the Sequencer to detect the second strongest trend in the data, and so on. 
7. `two_dimensional_objects.ipynb`: so far, we applied the Sequencer to datasets consisting of 1D objects. This notebook shows how to apply the Sequencer to a dataset consisting of 2D objects (images).

## Selected results

## References


