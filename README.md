# Enzyme Kinetics: Michaelis-Menten Fitting and Inhibition Analysis

**Estimating kinetic parameters from experimental data and identifying the type of enzyme inhibition.**

<p align="center">
  <img src="images/dataI258_fit.png" width="480" alt="Lineweaver-Burk plot for three inhibitor concentrations">
</p>

`Python` · `SciPy (curve_fit)` · `NumPy` · `pandas` · `Matplotlib` · `Jupyter`

---

## What this covers

**1. Michaelis-Menten model.** The rate law

$$V = \frac{V_{max}\,[S]}{K_m + [S]}$$

is explored for different values of $K_m$ and $V_{max}$. The notebook also discusses the quasi-steady-state assumptions ($[S] \gg [E]$) and why $V_{max} = k_2 [E]_{total}$.

**2. Parameter estimation from data.** $K_m$ and $V_{max}$ are estimated from measured rates in two ways:

| Method | $V_{max}$ | $K_m$ |
|---|---|---|
| Nonlinear least squares on the Michaelis-Menten curve | 9.95 | 0.462 |
| Linear fit of the Lineweaver-Burk transform ($1/V$ vs. $1/[S]$) | 9.92 | 0.437 |

The two agree within 0.4% for $V_{max}$ and 5.5% for $K_m$. The Lineweaver-Burk transform is convenient but amplifies noise at low $[S]$, so the direct nonlinear fit is the more reliable estimator.

**3. Inhibition.** Competitive, uncompetitive and noncompetitive inhibition models are implemented and compared, both as rate curves and as Lineweaver-Burk plots:

$$V_{comp} = \frac{V_{max}[S]}{(1 + [I]/K_i)K_m + [S]}, \quad V_{uncomp} = \frac{V_{max}[S]}{K_m + (1 + [I]/K_i)[S]}, \quad V_{noncomp} = \frac{V_{max}[S]}{(1 + [I]/K_i)(K_m + [S])}$$

For the experimental data at three inhibitor concentrations ($[I]$ = 2, 5, 8), the Lineweaver-Burk lines intersect on the $1/[S]$ axis. The slopes and intercepts grow with $[I]$ while their ratio ($K_m \approx 2$) stays constant, which is the signature of **noncompetitive inhibition**.

## Repository structure

```text
lawofmass.ipynb   Theory questions, model implementations, fits and plots
Data/             Measured rates (measuredData.csv) and inhibition experiments (DataI2/5/8.csv)
images/           Figures
```

## Getting started

```bash
pip install numpy scipy pandas matplotlib jupyterlab
jupyter lab lawofmass.ipynb
```

## Team

Assignment for a computational biology course (2024) by **Esther Bakels** and **Sacha Gijsbers**.
