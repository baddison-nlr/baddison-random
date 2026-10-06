<!-- Generated copy of research_notes/Exotic propulsion race US China/ai_for_physics.md. Do not edit here; edit research_notes/Exotic propulsion race US China/ai_for_physics.md. -->

# AI for advanced physics and propulsion, and what the US-China AI race is officially "for"

Research date: 2026-10-06. Light pass (about 20 tool calls). Status tags:
- **[V]** = the source was fetched or its text read this session (full text or substantial excerpt).
- **[R]** = reported in search-result snippets or secondary coverage only; the primary source was not read.
- **[M]** = recalled from memory and not re-checked this session.

## Fusion and plasma: what has AI actually done?

### Takeaway
AI in fusion is real and has been shown on working machines, but almost all of it is **control and surrogate modelling of known physics**. Examples are reinforcement-learning (RL) shape control on TCV, RL that avoids tearing instabilities on DIII-D, disruption prediction on EAST, and RL magnetic control on HL-3. It speeds up engineering and the operation of devices. It has not produced new plasma physics, and none of it is propulsion work. Fusion propulsion would come downstream of any gain in fusion power generally.

### Cited Findings
- **DeepMind/EPFL TCV (Nature, Feb 2022, Degrave et al.):** a deep-RL controller was trained on a free-boundary simulator. On the real TCV tokamak it read only magnetic measurements and set the coil power-supply voltages directly, holding a range of plasma shapes. This was the first RL magnetic control of a real tokamak plasma. [R] — [EPFL news](https://actu.epfl.ch/news/epfl-and-deepmind-use-ai-to-control-plasmas-for-nu); [DeepMind blog](https://deepmind.google/discover/blog/accelerating-fusion-science-through-learned-plasma-control/). A follow-up paper on making RL tokamak control practical: [arXiv 2307.11546](https://arxiv.org/pdf/2307.11546) [R]
- **Princeton/DIII-D (Nature 626, 746-751, 2024, Seo, Kolemen et al.):** a deep neural network was trained on past DIII-D shots to predict how likely a tearing instability is. That predictor was then used to train an RL controller, which adjusted plasma shape and neutral-beam power to keep the tearing likelihood below a threshold while holding H-mode, including at low safety factor and low torque. The authors frame it as *avoiding* instabilities before they appear, as opposed to suppressing them afterwards, and as a route to ITER scenarios. [R] — [Princeton MAE](https://mae.princeton.edu/about-mae/news/engineers-use-ai-wrangle-fusion-power-grid); [DOE FES highlight](https://science.osti.gov/fes/Highlights/2024/12a)
- **DeepMind and Commonwealth Fusion Systems (announced 16 Oct 2025):** the partnership uses DeepMind's open-source, differentiable plasma simulator **TORAX** to run "millions of virtual experiments" before SPARC operates and to "discover novel real-time control strategies" for SPARC. CFS had projected net energy on SPARC for late 2026 to early 2027. Google invested in CFS's 2021 round ($1.8B) and signed a 200 MW power purchase agreement (PPA) with CFS in June 2025, so it has a commercial stake. [R] — [ANS Nuclear Newswire](https://www.ans.org/news/2025-10-22/article-7484/commonwealth-fusion-systems-partners-with-google-deepmind/); [Axios](https://www.axios.com/2025/10/16/google-deepmind-clean-energy-fusion); [DCD](https://www.datacenterdynamics.com/en/news/google-deepmind-to-undertake-research-partnership-with-nuclear-fusion-firm-cfs/)
- **China, EAST:** a disruption database of all disrupted EAST shots has been built, and CNN, LSTM, random-forest and XGBoost models were trained to predict disruptions caused by impurity bursts, MARFEs and other causes. Imitation-learning control is being validated on EAST data; preliminary simulations report >92% trajectory-tracking accuracy and <2 ms inference latency. [R] — [IAEA conference contribution](https://conferences.iaea.org/event/393/contributions/36704/contribution.pdf); [IAEA FEC contribution](https://conferences.iaea.org/event/377/contributions/31638)
- **China, HL-3 (SWIP):** a fully data-driven dynamics model is used to train an RL agent that sends coil commands at 1 kHz over a 400 ms control horizon, with "zero-shot adaptation to new triangularity targets". Separately, a vision transformer infers six plasma-shape parameters from CCD camera images. [R] — [IAEA conference contribution](https://conferences.iaea.org/event/393/contributions/36713)
- **Chinese foundation-model approach:** "FusionMAE", a large-scale pretrained model for diagnosing and controlling fusion plasma (arXiv, Sep 2025). [R] — [arXiv 2509.12945](https://arxiv.org/pdf/2509.12945)
- **Europe, WEST:** DeepMind-style deep-RL magnetic control has also been reproduced on the French WEST tokamak. [R] — [HAL](https://hal.ccsd.cnrs.fr/INRIA/hal-04393963v1)

### Inferences
- The capability has spread internationally (EPFL/DeepMind, Princeton, CEA WEST, ASIPP EAST, SWIP HL-3). China is a close follower or peer in ML for tokamak control, not far behind. Neither side has a monopoly.
- All of these results speed up control and modelling of plasmas whose governing physics (MHD, transport) is already known. That fits "AI shortens fusion engineering timelines", not "AI discovers new propulsion physics".
- None of the sources mentions propulsion. Fusion propulsion depends on compact, high-gain fusion arriving first, and AI may modestly shorten that path.

### Gaps
- I did not fetch the Nature papers themselves (TCV 2022, DIII-D 2024), so figures come from press releases and abstracts.
- No independent check of the HL-3 and EAST claims beyond conference abstracts. I found no peer-reviewed Chinese counterpart in Nature or Science to the TCV or DIII-D papers in this pass.
- No 2026 update on whether TORAX-derived controllers have run on SPARC, or on SPARC's first-plasma status.

## Materials: GNoME, MatterGen, A-Lab and the critiques

### Takeaway
The headline AI materials claims have each drawn substantial expert pushback on **novelty** and **usefulness**. GNoME's 2.2M crystals were criticised for low utility and for many known or unrealistically ordered structures. A-Lab's "41 novel compounds" was formally corrected to 36 of 57 targets, which were "new to the lab, not necessarily new to science". The one compound MatterGen validated experimentally turned out to be a 1971 compound that was in its training set. AI is a useful screening and prediction accelerator. Its record on genuinely new functional materials is thin so far. I found no public evidence on AI-driven high-temperature alloys or hypersonic thermal protection systems (TPS).

### Cited Findings
- **GNoME (DeepMind, Nature, Nov 2023):** about 2.2M predicted crystal structures, about 380k of them flagged as stable. [M]
- **Cheetham & Seshadri critique (Chemistry of Materials, Apr 2024, UCSB):** found "scant evidence for compounds that fulfill the trifecta of novelty, credibility, and utility". The entries are crystalline inorganic compounds with no demonstrated application. The survey leaves out polymers, glasses, MOFs, heterostructures and composites. Many entries depend on metal-ion orderings unlikely to occur in real materials, and a large fraction of the 384,870 compositions adopt structures already in the ICSD. [R] — [PMC full text](https://pmc.ncbi.nlm.nih.gov/articles/PMC11044265); [The Register](https://www.theregister.com/2024/04/11/google_deepmind_material_study/)
- **A-Lab (Berkeley/LBNL, Nature 2023):** claimed 41 novel compounds from 58 targets in 17 days. Robert Palgrave (UCL) and others argued that the automated powder-XRD phase identification was flawed in several cases and that some "new" materials were already known. A later analysis raised further doubts. [R] — [Chemistry World](https://chemistryworld.com/news/new-analysis-raises-doubts-over-autonomous-labs-materials-discoveries/4018791.article); [VentureBeat](https://venturebeat.com/ai/ai-meets-materials-science-the-promise-and-pitfalls-of-automated-discovery)
- **A-Lab Author Correction:** the record now says **36 of 57** targets were synthesised, and that the targets were "new to the laboratory, not necessarily new to science". Earlier experimental reports existed for many of the same or closely related compositions. [R] — [Author Correction, PMC](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC12872444/)
- **MatterGen (Microsoft Research AI for Science, Nature, 16 Jan 2025):** a generative diffusion model. Its showcase validation was TaCr2O6, generated to target a bulk modulus of 200 GPa and measured at 169 GPa (synthesis with SIAT Shenzhen). [R] — [Microsoft Azure AI Foundry Labs](https://labs.ai.azure.com/innovations/mattergen/)
- **MatterGen critique (Juelsholt, Materials Horizons, 2026):** "this is not a novel compound but is identical to the previously reported Ta1/2Cr1/2O2, first described in 1971". That compound was in MatterGen's training data. The paper concludes that generative models struggle to predict disorder and need rigorous human verification. [V] (repository abstract page) — [HU Berlin edoc](https://edoc.hu-berlin.de/items/2081bca4-f044-43d3-a5f5-1d7c39f9e3e7/full)

### Inferences
- All three flagship results share one failure mode: a model's "novel" means novel to its database, not novel to science, and disorder or site-mixing is handled badly. For propulsion-relevant materials, the useful property (creep, oxidation and ablation resistance at 2000+ deg C) depends on microstructure, defects and processing. Current crystal-structure generators do not model any of these.
- The field is still producing value: faster screening, ML interatomic potentials and self-driving labs. The direction of travel is "accelerated incremental", not "revolutionary new materials".

### Gaps
- **Not researched in this pass:** AI for high-entropy or refractory alloys, ultra-high-temperature ceramics (UHTCs) and hypersonic TPS. I found no specific citable result, and that topic needs its own pass.
- The A-Lab correction's exact date (it looks like 2025-2026) was not confirmed.

## CFD, aero, hypersonics and the US AI-for-science programmes

### Takeaway
Public Chinese work on AI for hypersonics, as reported by SCMP, covers **AI-assisted wind-tunnel analysis, scramjet fuel and fault control on edge AI chips, and fast combustion simulation**. These are engineering speed-ups, not new physics. On the US side, the Genesis Mission (Nov 2025) is the main AI-for-science vehicle. It names fusion and fission, but not propulsion, aerospace or hypersonics, among its priority domains.

### Cited Findings
- **Scramjet control on an AI chip:** researchers at the Beijing Power Machinery Research Institute and Dalian University of Technology (led by Sun Ximing) used an Nvidia Jetson TX2i module. Calculations that had taken seconds took 25 ms, enabling "real-time optimisation of the fuel supply system, fault diagnosis, and fault-tolerant control in scramjet engines". [R] — [SCMP](https://amp.scmp.com/news/china/science/article/3259166/tech-war-how-chinese-scientists-rigged-low-cost-ai-computer-chip-power-hypersonic-weapon); [The Register](https://www.theregister.com/2024/04/16/china_nvidia_hypersonic_weapon/)
- **Shock-wave recognition in wind-tunnel tests (SCMP, 2022):** reported to be 85% more accurate than a human, at about 9 s per image on a regular GPU. [R] — [SCMP](https://scmp.com/news/china/science/article/3171533/ai-its-way-replacing-humans-hypersonic-weapon-design-chinese)
- **Scramjet combustion simulation:** SCMP reports Chinese software that "fully simulates" supersonic combustion physics in one week, versus "years" on a supercomputer. The article was paywalled (fetch returned 403), so I could not confirm whether this is AI/ML or conventional HPC/CFD. [R, unverified] — [SCMP](https://www.scmp.com/news/china/science/article/3347269/years-week-china-unveils-superfast-software-hypersonic-weapon-design); possibly related CAS CNIC note: [CNIC](https://english.cnic.cas.cn/rsearch/rp/202508/t20250801_1048962.html)
- **Genesis Mission executive order (24 Nov 2025):** aims to "double the productivity and impact of American science and engineering within a decade" through an integrated DOE AI platform: foundation models trained on federal datasets, AI agents, and AI-directed experimentation linked to supercomputers and automated labs. Darío Gil (DOE Under Secretary for Science) is director and Michael Kratsios (OSTP) coordinates. Deadlines are 90 days (compute), 120 days (datasets) and 240 days (review of AI-directed experimentation). The order commits no new funding. [V] — [AIP FYI](https://www.aip.org/fyi/trump-administration-launches-genesis-mission-to-boost-science-through-ai)
- **Genesis Mission priority domains:** at least 20 challenges across advanced manufacturing, biotechnology, critical materials, **nuclear fission and fusion energy**, quantum information science, and semiconductors/microelectronics. National security is one of three stated focus areas. Aerospace, hypersonics and propulsion are **not** named in the AIP summary. [V] — [AIP FYI](https://www.aip.org/fyi/trump-administration-launches-genesis-mission-to-boost-science-through-ai); [The Register](https://www.theregister.com/2025/11/25/trump_ai_genesis_mission/) [R]
- **AI Action Plan follow-on:** NSF announced $380M (reported elsewhere as "$400M") for 20 teams in an AI-enabled automated-lab network (the PCL Test Bed), explicitly implementing an Action Plan priority. [R] — [NSF](https://www.nsf.gov/tip/updates/nsf-announces-400m-investment-new-national-network-ai)

### Inferences
- Openly reported Chinese AI-for-hypersonics work is about faster design cycles and better onboard control. Chinese hypersonic programmes were already mature before modern ML, which suggests AI is an accelerant to an existing programme rather than its basis.
- The US frames AI-for-science around energy (including fusion), materials, biotech, quantum and chips. Propulsion is at most implicit, under "national security" or "advanced manufacturing".

### Gaps
- **Not covered in this pass:** NVIDIA Modulus/PhysicsNeMo for hypersonic or combustion surrogates, DARPA AI-for-science programmes, and DOE's FASST initiative (Frontiers in AI for Science, Security and Technology) and its relation to Genesis. I found no citable source in the searches run, so these need follow-up.
- I did not read the Genesis Mission EO text on whitehouse.gov directly, only AIP's summary of it.
- I did not check peer-reviewed Chinese journals (e.g., Acta Aeronautica et Astronautica Sinica, Physics of Fluids) for AI design of scramjets or waveriders. SCMP is a secondary source that tends to amplify claims.

## "AI discovering new physics": what is real by late 2026?

### Takeaway
2026 brought the first results that physicists themselves call significant. GPT-5.2 conjectured a formula for a gluon amplitude, proved by human co-authors (Feb 2026). Anthropic's Claude computed a nine-loop N=4 super Yang-Mills amplitude, which Lance Dixon verified (Sep 2026). AlphaEvolve improved a few bounds among 67 maths problems. Even supporters describe these as **hard calculations and pattern-finding within existing theoretical frameworks**: no new techniques, no new theory, and no experimentally relevant new physics. Nothing here bears on "new physics for propulsion".

### Cited Findings
- **GPT-5.2 gluon amplitude (Feb 2026):** preprint "Single-minus gluon tree amplitudes are nonzero", with researchers from IAS, Vanderbilt, Cambridge and Harvard. Tree amplitudes with one negative-helicity gluon were expected to vanish. GPT-5.2 identified a "half-collinear regime" where they do not. Humans proved the expression formally and checked it against standard amplitude tests. Nima Arkani-Hamed called the results "strikingly simple expressions" and said finding such formulas had "always been fiddly" work he believed could be automated. [R] — [OpenAI on X](https://x.com/OpenAI/status/2022390096625078389); [OpenAI blog](https://openai.com/index/new-result-theoretical-physics/) (403, not read); [Science news](https://www.science.org/content/article/chatgpt-spits-out-surprising-insight-particle-physics) (403, not read)
- **Claude nine-loop N=4 SYM calculation (Aug-Sep 2026):** Anthropic physicists Liam Fitzpatrick and Siddharth Mishra-Sharma used Claude ("Claude Fable 5.1" on the "Claude Science" platform) to compute the six-particle amplitude in planar N=4 super Yang-Mills to **nine loops**; humans had reached eight loops in 2023. Lance Dixon verified it on 1 Sep 2026, 25 days after the challenge was posed, and the compute cost was in the thousands of dollars. [V] — [Ethan Siegel, Starts With A Bang / Big Think, 30 Sep 2026](https://startswithabang.substack.com/p/ai-makes-its-first-meaningful-breakthrough)
- **Siegel's caveats on the same result:** he calls it "the most significant breakthrough in theoretical physics ever made by an LLM", yet says the LLM "relied heavily on existing work, delivered no fundamentally new insights, developed no new techniques", and that other groups had "mostly already solved" the problem independently. Dixon was surprised that Claude did it "directly", noting the calculation is "very fragile". [V] — [Big Think](https://bigthink.com/starts-with-a-bang/ai-first-breakthrough-theoretical-physics/)
- **AlphaEvolve (DeepMind; Georgiev, Gomez-Serrano, Tao, Wagner, Nov 2025):** an evolutionary LLM coding agent tested on 67 problems in analysis, combinatorics, geometry and number theory. It rediscovered the best-known solutions in most cases, improved on them in several, and sometimes generalised finite cases into formulas. It works best when guided by experts, and its outputs are constructions rather than proofs. [R] — [arXiv/alphaXiv 2511.02864](https://www.alphaxiv.org/abs/2511.02864v1); [Implicator](https://www.implicator.ai/deepminds-alphaevolve-scales-mathematical-search-proofs-still-need-people/)
- **Data-driven discovery in experiment (Emory, 2026):** a physics-tailored neural network trained on 3D particle tracks in dusty plasma learned non-reciprocal interparticle forces with >99% accuracy and overturned some long-held assumptions about them. This is a genuine but domain-specific empirical finding. [R] — [ScienceDaily, Apr 2026](https://www.sciencedaily.com/releases/2026/04/260422044635.htm)
- **Caution from the field:** a June 2026 study argues that AI trained on familiar physics may miss genuinely new phenomena, and that it may need to "unlearn" priors. [R] — [Phys.org](https://phys.org/news/2026-06-physics-ai-unlearn.html); [ScienceDaily](https://www.sciencedaily.com/releases/2026/06/260611024557.htm). See also the arXiv assessment "Can Theoretical Physics Research Benefit from Language Agents?" [R] — [arXiv 2506.06214](https://arxiv.org/pdf/2506.06214)
- **Background:** AI Feynman (Udrescu & Tegmark, 2020) and symbolic-regression tools rediscover known equations from data. They are not known to have found a new fundamental law. [M]

### Inferences
- The credible 2026 picture is that frontier LLMs and agents are now useful co-workers in **formal, well-posed** theoretical physics: amplitudes, bounds and conjectured closed forms checked by experts. This is a real shift since 2024.
- None of these results touches the physics that "exotic propulsion" would need: new interactions, inertia or gravity effects, or beyond-Standard-Model forces with engineering relevance. The bottleneck there is experimental evidence, and AI has not produced any.
- A plausible near-term effect on propulsion comes through engineering physics (plasma control, combustion surrogates, materials screening), not through new fundamental theory.

### Gaps
- I did not read the GPT-5.2 preprint itself, the OpenAI blog, the Science news piece, or the Claude/Dixon paper.
- I did not survey LLM "AI scientist" agents (Sakana AI Scientist, FutureHouse, Google AI co-scientist), their failure-mode critiques, or the 2025 GPT-5 physics claims beyond the gluon result.

## What do official strategies say the AI race is for?

### Takeaway
Neither government frames the AI race as being "about" propulsion or new physics. The US AI Action Plan (July 2025) frames it as economic, military and standards-setting dominance. Its science section is generic (automated labs, datasets), and the only propulsion-adjacent word in the whole document is a "space race" analogy. China's AI+ Opinions (Aug 2025) are overwhelmingly about economic diffusion: 70% and 90% agent and terminal penetration by 2027 and 2030, and an "intelligent economy" by 2035. Its science section is generic and names only biomanufacturing, quantum and 6G. The counterargument, that the race is mainly about productivity, military decision-making, compute and governance, is strongly supported by the primary texts.

### Cited Findings
**US AI Action Plan ("Winning the Race", July 2025) [V, full PDF text searched]** — [White House PDF](https://www.whitehouse.gov/wp-content/uploads/2025/07/Americas-AI-Action-Plan.pdf)
- Framing: "Whoever has the largest AI ecosystem will set global AI standards and reap broad economic and military benefits. Just like we won the space race, it is imperative that the United States and its allies win this race."
- Stated payoffs: "a new golden age of human flourishing, economic competitiveness, and national security". AI will "discover new materials, synthesize new chemicals, manufacture new drugs, and develop new methods to harness energy" and make "breakthroughs in scientific and mathematical theory".
- The "Invest in AI-Enabled Science" section recommends automated cloud-enabled labs for "engineering, materials science, chemistry, biology, and neuroscience", plus Focused Research Organizations and dataset-release incentives. It warns that "AI-enabled predictions are of little use if scientists cannot also increase the scale of experimentation."
- Fusion appears only as an energy source for powering AI data centres ("enhanced geothermal, nuclear fission, and nuclear fusion").
- A text search of the full plan found **no** occurrence of "propulsion", "hypersonic" or "aerospace". The only "space" hit is the space-race analogy. The defence content concerns DOD warfighting and back-office adoption, an "AI & Autonomous Systems Virtual Proving Ground", priority compute access in emergencies, and secure data centres.

**Genesis Mission EO (Nov 2025) [V via AIP]:** priority domains are manufacturing, biotech, critical materials, fission and fusion, quantum and semiconductors, with goals of discovery, national security, energy dominance and productivity. Propulsion and aerospace are not named. — [AIP FYI](https://www.aip.org/fyi/trump-administration-launches-genesis-mission-to-boost-science-through-ai)

**China, State Council "Opinions on Deepening the Implementation of the AI+ Initiative" (Guofa [2025] No. 11, released 21 Aug 2025) [V, CSET translation text searched]** — [CSET translation PDF](https://cset.georgetown.edu/wp-content/uploads/t0652_AI_plus_opinions_EN.pdf); [CSET page](https://cset.georgetown.edu/publication/china-ai-plus-opinions-2025/)
- Purpose: "promote the broad and deep integration of AI across all industries and areas of the economy and society ... drive revolutionary leaps for productive forces" and build a "smart economy and smart society".
- Targets: by 2027, penetration of smart terminals and intelligent agents above 70%; by 2030, above 90%, with the intelligent economy a "major growth pole"; by 2035, full entry into an "intelligent economy and smart society".
- Six actions: AI+ S&T, industry, consumption, livelihoods, governance and global cooperation.
- The AI+ S&T section: "Accelerate the exploration of new AI-driven scientific research paradigms to speed up the 'from zero to one' process of major scientific discoveries", plus large scientific models, upgrades to major S&T infrastructure, and open datasets. Fields named explicitly are "biomanufacturing, quantum technology, sixth-generation mobile communications (6G), and other fields". There is **no** mention of physics, fusion, aerospace or propulsion.
- Security content: "enhance the ability to apply AI in maintaining and shaping national security", AI-enabled cyberspace governance, and public-security early warning. "Air-space-ground-sea dynamic perception" appears only under **ecological governance and spatial planning**. Military applications are not discussed in this civilian document.

**NSCAI Final Report (1 Mar 2021) [R]:** framed around "defend[ing] and compet[ing] in the coming era of AI-accelerated competition and conflict". Part I, "Defending America in the AI Era", covers AI-enabled threats, future warfare and autonomous weapons. — [HFES summary](https://www.hfes.org/About/Latest-News/national-security-commission-on-artificial-intelligence-nscai-releases-final-report-and-recommendations); [Black Vault archive](https://www.theblackvault.com/documentarchive/final-report-of-the-national-security-commission-on-artificial-intelligence-march-2021/)

### Inferences
- In both countries' flagship documents, AI-for-science is one pillar among many and is expressed generically: platforms, datasets, labs. The weight falls on economic diffusion (China), and on ecosystem dominance, exports, compute, energy and military adoption (US).
- Fusion features in US documents mainly as an energy source for AI and as a Genesis science domain, not as a propulsion route.
- **The thesis "the AI race is about propulsion physics" has no support in official public strategy.** At most, propulsion-relevant work (hypersonics, materials, plasma control) is a minor sub-case inside defence modernisation and "critical materials", which matches the counterargument. If such a motive exists, it would sit in classified programmes and military doctrine, which this public-source review cannot see.

### Gaps
- I did not read China's 2017 New Generation AI Development Plan this session. From memory [M], it emphasises economic leadership by 2030 and military-civil fusion. It should be checked against the CSET or DigiChina translation.
- I did not read the NSCAI final report's text for any mention of hypersonics or directed energy.
- PLA writings on "intelligentized warfare" were not examined. They would be the place where any propulsion or weapons-physics rationale would appear.
- DARPA and DOE FASST documents were not reviewed (see the previous section).
