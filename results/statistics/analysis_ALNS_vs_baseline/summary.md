# ALNS vs baseline: paired comparison

d = (ALNS - baseline)/baseline in %, negative = ALNS better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 69 | 11 | 40 | 28 | 3 | -0.0112 | -0.1332 [-0.2216, -0.0622] | 1.111e-05 |
| instance best (120 pairs) | 120 | 24 | 65 | 31 | 10 | 3 | +0.0000 | -0.0390 [-0.0845, -0.0055] | 0.6814 |
| seed level (600 pairs, pseudo-replication) | 600 | 253 | 170 | 177 | 125 | 37 | +0.0000 | -0.1311 [-0.1851, -0.0857] | 1.046e-10 |
| seed level, both runs feasible under both Q_low | 599 | 253 | 170 | 176 | 125 | 37 | +0.0000 | -0.1314 [-0.1867, -0.0851] | 8.252e-11 |
| family A instance mean | 45 | 28 | 3 | 14 | 12 | 0 | -0.0123 | -0.0561 [-0.0836, -0.0307] | 0.0004998 |
| family B instance mean | 30 | 17 | 8 | 5 | 6 | 0 | -0.0094 | -0.1599 [-0.3532, -0.0375] | 0.001673 |
| family E instance mean | 25 | 15 | 0 | 10 | 5 | 0 | -0.0142 | -0.0320 [-0.0587, -0.0069] | 0.06263 |
| family M instance mean | 20 | 9 | 0 | 11 | 5 | 3 | +0.0011 | -0.3933 [-0.8198, -0.0545] | 0.6477 |

Wall time (mean per instance): baseline 78.1 s, ALNS 75.8 s, median ratio ALNS/baseline 0.983; median ratio of shaking iterations 7.993.
