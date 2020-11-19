# Digby Model: A Rock Physics Model to Estimate Pore Compressibility Change in Clastic Rocks Due to Pressure Drop

I reproduce the rock physics model proposed by Digby (1981) extensively discussed by Li and Ma (2019) in [their paper](https://ogst.ifpenergiesnouvelles.fr/articles/ogst/full_html/2019/01/ogst190120/ogst190120.html) using Python. [Here](https://asmedigitalcollection.asme.org/appliedmechanics/article-abstract/48/4/803/390095/The-Effective-Elastic-Moduli-of-Porous-Granular?redirectedFrom=fulltext) is Digby's original paper. 

This model can be important when we deal with reservoir with compressibility drive or reservoir compaction is dominant. People can quantitatively assess how much PV will reduce on a certain pressure drop during production, or how much will increase on a certain pressure buildup during injection or gas storage.

> Link to my Python notebook [here](https://github.com/yohanesnuwara/computational-geophysics/blob/master/digby1981.ipynb)

## Intro

Digby (1981) proposed a model that estimates the change of matrix compressibility due to change of differential pressure. He represented a rock as collection of grains with radius `r` and neighboring bonded particles with radius `a`. While **pore pressure** decreases, space `a` decreases to a new radius `b`. Digby (1981) used term **differential pressure** rather than pore pressure. Differential pressure (effective pressure) is confining pressure minus pore pressure: `P_eff = P_conf - Pp`. 

Actually Digby not explicitly solved for PV compressibility (he proposed model for matrix compressibility), but we can use [**Zimmerman (1986)**](https://www.researchgate.net/publication/220010850_Compressibility_of_Porous_Rocks) model to compute the PV compressibility from its relation with matrix compressibility.

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671187-42e15980-2aa4-11eb-9845-6299c95de49e.png" />
</p>

## Workflow

**First**, compute the coordination number `Cp` of a rock from its porosity. **Murphy (1982)** stated that `Cp` is proportional to `e^(1-porosity)`. Supposing the real equation that relates both is `Cp = 11.759 * e^(1 - porosity) - 12.748` (Li and Ma, 2019).

The following is result from such correlation.

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671614-db77d980-2aa4-11eb-9901-7397a9d55545.png" />
</p>

Supposing a sandstone has **20% porosity**, the coordination number therefore is 13.42.

**Second**, compute the rock matrix modulus. Supposing the sandstone is composed of **50% quartz** and **50% clay minerals**, and **Poisson's ratio of 0.4** (Typically sandstone has `poisson` between 0.1 and 0.4). Mineral bulk moduli (`Km`) and shear moduli (`Gm`) can be computed using **Voigt-Reuss-Hill model** (we can also use other model e.g. Hashin-Shtrikman model). The following is the result. 

```
Mineral bulk moduli: 27.678 GPa
Mineral shear moduli: 16.6811 GPa
Mineral density: 2.615 g/cc
```

**Third**, define the differential pressure. Pressure differential is confining pressure (can be caused by overburden) minus pore pressure. Supposing the sandstone is confined with 70 MPa of `P_conf` and has 60 MPa of `Pp`, thus the pressure differential is 10 MPa. 

**Fourth**, use Digby model to compute the matrix compressibility. First, we specify the ratio of grain radius `a/R` and solve a cubic equation where the root of it is `d`. After we found `d`, we calculate the deformed radius `b/R`. Finally, we calculate the dry matrix bulk modulus. The computed bulk modulus is 14.51 GPa. 

> Remember that bulk modulus is inverse of compressibility. 

**Finally**, use Zimmerman to calculate PV compressibility. The final result is 34.46 microsip.

## Conclusion

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671407-95227a80-2aa4-11eb-9335-2571eab37170.png" />
</p>
