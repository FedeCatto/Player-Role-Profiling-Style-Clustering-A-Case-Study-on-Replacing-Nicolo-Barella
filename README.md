# Player Role Profiling & Style Clustering: A Case Study on Replacing Nicolò Barella

---

## Project Overview

This project develops a **data-driven framework** for profiling football players and analyzing playing styles, with a focus on identifying potential replacements for **Nicolò Barella**, a key midfielder for Inter. The framework combines **clustering algorithms, player similarity metrics, and interactive visualization** to support evidence-based recruitment and tactical analysis.

---

## Motivation

- **Enhance scouting efficiency:** Move from subjective evaluations to systematic, data-driven insights.  
- **Maintain tactical identity:** Identify players who fit the team’s style of play, not just raw performance metrics.  
- **Support evidence-based recruitment:** Reduce uncertainty and financial risk in transfer decisions through structured analysis.  

---

## Objectives

1. **Data preprocessing & feature engineering:** Standardize and transform raw player statistics into meaningful metrics.  
2. **Clustering & similarity analysis:** Group players with similar styles and identify those most comparable to a reference player.  
3. **Interactive visualization:** Provide dashboards for exploring cluster membership, comparing profiles, and accessing similarity scores.  

---

## Dataset

- **Source:** FBref.com (advanced football statistics)  
- **Coverage:** Central midfielders from Serie A, LaLiga, and Premier League (2024/25 season)  
- **Size:** 496 players, 82 numeric features covering passing, possession, offensive, and defensive contributions  

---

## Methodology

1. **Data Acquisition:** Web scraping using Python (BeautifulSoup & Selenium)  
2. **Data Cleaning & Preparation:** Handle missing values, remove irrelevant features, normalize data, and reduce multicollinearity  
3. **Dimensionality Reduction (PCA):** Project data into 36 principal components capturing over 90% of variance  
4. **Clustering:**  
   - **K-Means** (2 and 3 clusters) to identify midfielder archetypes  
   - **Hierarchical clustering** for additional insight and validation  
5. **Player Similarity (k-NN):** Identify players most similar to Barella using multiple distance metrics (Euclidean, Manhattan, Cosine, Mahalanobis)  

---

## Key Findings

- **Midfielder Archetypes:**  
  - Creative/offensive midfielders (high chance creation, assists, progressive actions)  
  - Supportive/defensive midfielders (lower offensive involvement)  
  - Three-cluster K-Means distinguishes low-activity players additionally  
- **Barella’s Profile:** Consistently placed among dynamic, attack-oriented midfielders  
- **Closest Players (k-NN):**  
  - **Rodrigo De Paul** – statistically the most similar to Barella, making him a strong candidate replacement  
  - Bruno Guimarães, Enzo Fernández, Pedri, Martin Ødegaard, Luka Sučić, and Javier Guerra also show comparable attributes depending on distance metrics  

---

## Conclusion

This framework demonstrates how **data science can enhance traditional football scouting** by:  
- Providing objective, reproducible insights into player roles and styles  
- Supporting evidence-based recruitment and tactical decision-making  
- Identifying stylistic matches for key players, with **Rodrigo De Paul emerging as the most viable substitute for Nicolò Barella**  

---



## Repository Structure

