# Popper-Prospector

A teaching-scale reimplementation of the decision loop in **Mern, Corso, Burch, House & Caers (2024), Intelligent Prospector v2.0** (arXiv:2410.10610), motivated by **Caers (2025), The Future of AI in Critical Mineral Exploration** (arXiv:2512.02879).

**What it does:** generates synthetic geology, keeps a Bayesian belief over competing hypotheses, drills where expected information gain is highest, tests a max-entropy null hypothesis for falsification, compares against grid drilling, and ablates three likelihood families. Metrics go to BigQuery if you want them to.

**Honest scope (read this first):** full POMDP + SARSOP is out of scope. The belief is reduced to the hypothesis layer (no domain-geometry sampling) and the planner is myopic. That is deliberate: tractable, transparent, and it teaches the loop. The paper itself validates on synthetic ground truths (17 of them), because a drilling policy can only be scored against a truth you know - simulation is where the answer key is free. This notebook inherits that honestly, and Step 9c stress-tests what happens when the model's shape assumptions are wrong.

**Also honest:** no gradients, no training, no variational anything. The belief update is exact Bayes on four numbers; the planner is brute-force scoring of candidate cells; randomness is PCG64 (passes the TestU01 Big Crush battery) - the limitation of this notebook is not the quality of the random numbers, it is that the probability model is fiction. Step 13 says what to do about that.


