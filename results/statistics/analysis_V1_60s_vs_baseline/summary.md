# V1_60s vs baseline: paired comparison

d = (V1_60s - baseline)/baseline in %, negative = V1_60s better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 62 | 26 | 32 | 18 | 2 | -0.0037 | -0.0646 [-0.1147, -0.0283] | 0.0001208 |
| instance best (120 pairs) | 120 | 24 | 80 | 16 | 8 | 2 | +0.0000 | -0.0311 [-0.0617, -0.0075] | 0.08415 |
| seed level (600 pairs, pseudo-replication) | 600 | 206 | 274 | 120 | 98 | 35 | +0.0000 | -0.0628 [-0.1062, -0.0287] | 4.105e-08 |
| seed level, both runs feasible under both Q_low | 600 | 206 | 274 | 120 | 98 | 35 | +0.0000 | -0.0628 [-0.1062, -0.0287] | 4.105e-08 |
| family A instance mean | 45 | 29 | 6 | 10 | 6 | 0 | -0.0204 | -0.0360 [-0.0576, -0.0162] | 0.0007071 |
| family B instance mean | 30 | 14 | 12 | 4 | 5 | 1 | +0.0000 | -0.1095 [-0.2790, -0.0058] | 0.04317 |
| family E instance mean | 25 | 11 | 7 | 7 | 3 | 0 | +0.0000 | -0.0205 [-0.0422, -0.0016] | 0.1415 |
| family M instance mean | 20 | 8 | 1 | 11 | 4 | 1 | +0.0048 | -0.1166 [-0.2468, -0.0068] | 0.7381 |

Wall time (mean per instance): baseline 78.1 s, V1_60s 76.4 s, median ratio V1_60s/baseline 0.976; median ratio of shaking iterations 0.819.
