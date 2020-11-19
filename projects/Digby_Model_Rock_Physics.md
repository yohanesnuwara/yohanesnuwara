# Digby Model: A Rock Physics Model to Estimate Pore Compressibility in Clastic Rocks Change Due to Pressure Drop

I reproduce the rock physics model proposed by Digby (1981) in [his paper](https://asmedigitalcollection.asme.org/appliedmechanics/article-abstract/48/4/803/390095/The-Effective-Elastic-Moduli-of-Porous-Granular?redirectedFrom=fulltext) using Python. 

This model can be important when we deal with reservoir with compressibility drive or reservoir compaction is dominant. People can quantitatively assess how much PV will reduce on a certain pressure drop during production, or how much will increase on a certain pressure buildup during injection or gas storage.

> Link to my Python notebook [here]()

## Intro

Digby (1981) proposed a model that estimates the change of pore volume compressibility due to change of differential pressure. He represented a rock as collection of grains with radius `r` and neighboring bonded particles with radius `a`. While **pore pressure** decreases, space `a` decreases to a new radius `b`. Digby (1981) used term **differential pressure** rather than pore pressure. Differential pressure (effective pressure) is confining pressure minus pore pressure: `P_eff = P_conf - Pp`. A new term, coordination number or `Cp` was also introduced. **Murphy (1982)** stated that `Cp` is proportional to `e^(1-porosity)`.  

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671187-42e15980-2aa4-11eb-9845-6299c95de49e.png" />
</p>

## Workflow

**First**, compute the coordination number of a rock from its porosity. Murphy (1982) theory of proportionality of coordination number `Cp` and porosity. Supposing the real equation that relates both is `Cp = 11.759 * e^(1 - porosity) - 12.748` [(Li and Ma, 2019)](https://ogst.ifpenergiesnouvelles.fr/articles/ogst/full_html/2019/01/ogst190120/ogst190120.html).

The following is result from such correlation.

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671614-db77d980-2aa4-11eb-9901-7397a9d55545.png" />
</p>

**Second**, compute the rock matrix modulus. Supposing a sandstone has **50% porosity**, composed of **50% quartz** and **50% clay minerals**, and **Poisson's ratio of 0.4** (Typically sandstone has `poisson` between 0.1 and 0.4). Mineral bulk moduli (`Km`) and shear moduli (`Gm`) can be computed using **Voigt-Reuss-Hill method**. The following is the result. 

```
Mineral bulk moduli: 27.678304347826085 GPa
Mineral shear moduli: 16.68051724137931 GPa
Mineral density: 2.615 g/cc
```

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671407-95227a80-2aa4-11eb-9335-2571eab37170.png" />
</p>
