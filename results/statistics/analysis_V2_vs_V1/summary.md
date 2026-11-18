# V2 vs V1: paired comparison

d = (V2 - V1)/V1 in %, negative = V2 better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 38 | 35 | 47 | 3 | 7 | +0.0000 | -0.0003 [-0.0260, +0.0221] | 0.4792 |
| instance best (120 pairs) | 120 | 20 | 85 | 15 | 4 | 3 | +0.0000 | -0.0009 [-0.0112, +0.0105] | 0.5988 |
| seed level (600 pairs, pseudo-replication) | 600 | 120 | 333 | 147 | 44 | 53 | +0.0000 | -0.0000 [-0.0215, +0.0192] | 0.2024 |
| seed level, both runs feasible under both Q_low | 600 | 120 | 333 | 147 | 44 | 53 | +0.0000 | -0.0000 [-0.0215, +0.0192] | 0.2024 |
| family A instance mean | 45 | 15 | 7 | 23 | 0 | 3 | +0.0014 | +0.0122 [-0.0031, +0.0276] | 0.1892 |
| family B instance mean | 30 | 5 | 19 | 6 | 0 | 0 | +0.0000 | -0.0040 [-0.0147, +0.0051] | 0.8311 |
| family E instance mean | 25 | 6 | 8 | 11 | 0 | 1 | +0.0000 | +0.0123 [-0.0046, +0.0310] | 0.2069 |
| family M instance mean | 20 | 12 | 1 | 7 | 3 | 3 | -0.0081 | -0.0387 [-0.1819, +0.0901] | 0.2579 |

Wall time (mean per instance): V1 97.2 s, V2 91.8 s, median ratio V2/V1 0.947; median ratio of shaking iterations 1.024.

Adaptive diagnostics (600 runs): mean total-variation distance of the final probabilities from uniform 0.1781 (max 0.5395).

| family | two_opt | relocate | swap | two_opt_star | drop_add_replace | segment_exchange | min p | max p | segments | select share | update share |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A | 0.186 | 0.270 | 0.191 | 0.104 | 0.148 | 0.102 | 0.050 | 0.406 | 1007 | 0.00210 | 0.00013 |
| B | 0.187 | 0.279 | 0.202 | 0.093 | 0.133 | 0.105 | 0.050 | 0.440 | 829 | 0.00173 | 0.00010 |
| E | 0.164 | 0.312 | 0.178 | 0.095 | 0.155 | 0.096 | 0.050 | 0.706 | 1197 | 0.00253 | 0.00015 |
| M | 0.181 | 0.255 | 0.188 | 0.120 | 0.134 | 0.122 | 0.082 | 0.310 | 113 | 0.00021 | 0.00001 |
