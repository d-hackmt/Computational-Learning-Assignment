# 04. Sensitivity Analysis Using Derivatives

In a smart grid, an operator needs to know: "If the temperature rises by 2 degrees, how much more electricity do we need?" This is what Sensitivity Analysis answers.

## The Role of Derivatives
Sensitivity is mathematically expressed as a derivative. A derivative is simply the "rate of change."

### Partial Derivatives
Since demand $D$ depends on multiple factors (Weather $W$, Economics $E$), we use partial derivatives:
- $\frac{\partial D}{\partial W}$: Sensitivity to weather.
- $\frac{\partial D}{\partial E}$: Sensitivity to economic signals.

### Numerical Approximation
If we don't have a simple formula for the grid (which is usually the case), we use **Finite Differences** to approximate the derivative:

$$f'(x) \approx \frac{f(x + h) - f(x - h)}{2h}$$

Where $h$ is a very small change. We "nudge" the input slightly and see how much the output moves.

---

## Impact on Industry
| Sensitivity Level | Meaning | Operational Action |
| :--- | :--- | :--- |
| **High** | Small weather change = Massive demand spike. | Pre-load generation units; prepare for peak. |
| **Low** | Weather changes don't affect load much. | Normal operations; focus on maintenance. |

### Feedback Loop
```mermaid
graph LR
    P[Perturb Input: h] --> M[Run Forecast Model]
    M --> O[Observe Output Change]
    O --> S[Calculate Sensitivity]
    S --> D[Adjust Disaster Recovery Plans]
```

[Return to README](./README.md) | [Previous: Numerical Methods](./03_numerical_methods.md) | [Next: Stability & Error Analysis](./05_stability_error_analysis.md)
