# V2 vs baseline: paired comparison

d = (V2 - baseline)/baseline in %, negative = V2 better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 68 | 21 | 31 | 19 | 3 | -0.0046 | -0.0780 [-0.1363, -0.0330] | 2.484e-05 |
| instance best (120 pairs) | 120 | 31 | 77 | 12 | 10 | 1 | +0.0000 | -0.0406 [-0.0726, -0.0154] | 0.0006871 |
| seed level (600 pairs, pseudo-replication) | 600 | 213 | 272 | 115 | 104 | 37 | +0.0000 | -0.0762 [-0.1203, -0.0410] | 3.045e-10 |
| seed level, both runs feasible under both Q_low | 600 | 213 | 272 | 115 | 104 | 37 | +0.0000 | -0.0762 [-0.1203, -0.0410] | 3.045e-10 |
| family A instance mean | 45 | 23 | 4 | 18 | 6 | 1 | -0.0013 | -0.0270 [-0.0500, -0.0055] | 0.06536 |
| family B instance mean | 30 | 13 | 13 | 4 | 5 | 1 | +0.0000 | -0.1135 [-0.2833, -0.0076] | 0.05054 |
| family E instance mean | 25 | 15 | 3 | 7 | 3 | 1 | -0.0037 | -0.0097 [-0.0330, +0.0148] | 0.1982 |
| family M instance mean | 20 | 17 | 1 | 2 | 5 | 0 | -0.0336 | -0.2250 [-0.4481, -0.0557] | 2.67e-05 |

Wall time (mean per instance): baseline 78.1 s, V2 91.8 s, median ratio V2/baseline 1.138; median ratio of shaking iterations 0.992.

Adaptive diagnostics (600 runs): mean total-variation distance of the final probabilities from uniform 0.1781 (max 0.5395).

| family | two_opt | relocate | swap | two_opt_star | drop_add_replace | segment_exchange | min p | max p | segments | select share | update share |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A | 0.186 | 0.270 | 0.191 | 0.104 | 0.148 | 0.102 | 0.050 | 0.406 | 1007 | 0.00210 | 0.00013 |
| B | 0.187 | 0.279 | 0.202 | 0.093 | 0.133 | 0.105 | 0.050 | 0.440 | 829 | 0.00173 | 0.00010 |
| E | 0.164 | 0.312 | 0.178 | 0.095 | 0.155 | 0.096 | 0.050 | 0.706 | 1197 | 0.00253 | 0.00015 |
| M | 0.181 | 0.255 | 0.188 | 0.120 | 0.134 | 0.122 | 0.082 | 0.310 | 113 | 0.00021 | 0.00001 |
