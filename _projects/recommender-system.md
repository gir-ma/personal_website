---
title: "Video Game Recommender System"
excerpt: "Built a hybrid recommender system combining item-item collaborative filtering, factorization machines, and NLP-based explanations for Steam game recommendations."
skills:
  - Python
  - Pandas
  - Scikit-learn
  - Gensim
  - Collaborative Filtering
  - NLP
---

<!-- ## Video Game Recommender System -->

<!-- **Duration:** [Month Year] – [Month Year] -->
**Team:** Kristhian Ortiz, Aaron Arellano, Girma Trefa (CSE 158 Final Project)

### Skills Used

| Python | Pandas | Scikit-learn |
|:---:|:---:|:---:|
| **Gensim** | **Collaborative Filtering** | **NLP** |

### The Challenge
Steam's massive game catalog makes it hard for players to discover titles they'd actually enjoy, and most recommender systems are black boxes that give no insight into *why* a game was suggested. The goal was to build a system that's both accurate and explainable, using real user playtime, reviews, and game metadata.

### Approach
- **Candidate Generation:** Built an item-item collaborative filtering engine using cosine similarity on user-scaled playtime vectors, blended with Jaccard overlap and shrinkage regularization to reduce noise from low-overlap items.
- **Trait-Based Scoring:** Trained a **Factorization Machine** (via SGDRegressor) on one-hot encoded genres, tags, pricing, and developer/publisher tiers to capture latent game traits beyond pure collaborative signals.
- **NLP Feature Extraction:** Combined **TF-IDF** (for interpretable keywords per game) with **Word2Vec** embeddings trained on the review corpus (for semantic similarity), giving the system both symbolic and distributed language understanding.
- **Hybrid Fusion & Explainability:** Re-ranked candidates using a weighted blend of similarity, trait, and review scores, then generated dual-layer explanations — a natural-language summary for users and a technical metric breakdown for debugging.
- Evaluated with **Precision@k, Recall@k, NDCG@k, and Coverage**, run through an ablation study to isolate the contribution of each component (CF → +TF-IDF → +FM → full system) against a popularity baseline.

### Results
- Hybrid fusion of CF, FM, and NLP signals outperformed every single-technique baseline across ranking metrics.
- Every recommendation shipped with a human-readable explanation, directly addressing the "black box" problem common in recommender systems.
- Sparse matrix representations and caching kept the pipeline memory-efficient and fast enough for near real-time scoring.

### Key Achievements
-  Hybrid architecture (CF + FM + NLP) outperformed single-technique baselines on Precision/Recall/NDCG
-  Built a dual-layer explainability framework (user-facing + technical) for every recommendation
-  Designed a modular, production-oriented pipeline with caching, sparse matrices, and independent A/B-testable components