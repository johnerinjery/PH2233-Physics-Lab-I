# Stefan's Law

Stefan's Law, or Stefan-Boltzmann's Law gives the proportionality relation between the fourth power of temperature and power emitted by a perfect black body.

$$
P = \sigma T^{4}
$$

## Overview

In this experiment we use a voltmeter and an ammeter to measure current at various voltage settings and calculate power using the relation $P = VI$.

Temperature is measured by using resistance as a proxy. As resistance $R := V/I$, we solve the quadratic relation $R(T) = R_{0}[1 + \alpha T + \beta T^{2}]$ for temperature to calculate temperature.

## Flow of the program

1. Define all constants as given in LM. Only measured quantitites are voltage (V) and current (I). Store the measurements in corresponding arrays. The first value in both arrays must correspond to the "Glowing Temperature" measurement. The variables dV and dA are the least counts (uncertainities) in voltage and current, respectively.

2. Calculate mean resistance $R$, and uncertainity in resistance $dR$. $R_{0}$ is calculated using the zero index values from V, I, and using $T_{G} = 800K$ (Glowing temperature of Tungsten)

3. Calculating temperature and its uncertainity involves solving the quadratic in T for every value of resistance calculated. We do this using the SciPy function <a href="https://docs.scipy.org/doc/scipy-1.16.2/reference/generated/scipy.optimize.bisect.html">`scipy.optimize.bisect`</a>. We solve for T using R for mean value of T. Then we measure $T_{m}:=T(R+dR)$ and $T_{p}:=T(R-dR)$ and average them to calculate uncertainity in temperature $\delta T:= \frac{T_{p} - T_{m}}{2}$

4. Then it is straight forward calculation of power and its uncertainity, plotting graphs with error bars, and saving data.

## Notes

Error in resistance and and power is calculated using the formula given below, if $A = B \times C$ or $A = B / C$

$$
\delta A = A \sqrt{\left(\frac{\delta B}{B}\right)^2 + \left(\frac{\delta C}{C}\right)^2}
$$

and the uncertainity in temperature is calculated as described previously.
