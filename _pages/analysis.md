---
title: "Data Analysis Method"
layout: archive
permalink: /analysis/
tags:
  - content
toc: true
toc_sticky: true
---

**Work in progress**

**A lot of data analysis and mathematical formulations are done during research. This page showcases how I did them in detail.**

# X-ray Experiments Analysis

## Mathematical Formulation: X-ray Reflectivity

X-ray reflectivity is one of the most powerful tools to characterize the composition of the surface along the surface normal.
The specular reflectivity intensity profile as a function of incident (=reflection) angle contains information about the electron density of the material along the z-axis (when surface is x-y plane).

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \frac{1}{\rho_{\infty}} \int \frac{d \rho (z)}{dz} e^{i Q_{z}z} dz \right| ^{2} $$

Herein, \\(R_{F}(Q_{z})\\) is a normalization factor, \\(Q_{z}\\) is a vector that is determined by energy of the beam and angular difference between incident and reflected beams, \\(\rho(z)\\) is the electron density profile along the z-axis (EDP; what we want to know), and \\(\rho_{\infty}\\) is the electron density of the bulk of the substrate (water in my case). Shortly, the reflectivity shows us **the absolute squre of the Fourier transform of the derivative of the electron density**.

**There is no easy way to calculate the \\(\rho(z)\\) from the equation above directly.** To make this problem solvable, people formulate the model EDP \\(\rho(z)\\) with some fitting parameters and a **Slab Model** is one of the most widely used method. This model consists of several conceptual slabs with uniform electron densities. i-th slab has three fitting parameters: electron density \\(\rho_{i}\\), thickness \\(d_{i}\\), and roughness \\(\sigma_{i}\\). Then the model can be expressed as a sum of the error functions,

$$ \rho(z) = \rho_{0} + \sum_{i=1}^{N} \frac{\rho_{i}-\rho_{i-1}}{2} \left( erf \left( \frac{z-z_{i}}{\sqrt{2}\sigma_{i}} \right) +1 \right) $$

and allow us to deal with more computer-friendly equation:

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \sum_{i=0}^{N} \frac{\rho_{i}-\rho_{i+1}}{\rho_{\infty}} e^{-iQ_{z}d_{i}} e^{-Q_{z}^{2} \frac{\sigma_{i+1}^{2}}{2}} \right|^{2} $$

By minimizing the residual (chi-square) between the collected and the formulated reflectivity, the thickness, electron density, and roughness of each slab are determined.

## Mathematical Formulation: X-ray Fluorescence Near Total Reflection (XFNTR)

XFNTR enable us quantitative analysis of ions adsorbed to the surface. One of the fascinating features about fluorescence technique is that it provides ion-selective information: You can calculate the number density of a "Target Ion" from the mixture sample. X-ray optics near the critical angle is manipulated to assign "surface only" detection of the fluorescence signals.

When a beam incident to a matter from the angle higher than the critical angle (\\(\theta > \theta_{c}\\)), the beam penetrate the surface and reach the bulk. When it is shed from the small angle (\\(\theta < \theta_{c}\\)), the beam no longer penetrates the matter but travel along the surface. This is menisfested by a significant difference in penetration depth before and after the critical angle. (right) The beam intensity right at the surface of the matter is "Fresnel Transmission". (left)

![image-center](../assets/images/Fresnel_Transmission.png){: .align-center}{:style="border: 0px solid black; padding: 10px"}{:height="70%" width="70%"}


* Isotherm
* X-ray reflectivity
* ICP-MS data -> Extraction
* Kinetics of extraction