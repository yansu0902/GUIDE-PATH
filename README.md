
## Method in brief

* **GUIDE encoder**: heterogeneous skill–strategy graph (24 CEFR sub-skills, 8 strategies) → *Pedagogy-Modulated Graph Attention* (FiLM + strategy × edge-type bias on GATv2) → *Forgetting- and Relation-aware Temporal Attention*.
* **Strategy-Efficacy Head**: baseline + centred strategy uplift, trained with inverse-propensity weights.
* **EPSG**: Pedagogical Knowledge Base (5 rules) fused with the learned uplift; weights calibrated off-policy (SNIPS) by LGWO.
* **PATH**: ZPD-aware Lévy Grey Wolf Optimizer (cosine a(t), rank-weighted leaders, Lévy alpha, elite opposition learning, ZPD repair, knowledge-seeded wolves) planning (item, strategy) sequences with model-predictive re-planning.

## Key results

* Knowledge tracing: GUIDE AUC 0.8017 vs. 0.8023–0.8024 for SAKT/AKT/GAT-KT, with 51–68% fewer parameters; best delayed-outcome AUC (0.7854).
* Strategy guidance: ranking by immediate correctness gives 14.5% *less* learning than random; EPSG gives the best Hit@3 (0.611) and 14.6% more expected learning than the teacher rule.
* Learning paths, all 600 test learners: GUIDE-PATH E_p 0.454 vs. 0.437 for the teacher rule (+3.8%, p = 0.011); 7-day retention +4.6% (p = 0.006); 10–19% better than GA/PSO/GWO planners.
* Honest negatives, also reported in the paper: no KT-accuracy gain; EPSG vs. PKB-only not significant; LGWO calibration overfits the noisy SNIPS objective; LGWO is 2nd (not 1st) in the Friedman ranking on 10 benchmark functions.

## Important note on the data

All data are **simulated** by the documented EngPath-Sim learner model (`code/simulator.py`). No public English corpus logs pedagogical strategies together with counterfactual outcomes. The paper states this clearly and lists real-classroom validation as the main limitation.

## Reproduce

```bash
cd code
pip install -r requirements.txt
bash run_all.sh        # about 3–4 h on one CPU core; each step can also be run separately
```

Author names, affiliations, funding, CRediT and the generative-AI statement in the manuscript are placeholders for you to complete.
