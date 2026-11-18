# V1 RVND vs baseline GVNS: paired comparison

d = (V1 - baseline)/baseline in %, negative = V1 better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 71 | 26 | 23 | 20 | 1 | -0.0110 | -0.0777 [-0.1291, -0.0396] | 5.229e-08 |
| instance best (120 pairs) | 120 | 26 | 80 | 14 | 9 | 0 | +0.0000 | -0.0396 [-0.0763, -0.0125] | 0.002908 |
| seed level (600 pairs, pseudo-replication) | 600 | 226 | 276 | 98 | 104 | 24 | +0.0000 | -0.0759 [-0.1194, -0.0416] | 1.64e-14 |
| seed level, both runs feasible under both Q_low | 600 | 226 | 276 | 98 | 104 | 24 | +0.0000 | -0.0759 [-0.1194, -0.0416] | 1.64e-14 |
| family A instance mean | 45 | 30 | 7 | 8 | 6 | 0 | -0.0228 | -0.0391 [-0.0604, -0.0200] | 0.0001313 |
| family B instance mean | 30 | 14 | 12 | 4 | 5 | 1 | +0.0000 | -0.1095 [-0.2790, -0.0058] | 0.04317 |
| family E instance mean | 25 | 13 | 6 | 6 | 3 | 0 | -0.0004 | -0.0221 [-0.0434, -0.0036] | 0.04937 |
| family M instance mean | 20 | 14 | 1 | 5 | 6 | 0 | -0.0334 | -0.1864 [-0.3280, -0.0638] | 0.004578 |

Wall time (mean per instance): baseline 78.1 s, V1 97.2 s, median ratio V1/baseline 1.200; median ratio of shaking iterations V1/baseline 0.980.
