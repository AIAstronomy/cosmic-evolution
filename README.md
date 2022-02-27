# Cosmic evolution in galaxies with active nucleus 

Determine and underlying trend in Type I Activne nucleai Galaxies using a novel algorithm that detects one-dimensional sequences in complex datasets.

[Document of the Master Thesis](https://1drv.ms/w/s!AhVCX2iWzgmbhQgoTzNTDx9adnzd?e=Y8L41l)

## Table of Contents

- [Overview](#overview)
- [Authors](#Authors)
- [Requirements](#requirements)
- [How to use the algorithm](#How to use the algorithm)
- [Example Directory](#directory)
- [Selected Results](#acknowledgement)
- [References](#references)

## Overview

The Sequencer (Dalya Baron, https://arxiv.org/abs/2006.13948) is an algorithm that attempts to reveal the main sequence in a dataset, if it exists. To do so, it reorders objects within a set to produce the most elongated manifold describing their similarities which are measured in a multi-scale manner and using a collection of metrics. To be generic, it combines information from four different metrics: the Euclidean Distance, the Kullback-Leibler Divergence, the Monge-Wasserstein or Earth Mover Distance, and the Energy Distance. It considers different scales of the data by dividing each object in the input data into separate parts (chunks), and estimating pair-wise similarities between the chunks. It then aggregates the information in each of the chunks into a single estimator for each metric+scale.

The Sequencer is essentially an Unsupervised Dimensionality Reduction algorithm, since a sequence is a one-dimensional embedding of the input dataset.

Our goal is to explore the information content of AGN spectra, in particular the shape of some of the most important emission lines such as the hydrogen Balmer lines. To do
so, we use spectroscopic data from the QSOfit catalog created and analyzed Calderone et al. 2017 (MNRAS, 72,4), which includes 71252 Type I QSOs between redshifts of 0 < z < 2 (https://arxiv.org/abs/1612.01580)

We select systems with z < 0:3 so that the observed Hα emission line stays
at wavelengths shorter than 8500˚ A, above which residual telluric lines become non-negligible. This reduces the sample size to 1941 AGN. 
Calderone et al. 2017 present a catalogue of measured properties for these AGN which includes continuum and emission lines measurements around the Hα, Hβ, MgII, and CIV emission lines. 

In order to estimate the continuum flux, we shift the spectra to rest-frame wavelength and then interpolate them to a common wavelength grid from 4000˚ A to 7000˚ A with 1A resolution. This dataset is analyzed by the novel algorithm to find the underlying trend of the QSOs catalog.


## Authors

- Moras Acosta, Manuel David (manomoras@gmail.com)
- Guzmán-Álvarez, César Augusto (Universidad Internacional de Valencia)


## Requirements

The Sequencer is implemented in python and requires the following:

- python 3.7.1
- numpy 1.18.1
- scipy 1.3.1
- networkx 2.4
To run the Jupyter notebooks in the examples directory, and to compare the Sequencer to tSNE and UMAP, you will also need:

matplotlib 3.1.2
scikit-learn 0.22.1 (to run tSNE)
umap 0.3.9 (to run UMAP; https://github.com/lmcinnes/umap)


## How to use the algorithm

All code used in this project is available inside [`src/`](src) directory. It is written in C/C++.

For more information see: [src/README.md](src/README.md)

## Example Directory

## Selected results

## References


