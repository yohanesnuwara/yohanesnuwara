# Altmann Poroelastic Reservoir Model

> ### See here the [Python script](https://github.com/yohanesnuwara/computational-geophysics/blob/master/altmann2010_poroelasticity.ipynb)

I reproduce the calculation of reservoir stress path from [Altmann et al](https://www.sciencedirect.com/science/article/pii/S136516091000136X). This model is very important as we can observe how stress path changes as we produce from the reservoir, over distance from the wellbore and over time. 

## Intro

The analysis of stress path is very important to understand the impact of fluid depletion and injection on the effective stress change in the reservoir. Stress path is the ratio of minimum horizontal stress change to pore pressure change. In 1994, [Engelder and Fischer](https://www.researchgate.net/publication/249520094_Influence_of_poroelastic_behavior_on_the_magnitude_of_minimum_horizontal_stress_Sh_in_overpressured_parts_of_sedimentary_basins) proposed the formula of stress path for sedimentary rocks. However, the formula doesn't address the effect of time evolution and spatial. 

In 2010, Altmann et al modifies the formula that couples flow and geomechanics, such that now the stress path is a function of time and spatial (distance at one point from the wellbore). In his model, the stress path increases over distance, and decreases over time. At infinite time, the stress path will be equal to the value computed by Engelder and Fischer.

## Workflow

**Case.** The reservoir is composed of sandstone that has drained (dry) bulk modulus of 12 GPa, matrix (grain) bulk modulus of 40 GPa, shear modulus of 5.5 GPa, and hydraulic conductivity of 1x10^-7 m/s. It has porosity of 16.7% and saturated by fluid that has density of 1 g/cc and bulk modulus of 2 GPa.  

Calculate the stress path over the reservoir, from point 0 (wellbore) up to 500 m from the wellbore, over 1 year, 2 years, 5 years, and 20 years of production. 

Steps to do calculation are:
* Compute undrained (saturated) bulk modulus according to Biot-Gassmann fluid substitution
* Compute Biot-Willis coefficient
* Compute Lame's parameter λ for drained and undrained condition
* Compute diffusivity (is a function of hydraulic conductivity)
* Compute 

```
Kd = 12 # drained bulk modulus, GPa
Kg = 40 # grain bulk modulus, GPa
G = 5.5 # shear modulus, GPa
Kf = 2 # fluid bulk modulus, GPa
rhof = 1000 # fluid density, kg/m3
poro = 0.167 # porosity of sandstone
kf = 0.1E-6 # hydraulic conductivity, m/s
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99690483-cb6af480-2aba-11eb-8920-695045ed3422.png" />
</p>

