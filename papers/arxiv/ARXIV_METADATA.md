# arXiv submission metadata

## Title
The power of CGLMP inequalities: completing the resolution of IQOQI Vienna Open Quantum Problem 27

## Authors
Ansh Mishra, Aryan Senthilkumar

(Affiliations appear in the PDF only: Independent researcher, Cumming, GA, USA; Independent researcher, Johns Creek, GA, USA.
Corresponding author: Ansh Mishra, ansh.mishra2025@gmail.com.)

## Abstract (plain text, 1883 characters; arXiv limit 1920)

Open Quantum Problem 27 of IQOQI Vienna, "The power of CGLMP inequalities", asks (A) whether every nontrivial facet of the local polytope with two settings and $d$ outcomes per party is of CGLMP type, and (B) to show that the Fourier-type measurements of Durt, Kaszlikowski and Żukowski (DKZ) are necessarily optimal for the CGLMP inequality on a maximally entangled state, that they realize the highest resistance of the violation to noise, and that they give the best Kullback-Leibler discrimination against local realism. Part A was answered negatively by Bancal, Gisin and Pironio in 2010. We settle every clause of Part B as posed. (i) For every $d$, every local dimension and all projective measurements on maximally entangled states, the CGLMP value is at most the DKZ value, and DKZ is the only maximizer up to local unitaries and an inert ancilla. The proof combines an exact reduction to a clock model, a new strip inequality for a projection and a Hermitian matrix, obtained from a two-variable Bessis-Moussa-Villani positivity theorem with an explicit density, and a cone condition on Clausen kernels certified in interval arithmetic for every $d$; it is formalised in Lean 4, completely for $d \le 20$ and, for $d \ge 21$, up to the certified cone condition. (ii) The noise clause holds for every $d$ for the violation of the CGLMP inequality, with DKZ the unique optimum; in Gill's literal reading (uniformly random outcomes as noise, violation of any Bell inequality) it fails for every $d \ge 4$ on the maximally entangled state of two $d$-level systems, by projective measurements of coarse-grained CHSH type whose critical visibility we compute exactly. (iii) The Kullback-Leibler clause fails for every $d \ge 4$: explicit orthonormal-basis measurements reach a statistical strength of at least 0.0703 bits, DKZ at most 0.0688 bits. Open strengthenings are listed.

## Categories
- Primary: **quant-ph**
- Cross-lists: **math-ph**, **math.FA**

Justification. The question and its answer concern Bell nonlocality and optimal quantum measurements (quant-ph); rigorous
results on Bell inequalities with complete proofs fit math-ph. The new mathematics of the paper is analytic: a strip
inequality for a projection and a Hermitian matrix with an exact defect formula, a two-variable positivity theorem of
Bessis-Moussa-Villani (Stahl) type with an explicit density for matrix pencils, and a noncommutative continuum theorem for
conjugate functions (periodic Hilbert transforms) of operator-valued step fields. These are matrix/operator inequalities
and Laplace- and Hilbert-transform positivity results (MSC 47A63, 15A42, 44A10, 42A50), which is math.FA. math.OA
(C*- and von Neumann algebras) is less apt: no operator-algebraic structure is used beyond finite matrices, a normalised
trace and a tracial moment relaxation.

## Comments
22 pages, 1 figure, 4 tables; code, certificates, independent verifications and a Lean 4 formalisation: https://github.com/anshM123/anshM123-IQOQI-Vienna-Open-Problem-27

## Optional fields
- MSC classes: 81P40 (Primary); 15A42, 47A63, 42A50, 44A10, 65G40 (Secondary)
- Report number / journal reference / DOI: none
- License: authors' choice (the code and data repository is under the MIT license)

## Files to upload
`arxiv_source.zip` (contains `main.tex` and `figures/fig2.pdf` only). Single LaTeX file with an inline
`thebibliography` (no BibTeX run needed); intended for arXiv's default pdflatex.
