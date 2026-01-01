#  F1 Belgian GP 2023 – Race Prediction Model (V1)

## Overview

This project is a **rule-based, explainable prediction model** built to estimate **win probability** and **podium probability** for drivers at the **2023 Belgian Grand Prix (Spa‑Francorchamps)**.

The goal of this project is **not perfect prediction**, but to demonstrate:

* Clear reasoning
* Domain knowledge of Formula 1
* Structured data thinking
* A strong foundation for future machine‑learning extensions

This model was built as a learning + portfolio project with a focus on **transparency over black‑box AI**.

---

## Why Spa‑Francorchamps?

Spa is one of the most competitive and complex circuits on the calendar:

* Long lap length
* High‑speed sectors and heavy braking zones
* Overtaking opportunities
* Frequent weather variability

These characteristics make Spa ideal for a **data‑driven but explainable model**, where multiple factors meaningfully influence race outcomes.

---

## Model Philosophy

This is a **Version 1 (V1)** model.

Design priorities:

* Simple and understandable logic
* No machine learning or neural networks
* Every number can be explained
* Easy to extend in future versions

The model intentionally avoids overfitting and complex assumptions.

---

## Features Used

Each driver is evaluated using the following factors:

1. **Qualifying Position**
   Starting position strongly influences track position, especially at race start.

2. **FP2 Long‑Run Pace**
   FP2 is typically run with race fuel and provides the best indicator of race‑trim performance.

3. **Spa Track History**
   Historical average finishing position at Spa reflects driver comfort with elevation changes, high‑speed corners, and variable conditions.

4. **Team Form (2023 Season)**
   Average team performance across the 2023 season stabilizes predictions and accounts for car strength.

---

## Ranking Methodology

* Each factor is converted into a **rank**
* **Rank 1 = Best**, higher rank = worse performance
* All ranks are treated consistently across the model

### Total Score

```
Total Score = Quali Rank + FP2 Rank + Spa History Rank + Team Form Rank
```

* **Lower Total Score = Stronger Driver**

---

## Strength Conversion

Since probabilities require **higher = better**, Total Scores are inverted into a **Strength Score**:

```
Strength Score = (Max Total Score + 1) − Driver Total Score
```

This ensures:

* No zero values
* Preserved ranking order
* Clean probability calculation

---

## Win Probability

Win probability is calculated as:

```
Win Probability = Driver Strength / Sum of All Strengths
```

This produces a normalized probability distribution across all drivers included in the model.

---

## Podium Probability

Podium probability is derived heuristically:

```
Podium Probability = Win Probability × 1.5
```

* Capped at **100%**
* Reflects the higher likelihood of finishing Top‑3 compared to winning
* Used as a **V1 approximation**, not a full race simulation

---

## Current Scope & Limitations

* Small driver subset (expandable)
* No weather modeling
* No safety car simulation
* No tyre strategy modeling
* No stochastic race events

These limitations are intentional for V1 and will be addressed in future versions.

---

## Future Improvements

Planned extensions include:

* Adding more drivers
* Track‑specific weight adjustments
* Historical win‑to‑podium conversion ratios
* Weather impact modeling
* Full finishing‑position simulation
* Python implementation with Pandas
* Machine learning comparison models

---

## Key Takeaway

This project demonstrates how **domain knowledge + structured reasoning** can produce meaningful predictions **without black‑box AI**.

It serves as a strong baseline framework for more advanced Formula 1 analytics.

---

## Author

Built as a learning and portfolio project driven by a passion for Formula 1 and data analysis.

---

*Version: V1*
