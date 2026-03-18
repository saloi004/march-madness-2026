# march-madness-2026

# March Machine Learning Mania 2026 - Advanced Bradley-Terry Model

## Project Overview
This repository contains the code and methodology for predicting the 2026 NCAA Men's Basketball Tournament matchups. Our approach utilizes an advanced, dynamic-temperature **Bradley-Terry (BT) Model**. By combining official Kaggle box score data with advanced external metrics, the model evaluates team strength ($\Lambda$) through a balanced lens of current season efficiency, historical pedigree, and recent momentum.

## Authors
**Liya Shi** - University of Wisconsin-Madison

## Data Sources

Our model integrates official Kaggle competition data with several high-quality external analytics sources to capture both raw statistical efficiency and intangible tournament factors:

1. **Kaggle Official Data:** * `MRegularSeasonDetailedResults.csv`: Used to calculate base efficiency metrics, specifically the season-long Average Net Rating ($Z_{Efficiency}$).
2. **EvanMiya Analytics:** * Provided Bayesian Performance Rating (BPR) to measure absolute current-season strength ($Z_{BPR}$) and True Tempo to evaluate game pace.
3. **TeamRankings:** * Historical `TR RATING` data (2024-2026) to establish baseline program pedigree and floor ($Z_{Beta}$).
4. **Heat Check CBB:** * "Dark Horse," "Upset Alert," and "Cinderella" ratings to quantify late-season momentum ($Z_{Form}$).
5. **Historical Team Results:** * Performance Against Expectations (PAKE) to capture historical tournament over-performance ($Z_{PAKE}$).

## Methodology
The core of the prediction engine is a Latent Strength variable ($\Lambda$) calculated for each team, which blends the standardized (Z-score) metrics listed above:

`Lambda = (0.35 * Z_BPR) + (0.25 * Z_Beta) + (0.20 * Z_Efficiency) + (0.10 * Z_Form) + (0.10 * Z_PAKE)`

To account for the high variance of "March Madness," we implemented a **Dynamic Temperature Coefficient ($c$)**. This coefficient adjusts the standard BT probability curve, artificially increasing the upset probability when a lower-seeded team (Seed 12+) plays a top seed (Seed 1-4), specifically if the underdog dictates a highly volatile, fast-paced game (high Tempo).

## AI Usage Disclosure
In the interest of transparency and academic integrity, I declare the following use of Artificial Intelligence in this project:
* **Google Gemini:** Used for debugging.
