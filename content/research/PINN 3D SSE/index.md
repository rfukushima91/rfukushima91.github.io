---
title: Estimation of Spatially Variable Frictional Properties with Physics-Informed Neural Networks
date: 2024-03-31
links:
  - type: cite
    # url: https://github.com/pandas-dev/pandas
    url: https://doi.org/10.1029/2024JB030256
# tags:
#   - Hugo
#   - HugoBlox
#   - Markdown
---
Applied Physics-Informed Neural Networks (PINNs) to the simulation of a slow slip event with the
Boundary Integral Element Method in a 2D planar fault plane.

### Abstract

Slow Slip Events (SSEs), which are characterized by slower slip velocity and longer duration than regular earthquakes, have been observed in many subduction zones. Whether slip is seismic or slow might reflect different frictional properties of the subducting plate interface. 

However, inferring the frictional properties of a subduction interface and their spatial variations is a challenge that requires matching a dynamical model of fault slip to geodetic observations, for example, GNSS time series, using some inversion technique. The difficulty arises from the non-linearity of the dynamical model and the computational cost of the forward problem. 

In this paper, we address this challenge by employing a Physics-Informed Neural Network (PINN). We conducted the inversions for the frictional parameters from two types of synthetic observation data; slip velocity on the plate interface and displacement velocity on the surface. 

In the former inversion, the PINN-based method successfully estimates the frictional parameters. In the latter inversion, the geometry and friction properties of the velocity weakening region, the SSE fault patch, are successfully recovered, although frictional properties in the velocity strengthening region are not estimated well. Our results show the potential of the PINN-based method to estimate the spatial distribution of friction from GNSS observations.

### Paper
Fukushima, R., Kano, M., Hirahara, K., Ohtani, M., Im, K., & Avouac, J.-P. (2025). Physics-informed deep learning for estimating the spatial distribution of frictional parameters in slow slip regions. Journal of Geophysical Research: Solid Earth, 130, e2024JB030256.

<!--more-->
