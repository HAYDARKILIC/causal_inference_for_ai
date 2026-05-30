# CAUSAL INFERENCE FOR AI

> The causal machinery underpinning trustworthy machine-learning decisions, built from
> scratch in pure NumPy. A 6-week masterclass: potential outcomes, causal DAGs &
> d-separation, IPW/matching/doubly-robust AIPW, Double Machine Learning, Causal Forests &
> uplift, and quasi-experimental designs (IV, RDD, DiD) with sensitivity analysis — every
> estimate verified against a known ground truth from a simulator we control. Fully
> executed notebooks.

Predictive ML answers *what is*. Decisions require *what if I act* — `P(Y | do(X))` rather
than `P(Y | X)`. Recommenders, pricing models, clinical decision support, and RLHF reward
models all silently climb Pearl's Ladder of Causation the moment a human acts on their
output. This course rebuilds the formal tools for getting that step right, from the
Neyman–Rubin potential-outcomes model to modern ML-based estimators.

No high-level causal libraries. Just the mathematics, NumPy, and a touch of scikit-learn
where an estimator genuinely needs a flexible regressor. Because every dataset comes from a
simulator we wrote, we can compare each estimate to the true effect — the one luxury real
data never grants.

## Curriculum

| Week | Notebook | Topics |
|------|----------|--------|
| 1 | `01_potential_outcomes.ipynb` | Potential outcomes, the fundamental problem, ATE/ATT/ATC, selection-bias decomposition, randomization, regression adjustment, the g-formula |
| 2 | `02_causal_graphs_dseparation.ipynb` | DAGs from scratch, a d-separation oracle (Bayes-Ball), chains/forks/colliders, collider bias, the back-door criterion and adjustment-set search |
| 3 | `03_ipw_matching_aipw.ipynb` | Propensity scores via IRLS, overlap & SMD balance diagnostics, IPW (Horvitz–Thompson & Hájek), nearest-neighbour matching, g-computation, doubly-robust AIPW with a double-robustness stress test |
| 4 | `04_double_machine_learning.ipynb` | Regularization bias, Neyman-orthogonal scores, cross-fitting, partially-linear & AIPW Double Machine Learning, S/T/X meta-learners |
| 5 | `05_heterogeneous_effects_causal_forest.ipynb` | CATE, honest causal trees, causal forests, evaluating CATE without ground truth: Qini curve/coefficient and uplift-by-decile |
| 6 | `06_iv_rdd_did_sensitivity_capstone.ipynb` | Instrumental variables & 2SLS (and weak instruments), regression discontinuity, difference-in-differences, sensitivity analysis, and an end-to-end capstone |

## What gets built from scratch

- A directed-acyclic-graph engine with cycle detection, ancestor queries, and a full
  **d-separation** algorithm validated against textbook independencies.
- **Logistic regression by IRLS**, OLS via the normal equations, and influence-function
  standard errors — no statistics package.
- **IPW, stabilized IPW, propensity matching, g-computation, and AIPW**, with effective
  sample size and standardized-mean-difference diagnostics.
- **Cross-fitting and Double Machine Learning**, with a Monte-Carlo demonstration that
  cross-fitting removes regularization bias.
- **Honest causal trees and a causal forest**, splitting for treatment-effect heterogeneity
  rather than outcome variance.
- **Qini/uplift evaluation**, **2SLS**, **local-linear RDD**, **DiD**, and a **sensitivity
  contour** for hidden confounding.

## Running

```bash
pip install numpy scipy matplotlib pandas scikit-learn jupyter
jupyter lab
```

Open any notebook under `notebooks/`. They are committed **fully executed** with outputs and
figures, so they can also be read top-to-bottom without running anything. Figures are
written to `figures/`.

## Assumptions, made explicit

Every method here rests on assumptions that data alone cannot verify. The course foregrounds
them rather than hiding them:

1. **Unconfoundedness / ignorability** — all confounders measured (Weeks 1–5).
2. **Overlap / positivity** — every covariate profile can receive either treatment.
3. **SUTVA** — no interference, single version of treatment.

Week 6 covers what to do when unconfoundedness fails, and Week 6's sensitivity analysis asks
how strong a hidden confounder would have to be to overturn a conclusion. The discipline of
stating and stress-testing assumptions is the real subject of the course.

## License

MIT.
