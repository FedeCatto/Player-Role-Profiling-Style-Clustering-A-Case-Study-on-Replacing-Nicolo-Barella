# Player Role Profiling & Style Clustering
## A Case Study: Finding a Replacement for Nicolò Barella

> Unsupervised learning · k-NN similarity · PCA · interactive scouting dashboard

A data-driven scouting framework that profiles central midfielders from Europe's top leagues, clusters them by playing style, and identifies the players statistically closest to a given reference. Applied here to a concrete transfer problem: who could replace **Nicolò Barella** at Inter while preserving the team's tactical identity?

---

## Motivation

Traditional scouting relies heavily on subjective judgement and selective highlight reels. This framework treats player replacement as a structured data problem:

- **Tactical fit over raw metrics** — clustering by style of play, not just volume statistics
- **Reproducible analysis** — every similarity score is traceable to specific features and distance functions
- **Risk reduction** — structured evidence to support transfer decisions worth tens of millions

---

## Dataset

| Attribute | Details |
|-----------|---------|
| Source | FBref.com (scraped via BeautifulSoup & Selenium) |
| Scope | Central midfielders — Serie A, La Liga, Premier League (2024/25) |
| Size | 496 players · 82 numeric features |
| Features | Passing, possession, progressive actions, offensive & defensive contributions |

---

## Methodology

### 1. Data preparation
Missing value imputation, removal of low-variance and highly collinear features, per-90-minute normalisation to remove playing time bias.

### 2. Dimensionality reduction — PCA
82 features compressed into **36 principal components**, retaining over 90% of total variance. Reduces noise and makes clustering geometry more meaningful.

### 3. Clustering — midfielder archetypes
Two algorithms run in parallel for robustness:

- **K-Means (k=2 and k=3)** — identifies broad midfielder archetypes
- **Hierarchical clustering** — validates structure and reveals sub-groupings without a fixed k

**Archetypes identified:**
- *Dynamic/attack-oriented* — high chance creation, progressive carries, assists
- *Supportive/defensive* — lower offensive involvement, positional discipline
- *Low-activity* (three-cluster solution) — players with limited involvement across both dimensions

### 4. Player similarity — k-NN

Barella's nearest neighbours identified using four distance metrics:

| Metric | Captures |
|--------|----------|
| Euclidean | Overall statistical closeness |
| Manhattan | Robust to outlier features |
| Cosine | Stylistic direction, regardless of volume |
| Mahalanobis | Accounts for feature correlation structure |

Using multiple metrics guards against artefacts from any single distance function.

---

## Results

**Barella's profile:** consistently placed within the dynamic, attack-oriented midfielder cluster — high progressive actions, chance creation, and defensive work rate combined.

**Closest replacements by k-NN:**

| Player | Notes |
|--------|-------|
| **Rodrigo De Paul** | Most similar across metrics — strongest overall candidate |
| Bruno Guimarães | Strong defensive-offensive balance |
| Enzo Fernández | High progressive passing volume |
| Pedri | Creative profile, slightly lower defensive contribution |
| Martin Ødegaard | Similar chance creation, different league context |
| Luka Sučić / Javier Guerra | Emerging profiles worth monitoring |

De Paul emerges as the top candidate across multiple distance functions — a finding robust to metric choice, not dependent on a single measurement.

---

## Key Design Decisions

- **Per-90 normalisation** prevents players with more minutes from appearing artificially dominant
- **Multi-metric k-NN** surfaces candidates that are robust similarities, not artefacts of one distance function
- **PCA before clustering** removes correlated noise that would otherwise distort cluster boundaries
- **Style-first framing** — the question is not "who scores as many goals" but "who plays the same role in the same way"

---

## Limitations & Next Steps

- **Positional context** — raw statistics don't fully encode tactical role within a specific system
- **Injury and availability data** — a statistically similar player is less useful if unavailable
- **Extend to other positions** — the framework is position-agnostic and transferable
- **Dynamic updating** — re-run mid-season as statistics accumulate for more stable clustering

---

## Stack

`Python` `BeautifulSoup` `Selenium` `scikit-learn` `PCA` `K-Means` `hierarchical clustering` `k-NN` `football analytics` `unsupervised learning`
