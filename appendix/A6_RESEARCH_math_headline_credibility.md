<!-- Generated copy of research_notes/OpenAI math manuscript release/headline_results_credibility.md. Do not edit here; edit research_notes/OpenAI math manuscript release/headline_results_credibility.md. -->

> **Read before quoting.** Raw sweep, 7 Oct 2026; all expert reactions about one day old. The report `T13_OPENAI_MATH_RELEASE_REPORT.md` wins on conflicts.

# Credibility of the headline results in OpenAI's 6 Oct 2026 math release (as of 7 Oct 2026)

Tags: [V] = I read the fetched source (for the GitHub repo, I downloaded and read the raw files, including the Lean statements). [S] = search snippet or a secondary aggregator summary only. [M] = recalled from memory, not checked this session.

Overall caveat: the release is about 24 hours old. No named expert has published a line-by-line check of any headline result. Reactions so far are about **process** (pace, peer review, transparency, credit). They are not technical verdicts.

Repo facts used throughout:
- The repository `openai/math` (Apache-2.0) holds 722 manuscripts in 372 families. The model was "posed approximately 4,000 problems". The average is "three hours of ChatGPT Pro thinking compute" per result. Quoted disclaimers: "Some of the unformalized results could have issues" and "results at different stages of verification". [V] — [README](https://raw.githubusercontent.com/openai/math/main/README.md)
- Two efforts did not follow the fixed procedure: "work on a zero-free region for the Riemann zeta function and proof of the Hodge Conjecture for CM abelian varieties". The Re(s) > 11/12 zeta writeup "was human edited for readability". [V] — [README](https://raw.githubusercontent.com/openai/math/main/README.md)
- In the manuscript map, 235 of 372 families link to a Lean scope page. [V] — I counted links in [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md). Press reports say 162 manuscripts have a fully formalized main result and 73 have partial coverage. [S] — [kingy.ai](https://kingy.ai/blog/openai-math-722-manuscripts-results-proofs-compute-costs/), [cellcog](https://cellcog.ai/blog/openai-math-results/)

## (a) The zero-free half-plane for Dirichlet L-functions ("quasi-Riemann hypothesis", family 003)

### Takeaway
The claim is the strong reading, not a weaker variant. It is unconditional: every Dirichlet L-function, including zeta, has no zeros with Re(s) > 7/8, uniformly over every modulus and character. This is a genuine quasi-Riemann hypothesis. If correct, it is the biggest result in analytic number theory in over a century. The Lean statement is short and uses Mathlib's own definition of the L-function, so the risk that the formal statement says something different from the claim is unusually low. The remaining questions are whether the formal check is sound, and independent review by humans.

### Cited Findings
- The manuscript-map entry reads: "Proves that every Dirichlet L-function, including ζ(s), is zero-free in Re s > 7/8, resolving the quasi-Riemann hypothesis. The same half-plane is zero-free for every finite-order Hecke L-function over Q(sqrt(-3)). A companion gives a different proof of the zero-free half-plane Re s > 11/12." [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- The Lean scope page says theta = 7/8 holds "for the Riemann zeta function and every Dirichlet L-function, uniformly over all positive moduli and all characters". It excludes only the principal-character pole at s = 1. A separate formalized paper ("Uniform exclusion of Landau–Siegel zeros") proves 1 - beta >= c/log q with an unspecified constant c. [V] — [lean/docs/003.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/003.md)
- The exact Lean statement is `theorem LFunction_ne_zero_of_seven_eighths_lt_re {q : ℕ} [NeZero q] (χ : DirichletCharacter ℂ q) {s : ℂ} (hs : (7/8 : ℝ) < s.re) (hpole : ¬ (χ = 1 ∧ s = 1)) : DirichletCharacter.LFunction χ s ≠ 0`. It has no hypotheses beyond these, and the permitted axioms are limited to propext, Quot.sound and Classical.choice. [V] — [Nonvanishing.lean](https://raw.githubusercontent.com/openai/math/main/lean/OAI/NumberTheory/DirichletL/Nonvanishing.lean), [DirichletSevenEighths.json](https://raw.githubusercontent.com/openai/math/main/lean/ComparatorChallenges/DirichletSevenEighths.json)
- The comparator config sets `"enable_nanoda": false`. Nanoda is an independent second Lean kernel checker, so it was not turned on for this check. [V] — same JSON. (What this implies is my inference.)
- A community member, "davegoldblatt", rebuilt the quasi-Riemann Lean proof: "All 2,924 modules in the proof compiled with no errors and no warnings." He cautioned that this "checks the Lean proof, not the paper" and was "one run on one machine". [S, via WebFetch summary of the forum page] — [OpenAI Developer Community](https://community.openai.com/t/first-look-at-mathematics-manuscripts-from-an-internal-frontier-model-at-openai/1403886)
- Hacker News commenters: user "JoshuaZ", who describes himself as a number theorist, called the result Fields-Medal level. User "gavagai691", who describes himself as an analytic number theorist, said colleagues had considered ruling out Siegel zeros "plausible but unlikely in our lifetimes". Both are anonymous and I could not see the original thread. [S] — [explainx.ai summary](https://explainx.ai/blog/openai-math-results-that-matter-expert-reactions-2026)
- One aggregator, which I could not confirm against a primary source, says the Riemann-zeta work was the only part to undergo "extremely rigorous human review". [S] — [BigGo Finance](https://finance.biggo.com/news/1d522643-5fd9-4ac5-ae86-e4a5b99edfe2)
- Background [M]: the best unconditional zero-free regions known are thin regions that shrink toward Re(s) = 1, from de la Vallée Poussin (1896) and Vinogradov–Korobov (1958). For L-functions there is also the possible exceptional "Siegel zero". No fixed half-plane Re(s) > theta with theta < 1 was known even for zeta alone. For zeta, a 7/8 half-plane would give a prime-number-theorem error term of about x^(7/8 + epsilon). Uniformity over all Dirichlet characters would rule out Siegel zeros.

### Inferences
- The statement is clean. Mathlib's `DirichletCharacter.LFunction` is a community-vetted definition (the analytic continuation). The hypotheses are minimal. So this is the headline result least exposed to the risk that the formal statement does not match the claim. If the build is sound (no kernel bug, no smuggled axiom), the theorem is true as stated.
- One oddity to flag: the separate Siegel-zero paper proves a much weaker c/log q bound, even though the 7/8 half-plane already excludes all real zeros in (7/8, 1). It may be an earlier, independent attempt. It is not a contradiction, but it is worth asking about.
- The zeta part had more human involvement than the fixed automated procedure. This is a disclosed exception, so the zeta writeup should not be counted as a purely automated result.

### Gaps
- No named analytic number theorist (for example Maynard, Soundararajan or Iwaniec) has commented publicly in a form I could find.
- I did not read the 7/8 paper itself, so I cannot describe the method or judge whether the human-readable proof is checkable.
- I found no independent confirmation that the comparator check passed beyond the single forum report.

## (b) "The Mahler conjectures" (family 087)

### Takeaway
"Mahler conjectures" here means Mahler's **volume-product conjecture** in convex geometry, in both the symmetric and the general (nonsymmetric) form, in every dimension. It is not Mahler measure or Lehmer's problem. Both inequalities and their equality cases are stated as Lean-formalized. The functional versions are not formalized.

### Cited Findings
- The manuscript map says the release "Resolves the symmetric and nonsymmetric geometric Mahler conjectures in every dimension, with Hanner polytopes and simplices as the respective volume-product minimizers and all equality cases classified. The corresponding sharp functional Mahler inequalities also hold." It also claims that the symplectic Gromov width of K x K° is 4. [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- Lean scope: the symmetric bound |K||K°| >= 4^n/n! is formalized for all n >= 1, with equality exactly for linear images of Hanner bodies. The general bound inf over z in int K of |K||(K-z)°| >= (n+1)^(n+1)/(n!)^2 is formalized, with equality exactly for simplices. Quote: "The nonsymmetric Mahler conjecture and the functional inequalities are not included" in the first selected statement. The general case is formalized as a separate statement. [V] — [lean/docs/087.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/087.md)
- The Lean statement uses compact, convex, origin-symmetric sets with nonempty interior and Mathlib's `volume`. The polar body is defined locally as `coordinatePolar K = {p | ∀ v ∈ K, ∑ i, p i * v i ≤ 1}`, which is the standard polar. [V] — [MahlerConjecture.lean](https://raw.githubusercontent.com/openai/math/main/lean/ComparatorChallenges/MahlerConjecture.lean)
- Background [M]: Mahler posed the conjecture in 1939. Before this release it was proved only in dimension 2 (Mahler) and, for symmetric bodies, in dimension 3 (Iriyeva–Shibata 2020). The known general bounds were only within a factor c^n (Bourgain–Milman). The conjecture asks for the minimum volume of K times the volume of its "dual" body. It is a basic question in geometry of numbers and convex analysis.

### Inferences
- The symmetric statement is short and transparent. The one local definition (the polar) is correct by inspection. So the risk of a mismatch between the formal statement and the claim is low, as for (a).
- An all-dimension proof would be a landmark result in convex geometry.

### Gaps
- I found no reaction from convex geometers (for example Klartag, Milman or Artstein-Avidan).
- I did not read the GeneralMahler.lean statement directly.

## (c) Kaplansky's zero-divisor conjecture (family 196), plus direct-finiteness (family 197)

### Takeaway
Two separate families exist. **Family 196** disproves the zero-divisor conjecture itself. It gives a finitely presented torsion-free group G with nonzero alpha, beta in F_2[G] such that alpha*beta = 0, and the Lean statement is clean. **Family 197** is the one OpenAI highlights in its README. It disproves Kaplansky's direct-finiteness conjecture and claims a torsion-free, non-sofic group. However, the Lean-formalized direct-finiteness construction uses a group **with torsion**, and non-soficity is outside the formal statement. That is a real gap between the headline claim and what Lean checked. Aggregators also confuse the two families.

### Cited Findings
- The README's highlighted family is "197: Kaplansky's direct-finiteness conjecture in characteristic two". [V] — [README](https://raw.githubusercontent.com/openai/math/main/README.md)
- Family 196: "Constructs a finitely presented torsion-free group G whose group algebra F_2[G] has nonzero zero divisors, disproving Kaplansky's zero-divisor conjecture. The group has a finite two-dimensional classifying space." The paper is "A Torsion-Free Group Algebra with Zero Divisors" (dated 23 Sep 2026). [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md), [lean/docs/196.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/196.md)
- The Lean statement for 196: there exists a group G that is `Group.IsFinitelyPresented`, satisfies `TorsionFree` (defined locally as g^n = 1 with n > 0 implies g = 1), has a finite 2-dimensional K(G,1), and has α β : MonoidAlgebra (ZMod 2) G with α ≠ 0, β ≠ 0 and α * β = 0. [V] — [TorsionFreeZeroDivisors.lean](https://raw.githubusercontent.com/openai/math/main/lean/ComparatorChallenges/TorsionFreeZeroDivisors.lean)
- Family 197 claims "a finitely presented torsion-free nonsofic group whose group algebra over F_2 is not directly finite". It also claims to refute Gottschalk's surjunctivity conjecture and the Determinant Conjecture. [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- 197's Lean scope page says the detailed formalized construction "gives a finitely presented group with an element of odd prime order". Quote: "The further conclusion that the group is nonsofic is outside these statements." The odd-characteristic version also uses "a finitely generated group G with torsion". [V] — [lean/docs/197.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/197.md)
- One aggregator flags a "scope mismatch regarding claimed torsion-free properties". [S] — [kingy.ai](https://kingy.ai/blog/openai-math-722-manuscripts-results-proofs-compute-costs/)
- One aggregator lists "A counterexample to Kaplansky's zero-divisor conjecture" as Lean-checked. [S] — [cellcog](https://cellcog.ai/blog/openai-math-results/)
- The same release also claims a disproof of the Kadison–Kaplansky conjecture (via the Baum–Connes family 285) and a proof of Kaplansky's idempotent conjecture in characteristic zero (family 207). [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- Background [M]: Gardam (2021) disproved the **unit** conjecture over F_2 for the Hantzsche–Wendt (Promislow) group, using a SAT-solver search. The unit conjecture implies the zero-divisor conjecture, so a zero-divisor counterexample is strictly stronger and more surprising. The zero-divisor conjecture was known to hold for broad classes, such as orderable and elementary amenable torsion-free groups. Direct-finiteness holds for all sofic groups (Elek–Szabó), so any counterexample is automatically non-sofic. This ties into OpenAI's August "Astra" non-sofic group result. [S for the August release: [The Next Web](https://thenextweb.com/news/openai-astra-model-ten-math-proofs-non-sofic-groups)]
- An ERC project (Gardam's, as I recall [M]) was already aiming to build zero-divisor counterexamples with SAT solvers. [S] — [CORDIS 101076148](https://cordis.europa.eu/project/id/101076148)

### Inferences
- Family 196 has a crisp, low-risk formal statement. If the Lean build is sound, the zero-divisor conjecture is false over F_2. This would be a major result in group-ring theory and a natural next step after Gardam.
- For family 197, direct-finiteness can be disproved with groups that have torsion, so the formal result does refute Kaplansky's direct-finiteness conjecture. But "torsion-free" and "non-sofic" are not certified by Lean. Non-soficity actually follows from any direct-finiteness failure (Elek–Szabó), but "first torsion-free example" does not. Wherever the headline says "torsion-free nonsofic", that part currently rests on the unformalized paper.

### Gaps
- I found no reaction from Gardam, Thom, Kun or other group-ring specialists.
- I did not inspect the concrete group presentation (`ConcreteGroup.G`), so I cannot say how large or explicit the counterexample is.

## (d) Isomorphism of the free group factors (family 287)

### Takeaway
The claim is **isomorphism**: L(F_2) ≅ L(F_3). Through Dykema–Rădulescu interpolation it follows that all interpolated free group factors, including L(F_infinity), are isomorphic, and their common fundamental group is all of R_{>0}. This is the opposite of what most operator algebraists expected. A Lean scope page now exists, contradicting early press reports that it was unformalized. But the formal statement rests on about 200 lines of hand-built definitions (the group von Neumann algebra, corners, amplifications, the interpolation parameter) rather than on Mathlib. So, of the headline formalizations, it has the highest risk that the formal statement does not say what the claim says.

### Cited Findings
- The manuscript map says: "Resolves the free group factor isomorphism problem: L(F_2) ≅ L(F_3), and hence all interpolated free group factors, including L(F_∞), are isomorphic. Their common factor has fundamental group R_{>0}." It links to a Lean page. [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- Lean scope: "interpolated free group factors with any parameters r,s>1, including the infinite parameter, are normally trace-preservingly isomorphic". The fundamental-group conclusion "is a further consequence rather than a separate selected statement". [V] — [lean/docs/287.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/287.md)
- The comparator file is 225 lines. It defines `groupVonNeumann G` as the double commutant (centralizer of the centralizer) of left translations on ℓ²(G), the canonical trace as ⟨T δ_1⟩(1), a hand-built ultraweak topology, corners, a "stabilization" over ℕ × G, `interpolationScale r = 1/sqrt(r-1)`, and the final `theorem allInterpolatedIsomorphic (r s : ℝ≥0∞) (hr : 1<r) (hs : 1<s) : Nonempty (NormalTracialEquiv ...)`. Integer r uses the group algebra of `FreeGroup (Fin n)` directly. [V] — [InterpolatedFactors.lean](https://raw.githubusercontent.com/openai/math/main/lean/ComparatorChallenges/InterpolatedFactors.lean)
- Some early reports said the result had no Lean proof yet. [S] — [cellcog](https://cellcog.ai/blog/openai-math-results/); the same claim is attributed to an aggregator via search, [interestingengineering/unite](https://interestingengineering.com/ai-robotics/openai-largest-math-release-lean-proofs). This conflicts with the Lean doc and comparator file present in the repo on 7 Oct [V]. Possible reasons: the repo was updated after release, or the aggregators were wrong.
- The reasoning summary reportedly describes small trace-preserving perturbations of a generating tuple, so that an extra generator is recovered in the limit, with a separate L²-density argument for generation. [S] — [kingy.ai summary via search](https://kingy.ai/blog/openai-math-722-manuscripts-results-proofs-compute-costs/)
- Background [M]: Murray–von Neumann-era question (Kadison's list). Voiculescu's free probability and Dykema/Rădulescu (1994) proved the dichotomy: either all L(F_r), 1 < r <= infinity, are isomorphic, or none are. Most experts expected non-isomorphism, because invariants like free entropy dimension were expected to distinguish them.

### Inferences
- I checked by hand [M + own reasoning] that the local definitions are standard. The double commutant is the von Neumann algebra by the bicommutant theorem. The trace formula is correct. The scale 1/sqrt(r-1) matches the compression formula L(F_2)_t ≅ L(F_{1+1/t²}). Note that the integer cases r = 2 and r = 3 use the plain group von Neumann algebra, so L(F_2) ≅ L(F_3) is stated directly, not only through interpolation. So a quick reading finds no obvious mis-formalization. But a hand-built topology and a hand-built `NormalTracialEquiv` structure are exactly where a subtly weak or wrong definition could hide, for example an "isomorphism" notion missing the normality or *-preserving conditions. An operator-algebra expert should audit the 225-line file.
- An affirmative answer is the "surprising" direction. It would also give the first known II_1 factor of this type whose fundamental group is all of R_{>0} via free groups. Expect intense scrutiny.

### Gaps
- I found no reaction from operator algebraists (for example Popa, Ioana, Vaes, Jung or Shlyakhtenko).
- I did not read the `NormalTracialEquiv` structure definition (lines ~155–170) in full.

## Other notable headline claims

### Takeaway
The catalogue claims a run of famous problems. Several have Lean pages and several do not. The Hodge/CM result and Kakeya have none. Formal statements are sometimes narrower than the headline claims.

### Cited Findings
- **Family 017**: the irrationality exponent of pi is exactly 2, which also gives convergence of the Flint–Hills series. Lean scope covers the exponent and excludes the Flint–Hills consequence. [V] — [lean/docs/017.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/017.md)
- **Family 102**: "Proves Khot's Unique Games Conjecture", and separately NP-hardness of Max-Cut beyond Goemans–Williamson without assuming UGC. Lean formalizes a deterministic polynomial-time reduction from 3SAT to unique games with gap (1-epsilon, delta). [V] — [lean/docs/102.md](https://raw.githubusercontent.com/openai/math/main/lean/docs/102.md), [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- **Family 032**: the rational Hodge conjecture for all CM abelian varieties, giving the Tate conjecture for abelian varieties over finite fields. **Family 074**: Kakeya maximal in R^3 and the dimension conjecture in R^4. **Family 004**: Hilbert's tenth problem over Q has a negative answer. These three families have no Lean link in the map. [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md)
- **Further claims**, each with a Lean link [V] — [CONTENTS.md](https://raw.githubusercontent.com/openai/math/main/CONTENTS.md):
  - Family 143: uniform boundedness in Hilbert's 16th problem
  - Family 288: Kadison's similarity conjecture
  - Family 325: the complete Crouzeix conjecture
  - Family 007: the two-point Chowla conjecture
  - Family 362: global smoothness for relativistic Vlasov–Maxwell
- Lean statements narrower than headlines: the Family 130 Fourier result is "subsequential" in Lean. The integer-multiplication result has no Lean proof. 227 of 405 comparator challenge files are missing from `formalization.yaml`. [S] — [explainx.ai](https://explainx.ai/blog/openai-math-results-that-matter-expert-reactions-2026)

### Inferences
- The release claims resolutions of many famous open problems at once (UGC, Hilbert 10 over Q, Hodge for CM, Kadison similarity, Hilbert 16 uniform bound). Base rates make it very unlikely that all of them survive, especially the unformalized ones. The README itself concedes this.

### Gaps
- No family-level human audit exists yet. An arXiv paper titled "A Human Audit of OpenAI's AI-Generated Mathematical Proofs" (2608.14673) has an August 2026 number, so it presumably concerns the earlier August "Astra" release. I did not read it. [S] — [arXiv](https://arxiv.org/pdf/2608.14673)

## Named-mathematician reactions so far

### Takeaway
All on-record reactions concern **process** (pace, norms, credit, secrecy), not whether specific proofs are correct. No named expert has endorsed or refuted any headline result as of 7 Oct.

### Cited Findings
- **Terence Tao** criticized the "insane" pace of AI-lab results. [S] — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/). In a Mastodon thread on 6 Oct he reportedly described a "Math 1.0" mindset of pointing AI at open problems, with solutions "harvested in an unsustainable fashion". He proposed that labs compete to announce new insights rather than solutions. [S] — [explainx.ai](https://explainx.ai/blog/openai-math-results-that-matter-expert-reactions-2026), [Mathstodon search result](https://mathstodon.xyz/@tao/117221032761877425). I could not load the post text. Earlier, on 21 Sep, he blogged that his group was "advising OpenAI on how to coordinate the release". [S] — [tech-insider](https://tech-insider.org/openai-722-math-claims-mathematician-scrutiny-2026/)
- **Kevin Buzzard** posted on Xena, dated 1 Oct, before the release ("To grieve, or not to grieve?"). He urged OpenAI to "simply dump" its theorems, called secrecy "akin to censorship", and wrote "you cannot fool Lean". [S] — [unite.ai/interestingengineering snippets](https://www.unite.ai/openai-releases-722-math-manuscripts-from-an-unreleased-ai-model/). I could not locate the post itself.
- **Andrew Sutherland** (MIT): "Until and unless they release the model and people can replicate their results, I think you should treat any claims about one-shotting problems with a single agent as unverified." [V] — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- **Daniel Litt** (Toronto): "If we want to know the answers to these math questions, I see no reason why we should ask the company to keep them secret from us." [V] — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- **Bryna Kra** (Northwestern), co-author of the "Leiden Declaration": "Clearly, those opinions were ignored." [S] — [BigGo](https://finance.biggo.com/news/1d522643-5fd9-4ac5-ae86-e4a5b99edfe2)
- **Tristan Buckmaster** (NYU) alleged that OpenAI scooped a Navier–Stokes collaboration. [S] — [BigGo](https://finance.biggo.com/news/1d522643-5fd9-4ac5-ae86-e4a5b99edfe2)
- **Gowers and Hairer** (IAS advisory group): "We do not endorse this practice and demand that they stop." [S] — [BigGo](https://finance.biggo.com/news/1d522643-5fd9-4ac5-ae86-e4a5b99edfe2). This is a single unconfirmed aggregator, so treat it with caution.
- **Nature's headline**: "OpenAI posts 700 maths preprints online: mathematicians are up in arms". The article itself is paywalled and I could not fetch it. [S] — [Nature](https://www.nature.com/articles/d41586-026-03196-8)
- **Scientific American**: it "will take mathematicians months to parse". [S] — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)

### Inferences
- The community is split on norms. Litt and Buzzard favor releasing everything, while Tao, Kra, Sutherland and the IAS group are critical of the process. Nobody yet disputes a specific theorem.

### Gaps
- I found nothing from Gowers personally (beyond the attributed group statement), Ellenberg, Riehl, Harris, Davis, Kalai, Aaronson (relevant to UGC), Quanta, MathOverflow, the Lean Zulip or r/math. Search did not surface these sources within the time available. That reflects my search coverage, not evidence that they are silent.

## Errors, rediscoveries and overclaiming; comparison with the Oct 2025 Erdős episode

### Takeaway
No concrete error or rediscovery has been reported for any headline result yet. Visible risks are: gaps between headline claims and what Lean checked (197 torsion-free, 130 Fourier, 087 functional forms), catalogue lag, and undisclosed human input. The 2025 Erdős episode was a rediscovery problem. That failure mode is much less likely for these headline problems, because they are famous and their open status is well documented.

### Cited Findings
- No documented errors or overlap with prior literature yet. [S] — [tech-insider](https://tech-insider.org/openai-722-math-claims-mathematician-scrutiny-2026/), [kingy.ai](https://kingy.ai/blog/openai-math-722-manuscripts-results-proofs-compute-costs/)
- One reported overlap: the integer-multiplication claim builds on Harvey–van der Hoeven's n log n. [S] — [explainx.ai](https://explainx.ai/blog/openai-math-results-that-matter-expert-reactions-2026)
- Oct 2025 Erdős episode [M]: OpenAI's Kevin Weil posted that GPT-5 had "found solutions to 10 (!) previously unsolved Erdős problems". Thomas Bloom, who runs erdosproblems.com, called it a "dramatic misrepresentation": "open" on his site meant only that he did not know of a solution, and GPT-5 had found existing literature. Demis Hassabis replied "this is embarrassing". The post was deleted. Not re-verified this session.

### Inferences
- These problems were open in the strong sense, so the risk is not rediscovery but correctness and fidelity of the formal statement.

### Gaps
- I did not search for "already known" findings on the roughly 700 non-headline manuscripts. Rediscoveries are more likely there.

## What Lean formalization actually guarantees

### Takeaway
A passing comparator check means this: the stated Lean theorem follows from Lean's kernel and the three standard axioms, with no `sorry` and no extra axioms. It does **not** guarantee that the formal statement matches the English claim, that the definitions are correct, that the result is new, or that the paper's human-readable proof is right. How much it is worth depends on how much of the statement sits in vetted Mathlib definitions versus bespoke local definitions.

### Cited Findings
- From the release: "Lean formalization means a computer has checked the formal statement… it does not by itself show that the formal statement says exactly what the paper says, or that the result is new." [S] — [cellcog](https://cellcog.ai/blog/openai-math-results/)
- The comparator framework works like this: a "challenge" file holds the statement with `sorry`, a "solution" module holds the proof, `permitted_axioms` lists the allowed axioms, and `enable_nanoda: false` means no second kernel. [V] — [DirichletSevenEighths.json](https://raw.githubusercontent.com/openai/math/main/lean/ComparatorChallenges/DirichletSevenEighths.json), [README](https://raw.githubusercontent.com/openai/math/main/README.md)
- Lean scope pages explicitly mark consequences that were not formalized (non-soficity in 197, fundamental group in 287, Flint–Hills in 017, functional Mahler in 087). [V] — the lean/docs pages linked above
- In my reading [V for the files], the headline statements rank by how much bespoke definition they rely on:
  - Lowest: Dirichlet 7/8 (pure Mathlib)
  - Next: zero-divisor (Mathlib plus a transparent TorsionFree and CW-complex K(G,1))
  - Next: Mahler (one local polar definition)
  - Highest: free group factors (about 200 lines of bespoke operator-algebra infrastructure)

### Inferences
- Remaining failure modes for the formalized headlines: (1) a definition that is subtly wrong or vacuous (most plausible for 287); (2) a Lean or Mathlib soundness bug, which is rare but possible, and the second-kernel check was not used; (3) a gap between the paper and the formal statement, so the readable proof may be wrong even where Lean is right. For unformalized headlines (Hodge/CM, Kakeya, Hilbert 10 over Q) there is no machine guarantee at all.

### Gaps
- I found no independent re-run of the comparator checks on 196, 087 or 287.
