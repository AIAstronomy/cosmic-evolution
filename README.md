# Cosmic evolution in galaxies with active nucleus 

Determine and underlying trend in Type I Active nucleai Galaxies using a novel algorithm that detects one-dimensional sequences in complex datasets.

[Document of the Master Thesis](https://1drv.ms/w/s!AhVCX2iWzgmbhQx2upIgj9bBrJfO?e=70VReI)

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
- pandas 1.4.1
- scipy 1.3.1
- matplotlib 3.5.1
- astropy 5.0.1
- requests 2.27.1
- networkx 2.4

## How it works

All code used in this project is available inside [`main/`](main) directory. It is written in Python.

- Step 1: Download catalog and spectra data per AGN
- Step 2: Normaliza spectra to rest frame wavelength
- Step 3: Interpolated to a 4000 to 7000 common wavelength
- Step 4: Cubic Spline interpolation to estimate flux distribution
- Step 5: Remove continuum estimates
- Step 6: define Sequencer object (metrics and scales and seq function)
- Step 7: Execute sequencer object
- Step 8: Final output of secuence: final elongation of the dataset

For more information see: [src/README.md](src/README.md)

## Example Directory

The [main directory](https://github.com/br0ly23/cosmic-evolution/tree/main) contains several Jupyter notebooks that illustrate different aspects of the Sequencer algorithm. Users who are not familiar with the Sequencer are encouraged to go through the examples in the following order:
1. `ACE - Download Raw spectra data.ipynb`: This notebook contains the initial data wrangling of the main catalogue of spectral properties of Type 1 AGN (observed with SDSS DR10) which later is filter down for this work, to objects with redshift < 0.5, This parameter can be changed to contain the full catalog (z < 2). Afterwards it saves the relevant information for future steps in a json file.
2. `CE1 - Reproducion Dalya Dataset.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift less than 0.3, same parameters used in the Black hole estimation study by Dalya Baron (https://arxiv.org/abs/1903.01996). Firts it dowloads the necessary spectra for each object and further normalized it as explain on the "How it works" session. Once normalized it is send to the sequencer to find out the sequence present. The final output is shown on the MST graph.
3. `CE1 - Sequence for Redshift between less than 0.1.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift less than 0.1. following the same steps and the above notebook.
4. `CE1 - Sequence for Redshift between 0.1 and 0.2.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.1 and 0.2, following the same steps and the above notebook.
5. `CE1 - Sequence for Redshift between 0.2 and 0.3.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.2 and 0.3, following the same steps and the above notebooks.
6. `CE1 - Sequence for Redshift between 0.2 and 0.3.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.2 and 0.3, following the same steps and the above notebooks.
7. `CE1 - Sequence for Redshift between 0.3 and 0.5.ipynb`: This notebook analyze the sequence present in QSO objects with a redshift between 0.2 and 0.3, following the same steps and the above notebooks.

## Selected results

###QSOs with redshift < 0.3

Below the 1937 QSO's flux spectra normalized in no particular order:

[](dataset/1937 qso.png)



## References

- Antonucci, R. (1993). Antonucci, R. Annual Review of Astronomy and Astrophysics, 473-521. doi:10.1146/annurev.aa.31.090193.002353
- Baron, D. (2020, June 26). Extracting the main trend in a dataset. Retrieved from https://arxiv.org/pdf/2006.13948.pdf: https://arxiv.org/pdf/2006.13948.pdf
- Beaklini, E. A. (n.d.). UNAM. Retrieved from Galxias de nucleo activo: http://www.comoves.unam.mx/numeros/articulo/192/galaxias-de-nucleo-activo
- Bock, T. (n.d.). What is Distance Matrix? Retrieved from What is Distance Matrix?: https://www.displayr.com/what-is-a-distance-matrix/
- Boroson, T. A. (1992, May). The Emission-Line Properties of Low-Redshift Quasi-stellar Objects. ApJS, 80, 109. doi:10.1086/191661
- C. Ramos Almeida, N. A.-H.-S. (2011). Retrieved from https://arxiv.org/abs/1101.3335
- Chem, E. (n.d.). Retrieved from https://www.chemeurope.com/en/encyclopedia/Doppler_broadening.html
- Calderone et al. 2017. QSFit: Automatic analysis of optical AGN spectra. Retrieved from https://arxiv.org/abs/1612.01580
- Dayla Baron, B. M. (2020). Black hole mass estimation for Active Galactic Nuclei from a new angle. Retrieved from https://arxiv.org/abs/1903.01996
- Geophysics, I. (2002). Pressure Broadening. Retrieved from An Introduction to Atmospheric Radiation: https://www.sciencedirect.com/topics/earth-and-planetary-sciences/pressure-broadening
- Ghosh, D. (2019). KL Divergence for Machine Learning. Retrieved from The RL Probabilist: https://dibyaghosh.com/blog/probability/kldivergence.html
- Glenn, N. (n.d.). analystanswers.com. Retrieved from https://analystanswers.com/data-normalization-techniques-easy-to-advanced-the-best/
- Hil, C. (2016). Learning Scientific Programming with Python. Cambridge University Press . Retrieved from The Voigt profile: https://scipython.com/book/chapter-8-scipy/examples/the-voigt-profile/
- John A. Lee, M. V. (2010). Scale-independent quality criteria for dimensionality reduction. Retrieved from https://doi.org/10.1016/j.patrec.2010.04.013
- Lorentz. (1906). Retrieved from https://www.sjsu.edu/faculty/watkins/lorentzline.htm
- Maaten, L. v., & Hinton, G. (2008). t-SNE. Journal of Machine Learning Research, 26.
- Mi Sistema Solar. (n.d.). Retrieved from https://misistemasolar.com/galaxias-activas/
- Pettie, S., & Ramachandran, V. (2002). An Optimal Minimum Spanning Tree Algorithm. Journal of the ACM, Vol 29 No 1, 16-34. Retrieved from https://www.ijcaonline.org/journal/number8/pxc387321.pdf
- Prabhakaran, S. (2019, March 23). ML+. Retrieved from https://www.machinelearningplus.com/machine-learning/principal-components-analysis-pca-better-explained/
- R.D. Blandford, H. N. (1990). Retrieved from https://ned.ipac.caltech.edu/level5/March02/Netzer/paper.pdf
- Rizzo, M. L., & Székely, G. J. (2015, December 28). Energy Distance. WIREs Computational Statistics, 27-38. doi:https://doi.org/10.1002/wics.1375
- Robert Sedgewick, K. W. (2011). Algorithms. In K. W. Robert Sedgewick, Algorithms. 
- Shen, Y. H. (2014). The diversity of quasars unified by accretion and orientation. Nature, 210-213. doi:10.1038/nature13712
- TANIGUCHI, Y. (2019). Understanding the Breadth-First Search with Python. Retrieved from Understanding the Breadth-First Search with Python: https://medium.com/@yasufumy/algorithm-breadth-first-search-408297a075c9
- Wattenberg, e. a. (2016). "How to Use t-SNE Effectively". Retrieved from Distill: http://doi.org/10.23915/distill.00002
- Y. Rubner, C. T. (1998). The Earth Mover's Distance. IEEE International Conference on Computer Vision, 59-66. Retrieved from http://doi.org/10.1023/A:1026543900054
- YORK, D. G. (2000). The Sloan Digital Sky Survey: Technical Summary. The Astronomical Journal, 120, 1579-1587. doi:10.1086/301513




