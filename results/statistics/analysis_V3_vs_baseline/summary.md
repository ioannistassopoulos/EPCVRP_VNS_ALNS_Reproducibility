# V3 vs baseline: paired comparison

d = (V3 - baseline)/baseline in %, negative = V3 better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 67 | 15 | 38 | 26 | 4 | -0.0194 | -0.0861 [-0.1414, -0.0427] | 6.845e-05 |
| instance best (120 pairs) | 120 | 18 | 70 | 32 | 11 | 5 | +0.0000 | -0.0204 [-0.0478, +0.0017] | 0.6877 |
| seed level (600 pairs, pseudo-replication) | 600 | 220 | 205 | 175 | 125 | 48 | +0.0000 | -0.0842 [-0.1271, -0.0494] | 6.374e-08 |
| seed level, both runs feasible under both Q_low | 598 | 219 | 205 | 174 | 125 | 48 | +0.0000 | -0.0845 [-0.1308, -0.0503] | 5.822e-08 |
| family A instance mean | 45 | 32 | 4 | 9 | 11 | 0 | -0.0423 | -0.0577 [-0.0812, -0.0360] | 6.246e-06 |
| family B instance mean | 30 | 14 | 9 | 7 | 7 | 2 | +0.0000 | -0.1282 [-0.3016, -0.0171] | 0.02901 |
| family E instance mean | 25 | 13 | 2 | 10 | 3 | 0 | -0.0031 | -0.0117 [-0.0388, +0.0144] | 0.5009 |
| family M instance mean | 20 | 8 | 0 | 12 | 5 | 2 | +0.0084 | -0.1798 [-0.3647, -0.0168] | 0.8408 |

Wall time (mean per instance): baseline 78.1 s, V3 94.0 s, median ratio V3/baseline 1.174; median ratio of shaking iterations 0.996.
