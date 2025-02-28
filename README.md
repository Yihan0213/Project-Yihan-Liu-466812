# Project-Yihan-Liu-466812
#Calibration and Analysis of Tax Reform in a Heterogeneous Agent Model

##1.Introduction

This project analyzes the impact of increasing the progressivity of the labor income tax in a heterogeneous agent economy. We compare two economies: a baseline economy with a flat tax system (λ = 0) and a reformed economy with a progressive tax system (λ = 0.15). The analysis focuses on key equilibrium outcomes including the equilibrium interest rate (r), wage rate (w), tax rate (τ), capital-to-output ratio, and inequality measures (Gini coefficients for after-tax labor income and assets). Additionally, i provide graphical comparisons of the value functions, policy functions, the marginal asset distribution, and the Lorenz curves for both income and wealth.

##2.Model Description and Bellman Equation

Agents maximize their expected lifetime utility:

\[
\max_{\{c_{i,t}\}} \; E_0 \sum_{t=0}^\infty \beta^t \, u(c_{i,t}),
\]

with period utility defined as

\[
u(c_{i,t}) = \frac{c_{i,t}^{1-\text{crra}} - 1}{1-\text{crra}} \quad \text{（and } u(c_{i,t})=\ln c_{i,t} \text{ if crra }=1\text{）}.
\]

Agents face the budget constraint

\[
c_{i,t} + a_{i,t+1} = y_{i,t} - T(y_{i,t}) + (1+r)a_{i,t},
\]

where labor income is given by

\[
y_{i,t} = z_{i,t}w,
\]

and the tax function is specified as

\[
T(y_{i,t}) = y_{i,t} - (1-\tau)\left(\frac{y_{i,t}}{\bar{y}}\right)^{1-\lambda}\bar{y}.
\]

Thus, after-tax labor income becomes

\[
\tilde{y}_{i,t} = (1-\tau)y_{i,t}^{1-\lambda}\bar{y}^{\lambda}.
\]

The household’s decision problem is characterized by the following Bellman equation:

\[
V(a,z) = \max_{a'\geq -\phi} \left\{ u\Big(z\cdot w - T(z\cdot w) + (1+r)a - a'\Big) + \beta \sum_{z'} P(z'|z)V(a',z') \right\}.
\]

In our calibration, we set the borrowing limit \(\phi = 0\).

##3.Calibration of Model Parameters

The model involves several parameters: \(\beta\), crra (formerly “γ”, renamed to avoid conflicts), \(\tau\), \(\lambda\), \(\rho\), \(z_{\text{bar}}\), \(\sigma\), \(\alpha\), \(\delta\), \(A\), and \(\phi\). I set:

Preferences:
  \(\text{crra} = 2\) (risk aversion)  
  \(\beta = 0.96\)

Productivity Process:
  The idiosyncratic productivity follows an AR(1) process:
  \[
  \ln z_{t+1} = \rho \ln z_t + (1-\rho)\ln(z_{\text{bar}}) + \varepsilon_{t+1},
  \]
  with \(\rho = 0.9\), \(\sigma = 0.4\), and mean \(z_{\text{bar}} = 1\). The process is discretized using Tauchen’s method with 5 grid points.

Production and Government Sector: 
  The production function is:
  \[
  Y = A K^\alpha,
  \]
  with labor normalized to \(L = 1\). Using data from sources such as the Penn World Tables，I set \(\alpha = 0.36\) (implying a labor share of about 64%). The calibration for the baseline economy (λ = 0) relies on:
  1.Wage Rate:\(w = (1-\alpha)A K^\alpha = 1\) (thus, \(A K^\alpha = \frac{1}{1-\alpha}\)).
  2.Interest Rate:\(r = \alpha A K^{\alpha-1} - \delta = 0.04\).
  3.Investment-to-Output Ratio:\(\frac{\delta K}{A K^\alpha} = 0.2\).
  4.Government Expenditure-to-Output Ratio:\(\frac{G}{A K^\alpha} = 0.2\), which implies the tax rate \(\tau = 0.2/(1-\alpha)\) since the average labor income is normalized to 1.

  With an initial choice of \(\delta = 0.08\), we solve for \(K\), \(A\), \(\tau\), and \(r\).

Tax Reform:
  For the progressive tax system, I set \(\lambda = 0.15\). To ensure comparability, the tax revenue (and hence \(\tau\)) is kept constant across both economies.

##4.Numerical Solution and Accuracy

The household problem is solved via value function iteration on a discretized asset grid (1000 points). Convergence is achieved when the maximum difference between successive iterations falls below \(10^{-6}\). The stationary distribution is computed by iterating on the policy function with a tolerance of \(10^{-8}\). I also conduct sensitivity analysis regarding grid size and iteration tolerances, ensuring that the numerical solution is robust and accurate.

##5.Equilibrium Statistics and Graphical Analysis

For both the baseline (\(\lambda = 0\)) and tax reform (\(\lambda = 0.15\)) economies, i report:
1.Equilibrium Interest Rate \(r\)
2.Equilibrium Wage Rate \(w\) (set at 1)
3.Tax Rate \(\tau\)
4.Capital-to-Output Ratio \(\displaystyle \frac{K}{A K^\alpha}\)
5.Gini Coefficient for After-tax Labor Income
6.Gini Coefficient for Assets

The following plots are generated:
Value Functions:Comparing households’ value functions across tax regimes.
Policy Functions:Optimal asset choices (next-period assets) in both economies.
Marginal Distribution of Assets: Stationary asset distribution.
Lorenz Curves:For after-tax labor income and assets, illustrating the extent of inequality.

##6.Discussion of Economic Mechanisms

Switching from a flat tax (\(\lambda = 0\)) to a progressive tax (\(\lambda = 0.15\)) affects household decisions. Progressive taxation imposes higher marginal taxes on high-income agents, reducing their effective disposable income and consequently their savings incentives. This redistributive effect is reflected in lower Gini coefficients for both after-tax income and assets. On the other hand, the adjustment in tax policy can alter aggregate variables such as the capital-to-output ratio and the equilibrium interest rate, highlighting the trade-off between equity and efficiency inherent in tax reforms.

##7.Conclusion

This study demonstrates that increasing tax progressivity can reduce inequality while influencing key macroeconomic variables. The calibrated model and its robust numerical solution provide valuable insights into the redistribution and efficiency implications of tax policy changes. Overall, the results underscore the importance of careful parameter calibration and numerical accuracy in evaluating policy impacts within heterogeneous agent models.

