<!-- Generated copy of research_notes/OpenAI math manuscript release/release_contents.md. Do not edit here; edit research_notes/OpenAI math manuscript release/release_contents.md. -->

> **Read before quoting.** Raw sweep, 7 Oct 2026. Where it differs from `T13_OPENAI_MATH_RELEASE_REPORT.md`, the report wins. Kaplansky: family 196 = zero-divisor (formalized, torsion-free); family 197 = direct-finiteness (formalized group has torsion). '162' counts papers, not results.

# OpenAI "Sharing AI progress in mathematics" (6 Oct 2026): release contents, process, verification, framing

Researched 2026-10-07. Tags: [V] = primary source or fetched page read in full this session; [S] = search-result snippet only; [M] = from memory. Repo facts marked [V-repo] come from a shallow clone of github.com/openai/math (single commit `adc7f12`, "Initial commit", 2026-10-06 14:58:50 -0700) and counts computed directly from its files.

Note on access: openai.com returned HTTP 403 to direct fetch; the blog text was read through a reader proxy (r.jina.ai), which returned what looks like the full post (about 2.6 KB, seven paragraphs). X/Twitter posts could not be fetched (blocked), so all executive tweets are [S] or second-hand.

## 1. What exactly was released: numbers, repo, structure, fields

### Takeaway
All five headline numbers check out against the repo itself: 722 manuscripts, 372 result families, 17 subject sections, 162 papers in the Lean formalization catalogue, Apache-2.0 license. One caveat: "17 fields" and "162 Lean" do not appear as stated numbers in the blog or README. They come from the overview's table of contents and from the `lean/formalization.yaml` catalogue (162 entries). The blog post itself gives none of these numbers except "10 summaries" and "three hours".

