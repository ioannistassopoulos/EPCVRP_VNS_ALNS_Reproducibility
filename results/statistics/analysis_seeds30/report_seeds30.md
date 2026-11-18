# 30-seed analysis: V1 (60 s calibration) and ALNS

Instances: 120; seeds 1..30; reference = revised Trachanatzi minimum (cells below the proven lower bounds removed: {'A-n32-k5_5': {'FA2020_Gurobi': 4606.0, 'FA2020_FAC': 4611.0, 'FA2020_BA': 4618.2, 'FA2020_cPSO': 4624.799999999999, 'TLBO2021_Gurobi': 4606.0, 'TLBO2021_BA': 4618.0, 'TLBO2021_cPSO': 4625.0, 'TLBO2021_TLBO-CRE': 4623.0}, 'A-n53-k7_3': {'FA2020_BA': 5640.799999999999, 'TLBO2021_BA': 5641.0}, 'A-n53-k7_5': {'FA2020_BA': 5526.900000000001, 'TLBO2021_BA': 5527.0}, 'E-n51-k5_1': {'TLBO2021_TLBO-CRE': 3322.0}, 'E-n51-k5_5': {'FA2020_FAC': 3457.8}}).

Final Q_low mode differs between V1 and ALNS for: {'A-n53-k7_5': ('max', 'long'), 'A-n80-k10_2': ('long', 'max')} (all 30 seeds feasible under both definitions on both sides: checked).

## Against the revised Trachanatzi reference (4 s.d.)

| algorithm | best of 30: better / equal / worse | E[best of 5]: better / equal / worse | MC best of 5 (mean [2.5%, 97.5%]) better | per-seed wins |
|---|---|---|---|---|
| V1_60s | 111 / 9 / 0 | 110.41 / 9.29 / 0.31 | 110.40 [109, 111] | 3160/3600 (87.78 %) |
| ALNS | 111 / 9 / 0 | 110.85 / 9.07 / 0.08 | 110.85 [110, 111] | 3293/3600 (91.47 %) |

Seeds 1..5 cross-check (documented 5-seed results: V1_60s 111/9/0 and 524 run wins, ALNS 110/10/0 and 548):
- V1_60s: {'counts': {'better': 111, 'equal': 9}, 'run_wins': 524}
- ALNS: {'counts': {'better': 110, 'equal': 10}, 'run_wins': 549}

Per-seed win rate by family (%): V1_60s A 85.9, B 92.4, E 75.7, M 100.0; ALNS A 92.1, B 94.3, E 80.0, M 100.0

Instances where not every one of the 30 seeds beats the reference:
- V1_60s: ['A-n32-k5_2', 'A-n32-k5_3', 'A-n32-k5_4', 'A-n32-k5_5', 'A-n37-k6_1', 'A-n37-k6_5', 'A-n48-k7_1', 'A-n48-k7_2', 'A-n48-k7_3', 'A-n53-k7_5', 'B-n39-k5_2', 'B-n39-k5_3', 'B-n41-k6_3', 'B-n50-k7_1', 'B-n50-k7_2', 'B-n50-k7_3', 'B-n50-k7_4', 'B-n56-k7_1', 'B-n56-k7_3', 'B-n56-k7_4', 'B-n63-k10_3', 'E-n23-k3_1', 'E-n23-k3_2', 'E-n23-k3_3', 'E-n23-k3_4', 'E-n23-k3_5', 'E-n33-k4_2', 'E-n33-k4_4', 'E-n33-k4_5', 'E-n51-k5_1', 'E-n51-k5_5']
- ALNS: ['A-n32-k5_2', 'A-n32-k5_3', 'A-n32-k5_4', 'A-n32-k5_5', 'A-n53-k7_5', 'B-n39-k5_3', 'B-n56-k7_4', 'E-n23-k3_1', 'E-n23-k3_2', 'E-n23-k3_3', 'E-n23-k3_4', 'E-n23-k3_5']

## ALNS vs V1_60s, paired (d = (ALNS - V1)/V1 * 100, negative = ALNS better)

| group | n | wins | ties | losses | material wins | material losses | median d % | mean d % [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| mean of 30, all (120 pairs) | 120 | 66 | 11 | 43 | 16 | 1 | -0.0046 | -0.0543 [-0.1019, -0.0196] | 0.004549 |
| mean of 30, family A | 45 | 26 | 4 | 15 | 6 | 0 | -0.0062 | -0.0223 [-0.0448, -0.0010] | 0.08727 |
| mean of 30, family B | 30 | 16 | 4 | 10 | 3 | 1 | -0.0116 | -0.0261 [-0.0521, -0.0039] | 0.03122 |
| mean of 30, family E | 25 | 12 | 3 | 10 | 2 | 0 | +0.0000 | -0.0144 [-0.0426, +0.0068] | 0.6327 |
| mean of 30, family M | 20 | 12 | 0 | 8 | 5 | 0 | -0.0120 | -0.2186 [-0.4839, -0.0324] | 0.2943 |
| SECONDARY best of 30 (120 pairs) | 120 | 14 | 73 | 33 | 3 | 0 | +0.0000 | +0.0011 [-0.0064, +0.0078] | 0.08361 |
| SECONDARY median of 30 (120 pairs) | 120 | 37 | 44 | 39 | 12 | 2 | +0.0000 | -0.0387 [-0.0856, -0.0064] | 0.4878 |
| half seeds 1..15, ALNS vs V1 | 120 | 65 | 14 | 41 | 15 | 3 | -0.0055 | -0.0567 [-0.1094, -0.0197] | 0.001463 |
| half seeds 16..30, ALNS vs V1 | 120 | 57 | 15 | 48 | 15 | 2 | +0.0000 | -0.0519 [-0.0967, -0.0181] | 0.03816 |
| NOISE V1_60s: seeds 16..30 vs 1..15 (same algorithm) | 120 | 52 | 19 | 49 | 4 | 3 | +0.0000 | +0.0005 [-0.0150, +0.0153] | 0.9258 |
| NOISE ALNS: seeds 16..30 vs 1..15 (same algorithm) | 120 | 41 | 38 | 41 | 1 | 2 | +0.0000 | +0.0053 [-0.0009, +0.0143] | 0.7236 |

Mean wall time per run (same load, 32 parallel runs): {'V1_60s': 100.85937281805556, 'ALNS': 99.27203444671028}

Coefficient of variation of the 30 seeds (% of mean, mean over instances), by family: {'V1_60s': {'A': 0.05972156103757979, 'B': 0.07732388376581198, 'E': 0.05246684143885406, 'M': 0.2895151019081816}, 'ALNS': {'A': 0.025014351589611815, 'B': 0.011711427826148674, 'E': 0.019524038390367395, 'M': 0.11336457412401688}}
