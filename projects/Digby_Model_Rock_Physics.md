# Digby Model: A Rock Physics Model to Estimate Pore Compressibility in Clastic Rocks Change Due to Pressure Drop

I reproduce the rock physics model proposed by Digby (1981) in [his paper](https://asmedigitalcollection.asme.org/appliedmechanics/article-abstract/48/4/803/390095/The-Effective-Elastic-Moduli-of-Porous-Granular?redirectedFrom=fulltext) using Python. 

> Link to my Python notebook [here]()

Digby (1981) proposed a model that estimates the change of pore volume compressibility due to change of differential pressure. He represented a rock as collection of grains with radius `r` and neighboring bonded particles with radius `a`. While **pore pressure** decreases, space `a` decreases to a new radius `b`. Digby (1981) used term **differential pressure** rather than pore pressure. Differential pressure (effective pressure) is confining pressure minus pore pressure: `P_eff = P_conf - Pp`. A new term, coordination number or `Cp` was also introduced. **Murphy (1982)** stated that `Cp` is proportional to `e^(1-porosity)`.  

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671187-42e15980-2aa4-11eb-9845-6299c95de49e.png" />
</p>

jAHKJSAA

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671614-db77d980-2aa4-11eb-9901-7397a9d55545.png" />
</p>

jsahiqdsds

<p align="center">
  <img src="https://user-images.githubusercontent.com/51282928/99671407-95227a80-2aa4-11eb-9335-2571eab37170.png" />
</p>