### Cited Findings
- [V] The blog post never says 722, 372, 17 or 162. It says OpenAI is "releasing a broad range of new mathematical results produced by an internal frontier model", published "in a GitHub repository, with protocols for paper revisions and citations", with "formalizations of many of the proofs in Lean". — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V-repo] The README says: "The current catalogue contains 722 manuscripts organized into 372 families. A family groups related papers, which may include a principal result, companion arguments, consequences, or alternative proofs. Each family is classified by mathematical discipline." — [openai/math README](https://github.com/openai/math)
- [V-repo] `preprints/` has exactly 722 subdirectories. Each holds a PDF, LaTeX source and a README with a BibTeX block (author `{OpenAI}`, `howpublished = {OpenAI Math Release preprint ...}`). — [openai/math preprints](https://github.com/openai/math/tree/main/preprints)
- [V-repo] License: `LICENSE` is the Apache License 2.0. `lean/formalization.yaml` also declares `license: "Apache-2.0"`. — [openai/math LICENSE](https://github.com/openai/math/blob/main/LICENSE)
- [V-repo] Top-level layout: `README.md`, `CONTENTS.md` (the "manuscript map": every family's summary plus each paper's abstract and PDF link, 9,169 lines), `overview.pdf`/`overview.tex` ("OpenAI Research Catalog", dated October 6, 2026, which says "entry numbers follow the catalog order and do not indicate a ranking"), `preprints/`, `reasoning_traces/` (10 PDFs), `lean/` (Lean 4 library, toolchain `leanprover/lean4:v4.34.1`), `LICENSE`. The working tree is about 3.1 GB and holds 132,851 files. — [openai/math](https://github.com/openai/math)
- [V-repo] Lean library scale: 121,734 `.lean` files and about 25.9 million lines under `lean/OAI/`. A word search found no file containing `sorry` (I did not build the library). The library builds on mathlib4, PrimeNumberTheoremAnd, and community libraries such as ClassFieldTheory, AINTLIB, strongpnt and rellich-kondrachov. — [lean/formalization.yaml](https://github.com/openai/math/blob/main/lean/formalization.yaml)
- [V-repo] Manuscript dates, from the directory-name suffixes, run from 10 Sep 2026 to 6 Oct 2026. Most fall on 23 Sep (177), 24 Sep (193), 25 Sep (90) and 5 Oct (112).
- [V-repo] The overview lists 17 subject sections. Families and manuscript links per field, counted from `overview.tex` (totals reconcile to 372 / 722):

| Field | Families | Manuscripts |
|---|---|---|
| Number theory | 31 | 58 |
| Algebraic and complex geometry | 36 | 89 |
| Real and complex analysis | 16 | 26 |
| Convex and metric geometry | 15 | 30 |
| Theoretical computer science | 40 | 73 |
| Dynamical systems and ergodic theory | 12 | 19 |
| Combinatorics | 37 | 50 |
| Algebra | 18 | 29 |
| Probability and statistical mechanics | 29 | 105 |
| Mathematical logic | 6 | 8 |
| Group theory | 14 | 22 |
| Mathematical physics | 25 | 59 |
| Operator algebras | 19 | 31 |
| Topology | 18 | 26 |
| Functional analysis | 11 | 19 |
| Differential geometry | 29 | 49 |
| Partial differential equations | 16 | 29 |
| **Total** | **372** | **722** |

- [V-repo] Lean coverage at three levels:
  - (a) `lean/formalization.yaml`, "Catalog of papers with a formalized main result", lists exactly **162** source papers. Its `status.scope` is "Partial progress.", `review.status` is "unchecked", and `automation.methods` is "agent".
  - (b) The same file's `status.main_results` lists 185 formalized declarations, each with a Comparator config.
  - (c) `CONTENTS.md` links a `[Lean]` scope page (`lean/docs/NNN.md`) for **235** of the 372 families, and there are 235 doc pages. `lean/ComparatorChallenges/` holds 405 JSON challenge configs.
  - So "162" is a count of papers with a formalized main result, not of families or results. — [lean/formalization.yaml](https://github.com/openai/math/blob/main/lean/formalization.yaml), [CONTENTS.md](https://github.com/openai/math/blob/main/CONTENTS.md)
- [V] Third-party counts agree: 235 families with a Lean page and 162 papers with a fully formalized main result. tech-insider attributes this to a FourWeekMBA analysis and gives the repo as openai/math under Apache-2.0. — [tech-insider](https://tech-insider.org/openai-722-math-manuscripts-unreleased-model-2026/)
- [V] Some press counts differ. Gizmodo's headline says "377" new results and cites the NYT; Scientific American, Quartz and The Decoder say 372. — [Gizmodo](https://gizmodo.com/openai-dumps-377-new-math-results-on-github-publishes-hand-wringing-blog-post-2000822613); [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- [V] Timing: Scientific American says the repository went public at 6 P.M. EDT on 6 Oct. That matches the commit time of 14:58 PDT. — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)

### Inferences
- "17 fields" is a fair reading of the overview's 17 sections. OpenAI did not state it as a headline number.
- "Lean formalizations for 162 main results" is slightly loose. The repo says 162 *papers* have a formalized main result, covering 185 main-result declarations. Separately, 235 families have some Lean scope page, and those pages often cover only selected statements, not the full paper (see section 3).

### Gaps
- I did not compile the Lean library or run Comparator, so "no `sorry`" is a text search only, not a check.
- I could not find a stated per-paper or per-family mapping of "fully formalized" against "partially formalized" other than the scope pages.

## 2. Model and process

### Takeaway
The model is unnamed and unreleased. OpenAI calls it an "internal frontier model" and links to the Navier–Stokes post, which describes it as "significantly more capable than GPT-6 Astra" and trained by large-scale RL since 28 Aug 2026. The README states the process: roughly 4,000 problems posed during model evaluation, an average of about three hours of "ChatGPT Pro thinking compute" per result, then aggregation into families and a significance filter. Two results were exceptions to the fixed procedure, and one write-up was human-edited. A spokesperson told press that almost every result came from a single prompt to a single agent, while some may have taken multiple attempts.

### Cited Findings
- [V] The blog says the results were "produced by an internal frontier model", with the phrase hyperlinked to the Navier–Stokes post. — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] The Navier–Stokes post (Sept 2026) says: "we used an internal model that is significantly more capable than GPT-6 Astra"; "Since August 28 we have been training a new internal model ... This model's training is ongoing"; "developed through large-scale reinforcement learning on top of a previously pretrained model." — [OpenAI, On the Navier–Stokes Millennium Prize Problem](https://openai.com/index/navier-stokes-solution/)
- [V-repo] The README says the results came from model evaluation: "As part of model development, we evaluate our models on open research problems. We expanded these evaluations after performance on our existing mathematical evaluations saturated. Some outputs build upon earlier results produced by the models." — [README](https://github.com/openai/math)
- [V-repo] The README describes the procedure: "The vast majority of results were obtained with the same procedure using an unreleased internal OpenAI model. On average, each result used three hours of ChatGPT Pro thinking compute with that model. Over the course of the evaluation, the model was posed approximately 4,000 problems. Aggregating the output into result families and manuscripts and requiring an appropriate level of significance led to the catalog outlined above." — [README](https://github.com/openai/math)
- [V-repo] It names the exceptions: "Exceptions to this fixed procedure include work on a zero-free region for the Riemann zeta function and proof of the Hodge Conjecture for CM abelian varieties. Additionally, the writeup for the Re(s) > 11/12 zero-free region for the Riemann zeta function was human edited for readability." — [README](https://github.com/openai/math)
- [V] The blog frames compute the same way: "The average result used the equivalent compute of roughly three hours of ChatGPT Pro thinking." It also promises "estimations of compute spent in terms of Pro usage on ChatGPT, and statistics about the number of attempted problems." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] An OpenAI spokesperson told SciAm the model "produced almost every one of the results in response to a single prompt handed to a single AI agent", and also that "some results might have taken multiple attempts." — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/). The Decoder repeats this: "Nearly every result came from a single prompt to a single AI agent ... though some took multiple attempts." — [The Decoder](https://the-decoder.com/openai-dumps-372-ai-generated-math-proofs-on-github-telling-the-academic-world-to-keep-up/)
- [V] Navier–Stokes, for contrast: about 10,000 concurrent agents, 88 hours, and 17 more hours of Lean formalization "via GPT-6 Astra". Across all problems attempted in that effort, agents sent 4.9 million messages and used about 300 billion output tokens. — [OpenAI Navier–Stokes post](https://openai.com/index/navier-stokes-solution/)
- [V] SciAm reports that OpenAI disclosed only *average* compute and no prompts, although the AGMAI recommendations ask for the model, the exact prompt and the compute behind each result. — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- [V-repo] Lean formalization was automated: `automation: methods: - method: agent` in `lean/formalization.yaml`. — [formalization.yaml](https://github.com/openai/math/blob/main/lean/formalization.yaml)
- [V-repo] Every manuscript and catalogue entry lists "OpenAI" as the sole author. No human authors are named. — [formalization.yaml](https://github.com/openai/math/blob/main/lean/formalization.yaml)

### Inferences
- How the roughly 4,000 problems were chosen is not described beyond "open research problems" in an evaluation that expanded after existing math evals saturated. The 722 were selected by aggregation plus "requiring an appropriate level of significance", with no stated criterion or judge.
- "Autonomous" is not OpenAI's word. The fixed procedure (one prompt, one agent) suggests minimal human steering for most results. Humans clearly intervened in at least the two named exceptions and the 11/12 write-up edit, and humans or agents did the aggregation and selection.
- "Three hours of ChatGPT Pro thinking" is a normalized compute unit, not wall-clock time or dollars. It is an average per *result* and is not reported per family.

### Gaps
- No model name, model card, parameter count or benchmarks (also noted by [orcarouter](https://www.orcarouter.ai/blog/openai-722-math-manuscripts-unreleased-model) [S]).
- The blog promises "statistics about the number of attempted problems". The only statistic I found in the repo is the "approximately 4,000" in the README. There is no success rate, per-field attempt count, or failure log.
- No list of the 4,000 problems or of the prompts.

## 3. How correctness was checked; caveats and disclaimers

### Takeaway
Verification rests on Lean plus the Comparator tool. OpenAI does not claim human peer review or per-result human checking, and the Lean catalogue marks its own review status as "unchecked". OpenAI's explicit caveats are short: results are at "different stages of verification", not all have Lean, "some of the unformalized results could have issues", and corrections will be versioned. The blog also concedes that citations and exposition need improving. Neither the blog nor the README contains a phrase like "not peer reviewed"; that framing comes from coverage. No error rate or known failure is disclosed.

### Cited Findings
- [V-repo] README: "This collection includes results at different stages of verification. Not all have accompanying Lean formalizations. We will continue to update this repository with Lean formalizations as we obtain them. Some of the unformalized results could have issues. We will endeavor to fix any such issues quickly. We are also exploring community-hosted repositories for these materials." — [README](https://github.com/openai/math)
- [V-repo] README on versioning: "We will preserve the public release history of this collection. Corrections and revisions will be recorded as new versions, with previously released versions remaining accessible." — [README](https://github.com/openai/math)
- [V-repo] Checking method: `lean/ComparatorChallenges/README.md` tells users to install `comparator`, `landrun` and `lean4export` and then run, for example, `lake env comparator ComparatorChallenges/QuasiRiemannHypothesis.json`. Challenge configs pin the theorem names and allow only the axioms `propext`, `Quot.sound` and `Classical.choice`. — [Comparator README](https://github.com/openai/math/blob/main/lean/ComparatorChallenges/README.md), [Comparator](https://github.com/leanprover/comparator)
- [V-repo] `formalization.yaml`: `status: scope: "Partial progress."` and `review: status: unchecked`. — [formalization.yaml](https://github.com/openai/math/blob/main/lean/formalization.yaml)
- [V-repo] The Lean scope pages often formalize only part of a paper. Examples: in family 087 "The nonsymmetric Mahler conjecture and the functional inequalities are not included" in the symmetric block. In 159 the quantitative Szemerédi-type bound "is outside this statement". In 017 the Flint–Hills consequence is outside. In 003 "The paper's later applications are not included". — [lean/docs](https://github.com/openai/math/tree/main/lean/docs)
- [V] The blog commits only to future improvement: "For future releases, we are committed to further improving the quality of the papers via the citations, mathematical exposition, and presentation of the results for better understanding." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] A spokesperson told SciAm that "many of the company's newly released results are not yet understood by its own mathematicians." — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- [V] Press on the lack of peer review: The Decoder notes OpenAI "put its results on GitHub instead of peer-reviewed journals", and that "Lean formalizations can verify logical correctness, but they can't judge whether a result is mathematically relevant or original." — [The Decoder](https://the-decoder.com/openai-dumps-372-ai-generated-math-proofs-on-github-telling-the-academic-world-to-keep-up/). tech-insider estimates "roughly 56 percent of the families" lack a full Lean check. — [tech-insider](https://tech-insider.org/openai-722-math-manuscripts-unreleased-model-2026/)
- [S] An orcarouter summary says: "It is not a paper: nothing here has been peer reviewed." — [orcarouter](https://www.orcarouter.ai/blog/openai-722-math-manuscripts-unreleased-model)
- [S] An arXiv preprint titled "A Human Audit of OpenAI's AI-Generated Mathematical Proofs" (2608.14673) showed up in search. Its arXiv number means August 2026, so it would predate this release and probably concerns earlier OpenAI outputs. I did not read it. — [arXiv 2608.14673](https://arxiv.org/pdf/2608.14673)

### Inferences
- The Lean-checked subset, if the formal statements faithfully match the informal claims, is the high-confidence core. Statement fidelity is the weak point: a Comparator check proves the stated Lean theorem, not that the theorem means what the paper claims. The catalogue's own "review: unchecked" flag says this fidelity review has not been done.
- About 137 of the 372 families (372 - 235) have no Lean page at all, including family 032 (rational Hodge for CM abelian varieties), which was also a procedural exception.

### Gaps
- No error rate, known-wrong results, or retractions as of 7 Oct.
- No statement on prior-literature or novelty checks, beyond the blog's promise to improve citations. Will Depue's citedbyagi.com tracks which human papers the release cites ([latent.space](https://www.latent.space/p/ainews-quasi-riemann-hypothesis-openai) [V], second-hand).
- I found no named external reviewers or human-review process for the release.

## 4. Headline results in OpenAI's own words

### Takeaway
The repo's overview states its claims flatly as "Proves", "Resolves" and "Disproves", with no confidence qualifiers per result. For most headline results, confidence comes from whether a Lean scope page exists. The Mahler, Kaplansky zero-divisor, free group factor, quasi-Riemann, π irrationality exponent, Erdős AP and Vlasov–Maxwell results all have Lean pages, though some cover only part of the claim. The rational Hodge result for CM abelian varieties has no Lean page. The blog post itself names no specific results.

One correction to the brief: the repo has both a Kaplansky **zero-divisor** counterexample (family 196) and a separate **direct-finiteness** counterexample (197). The reasoning trace is for 197, not 196.

### Cited Findings
Summaries are from `overview.tex` / `CONTENTS.md` [V-repo]; Lean status is from `lean/docs/NNN.md` [V-repo].
- **003 Quasi-Riemann hypothesis.** "Proves that every Dirichlet L-function, including ζ(s), is zero-free in Re s>7/8, resolving the quasi-Riemann hypothesis. The same half-plane is zero-free for every finite-order Hecke L-function over Q(√−3). A companion gives a different proof of the zero-free half-plane Re s>11/12." The family also includes "Uniform exclusion of Landau–Siegel zeros". Lean: yes. The 7/8 bound is formalized for zeta, Dirichlet and Hecke over Q(√−3), plus a uniform c/log q real-zero gap ("No explicit value of c is given"). The README flags the Riemann-zeta zero-free work as an exception to the fixed procedure and the 11/12 write-up as human-edited. — [overview](https://github.com/openai/math/blob/main/overview.pdf), [lean/docs/003.md](https://github.com/openai/math/blob/main/lean/docs/003.md)
- **087 Mahler conjectures and symplectic width.** "Resolves the symmetric and nonsymmetric geometric Mahler conjectures in every dimension, with Hanner polytopes and simplices as the respective volume-product minimizers and all equality cases classified. The corresponding sharp functional Mahler inequalities also hold. For n≥2, every symmetric polar product K×K° in dimension 2n has Gromov width 4." Lean: the symmetric case with equality (Hanner bodies), the general/simplex bound with equality, and Gromov width 4 are formalized. The functional inequalities are not. Reasoning trace: yes. — [lean/docs/087.md](https://github.com/openai/math/blob/main/lean/docs/087.md)
- **196 Kaplansky zero-divisor.** "Constructs a finitely presented torsion-free group G whose group algebra F_2[G] has nonzero zero divisors, disproving Kaplansky's zero-divisor conjecture. The group has a finite two-dimensional classifying space." Lean: yes. The construction with α·β=0 and the finite 2-D K(G,1) are formalized. — [lean/docs/196.md](https://github.com/openai/math/blob/main/lean/docs/196.md)
- **197 Nonsofic groups / Kaplansky direct finiteness.** "Constructs a finitely presented torsion-free nonsofic group whose group algebra over F_2 is not directly finite, disproving Kaplansky's conjecture even without torsion. Companion examples ... refuting Gottschalk's surjunctivity conjecture. Another counterexample ... disproving the unrestricted Determinant Conjecture." Lean: the direct-finiteness counterexample is formalized, but the Lean version uses "a finitely presented group with an element of odd prime order" (so not torsion-free), and "nonsofic is outside these statements". The Determinant Conjecture counterexample is formalized. Reasoning trace: yes. — [lean/docs/197.md](https://github.com/openai/math/blob/main/lean/docs/197.md)
- **287 Free group factors.** "Resolves the free group factor isomorphism problem: L(F_2)≅L(F_3), and hence all interpolated free group factors, including L(F_∞), are isomorphic. Their common factor has fundamental group R_{>0}." Lean: yes. The doc page says interpolated free group factors for all r,s>1, including ∞, are "normally trace-preservingly isomorphic". The fundamental-group statement is "a further consequence rather than a separate selected statement". Comparator config: `InterpolatedFactors.json`. I found no title match for this paper in the 162-entry yaml source list, so it may be outside the 162-paper "main result" catalogue (unconfirmed). Reasoning trace: yes. — [lean/docs/287.md](https://github.com/openai/math/blob/main/lean/docs/287.md)
- **032 Rational Hodge for CM abelian varieties and products of K3s.** "Proves the rational Hodge conjecture for every complex CM abelian variety, in every dimension and codimension. Through Milne's theorems, this also gives the Tate conjecture for all abelian varieties over finite fields and the Hodge standard conjecture for abelian varieties in every characteristic." Lean: **no page.** README: an exception to the fixed procedure. — [overview](https://github.com/openai/math/blob/main/overview.pdf)
- **Other families with reasoning traces** (Lean status in brackets):
  - 007, two-point Chowla / binary Elliott [Lean page exists].
  - 017, "irrationality exponent of π is exactly 2", plus Flint–Hills convergence [Lean: exponent yes, Flint–Hills no].
  - 102, NP-hardness at the basic semidefinite threshold.
  - 159, Erdős reciprocal-sum conjecture plus quasipolynomial Szemerédi bounds [Lean: the Erdős statement only].
  - 221, Mézard–Parisi formula for diluted spin glasses, under the Panchenko–Talagrand assumptions.
  - 271, Bloch's T^{3/2} law and spontaneous magnetization for the quantum Heisenberg ferromagnet.
  - 362, large-data global smoothness for 3-D relativistic Vlasov–Maxwell [Lean: yes].
  - Source: [README reasoning summaries table](https://github.com/openai/math)
- **Other notable claims in the overview** (selection; [V-repo]):
  - 002/006: full BSD formula in Selmer corank 0/1; Goldfeld's conjecture.
  - 004: Hilbert's tenth problem over Q (negative).
  - 005: irrationality of Catalan's constant.
  - 008: Deligne–Drinfeld.
  - 074: Kakeya maximal conjecture in 3-D and the Hausdorff-dimension conjecture in 4-D.
  - 095: disproof of the generalized Lax conjecture.
  - 107: ω ≤ 9/4.
  - 109: integer multiplication in O(n (log n)^{1−κ}) with κ=2^{−182}, "disproves the Schönhage–Strassen n log n optimality conjecture".
  - 126: exponential SDP extension complexity of the perfect matching polytope.
  - 285: counterexamples to Baum–Connes and Kadison–Kaplansky.
  - 294: Kaplansky quasitrace counterexample.
  - 372: global uniqueness for smooth isotropic elasticity in R^3.
  - Source: [overview](https://github.com/openai/math/blob/main/overview.pdf)
- [S] BigGo (search snippet) also lists Khot's Unique Games Conjecture among the claims. I did not verify this against the overview. — [BigGo Finance](https://finance.biggo.com/news/1d522643-5fd9-4ac5-ae86-e4a5b99edfe2)
- [V] One analysis estimates "about 20% of the results are disproofs or counterexamples" (via latent.space, from an X post). — [latent.space AINews](https://www.latent.space/p/ainews-quasi-riemann-hypothesis-openai)

### Inferences
- OpenAI expresses confidence structurally, through Lean and Comparator, rather than in words. Within a family, the Lean scope can be narrower than the overview claim. Examples: 197's Lean counterexample has torsion while the headline says "without torsion"; 087 omits the functional inequalities; 159 omits the quantitative bounds. Readers should compare the overview wording against `lean/docs/NNN.md` for each result.
- The brief's phrase "zero-free half-plane for Dirichlet L-functions" matches OpenAI's own framing (Re s > 7/8, "quasi-Riemann hypothesis"). It is not a claim about the Riemann hypothesis itself.

### Gaps
- I did not read the reasoning-trace PDFs or the manuscripts themselves.
- I did not verify the UGC claim or check all 372 entries for Lean status.

## 5. Why release publicly; plans for journals, product, researcher access

### Takeaway
OpenAI frames the release as transparency guided by the IAS-hosted Advisory Group on Mathematics and AI (AGMAI): a GitHub repo now, community-hosted repositories under exploration, funded workshops and conferences, and a model release it is "working to responsibly" deliver, with no date. There is no stated plan for journal submission. OpenAI also says it will keep evaluating internal models on open math problems, which AGMAI had explicitly asked labs to stop doing.

### Cited Findings
- [V] The blog cites AGMAI: "we've been consulting with the independent Advisory Group on Mathematics and Artificial Intelligence at the Institute for Advanced Study to develop best practices, and we have drawn on their advice and public recommendations to inform how we release these results." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] On venue: "We're continuing to explore other community-hosted alternatives for this release which meet the committee's guidelines." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] On transparency: "To promote scientific transparency and openness, we are also publishing additional details about how we obtained the results ... 10 summaries of the model's reasoning, estimations of compute spent ... and statistics about the number of attempted problems." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] On funding: "We want this progress to push the frontier of human knowledge and enable further progress in mathematics. We will be funding a series of workshops, conferences, and special programs around the understanding of major results produced by AI—we will share more on this in the near future." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] On model access and continued evaluation: "We want to directly empower scientists with state-of-the-art capabilities and are working to responsibly release the model that produced these results. This is why it is important to continue to evaluate our internal frontier models on mathematics and other sciences ... We will continue to act on feedback from the community and update our standards for future disclosures of major scientific advancements." — [OpenAI blog](https://openai.com/index/sharing-ai-progress-in-mathematics/)
- [V] The AGMAI recommendations (29 Sep 2026) say: "we do not endorse this practice, and we ask them to stop testing advanced mathematical problems on proprietary models." For results nobody understands, they ask labs to scour the literature and cite it, produce conventional write-ups, deposit results in scholarly repositories "not ... controlled by any AI lab" with persistent identifiers, and fund human understanding. — [AGMAI, Responsible Release of AI-Generated Mathematics](https://agmai.org/general-sep29/)
- [V] Quartz, citing WSJ: OpenAI drew on the recommendations "with one exception": it would keep testing frontier problems on proprietary models. — [Quartz](https://qz.com/openai-math-results-github-millennium-prize-100726)
- [V] The Decoder: OpenAI set a boundary that the advisers "can advise on how results get communicated, but not on whether or how fast they're produced." — [The Decoder](https://the-decoder.com/openai-dumps-372-ai-generated-math-proofs-on-github-telling-the-academic-world-to-keep-up/)
- [V] A spokesperson told SciAm the company is "not bound by these recommendations". SciAm also reports that OpenAI says it "can't slow down because these math problems are an indispensable test to show that their AI really is getting smarter." — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- [V] Spokesperson Lindsay McCallum Rémy to Gizmodo: "AGMAI's advice and public recommendations have informed how we're sharing the results. We'll continue incorporating community feedback and improving our standards for sharing major scientific advances." — [Gizmodo](https://gizmodo.com/openai-dumps-377-new-math-results-on-github-publishes-hand-wringing-blog-post-2000822613)
- [V] Navier–Stokes post framing, which this release links to: "Our goal in releasing this result is to report on the substantial progress of our AI models ... We believe it is important to inform the world about the pace of AI progress and what to expect from upcoming models." — [OpenAI Navier–Stokes post](https://openai.com/index/navier-stokes-solution/)

### Inferences
- The stated motivations are threefold: transparency and community norms, showing capability progress (the README's "evaluations ... saturated" framing), and seeding human understanding through funded programs. Journal submission is conspicuously absent. Sole "OpenAI" authorship sits awkwardly with journal norms on author responsibility, which AGMAI section 2.A emphasizes.

### Gaps
- No timeline for the model release, the workshop program, or a community-hosted mirror (e.g. arXiv or Zenodo DOIs).

## 6. Executive statements and press coverage

### Takeaway
I could verify only one executive statement: Sam Altman called it "a new era of discovery" (an X post, seen second-hand). I found no statements on this release from Pachocki, Mark Chen, Noam Brown or Bubeck. On-record comments come from spokespeople, Lindsay McCallum (Rémy). Coverage (SciAm, Quartz, Gizmodo, The Decoder, latent.space, tech-insider; WSJ, NYT, WIRED and The Verge cited second-hand) mixes amazement with skepticism about transparency, the unreleased model, and AGMAI non-compliance.

### Cited Findings
- [V, second-hand] Sam Altman called it "a new era of discovery" (X post 2107623610483720463). The official OpenAI announcement tweet is x.com/OpenAI/status/2107596713791767021, at about 19.0K engagement. — [latent.space AINews](https://www.latent.space/p/ainews-quasi-riemann-hypothesis-openai)
- [S] A search summary links Brown, Pachocki, Chen and Bubeck only generically to OpenAI's reasoning work. I found no release-specific quotes from them. — search result; no reliable source
- [V] Levent Alpöge (Anthropic employee; Navier–Stokes/Euler competitor) said: "It's obviously the most significant moment in mathematical history", and praised the quasi-Riemann and no-Siegel-zeros results. He also raised scooping and conflict-of-interest issues. — [latent.space AINews](https://www.latent.space/p/ainews-quasi-riemann-hypothesis-openai)
- [V] Andrew Sutherland (MIT): "Until and unless they release the model and people can replicate their results, I think you should treat any claims about one-shotting problems with a single agent as unverified ... We should ask for receipts." Daniel Litt (Toronto): "I see no reason why we should ask the company to keep them secret from us ... it's going to be a good thing for mathematics." SciAm says Terence Tao has criticized the "insane" pace. — [Scientific American](https://www.scientificamerican.com/article/openai-unleashes-hundreds-more-math-results-upon-a-field-already-in-shock/)
- [V] Quartz, citing WSJ: the release touches three of the five remaining Millennium Prize Problems, including Riemann. Quartz also cites an open letter by more than two dozen Fields medalists, and Andreas Thom's accusation of "dishonesty". — [Quartz](https://qz.com/openai-math-results-github-millennium-prize-100726)
- [V] The Decoder cites the open letter "A Severe Misalignment of AI in Mathematics" by 25 Fields medalists, and notes that the AGMAI includes Timothy Gowers. — [The Decoder](https://the-decoder.com/openai-dumps-372-ai-generated-math-proofs-on-github-telling-the-academic-world-to-keep-up/)
- [V] Before release, WIRED (via Superpower Daily) reported the 6 Oct GitHub plan. Bryna Kra (Northwestern) said that about 40 mathematicians who met OpenAI in August urged it to publish explanatory papers, and that she believes this advice was ignored. On 21 Sep, OpenAI had claimed its model solved "more than 100 long-standing open problems". — [Superpower Daily](https://superpowerdaily.com/posts/openai-is-reportedly-preparing-a-github-math-release-as-researchers-demand-papers)
- [V] Other reactions (via latent.space): Will Depue expects some results "should not survive scrutiny"; Teortaxes says three hours of compute "is not much"; François Chollet questions whether the gains generalize beyond verifiable domains. — [latent.space AINews](https://www.latent.space/p/ainews-quasi-riemann-hypothesis-openai)
- [S] Nature's daily briefing headline: "OpenAI claims a huge maths breakthrough". I did not read it. — [Nature briefing](https://www.nature.com/articles/d41586-026-02867-w)
- [S] I saw no Quanta, Ars Technica, The Information, Unite.ai or Dealroom pieces in search results. The NYT (nytimes.com/2026/10/06/science/openai-math-problems.html), WSJ and The Verge are cited by others but I did not read them.

### Inferences
- The executive messaging appears thin, with Altman's tagline plus spokesperson statements. That may reflect a deliberately lower-key posture after the Navier–Stokes controversy, though this is my inference.

### Gaps
- X was blocked, so I could not read posts from OpenAI, Altman or researchers directly.
- No primary NYT, WSJ, WIRED or Verge text. No Quanta or Science news coverage found as of 7 Oct.
