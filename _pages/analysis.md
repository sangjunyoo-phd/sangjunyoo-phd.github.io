---
title: "Data Analysis Method"
layout: splash
permalink: /analysis/
---

A lot of data analysis and mathematical formulations are done during research. This page showcases how I did them in detail.

## X-ray Reflectivity Analysis

X-ray reflectivity is one of the most powerful tools to characterize the composition of the surface along the surface normal.
The specular reflectivity intensity profile as a function of incident (=reflection) angle contains information about the electron density of the material along the z-axis (when surface is x-y plane).

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \frac{1}{\rho_{\infty}} \int \frac{d \rho (z)}{dz} e^{i Q_{z}z} dz \right| ^{2} $$

Herein, \\(R_{F}(Q_{z})\\) is a normalization factor, \\(Q_{z}\\) is a vector that is determined by energy of the beam and angular difference between incident and reflected beams, \\(\rho(z)\\) is the electron density along the z-axis (what we want to know), and 
\\(\rho_{\infty}\\) is the electron density of the bulk of the substrate (water in my case).

There is no easy way to fit the data with the equation above directly. Instead, formulating the model electron density profile \\(\rho(z)\\) with some fitting parameters is one of the most widely used method.

* Isotherm
* X-ray reflectivity
* ICP-MS data -> Extraction
* Kinetics of extraction