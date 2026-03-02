# 05. Numerical Stability & Error Analysis

Numerical models are only as good as their reliability. If a small error in input leads to a massive error in prediction, the model is "unstable."

## 1. Numerical Stability
Stability refers to whether errors (caused by noise or rounding) will grow or shrink as the calculation proceeds.

### Runge’s Phenomenon
When using high-order **Polynomial Interpolation**, the curve often starts "wiggling" violently near the edges of the data range. This is called Runge's Phenomenon.
- **Solution**: Use **Spline Interpolation** instead, which uses multiple low-order curves to avoid these oscillations.

### The Condition Number ($\kappa$)
In numerical analysis, stability is often measured via the **Condition Number**. For our demand function $D(x)$:
$$\kappa = \left| \frac{x f'(x)}{f(x)} \right|$$
- If $\kappa$ is **small**, the problem is "well-conditioned" (stable).
- If $\kappa$ is **large**, small errors in weather data will explode into massive forecasting failures.

---

## 2. Error Propagation
Error propagation describes how uncertainties in your input (like a sensor error) travel through your math using **Taylor Series Expansion**.

### 📝 The Propagation Formula
If demand $D$ depends on temperature $T$, and temperature has an uncertainty $\sigma_T$, the uncertainty in the demand $\sigma_D$ is:

$$\sigma_D^2 \approx \left( \frac{\partial D}{\partial T} \right)^2 \sigma_T^2$$

This means if the sensitivity ($\frac{\partial D}{\partial T}$) is high, even a tiny error in the weather sensor will cause a large error in the forecast.

### 🔹 Summary of Stability Factors
| Factor | Effect on Stability | Mitigation |
| :--- | :--- | :--- |
| **Data Noise** | Accumulates over time steps. | Filter data using smoothing techniques. |
| **Model Horizon** | Extrapolation error grows farther out. | Use ensemble models (multiple models) to average errors. |
| **Polynomial Degree**| Higher degree = higher oscillation risk. | Use piecewise linear or cubic splines. |

[Return to README](./README.md) | [Previous: Sensitivity Analysis](./04_sensitivity_analysis.md) | [Next: Operational Decisions](./06_operational_decisions.md)
