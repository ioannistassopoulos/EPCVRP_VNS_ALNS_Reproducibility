# ALNS vs V1_60s: paired comparison

d = (ALNS - V1_60s)/V1_60s in %, negative = ALNS better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 54 | 17 | 49 | 17 | 5 | +0.0000 | -0.0688 [-0.1394, -0.0209] | 0.02506 |
| instance best (120 pairs) | 120 | 21 | 65 | 34 | 4 | 2 | +0.0000 | -0.0080 [-0.0282, +0.0068] | 0.3836 |
| seed level (600 pairs, pseudo-replication) | 600 | 190 | 209 | 201 | 83 | 47 | +0.0000 | -0.0682 [-0.1046, -0.0374] | 0.01914 |
| seed level, both runs feasible under both Q_low | 599 | 190 | 209 | 200 | 83 | 46 | +0.0000 | -0.0686 [-0.1053, -0.0378] | 0.01599 |
| family A instance mean | 45 | 22 | 7 | 16 | 4 | 3 | +0.0000 | -0.0201 [-0.0420, +0.0010] | 0.1216 |
| family B instance mean | 30 | 13 | 6 | 11 | 6 | 1 | +0.0000 | -0.0507 [-0.0941, -0.0127] | 0.06043 |
| family E instance mean | 25 | 8 | 4 | 13 | 2 | 0 | +0.0013 | -0.0116 [-0.0365, +0.0087] | 0.6827 |
| family M instance mean | 20 | 11 | 0 | 9 | 5 | 1 | -0.0056 | -0.2775 [-0.6718, -0.0109] | 0.4304 |

Wall time (mean per instance): V1_60s 76.4 s, ALNS 75.8 s, median ratio ALNS/V1_60s 0.999; median ratio of shaking iterations 9.659.
