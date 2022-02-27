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

## Authors

- Moras Acosta, Manuel David (manomoras@gmail.com)
- Guzmán-Álvarez, César Augusto (Universidad Internacional de Valencia)


## Requirements

![image](https://user-images.githubusercontent.com/15159632/111384462-d2d98d80-86a9-11eb-8b58-5c0a937c8351.png)


## How to use the algorithm

All code used in this project is available inside [`src/`](src) directory. It is written in C/C++.

For more information see: [src/README.md](src/README.md)

## Example Directory

## Selected results

## References


