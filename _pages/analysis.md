---
title: "Data Analysis Method for Research Projects"
permalink: /analysis/
toc: true
toc_sticky: true
---

**Work in progress**

# 1. X-ray Experiments Analysis

## 1.1. X-ray Scattering Image Processing
![image-center](../assets/images/exp_setup.png){: .align-center}{:style="border: 0px solid black; padding: 10px"}{:height="75%" width="75%"}
__X-ray reflectivity experiment setup. The blue box represents the Area Detector.__ <br/>

The X-ray signal reflected from a surface contains valuable information about the material's composition. X-ray area detector is positioned accordingly to the incident angle to optimally collect signals from the reflected X-ray beam. Image processing should be preceded to properly analyze the X-ray reflectivity data.

## 1.2. Mathematical Formulation: X-ray Reflectivity

X-ray reflectivity is one of the most powerful tools to characterize the composition of the surface along the surface normal.
The specular reflectivity intensity profile as a function of incident (=reflection) angle contains information about the electron density of the material along the z-axis (when a surface is an XY plane).

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \frac{1}{\rho_{\infty}} \int \frac{d \rho (z)}{dz} e^{i Q_{z}z} dz \right| ^{2} $$

Herein, \\(R_{F}(Q_{z})\\) is a normalization factor, \\(Q_{z}\\) is a vector that is determined by the energy of the beam and angular difference between incident and reflected beams, \\(\rho(z)\\) is the electron density profile along the z-axis (EDP; what we want to know), and \\(\rho_{\infty}\\) is the electron density of the bulk of the substrate (water in my case). Shortly, the reflectivity shows us **the absolute square of the Fourier transform of the derivative of the electron density**.

**There is no easy way to calculate the \\(\rho(z)\\) from the equation above directly.** To make this problem solvable, people formulate the model EDP \\(\rho(z)\\) with some fitting parameters, and a **Slab Model** is one of the most widely used methods. This model consists of several conceptual slabs with uniform electron densities. The i-th slab has three fitting parameters: electron density \\(\rho_{i}\\), thickness \\(d_{i}\\), and roughness \\(\sigma_{i}\\). Then the model can be expressed as a sum of the error functions,

$$ \rho(z) = \rho_{0} + \sum_{i=1}^{N} \frac{\rho_{i}-\rho_{i-1}}{2} \left( erf \left( \frac{z-z_{i}}{\sqrt{2}\sigma_{i}} \right) +1 \right) $$

and allow us to deal with a more computer-friendly equation:

$$ \frac{R(Q_{z})} {R_{F} (Q_{z})} = \left| \sum_{i=0}^{N} \frac{\rho_{i}-\rho_{i+1}}{\rho_{\infty}} e^{-iQ_{z}d_{i}} e^{-Q_{z}^{2} \frac{\sigma_{i+1}^{2}}{2}} \right|^{2} $$

By minimizing the residual (chi-square) between the collected and the formulated reflectivity, the thickness, electron density, and roughness of each slab are determined.

## 1.3. Mathematical Formulation: X-ray Fluorescence Near Total Reflection (XFNTR)

XFNTR enables quantitative analysis of ions adsorbed to the surface. One of the fascinating features of the fluorescence technique is that it provides ion-selective information: You can calculate the number density of a "Target Ion" from the mixture sample. X-ray optics near the critical angle is manipulated to assign "surface only" detection of the fluorescence signals.

When a beam meets the surface of matters, the incident beam is either reflected or transmitted (or refracted). The transmitted portion of the incident light can interact with matters and allow us to characterize the matter. The transmission (\\(T\\)) is sensitive to the angle of incidence. (See the graph below) From an angle higher than the critical angle (\\(\theta > \theta_{c}\\)), the beam penetrates the surface and reaches the bulk. The distance that the beam penetrates the matter is called "penetration depth (\\(\Lambda\\))". When the surface is shed from the small angle (\\(\theta < \theta_{c}\\)), the beam no longer penetrates the matter (only a few nano-meters) but travels along the surface. This is manifested by a significant difference in penetration depth before and after the critical angle.

![image-center](../assets/images/Fresnel_Transmission.png){: .align-center}{:style="border: 0px solid black; padding: 10px"}{:height="70%" width="70%"}

The fluorescence signal from an atom is linearly correlated with the beam intensity (by \\(C\\)) that reaches the location of the atom. Considering that the "surface-only" mode described above, it is reasonable to split the overall fluorescence signal intensity to **surface**, **bulk**, and background noise terms. When varaibles are defined as a picture below, the fluorescence signal intensity can be formulated as a following equation.

![image-center](../assets/images/XFNTR_setup.png){: .align-center}{:style="border: 0px solid black; padding: 10px"}{:height="70%" width="70%"}

$$\begin{align}\frac{I}{I_{0}} = & \frac{C}{A_{ion}} \int T(\alpha) e^{-\mu_{0}x'}dx'\\
& + C \cdot n_{ion} \int \int T(\alpha) e^{-|z|/\Lambda (\alpha)} e^{-\mu_{0}x'} dx'dz\\
& + I_{bg}/I_{0}
\end{align}$$

There is an assumption regarding the ion distribution near the surface. 

# 2. Kinetic Model of Solvent Extraction (ICP-MS)

## 2.1. Order of Chemical Reaction
What is chemical reaction order and how to determine.

## 2.2. Data Engineering: ICP-MS signal to Extraction Performance
How did I change ICP-MS data to Extraction curve.   
Include code

## 2.3. Non-Linear Regression and Its Interpretation
Exponentials and their interpretation

# 3. Isotherm of Langmuir Monolayer
Brief description of Langmuir monolayer

## 3.1. Trouble Shooting: Langmuir Trough and the Barrier Position
Malfunctioning barrier position sensor.

## 3.2. Software Approach Problem Solving
Include code