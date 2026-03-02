# 03. Numerical Interpolation & Extrapolation

When we gather data from a smart grid, it is rarely perfect. We use two main mathematical tools to handle this: **Interpolation** (looking inside) and **Extrapolation** (looking outside).

## 1. Numerical Interpolation
Interpolation is the process of estimating missing data points *within* the range of your known data.

### Techniques
| Method | How it works | Best used for... |
| :--- | :--- | :--- |
| **Linear Interpolation** | Connects two points with a straight line. | Fast, rough estimates of gaps. |
| **Spline Interpolation** | Fits a smooth curve (piecewise polynomial) through points. | High-resolution consumption data where smoothness matters. |
| **Polynomial Interpolation** | Fits one high-order curve through all points. | Small datasets only (risk of high oscillations). |

### Why Splines?
Cubic splines are preferred for energy data because energy consumption usually doesn't "jump" instantly. Splines maintain continuity in the first and second derivatives, making the graph look smooth and realistic.

---

## 2. Numerical Extrapolation
Extrapolation is the process of predicting future values *beyond* the known historical range.

### Techniques
- **ARIMA (Statistical)**: USes past patterns and trends to project forward. It is highly interpretable.
- **Richardson Extrapolation**: A trick to improve the accuracy of a result by comparing it at different "step sizes." It helps reduce truncation errors.
- **Machine Learning (LSTM)**: Neural networks that "remember" previous peaks and learn the context of weather and time.

### Challenges of Extrapolation
Projecting into the future is inherently uncertain. While interpolation stays within the "safety" of our data, extrapolation assumes the future will behave like the past.

[Return to README](./README.md) | [Previous: Mathematical Modeling](./02_mathematical_modeling.md) | [Next: Sensitivity Analysis](./04_sensitivity_analysis.md)
