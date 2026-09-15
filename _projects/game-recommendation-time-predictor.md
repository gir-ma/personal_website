---
title: "Game Recommendation & Time Prediction System"
excerpt: "Built a hybrid machine learning system combining Bayesian Personalized Ranking and collaborative filtering to predict game play and playtime."
skills:
  - Python
  - NumPy
  - Scikit-learn
  - Bayesian Personalized Ranking
  - Collaborative Filtering
---

<!-- ## Game Recommendation & Time Prediction System -->

<!-- **Duration:** [Month Year] – [Month Year] -->

### Skills Used

| Python | NumPy | Scikit-learn |
|:---:|:---:|:---:|
| **Bayesian Personalized Ranking** | **Collaborative Filtering** | **Ridge Regression** |

### The Challenge
Gaming platforms need to predict two distinct behaviors: whether a user will play a given game, and how long they'll play it. Both tasks are complicated by sparse interaction data, where most users have only played a small fraction of available games, making it hard to generalize from limited signal.

### Approach
- **Play Prediction:** Built a hybrid ranking system using **Bayesian Personalized Ranking** (K=70 latent dimensions, popularity-weighted negative sampling) fused with Jaccard similarity between users' game libraries, scoring the top 50% of ranked games per user as "played."
- **Hours Prediction:** Engineered a dual-model ensemble combining a **Ridge regression** model on user/game features (mean playtime, play rate, popularity) with an iterative **collaborative filtering bias model** (global mean + user/game biases, solved via alternating least squares), blended at an 80/20 weighting favoring the CF model.
- Prioritized numerically stable, reproducible implementations — fixed random seeds, bounded sigmoid computations, and sparse data structures (defaultdicts, scipy sparse matrices) to handle thousands of users and games efficiently.

### Results
- **Play prediction:** Scored 9.5/10 on held-out accuracy, substantially outperforming popularity-only and logistic regression baselines by fusing embeddings with content-based similarity.
- **Hours prediction:** Scored 10/10, driven by the ensemble blend of feature-based regression and collaborative filtering biases, which stabilized predictions across sparse user-game pairs.
- Validated ranking quality via pairwise AUC on a 6,710-sample validation set.

### Key Achievements
-  **9.5/10** on play prediction via hybrid BPR + similarity fusion
-  **10/10** on hours prediction via ensemble regression + CF bias modeling
-  Designed a modular, scalable pipeline handling sparse gaming interaction data end-to-end