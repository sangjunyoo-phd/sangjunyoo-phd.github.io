---
title: "Data Analysis Method"
layout: splash
permalink: /analysis/
---

A lot of data analysis and mathematical formulations are done during research. This page showcases how I did them in detail.

# X-ray Reflectivity Analysis

## Mathematical Formulation

X-ray reflectivity is one of the most powerful tools to characterize the composition of the surface along the surface normal.
The specular reflectivity intensity profile as a function of incident (=reflection) angle contains information about the electron density of the material along the z-axis (when surface is x-y plane).

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \frac{1}{\rho_{\infty}} \int \frac{d \rho (z)}{dz} e^{i Q_{z}z} dz \right| ^{2} $$

Herein, \\(R_{F}(Q_{z})\\) is a normalization factor, \\(Q_{z}\\) is a vector that is determined by energy of the beam and angular difference between incident and reflected beams, \\(\rho(z)\\) is the electron density profile along the z-axis (EDP; what we want to know), and \\(\rho_{\infty}\\) is the electron density of the bulk of the substrate (water in my case). Shortly, the reflectivity shows us **the absolute squre of the Fourier transform of the derivative of the electron density**.

**There is no easy way to calculate the \\(\rho(z)\\) from the equation above directly.** To make this problem solvable, people formulate the model EDP \\(\rho(z)\\) with some fitting parameters and a **Slab Model** is one of the most widely used method. This model consists of several conceptual slabs with uniform electron densities. i-th slab has three fitting parameters: electron density \\(\rho_{i}\\), thickness \\(d_{i}\\), and roughness \\(\sigma_{i}\\). Then the model can be expressed as a sum of the error functions,

$$ \rho(z) = \rho_{0} + \sum_{i=1}^{N} \frac{\rho_{i}-\rho_{i-1}}{2} \left( erf \left( \frac{z-z_{i}}{\sqrt{2}\sigma_{i}} \right) +1 \right) $$

and allow us to deal with more computer-friendly equation:

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \sum_{i=0}^{N} \frac{\sigma_{i}-\sigma_{i+1}}{\sigma_{\infty}} e^{-iQ_{z}d_{i}} e^{-Q_{z}^{2} \frac{\sigma_{i+1}^{2}}{2}} \right|^{2} $$

* Isotherm
* X-ray reflectivity
* ICP-MS data -> Extraction
* Kinetics of extraction