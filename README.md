<!-- solve-problem:cb220c97-6126-486b-90c3-b3e8169ecaa2 -->
# Counting SETH

A [Tangle Solve problem](https://solve.tangle.tools/problems/cb220c97-6126-486b-90c3-b3e8169ecaa2).

## What is the problem?

**#SETH (Counting Strong Exponential Time Hypothesis).** Let #SAT denote the problem: given a CNF formula F with n variables and m = poly(n) clauses, output the *number* |F⁻¹(1)| of satisfying assignments. The best known algorithms run in O(2ⁿ · poly(n)) time (trivially by summation; also via sharp-SAT solvers). The open question:

> Is there an algorithm for #SAT on sparse CNF formulas running in time O(2^{(1−ε)n} · poly(m)) for some ε > 0? #SETH asserts **no**: for every ε > 0 there is a k such that #SAT on k-CNF formulas with n variables and O(n) clauses requires 2^{(1−ε)n} time.

Formal setting: worst-case Turing-machine time, input formulas with unbounded or bounded clause width k and linearly many clauses (sparsity is essential — with exponentially many clauses one can force hardness trivially). Two subtleties: (1) outputs are integers of up to n bits, so the model must at least allow near-linear output size; (2) the natural reduction preserves assignment counts *exactly*, so decision-SETH (about the existence of an assignment) does not obviously transfer — a decision algorithm can be faster than any counting algorithm. Ambiguity note: some formulations state #SETH for k-CNF as k grows; others for general sparse CNF; these are equivalent up to standard encodings (verify).

## Why does it matter?

#SETH is the standard base hypothesis for conditional lower bounds on *exact counting*: Dell–Grochow–Wollan (2014) showed that #SETH (or weaker sparsification-based counting lemmas) yields tight 2ⁿ lower bounds for the permanent and for the Tutte polynomial at most fixed points, and it underpins lower bounds for counting matchings, reliability polynomials, and partition-function evaluation. A refutation (a 2^{(1−ε)n} #SAT algorithm) would collapse this entire lower-bound edifice and likely yield faster exact algorithms for counting in AI inference, network reliability, and statistical mechanics.

## What's already known?

- Decision SETH (Impagliazzo–Paturi–Zane 2003) gives 2^{(1−ε)n} lower bounds for sparse k-SAT *decision*; the sparsification lemma reduces to O(n) clauses.
- #SETH was formulated and systematically used by Dell, Grochow, and Wollan (2014), who proved that the permanent and the Tutte polynomial require 2^{(1−o(1))n} time even on bounded-degree graphs under #SETH.
- Known: #SETH is *not* known to be implied by decision SETH; a fast decision algorithm could coexist with #SETH. Conversely, refuting #SETH's sparsified form may not refute SETH.
- Known upper bound: O(1.985·2ⁿ)… in fact nothing beating 2^{(1−ε)n} is known for exact #SAT even for 3-CNF; the barrier is that algebraic/interpolation techniques (e.g., from polynomial-time approximations) do not preserve exact counts.

## What would count as solving it?

Either direction:
1. **Refutation:** an algorithm computing #SAT for k-CNF with n variables and cn clauses in 2^{(1−ε)n} poly(m) time for some absolute ε > 0 (any fixed k suffices if formulated per-k).
2. **Confirmation:** a proof, in any accepted foundation (e.g., via relativization-breaking techniques, or in a proof system), that no such algorithm exists — currently out of reach, so intermediate goals are also valued: e.g., proving #SETH from weaker/more believable hypotheses, oracle separations, or showing decision SETH ⟹ / ⟸ ⟹ #SETH (either direction would be major).

## How to start

1. Read Impagliazzo–Paturi–Zane (2003) for the sparsification lemma — check whether its counting-preservation fails (it does not preserve counts; this is exactly why #SETH is a separate hypothesis; understand where).
2. Read Dell–Grochow–Wollan (2014) Sections 1–3 to see how #SETH reductions work and what "matching lower bounds" means operationally.
3. Try small cases: exact #3-SAT in 2^{0.99n}. Attempt algebraic approaches — convert #SAT to evaluating a polynomial and use fast evaluation; the obstacle is that interpolation over 2ⁿ monomials is itself 2ⁿ.
4. Investigate the logical relationship: does a 2^{(1−ε)n} #SAT algorithm imply anything for decision SAT via isolation/hash-based reductions? This is the most tractable publishable subproblem.

## Key references

- R. Impagliazzo, R. Paturi, F. Zane, "Which problems have strongly exponential complexity?" *JCSS* 63(4):512–530, 2001. Introduces SETH and the sparsification lemma; the decision-side foundation. https://doi.org/10.1006/jcss.2001.1774
- H. Dell, J. Grochow, T. Wollan, "Computing the partition function of the Tutte polynomial," and the associated work cited as *Exponential Time Complexity of the Permanent and the Tutte Polynomial* (2014). Formalizes #SETH and proves 2^{(1−o(1))n} conditional lower bounds for the permanent and Tutte polynomial. (Census-cited; verify exact venue: appears as Dell–Grochow–Wollan, "Computing the partition function of the Tutte polynomial," https://arxiv.org/abs/1208.2604.)

## Warnings

- Do not conflate SETH and #SETH: the sparsification lemma does not preserve the number of solutions, so decision hardness does not transfer.
- Sparsity of the input (O(n) clauses) is essential; without it #SETH is false via padding/clause-count arguments.
- Exact counts are needed: FPRAS / approximation results for #SAT-like problems are irrelevant unless they give exactness.
- The census record cites Dell et al. 2014 with a title that may be imprecise; verify the citation before relying on theorem numbering.

---
*`ALGO-000075` · unverified*

## Acceptance guidance

Either direction:
1. **Refutation:** an algorithm computing #SAT for k-CNF with n variables and cn clauses in 2^{(1−ε)n} poly(m) time for some absolute ε > 0 (any fixed k suffices if formulated per-k).
2. **Confirmation:** a proof, in any accepted foundation (e.g., via relativization-breaking techniques, or in a proof system), that no such algorithm exists — currently out of reach, so intermediate goals are also valued: e.g., proving #SETH from weaker/more believable hypotheses, oracle separations, or showing decision SETH ⟹ / ⟸ ⟹ #SETH (either direction would be major).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/cb220c97-6126-486b-90c3-b3e8169ecaa2?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000075.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000075)
