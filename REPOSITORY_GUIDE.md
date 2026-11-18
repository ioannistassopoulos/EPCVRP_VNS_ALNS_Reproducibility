# Repository Guide

Contents of the reproducibility repository of the paper
**"Variable Neighborhood Search and Its Variants on the Environmental Prize-Collecting Vehicle Routing Problem:
A Comparison with Adaptive Large Neighborhood Search"** and their relation to its sections and tables.

Conventions used in all files:

- instance names `<type>_<v>` with `v = 1..5`, i.e. demand ratio r = 0.60, 0.65, 0.70, 0.75, 0.80;
- objective = `E − P + 1000·K`, with `E = Σ d_ij · (0.772 + 0.324 · load_ij / capacity)` and Euclidean distances
  rounded to three decimals;
- routes: one list per vehicle, depot = node `1`, customer `i` of the instance file = node `i + 1`, **pick-up direction**;
- method codes: `gvns` = baseline GVNS, `v1` = V1-60, `v1w` = V1-W, `v2` = V2, `v3` = V3, `alns` = ALNS (see `README.md`);
- `qlow_mode`: `long` = Q<sub>low</sub> stored in the instance file; `max` = max(Q<sub>low</sub> of the file, ⌈r · total demand⌉);
- "Q<sub>low</sub> r × total demand" / `trachanatzi`: the definition Q<sub>low</sub> = r · total demand stated by Trachanatzi et al.

## 1. Executable — `epcvrp_vns`

Compiled GNU/Linux x86-64 executable with the six methods of the paper (Nuitka, one file). Instructions, arguments,
output format and system requirements: [`README.md`](README.md).

## 2. Run records — `results/run_records/<method>/`

One JSON file per run, as written by the executable, named `<instance>__<method>__q<mode>__seed<NNN>.json`:

| Folder | Runs | Content |
|---|---|---|
| `gvns/`, `v1w/`, `v2/` | 660 each | seeds 1–5 of the 120 instances with `qlow_mode = long`, plus the repeated runs with `max` |
| `v3/` | 665 | as above (13 instances repeated with `max`) |
| `v1/`, `alns/` | 4,020 each | seeds 1–30 of the 120 instances (`long`), plus the repeated runs with `max` (14 instances) |

The records are the output of the solvers as they were run for the paper, with three changes made for the release:
the routes are written in the pick-up direction (the solvers build them in the opposite direction; field
`routes_direction`), the field `method` was added, and the field `source_sha256` (hashes of source files that are not
distributed) was removed. The search does not depend on any of these fields.

`results/raw_runs.csv` has one row per run (10,685 rows): method, instance, Q<sub>low</sub> mode, `used_in_paper`, seed,
objective, E, P, K, served demand, both Q<sub>low</sub> values and the feasibility of the solution under both definitions,
iterations, work units, wall time and routes.

Every solution was re-certified by an independent validator when the runs were made (objective recomputed from the routes;
all K routes non-empty, capacity, Q<sub>low</sub> under both definitions).

## 3. Best solutions — `results/best_solutions/`

| File | Content |
|---|---|
| `best_solutions.csv`, `best_solutions.json` | for each of the 120 instances, the best solution over all runs of the paper that are feasible under both Q<sub>low</sub> definitions: objective, E, P, K, served demand, Q<sub>low</sub> values, method, seed, number of runs reaching it and routes |
| `routes/<instance>.txt` | the same solution in readable form |

## 4. Comparison with the published results — `results/comparison/` (Section 3.2)

| File | Content |
|---|---|
| `published_values_trachanatzi.csv` | all values transcribed from Trachanatzi et al. (2020), Tables 6–9, and (2021), Tables 3–8: Gurobi and the metaheuristics, per instance, with the minimum over all columns and the internal inconsistencies of the 2021 study |
| `published_values_long_format.csv` | the same values, one per row, with table and PDF page |
| `reference_revised.csv` | reference used in the paper: the minimum of all published values, without the published values proven not to correspond to feasible solutions (five instances, Section 3.1) |
| `table_<method>.csv` | per instance and method: best, mean and worst score of the runs, feasibility and comparison with the reference |
| `five_runs_vs_reference_summary.json` | counts better / equal / worse than the reference (best of seeds 1–5) and runs that beat it, for every method |

## 5. Statistics — `results/statistics/` (Sections 3.3 and 3.4)

One folder per paired comparison (`analysis_<variant>_vs_<reference>`, wins, ties and losses, mean difference with bootstrap
interval, Wilcoxon test, per-instance differences), and `analysis_seeds30` for the thirty-run analysis of V1-60 and ALNS
(`report_seeds30.md`, `analysis_seeds30.json`, per-instance tables). The folder names use the codes `V1_60s` (V1-60) and `V1` (V1-W).

## 6. Exact model — `results/exact_model/` (Section 3.1, Table 4)

One folder per Gurobi run with `result.json` (status, bound, best objective, gap, time, routes of the best solution found),
`gurobi.log` and `checkpoints.csv`; `exact_model_summary.csv` lists all 15 runs:

- `*__tieopt`, `*__optimal`: optimality proofs (status `OPTIMAL`) of the nine tie instances and of A-n32-k5_5 under both
  Q<sub>low</sub> definitions;
- `*__proof`: lower bounds that exclude the published values of A-n53-k7_3, A-n53-k7_5, E-n51-k5_1 and E-n51-k5_5
  (`qmin` = smaller of the two Q<sub>low</sub> definitions, `qzero` = Q<sub>low</sub> = 0).

## 7. Replay of the executable — `results/executable_replay/`

`replay_report.csv`: 72 recorded runs (12 instance/seed combinations for each of the six methods, among them the `max` mode of A-n32-k5_5, B-n78-k10_5 and A-n80-k10_5) repeated with the distributed executable; 72 of 72 identical to the records in objective, routes, work units, iterations and budget.
