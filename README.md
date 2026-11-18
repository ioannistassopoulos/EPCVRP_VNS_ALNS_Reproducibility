# Variable Neighborhood Search and Its Variants on the Environmental Prize-Collecting Vehicle Routing Problem: A Comparison with Adaptive Large Neighborhood Search

## Overview

This repository is the reproducibility package of the research paper
**"Variable Neighborhood Search and Its Variants on the Environmental Prize-Collecting Vehicle Routing Problem:
A Comparison with Adaptive Large Neighborhood Search"**.

The paper studies the Environmental Prize-Collecting Vehicle Routing Problem (EPCVRP): a limited fleet of identical
vehicles selects and serves a subset of customers so that the collected demand reaches a minimum threshold
Q<sub>low</sub>, while the objective `E − P + 1000·K` (load-dependent CO₂ emissions, minus collected prizes, plus a
fixed cost per vehicle) is minimized. It compares a baseline general variable neighborhood search (GVNS), three
variants of it that each change one component (V1: random order of the neighborhoods, V2: adaptive choice of the
neighborhood, V3: skewed acceptance), and an adaptive large neighborhood search (ALNS) with the best values
published for the problem by Trachanatzi et al., on the 120 benchmark instances of Long et al. (2019).

The search budget is expressed in **deterministic work units** instead of seconds. Therefore **the same method,
instance, Q<sub>low</sub> mode and seed give exactly the same run on any computer**. The executable of this repository
reproduces the runs reported in the paper exactly; see [Reproducing the paper](#reproducing-the-paper).

This repository provides:

- the compiled executable `epcvrp_vns` (GNU/Linux x86-64; no Python installation is needed) with the six methods of the paper;
- the raw record of every run reported in the paper (five seeds for every method, thirty seeds for V1-60 and ALNS), including the routes;
- the **best solution (routes) found for each of the 120 instances**;
- the data of the comparisons and statistical tests of the paper;
- the results and logs of the exact model solved with Gurobi (optimality proofs and lower bounds);
- SHA-256 checksums of all files and of the benchmark instance files.

A file-by-file description is given in [`REPOSITORY_GUIDE.md`](REPOSITORY_GUIDE.md).

---

## Methods

The executable runs one method per call, chosen with `--method`:

| `--method` | Name in the paper | Description | Budget |
|---|---|---|---|
| `gvns` | Baseline | GVNS: variable neighborhood descent over six neighborhoods in a fixed order, destroy-and-repair shaking, acceptance of improvements only | calibrated to about 60 s (46 to 57 million work units) |
| `v1` | V1-60 | V1: the order of the neighborhoods in the descent is random | calibrated to its own work rate, about 60 s (25.6 to 44.7 million units) |
| `v1w` | V1-W | V1 with the budget of the baseline (equal work) | as the baseline |
| `v2` | V2 | adaptive choice of the neighborhood with ALNS-style weights | as the baseline |
| `v3` | V3 | skewed acceptance of slightly worse solutions that are far from the current one | as the baseline |
| `alns` | ALNS | adaptive large neighborhood search after Ropke and Pisinger (2006) | calibrated to its own work rate, about 60 s (108 to 151 million units) |

All parameters are fixed to the values of the paper and cannot be changed from the command line.

---

## Quick start

```bash
# 1. get the executable (this repository) and make it executable
chmod +x epcvrp_vns

# 2. get the benchmark instances of Long et al. (2019)
wget https://github.com/longjianyuGH/PCVRP/raw/master/InstancesOfPCVRP.zip
unzip InstancesOfPCVRP.zip            # creates InstancesOfPCVRP/ with 120 files A-n32-k5_1.txt ... M-n200-k17_5.txt

# 3. (optional) check that the instance files are the ones used in the paper
cd InstancesOfPCVRP && sha256sum -c ../instances/INSTANCE_CHECKSUMS.sha256 && cd ..

# 4. run the baseline GVNS with seed 1 on instance A-n32-k5 with r = 0.60
./epcvrp_vns --method gvns --instance InstancesOfPCVRP/A-n32-k5_1.txt --seeds 1 --out-dir my_results
```

Expected output (the wall-clock time depends on the computer; everything else is identical on every computer):

```text
epcvrp_vns 1.0 (method gvns)
instance=.../InstancesOfPCVRP/A-n32-k5_1.txt qlow_mode=long budget=calibrated seeds=[1] out=.../my_results
seed 1: objective 4296.599434 (4.297E+03), served demand 395, feasible Q_low Long=True Q_low r*TotalDemand=True, 23368 iterations, 78.4 s -> A-n32-k5_1__gvns__qlong__seed001.json
  route 1: 1 28 25 1
  route 2: 1 22 32 20 18 14 8 27 1
  route 3: 1 15 19 9 12 5 24 3 4 7 1
  route 4: 1 13 2 17 31 1
  route 5: 1 30 23 10 16 11 26 6 21 1
done in 78.5 s
```

This is exactly run `A-n32-k5_1`, seed 1, of the baseline in the paper
(`results/run_records/gvns/A-n32-k5_1__gvns__qlong__seed001.json`).

The first start of the executable takes a few extra seconds, because it unpacks itself to a temporary folder.

Command-line help:

```bash
./epcvrp_vns --help
./epcvrp_vns --version
```

---

## Command-line arguments

| Argument | Required | Description |
|---|---|---|
| `--method` | yes | `gvns`, `v1`, `v1w`, `v2`, `v3` or `alns` (see above). |
| `--instance` | yes | Path of a benchmark file of Long et al., named `<type>_<v>.txt` with `v = 1..5` (e.g. `A-n32-k5_1.txt`). The suffix `v` gives the demand ratio r = 0.60, 0.65, 0.70, 0.75, 0.80. |
| `--seeds` | no | Random seeds: `1`, `1 2 3`, `1,2,3`, `1-30` (default `1`). One run per seed, executed one after the other. |
| `--qlow-mode` | no | `long` (default): Q<sub>low</sub> as stored in the file. `max`: Q<sub>low</sub> = max(Q<sub>low</sub> of the file, ⌈r · total demand⌉). |
| `--budget` | no | `calibrated` (default): the work budget used in the paper. Or a positive integer number of work units (e.g. for a quick test). |
| `--out-dir` | no | Folder for the JSON results (default: current folder). Existing result files are not overwritten. |
| `--version` | no | Print the version and exit. |

Several runs can be executed in parallel by starting several processes, e.g. one per seed or per method:

```bash
for s in 1 2 3 4 5; do ./epcvrp_vns --method alns --instance InstancesOfPCVRP/A-n32-k5_1.txt --seeds $s --out-dir my_results & done; wait
```

### Output

One JSON file per run, `<instance>__<method>__q<mode>__seed<NNN>.json`, with the same fields as the run records of
this repository. The most important fields are:

| Field | Meaning |
|---|---|
| `objective` | objective value `E − P + 1000·K` of the best solution (full precision) |
| `score_4sd` | the objective with four significant digits, as compared with the published values |
| `routes`, `routes_direction` | the routes of the best solution: one list per vehicle, depot = node `1`, customer `i` of the file = node `i + 1`, in **pick-up direction** (the load grows along the route) |
| `served_demand`, `qlow_search` | collected demand of the best solution and the Q<sub>low</sub> used in the search |
| `feasible_qlow_long`, `feasible_qlow_trachanatzi` | feasibility of the best solution with respect to the Q<sub>low</sub> of the file and to Q<sub>low</sub> = r · total demand |
| `budget_units`, `units_used` | work budget and work units consumed (the run stops at the first check after the budget is reached) |
| `gvns_iterations` | number of iterations of the main loop (shaking steps for the VNS methods, ALNS iterations for `alns`) |
| `improvements`, `stats`, `work_by_kind` | the improvements found (work units, wall time, objective), counters of the search and work units by kind of operation |
| `adaptive`, `skewed`, `alns` | diagnostics specific to `v2`, `v3` and `alns` (weights, acceptance counts, temperature, ...) |
| `wall_s`, `host` | wall-clock time and computer name (recorded only; they do not influence the search) |

---

## Reproducing the paper

The comparison with the published results uses the best of seeds 1 to 5 of every method; the 30-run analysis of the
paper uses seeds 1 to 30 of V1-60 (`v1`) and ALNS (`alns`). The Q<sub>low</sub> protocol is: every instance is first run with
`--qlow-mode long`; an instance whose solution (or whose seeds) violate Q<sub>low</sub> = r · total demand is run again with
`--qlow-mode max`, so that a result holds under either definition. The column `used_in_paper` of
`results/raw_runs.csv` marks the runs used in the paper; the runs with the other mode are also kept. Any run can be repeated
with the executable, e.g.

```bash
./epcvrp_vns --method alns --instance InstancesOfPCVRP/A-n80-k10_5.txt --qlow-mode max --seeds 1-30 --out-dir rerun
```

and the result must coincide with the stored record in `objective`, `routes`, `units_used` and `gvns_iterations`.

**Replay check performed for this release:** 72 recorded runs were repeated with the distributed executable, using the instance files as downloaded from Long et al.: 12 instance and seed combinations for each of the six methods (groups A, B, E and M; three of them in the repeated `max` mode: A-n32-k5_5, B-n78-k10_5 and A-n80-k10_5). All 72 runs are identical to the records of the paper in objective value, routes, work units, number of iterations and budget; see `results/executable_replay/replay_report.csv` (the wall-clock times differ, as expected).

The calibrated budgets correspond to about 60 s per run on the computer used for the calibration (AMD Ryzen 9 5900X);
on other computers only the wall-clock time changes. The 30-seed runs of the paper were executed on an Intel Core
i9-14900K with 32 logical cores, with several runs in parallel, so their wall-clock times are not comparable with those
of the five-seed runs.

---

## Best solutions

`results/best_solutions/` contains, for each of the 120 instances, the best solution found over all methods and seeds
of the paper among the runs that are feasible with respect to both definitions of Q<sub>low</sub>:

- `best_solutions.csv` / `best_solutions.json`: objective, emissions E, prizes P, number of vehicles K, served demand,
  both Q<sub>low</sub> values, the method and seed of the run and the number of runs that reach the same value;
- `routes/<instance>.txt`: the same solution in readable form, e.g. `routes/A-n32-k5_5.txt`:

```text
instance A-n32-k5_5, best solution over all methods and seeds of the paper
method gvns, seed 2, Q_low mode max, reached by 52 runs of methods: alns gvns v1 v1w v2 v3
objective 4628.10373768 = E 581.10373768 - P 953 + 1000 x K 5
served demand 328 (Q_low of the file 315, r x total demand 328.0)
routes (depot = 1, pick-up direction):
  vehicle 1: 1 17 8 2 13 1
  vehicle 2: 1 21 30 23 10 19 9 12 5 29 24 4 1
  vehicle 3: 1 15 25 28 1
  vehicle 4: 1 7 18 20 32 22 14 27 1
  vehicle 5: 1 31 1
```

For the instances with a proven optimum (`results/exact_model/`) the best solution is optimal.

---

## Routes: pick-up direction

The paper models the problem as a pick-up problem: a vehicle leaves the depot empty and the load on board grows as
customers are visited. All routes of this repository are given in that direction. For every run record, the objective
was recomputed from the stored routes with the pick-up formula
`E = Σ d_ij · (0.772 + 0.324 · load_ij / capacity)`, where `load_ij` is the demand collected before the arc (i, j);
all 10,685 records agree with the stored objective to 1e-6.

---

## System requirements

- GNU/Linux, x86-64
- glibc ≥ 2.38
- tested on Ubuntu 24.04 LTS

The executable is self-contained: Python and all dependencies of the solvers are included. On the first start the
executable unpacks itself to a temporary folder. The executable is about 24 MB.

Build environment of the distributed executable:

| Component | Version |
|---|---|
| Python | 3.14.10 |
| Nuitka | 4.3.5 (`--mode=onefile`) |
| NumPy | 2.5.4 |
| GCC | 13.3.0 |

These are the same versions of Python and NumPy that were used for the runs of the paper.

---

## Benchmark instances

The 120 benchmark instances are those of Long et al. (2019), available at
<https://github.com/longjianyuGH/PCVRP> (file `InstancesOfPCVRP.zip`). They are not redistributed here.
`instances/INSTANCE_CHECKSUMS.sha256` lists the SHA-256 of every file used in the paper; the files of
`InstancesOfPCVRP.zip` are byte-identical to them.

---

## Source code availability

The executable provides access to the methods of the paper for reproducibility and evaluation purposes. The source
code of the solvers is not distributed in this repository.

---

## Integrity

`CHECKSUMS.sha256` lists the SHA-256 of every file of this repository. To verify:

```bash
sha256sum -c CHECKSUMS.sha256
```

SHA-256 of the executable:

```text
ba41655e4866fc0ddc584d47aff33358ad2ee965ee6eabedd5843209a1386d26  epcvrp_vns
```

---

## Citation

If you use this repository, please cite the paper:

**"Variable Neighborhood Search and Its Variants on the Environmental Prize-Collecting Vehicle Routing Problem:
A Comparison with Adaptive Large Neighborhood Search."**

The final journal citation will be added after publication.
