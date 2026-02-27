Econ 3916 — Assignment 3: Causal Inference & Non-Parametric Statistics
Overview
This notebook applies advanced econometric and statistical methods to real-world business scenarios using SwiftCart, a fictional gig-economy delivery platform. The analysis spans four phases: bootstrapping, permutation testing, causal inference via propensity score matching, and AI-assisted visualization.

Phase 1: Bootstrapping Non-Parametric Uncertainty
Simulated a zero-inflated tip distribution (n=250) combining 100 zero-tips and 150 exponential draws. Built a manual bootstrap engine from scratch using NumPy to resample the distribution 10,000 times and extract a 95% non-parametric confidence interval for the median. Analyzed the asymmetry of the interval as evidence of why the Central Limit Theorem fails in this topological space.
Phase 2: Falsification in Logistics A/B Testing
Generated synthetic A/B test data for 1,000 deliveries — Normal control and Log-Normal treatment — to simulate a routing algorithm evaluation with extreme outliers. Constructed a manual permutation test over 5,000 iterations using NumPy to compute an exact empirical p-value, bypassing the violated homoscedasticity assumption of a standard T-test.
Phase 3: Causal Control and the Mitigation of Selection Bias
Identified and corrected severe selection bias in SwiftCart's loyalty program data. Computed the naive Simple Difference in Means (SDO) and demonstrated its inflation due to self-selection. Applied Propensity Score Matching (PSM) using Logistic Regression and Nearest Neighbor Matching to construct a valid counterfactual control group and isolate the true Average Treatment Effect on the Treated (ATT).
Phase 4: AI Expansion — Love Plot Visualization
Utilized the P.R.I.M.E. Framework to prompt Claude (LLM) to generate a Love Plot visualizing covariate balance before and after PSM. The plot demonstrates successful bias mitigation by showing all post-matching standardized mean differences fall below the 0.1 threshold.

Tools & Libraries

Python, NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn
Google Colab
Claude (Anthropic) — AI Co-Pilot for Phase 4


Key Results
MetricValueBootstrap 95% CI($0.27, $1.36)Permutation P-Value0.0004Naive SDO
