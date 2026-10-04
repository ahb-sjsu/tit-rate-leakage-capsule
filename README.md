# Numerical checks for "Rate, Leakage, and Distortion for Gaussian Sources: Water-Filling on a Tilted Weight"

Andrew H. Bond, San Jose State University.

This repository is a Code Ocean capsule. It runs the numerical checks described in the appendix
"Numerical Checks" of the manuscript. No proof depends on them. They
check identities and instances of theorems proved in the text.

## Running

`code/run` runs the fourteen Python scripts in turn. Each script prints
PASS or FAIL lines. Its output goes to `results/<script>.txt`, and a table
of exit codes, PASS and FAIL counts, and run times goes to
`results/summary.txt`. A clean run ends with
`nonzero exits plus FAIL lines: 0`. All random draws are seeded.

Environment: Python 3.12 with numpy 2.2.6, scipy 1.17.1, cvxpy 1.9.2 and
sympy 1.14.0 (`environment/Dockerfile`, `environment/requirements.txt`).
These are the versions that produced the recorded outputs.

## Scripts and the results they check

| Script | Checks |
|---|---|
| `verify_general.py` | pencil value of Theorem 16 against brute force, convexity of both costs in the error covariance (Theorem 5), uniqueness of weighted minimizers, Theorems 20 and 22 |
| `verify_commuting.py` | closed form of Theorem 13, activation rule, block-diagonal optimum of Theorem 12 |
| `verify_coupled.py`, `verify_parallel.py`, `verify_pencil.py` | scalar identity of Corollary 17 (symbolic), determinant program against brute force, certificate, allocation, numbers in the Examples section |
| `tqp_leakage_demo.py` | Table I and Fig. 1 (fixed-rate scalar quantizers) |
| `verify_decoder_si.py` | Lemma 30 with a non-Gaussian description, reduction of Theorem 31(b) |
| `verify_fixed_read.py` | fixed-direction leakage, Proposition 24, Theorem 25 |
| `verify_lowdist.py` | Theorem 15 and the rank bound of Proposition 6 |
| `verify_tilted.py` | Theorem 7 at the optimum of an independent determinant program, Corollary 9 |
| `verify_scalar_path.py` | Theorem 18 and its secular equation |
| `verify_mm.py` | monotone iteration of Proposition 11 |
| `verify_decsi_identities.py` | decoder side-information identities on random matrices, Monte Carlo check of the fixed-gain estimate |
| `verify_decbounds.py` | example after Proposition 32, inner and outer bounds, degraded cases |

Theorem numbers refer to the submitted manuscript.

## Recorded outputs

`data/recorded/` holds the outputs recorded when the manuscript was
written, for comparison with a fresh run. It also holds the records of the
symbolic and formal checks below.

## Not run by the capsule

- `code/matlab_checks.m` needs MATLAB with the Symbolic Math Toolbox. Its
  recorded output is in `data/recorded/symbolic_and_lean-*.txt`.
- `code/lean/` holds the Lean 4 modules `RateLeakage.lean` and
  `LogDet.lean` (Lean v4.32.2, Mathlib v4.32.2). Building them needs
  Mathlib, which is several gigabytes. With `elan` installed, run
  `lake exe cache get` and then `lake build` in `code/lean`. The recorded
  builds and axiom audits are in `data/recorded/lean-2026-10-03.txt` and
  `data/recorded/lean-logdet-2026-10-03.txt`.

## Source

Public repository `https://github.com/ahb-sjsu/geometric-observation`,
directory `paper/tit-rate-leakage`. Archived at
`https://doi.org/10.5281/zenodo.23127802`.

## License

Two licenses, split by what the file is.

| Files | License |
|---|---|
| Code (`code/`, `environment/`) | MIT, see `LICENSE` |
| Text and recorded outputs (`README.md`, `data/`) | CC BY 4.0, see `LICENSE-TEXT` |

The manuscript itself is not part of this repository.
