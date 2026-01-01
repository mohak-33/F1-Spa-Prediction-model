# F1 Belgian GP 2023 Prediction Model (V2)

## Overview

This project is a **simple, explainable Formula 1 prediction model** built to estimate **win** and **podium probabilities** for the **2023 Belgian Grand Prix (Spa‑Francorchamps)**.

The goal is not perfect accuracy, but to show **clear thinking**, **F1 knowledge**, and **basic data modeling using Python**.

---

## Why Spa?

Spa is a fast, competitive track where:

* Race pace matters more than pure qualifying
* Team performance plays a big role
* Past experience at the track helps

This makes it a good circuit for a multi‑factor model.

---

## Model Logic (Simple)

Each driver is ranked using four factors:

* Qualifying position
* FP2 long‑run pace (race trim)
* Past performance at Spa
* Team form during the 2023 season

**Rank rule:**
Rank 1 = best, higher rank = worse

---

## Scoring Method

A weighted score is calculated:

```
Total Score =
0.35 × FP2 Rank
+ 0.25 × Qualifying Rank
+ 0.20 × Team Form Rank
+ 0.20 × Spa History Rank
```

Lower total score means a stronger driver.

---

## Probabilities

* Total scores are converted into a **strength score**
* Win probability is based on each driver’s strength relative to others
* Podium probability is estimated as:

```
Podium Probability = Win Probability × 1.5
```

(capped at 100%)

---

## Output

The model outputs:

* Win probability (%)
* Podium probability (%)

Results for all 20 drivers are saved in:

```
spa_2023_predictions_v2.csv
```

---

## Limitations

* No weather or safety‑car modeling
* FP2 race pace is approximate
* Podium probability is a simple heuristic

These are intentional to keep the model easy to understand.

---

## Status

**Complete – Version 2 (Weighted Spa Model)**

Built as a learning and portfolio project using Python.
