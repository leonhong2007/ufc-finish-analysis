# UFC Fight Finishes: Weight Classes and Trends (2013–2025)

## Question / why it matters
Do UFC fight outcomes (KO/TKO, submission, decision) differ by weight class, and how has that mix shifted over time? I am interested in MMA strategy and whether different weight classes tend to finish fights in different ways.

## Data and licensing
- **Dataset:** Nicholas Bair, *UFC Data: scorecards, round statistics, and betting odds, 2013 to 2026*, v0.1.1 (2026), https://doi.org/10.5281/zenodo.23458636
- **GitHub source:** https://github.com/nlbair/ufc-data
- **License:** [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Attribution is required. Original source credits include UFCStats and MMA Decisions; this is not an official UFC project.
- **Unit of analysis:** one UFC fight. Analysis excludes 2026 to use complete years. No private personal information is used.

## Cleaning log
Starting file: 6,743 rows. I did not replace unknown outcomes with guesses.
- Duplicate fight IDs: 6,743 -> 6,743 (removed 0)
- Invalid dates or outside 2013–2025: 6,743 -> 6,302 (removed 441)
- Missing / nonstandard division: 6,302 -> 6,235 (removed 67)
- Draw/NC/overturned/missing or unclassified outcome: 6,235 -> 6,147 (removed 88)
**Rows analyzed:** 6,147. Division comparisons include 11 divisions with at least 75 classified fights.

## Method and statistics
I standardized finish methods into KO/TKO, submission, and decision, then computed counts and proportions. I used a chi-square contingency test to examine association between division and finish type, plus Cramer's V as an effect-size summary. All percentages are proportions of classified outcomes only; no imputation. Statistical association does not prove causation.

## Findings
1. Of 6,147 classified UFC fights (2013–2025), 32.0% ended by KO/TKO, 17.8% by submission and 50.2% by decision.
2. Among divisions with at least 75 fights, Heavyweight had the highest KO/TKO share (49.3%), while Women's Strawweight had the lowest (12.3%).
3. KO/TKO share was 34.9% in 2013 and 32.9% in 2025; this describes an observed pattern, not a causal trend.
4. The weight-class-versus-finish association test gave chi-square=255.95 (df=20, p=7.19e-43) and Cramer's V=0.148.

## Figures
![Distribution of outcomes](charts/01_overall_finish_types.png)
![Finish mix by weight class](charts/02_weight_class_finish_mix.png)
![Finish mix by year](charts/03_finish_trends_by_year.png)

## Limitations and ethical notes
- This is observational data, so the analysis cannot prove weight class causes a particular method of victory.
- Bout duration, stylistic matchups, schedule length, injury, rules, fighter ability, and selection could confound results.
- The underlying public dataset combines multiple independently matched sources. Some records may be incomplete or inaccurate.
- Draws, overturned fights and no-contests are omitted rather than silently classed as decisions.
- Some divisions are excluded from the weight-class chart by the 75-bout threshold; changing this choice can change comparisons.
- Fighter names may appear in the source but no sensitive personal information was collected or exposed.
- AI was used to help draft code, structure the report, and create the notebook. I reviewed the methodology, reran the code and am responsible for interpreting findings. See `AI_PROMPT_LOG.md`.

## Reproduce
1. Install Python 3.10+ and `pip install -r requirements.txt`.
2. Open `ufc_finish_analysis.ipynb` in Jupyter or Google Colab.
3. Run **Runtime -> Run all** (or **Run All Cells**). The notebook downloads the public data, audits cleaning, generates three PNG charts, and refreshes this README.
4. For strict reproducibility, archive the source CSV or use the cited v0.1.1 Zenodo release; the repository's `main` branch may update later.

## Public repository
https://github.com/leonhong2007/ufc-finish-analysis
