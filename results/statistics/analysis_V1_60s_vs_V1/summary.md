# V1_60s vs V1_baseline_units: paired comparison

d = (V1_60s - V1_baseline_units)/V1_baseline_units in %, negative = V1_60s better.

| analysis | n | wins | ties | losses | material wins | material losses | median d | mean d [95% CI] | Wilcoxon p |
|---|---|---|---|---|---|---|---|---|---|
| instance mean (120 pairs) | 120 | 0 | 89 | 31 | 0 | 3 | +0.0000 | +0.0132 [+0.0071, +0.0202] | 9.313e-10 |
| instance best (120 pairs) | 120 | 0 | 106 | 14 | 0 | 2 | +0.0000 | +0.0086 [+0.0028, +0.0170] | 0.0001221 |
| seed level (600 pairs, pseudo-replication) | 600 | 0 | 517 | 83 | 0 | 24 | +0.0000 | +0.0132 [+0.0092, +0.0179] | 2.503e-15 |
| seed level, both runs feasible under both Q_low | 600 | 0 | 517 | 83 | 0 | 24 | +0.0000 | +0.0132 [+0.0092, +0.0179] | 2.503e-15 |
| family A instance mean | 45 | 0 | 38 | 7 | 0 | 0 | +0.0000 | +0.0031 [+0.0005, +0.0068] | n/a |
| family B instance mean | 30 | 0 | 30 | 0 | 0 | 0 | +0.0000 | +0.0000 [+0.0000, +0.0000] | n/a |
| family E instance mean | 25 | 0 | 19 | 6 | 0 | 0 | +0.0000 | +0.0016 [+0.0003, +0.0033] | n/a |
| family M instance mean | 20 | 0 | 2 | 18 | 0 | 3 | +0.0687 | +0.0700 [+0.0438, +0.1006] | 7.629e-06 |

Wall time (mean per instance): V1_baseline_units 97.2 s, V1_60s 76.4 s, median ratio V1_60s/V1_baseline_units 0.834; median ratio of shaking iterations 0.839.
