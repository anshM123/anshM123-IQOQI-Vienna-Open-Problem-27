# The remaining clauses of OQP 27

This folder settles the clauses of Problem 27 that go beyond the optimality and uniqueness theorem of the papers,
and contains one strengthening of that theorem (POVMs, d = 3..8).
[`LEDGER.md`](LEDGER.md) has the exact wording of the problem and the verdict on every clause.

| Folder | Clause | Result | Checks |
|---|---|---|---|
| [`noise-cglmp/`](noise-cglmp/) | 27B(ii), noise resistance of the CGLMP violation | true for every d; DKZ is the unique optimum | Lean: `../lean/OQP27/CglmpNoise.lean` |
| [`noise-literal/`](noise-literal/) | 27B(ii), Gill's literal reading (uniform outcome noise, all Bell inequalities) | false for every d >= 4, on Phi_d itself | `python verify_theorem.py` (17 checks, about 3 min); two independent verifications |
| [`kl-divergence/`](kl-divergence/) | 27B(iii), Kullback-Leibler discrimination | false for every d >= 4 | `python verify_main.py` and the scripts listed in THEOREM.md; one independent verification |
| [`povm/`](povm/) | strengthening of 27B(i): arbitrary POVMs instead of projective measurements | DKZ optimal and unique among all POVMs for d = 3..8 (every local dimension) | `cd certs && python ../verify_povm.py 3 4 5 6 7 8` (exact; add `iv` first for the interval check); one independent verification |

Each theorem is stated and proved in the folder's `THEOREM.md`. Every computational input is checked in exact
rational/algebraic arithmetic or with rigorous interval enclosures; no decision rests on a floating-point comparison.
The independent verifications re-derived the proofs and re-checked the computations with separate code; their reports
are `INDEPENDENT_VERIFICATION*.md`, and their scripts and logs are in the `independent-check*` subfolders.

Requirements: Python 3 with numpy, scipy, sympy and mpmath. Run each script from its own folder with
`OMP_NUM_THREADS=1`.
