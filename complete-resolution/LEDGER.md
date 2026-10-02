# OQP 27: clause-by-clause ledger

Status as of 2026-10-02. A clause is marked TRUE or FALSE only with a rigorous proof or a rigorous counterexample that
has been checked independently. Other statuses: NUMERICAL (strong numerical evidence only), OPEN.

## The problem as posed

IQOQI Vienna Open Quantum Problem 27, "The power of CGLMP inequalities" (proposed by R. Gill, 2006), in the setting of
two parties, two settings and d outcomes
([archived page](http://web.archive.org/web/20231029013544/https://oqp.iqoqi.oeaw.ac.at/the-power-of-cglmp-inequalities)):

> **Problem 27.A** Show that every face of the local polytope, which is not already contained in a face of the
> no-signalling polytope is of CGLMP type, i.e., an inequality of the form first written out in [1], but possibly lifted
> from lower dimensions by fusing together some outcomes.
>
> **Problem 27.B** Numerically, the observables maximally violating the CGLMP inequality on a maximally entangled state
> are of a very specific form [2], involving measurements in computational basis, transformed by only discrete Fourier
> transformation and diagonal unitaries [1]. Show that this is necessarily the case. Show also that these measurements
> realize the highest resistance of violation to noise, and the best discrimination against classical realism in the
> sense of Kullback-Leibler divergence [3].

([1] Collins, Gisin, Linden, Massar, Popescu, PRL 88, 040404 (2002); [2] Durt, Kaszlikowski, Zukowski, PRA 64, 024101
(2001); [3] van Dam, Grunwald, Gill, quant-ph/0307125.) In Gill's paper behind the problem (R. Gill, "Better Bell
inequalities (passion at a distance)", IMS Lecture Notes 55 (2007), arXiv:math/0610115), noise resistance means how
much the behaviour can be mixed with "completely random, uniform outcomes" while local realism is still violated.

## A. The clauses as posed

| Clause | Verdict | Proof / counterexample | Credit |
|---|---|---|---|
| **27A** every non-trivial facet of the (2,2,d) local polytope is of CGLMP type | **FALSE** | d = 4 has non-CGLMP facets | Bancal, Gisin, Pironio, J. Phys. A 43, 385303 (2010) (prior work, not ours) |
| **27B (i)** the observables maximally violating CGLMP on a maximally entangled state are necessarily the DKZ (DFT + diagonal unitaries) measurements | **TRUE for every d**: optimal for every local dimension D and all projective measurements, and the unique optimum up to local unitaries u (x) conj(u) and an inert ancilla (d \| D) | `../papers/math`, Theorems A and B; Lean `../lean/` (complete for 2 <= d <= 20; every d given the certified cone condition CONE_d for d >= 21, `../cone-certificates/`) | this work |
| **27B (ii)** "highest resistance of violation to noise", read as: noise resistance of the **CGLMP** violation (uniform outcome noise) | **TRUE for every d**; the threshold of every projective strategy is 2/I_d >= 2/I_ME(d), with equality only for DKZ | `noise-cglmp/THEOREM.md`; Lean `../lean/OQP27/CglmpNoise.lean` (only the standard axioms) | this work |
| **27B (ii)** read literally with Gill's noise: violation of **local realism** (all Bell inequalities) under uniform outcome noise | **FALSE for every d >= 4**, on the maximally entangled state Phi_d itself: an explicit projective strategy with critical visibility 4(d-1)/(4(d-1)+(sqrt2-1)d^2) (even d), 4/(4+(sqrt2-1)d) (odd d) beats DKZ, whose critical visibility is >= 1/2 for every d and within 1.02e-7 of 2/I_ME(d) for d = 3..20. (d = 2: true; d = 3: true on Phi_3, false on Phi_2.) | `noise-literal/THEOREM.md`, verifier `noise-literal/verify_theorem.py` (17 checks); two independent verifications `noise-literal/INDEPENDENT_VERIFICATION_A.md`, `..._B.md` | this work (exact theorem for every d). The effect was observed before: Acin, Durt, Gisin, Latorre, PRA 65, 052325 (2002), eq. (14) (the even-d threshold for a Schmidt-rank-2 state); Baek, Ryu, Lee, New J. Phys. 27, 053001 (2025) (numerical, d = 4 and 16) |
| **27B (iii)** best discrimination in the Kullback-Leibler sense | **FALSE for every d >= 4**: explicit orthonormal-basis strategies on Phi_d have statistical strength >= 0.0703204 bits > 0.0687803 >= S(DKZ_d) (all three van Dam-Grunwald-Gill strengths) | `kl-divergence/THEOREM.md`; independent verification `kl-divergence/INDEPENDENT_VERIFICATION.md` | d = 4 first by Y. Zhang (Zenodo, 2026, doi:10.5281/zenodo.23022433); every d >= 4: this work |

**Summary.** Every clause of Problem 27 as posed is now settled: 27A false (2010); 27B(i) true for every d;
27B(ii) true for the CGLMP violation and false (d >= 4) for Gill's literal reading; 27B(iii) false for every d >= 4.

## B. Precise variants

| Variant | Status |
|---|---|
| 27B(ii) with white noise on the state, CGLMP witness, projective measurements whose outcomes have unequal ranks (the noise is then the product of the marginals, not uniform) | OPEN; no counterexample in rank-pattern searches for d = 3..6 (exhaustive for d = 3 with local dimension <= 9 and d = 4 with local dimension <= 8; largest value 1.98569 < 2) |
| 27B(iii) at d = 3 | DKZ_3 is a strict local maximiser of the strength (PROVED, independently checked); global optimality NUMERICAL |

## C. Strengthenings (not asked by the problem)

| Strengthening | Status |
|---|---|
| 27B(i) for arbitrary POVMs on maximally entangled states | OPEN in general (no POVM advantage found numerically) |
| Noise resistance against all Bell inequalities with white noise on the state (every outcome used) | NUMERICAL: DKZ optimal in all global searches for d <= 8; d = 3 proved; OPEN in general |
| Maximum of CGLMP over all states (Tsirelson bound) equals 2(lambda_max(K_d) - 1)/(d - 1), K_d = [sec(pi(k-l)/2d)] | exact for d <= 8 (d = 3, 4 Ioannou-Rosset; d = 5..8 our earlier certificates); OPEN for d >= 9 |

## Labels used in the documents of this folder
A1 = 27A; A2 = 27B(i); A3a = 27B(ii), CGLMP reading; A3b = 27B(ii), Gill's literal reading; A4 = 27B(iii);
B1 = 27B(ii) with white noise on the state, CGLMP witness, unequal ranks; C1 = POVM strengthening of 27B(i);
C2 = noise resistance against all Bell inequalities with white noise on the state; C3 = the KL clause at d = 3;
C4 = the all-state Tsirelson bound. (In the verifier output, items C1-C12 and S1-S4 are check numbers, not these labels.)
