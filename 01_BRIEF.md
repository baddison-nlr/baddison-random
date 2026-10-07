# Brief — Random

**What this project is:** Bennett's personal curiosity space. He picks topics on a whim and
we take a pass at each. No deliverable. Public sources only.

**Current topic:** 13, OpenAI's 6 Oct 2026 math release.

**Canonical file per topic** (each wins for its own topic):

| Topic | File | Research date |
|---|---|---|
| 13, OpenAI math release | `T13_OPENAI_MATH_RELEASE_REPORT.md` | 7 Oct 2026 |
| 12, exotic propulsion race | `T12_PROPULSION_RACE_REPORT.md` | 6 Oct 2026 |
| 11, Lutnick / Andriesz death | `T11_LUTNICK_ANDRIESZ_BRIEF.md` | 5 Oct 2026 |

Topics 1-10 (Sept 2026) exist only as rows in `02_CONTEXT.md`. Research threads, gaps and
appendix contents are mapped in `05_RESEARCH_INDEX.md`.

---

## Topic 13 (7 Oct 2026): OpenAI's 722 AI math papers

**What happened.** On 6 Oct 2026, OpenAI posted 722 math manuscripts in 372 "result
families" across 17 fields to a public GitHub repo (openai/math, Apache-2.0). The only author
listed is "OpenAI". They came from an unnamed internal model that has not been released. The
model was posed about 4,000 open problems, and each result used on average about three
hours of ChatGPT Pro-level thinking. It is a repo, not a journal: no peer review, and no
human authors listed.

**Machine checking.** 162 papers have their main result proved in Lean, a proof-checking
language; that is 185 formal statements. Another 235 families have partial Lean coverage.
The catalogue labels its own formal statements "unchecked", and the formal proofs were
themselves written by AI agents. A Lean check proves the formal statement is true. It does
not prove that the formal statement says what the English headline says.

**Headline claims, in plain terms:**
- **Quasi-Riemann hypothesis (family 003).** No zeros of any Dirichlet L-function (zeta
  included) with real part above 7/8. The Riemann hypothesis would put the line at 1/2;
  until now, nobody could prove any fixed line short of 1. If true, this is a historic
  result about how regularly the primes are distributed. It has a Lean proof built only on
  standard library definitions, so it is the lowest-risk headline. Caveats: the zeta work was
  an exception to the automated procedure, a human edited one write-up, and an independent
  second proof-checker was not run.
- **Mahler's conjecture (087).** In convex geometry: the smallest possible value of a
  shape's volume times its "polar" (dual) shape's volume, in every dimension. Lean covers
  both main bounds.
- **Kaplansky zero divisors (196).** A group with no elements of finite order whose "group
  algebra" still has two nonzero elements multiplying to zero. This disproves a conjecture
  from the 1950s. The Lean statement is clean. Do not confuse it with family 197, a different
  Kaplansky problem, where the formalized group does not match the headline claim.
- **Free group factors (287).** A famous question in operator algebras: whether the von
  Neumann algebras built from free groups on 2 and on 3 generators are the same. The claim is
  "yes, all of them are isomorphic", against most experts' expectation. It is formalized, but
  on about 200 lines of home-made definitions, so it has the highest risk that the formal
  statement is off.
- **The long tail.** Unique Games Conjecture, Hilbert's tenth problem over the rationals,
  Kakeya in 3 and 4 dimensions, the Hodge conjecture for CM abelian varieties (no Lean
  proof), the irrationality exponent of pi equal to 2, matrix-multiplication exponent at most
  9/4, integer multiplication faster than n log n, and dozens more. Base rates say not all of
  these will survive.

**How credible is it?** No named mathematician has yet confirmed or refuted any single
result; reactions are about a day old. Every reaction on record is about process (pace,
credit, secrecy), not whether the proofs are right. OpenAI's track record raises the odds:
the May 2026 unit-distance disproof was called journal-worthy by Gowers and Litt, and a
human audit of the August batch of ten found no error that held up in a main result.

**The trajectory.** IMO silver (2024), then IMO gold (2025), then the overclaimed Erdős
episode (Oct 2025), then the First Proof challenge (Feb 2026), the unit-distance disproof
(May), ten Lean-certified results (Aug), the forced Navier–Stokes claim (Sept) and now 722
(Oct). Benchmarks saturated along the way: about 98% on FrontierMath Tier 4.

**Reactions:**
- **The establishment:** 25 Fields Medalists signed a September open letter saying AI-lab
  and math-community goals are "severely misaligned". Tao, who co-chairs the IAS advisory
  group, warns against "harvesting" open problems.
- **For releasing it all:** Litt wants everything public, and Buzzard says "you cannot fool
  Lean".
- **The skeptic:** Sutherland wants receipts, meaning the model has to be released so others
  can replicate.
- **OpenAI** says it is "not bound" by the advisory group's request to stop testing
  unreleased models on open problems.

**Implications:**
- Generation is now cheap and human understanding is the bottleneck. Expect a two-tier
  literature: Lean-certified results trusted provisionally, unformalized ones treated as
  conjectures.
- Labs are scooping researchers: there is a credit fight over Navier–Stokes and alleged use
  of a user's Codex sessions.
- Physics spillover has started (Claude's nine-loop amplitude).
- No threat to deployed cryptography.
- For the AI race, math is the public demonstration of "automated research". OpenAI says it
  hit its "automated research intern" goal in Sept 2026, with an AI researcher targeted for
  March 2028.
- The decisive limit: nobody outside OpenAI can run the model, measure its failure rate, or
  see how much curation sat between 4,000 prompts and 372 families.

**Verdict.** As a capability demonstration, it is as big as it looks. As settled theorems,
it is nothing yet. Watch the short list of formally clean claims (003, 196, 087) over the
coming weeks.

**Bennett's angle:** the analogy to a spectrometer. Lean guarantees the reading, not the
meaning. The topic also ties back to topic 12, which concluded that AI accelerates
calculation within known theory. This release pushes on that conclusion: it is still within
known frameworks, but now at the frontier of pure math.

---

## Topic 12 (6 Oct 2026): is exotic propulsion the real US-China race?

The tweet claimed propulsion is the top race and AI is the tool for it. **Verdict: the order
is backwards.**
- **Hypersonics** is a real race, and China leads by about five years in fielded weapons.
- **Space nuclear power** is a real policy race over lunar reactors. The US cancelled its
  nuclear rocket (DRACO) in 2025.
- **Fusion** is a power-plant race.
- **Exotic propulsion** (UAP, warp, EmDrive) is claim/theory with nothing behind it.
- **AI** speeds up engineering, and neither country's AI strategy mentions propulsion.
- **The nuclear-race analogy fails.**

The tweet's author was not found; the closest match is Eric Weinstein.

## Topic 11 (5 Oct 2026): Lutnick and the Andriesz death

Simon Andriesz, a British ex-BGC banker, found Lutnick-Epstein business ties (Adfin
emails, a plan to "buy a prince") in the Epstein files. He died in late September 2026,
reported as suicide at a trauma treatment centre. No gunshot appears in any source. Lutnick's
public account (cut off contact in 2005) was contradicted by his own sworn testimony.
