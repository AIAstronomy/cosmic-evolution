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

The [main directory](https://github.com/br0ly23/cosmic-evolution/tree/main) contains several Jupyter notebooks that illustrate different aspects of the Sequencer algorithm. Users who are not familiar with the Sequencer are encouraged to go through the examples in the following order:
1. `ACE - Download Raw spectra data.ipynb`: This notebook contains the initial data wrangling of the main catalogue of spectral properties of Type 1 AGN (observed with SDSS DR10) which later is filter down for this work, to objects with redshift < 0.5, This parameter can be changed to contain the full catalog (z < 2). Afterwards it saves the relevant information for future steps in a json file.
2. `CE1 - Reproducion Dalya Dataset.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift less than 0.3, same parameters used in the Black hole estimation study by Dalya Baron (https://arxiv.org/abs/1903.01996). Firts it dowloads the necessary spectra for each object and further normalized it as explain on the "How it works" session. Once normalized it is send to the sequencer to find out the sequence present. The final output is shown on the MST graph.
3. `CE1 - Sequence for Redshift between less than 0.1.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift less than 0.1. following the same steps and the above notebook.
4. `CE1 - Sequence for Redshift between 0.1 and 0.2.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.1 and 0.2, following the same steps and the above notebook.
5. `CE1 - Sequence for Redshift between 0.2 and 0.3.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.2 and 0.3, following the same steps and the above notebooks.
6. `CE1 - Sequence for Redshift between 0.2 and 0.3.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.2 and 0.3, following the same steps and the above notebooks.
7.`CE1 - Sequence for Redshift between 0.3 and 0.5.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.2 and 0.3, following the same steps and the above notebooks.

## Selected results

## References


