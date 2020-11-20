# Altmann Poroelastic Reservoir Model

I reproduce

## Intro

The analysis of stress path is very important to understand the impact of fluid depletion and injection on the effective stress change in the reservoir. Stress path is the ratio of minimum horizontal stress change to pore pressure change. In 1994, [Engelder and Fischer](https://www.researchgate.net/publication/249520094_Influence_of_poroelastic_behavior_on_the_magnitude_of_minimum_horizontal_stress_Sh_in_overpressured_parts_of_sedimentary_basins) proposed the formula of stress path for sedimentary rocks. However, the formula doesn't address the effect of time evolution and spatial. 

In 2010, [Altmann et al](https://www.sciencedirect.com/science/article/pii/S136516091000136X) modifies the formula that couples flow and geomechanics, such that now the stress path is a function of time and spatial (distance at one point from the wellbore). 

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

