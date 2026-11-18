# V3 vs V1: paired comparison

d = (V3 - V1)/V1 in %, negative = V3 better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 48 | 27 | 45 | 9 | 12 | +0.0000 | -0.0084 [-0.0269, +0.0078] | 0.7259 |
| instance best (120 pairs) | 120 | 9 | 72 | 39 | 3 | 9 | +0.0000 | +0.0193 [+0.0064, +0.0341] | 0.0001269 |
| seed level (600 pairs, pseudo-replication) | 600 | 139 | 244 | 217 | 60 | 75 | +0.0000 | -0.0080 [-0.0306, +0.0115] | 0.02839 |
| seed level, both runs feasible under both Q_low | 598 | 138 | 244 | 216 | 60 | 75 | +0.0000 | -0.0081 [-0.0312, +0.0109] | 0.03222 |
| family A instance mean | 45 | 23 | 9 | 13 | 3 | 2 | -0.0013 | -0.0185 [-0.0376, -0.0004] | 0.05157 |
| family B instance mean | 30 | 12 | 10 | 8 | 3 | 2 | +0.0000 | -0.0187 [-0.0459, +0.0058] | 0.1536 |
| family E instance mean | 25 | 7 | 8 | 10 | 0 | 2 | +0.0000 | +0.0103 [-0.0075, +0.0286] | 0.2842 |
| family M instance mean | 20 | 6 | 0 | 14 | 3 | 6 | +0.0474 | +0.0064 [-0.0834, +0.0792] | 0.09731 |

Wall time (mean per instance): V1 97.2 s, V3 94.0 s, median ratio V3/V1 0.967; median ratio of shaking iterations 1.015.
