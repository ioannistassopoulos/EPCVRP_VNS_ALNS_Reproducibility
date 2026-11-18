# ALNS vs V1: paired comparison

d = (ALNS - V1)/V1 in %, negative = ALNS better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 50 | 17 | 53 | 17 | 10 | +0.0000 | -0.0558 [-0.1221, -0.0106] | 0.2149 |
| instance best (120 pairs) | 120 | 18 | 65 | 37 | 4 | 5 | +0.0000 | +0.0005 [-0.0137, +0.0125] | 0.048 |
| seed level (600 pairs, pseudo-replication) | 600 | 174 | 210 | 216 | 74 | 58 | +0.0000 | -0.0551 [-0.0902, -0.0254] | 0.7173 |
| seed level, both runs feasible under both Q_low | 599 | 174 | 210 | 215 | 74 | 57 | +0.0000 | -0.0555 [-0.0908, -0.0257] | 0.6714 |
| family A instance mean | 45 | 22 | 7 | 16 | 4 | 3 | +0.0000 | -0.0169 [-0.0392, +0.0042] | 0.226 |
| family B instance mean | 30 | 13 | 6 | 11 | 6 | 1 | +0.0000 | -0.0507 [-0.0941, -0.0127] | 0.06043 |
| family E instance mean | 25 | 7 | 4 | 14 | 2 | 0 | +0.0020 | -0.0100 [-0.0349, +0.0105] | 0.5854 |
| family M instance mean | 20 | 8 | 0 | 12 | 5 | 6 | +0.0213 | -0.2080 [-0.5819, +0.0422] | 0.7285 |

Wall time (mean per instance): V1 97.2 s, ALNS 75.8 s, median ratio ALNS/V1 0.826; median ratio of shaking iterations 8.077.
