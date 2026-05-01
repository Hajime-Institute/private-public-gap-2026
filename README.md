# Private–Public Gap (CogSci 2026)

Companion repository for the paper:

> **Hotta, H. & Nguyen, M. T.** (2026).
> *From Private Beliefs to Public Silence: A Multi-Agent LLM Simulation
> of Psychological Safety.*
> Annual Meeting of the Cognitive Science Society (CogSci 2026).

This repository holds the full prompt templates and lexical audit
referenced in the paper, so reviewers and readers can reproduce, audit,
or build on the simulation without having to reverse-engineer it from
the manuscript text.

---

## Why this repo exists

A central methodological commitment of the paper is the
**Non-Circular Prompting Protocol**: agents are prompted with universal
psychological principles (impression management, interpersonal risk,
trust) rather than with the target outcome. To make that claim auditable
we publish every prompt verbatim. If a reader believes a prompt encodes
the result we report, they can show *which sentence* and *how*; we treat
that openness as part of the contribution.

---

## Repository layout

```
private-public-gap-2026/
├── README.md                       ← you are here
└── prompts/
    ├── 01_private_belief.md        ← AGENT_INTERNAL_UPDATE
    ├── 02_public_statement.md      ← AGENT_SAFETY_FILTER_MAIN  (core mechanism)
    ├── 03_phase_judges.md          ← PHASE_TRANSITION_CHECK + PHASE_VIOLATION_CHECK
    ├── 04_consensus_judges.md      ← CONSENSUS_CHECK + OBSERVER_CONSENSUS_QUALITY
    └── 05_intervention.md          ← INTERVENTION_GENERATION (optional, not used in main results)
```

Each `prompts/*.md` file gives the prompt verbatim, the input variables
it expects, and a short explanation of where it sits in the simulation
pipeline.

---

## How prompts map to the paper

| Paper section | Prompt(s) used | What it produces |
|---|---|---|
| Dual-Process Agent Design (Fig. 1) | `01_private_belief.md` | Private Belief — what the agent thinks |
| Cognitive Process Tracing (Fig. 1, four steps) | `02_public_statement.md` | Public Statement + self-classified disclosure level |
| Discussion Protocol (Fig. 2 — three phases) | `03_phase_judges.md` | Phase pacing decisions (controller-level only) |
| Measurement / Consensus Turn | `04_consensus_judges.md` | When the team reached agreement, and whether that agreement was genuine |
| Active observer (extension, not in main results) | `05_intervention.md` | Intervention message when fake consensus is detected |

The reversal experiment reported in §"Non-Circular Design" varies the
framing inside `02_public_statement.md`; every other prompt is held
constant.

---

## Reproducing the main numbers

The paper reports four numerical anchors that depend directly on these
prompts:

- **Trust–disclosure correlation** *r = +0.51* (n = 210 teams,
  GPT-5-mini)
- **Reversal-frame correlation** *r = −0.26* (n = 90 teams)
- **Faction-trust observation bias**:
  ~44 → ~5 hidden items as inter-faction trust moves 1 → 5 (n = 540
  teams)
- **Within-topic correlations** *r = +0.41 to +0.63* across the ten
  scenario archetypes

If you re-run the prompts in this repo against a current frontier model
and obtain a meaningfully different sign or magnitude, please open an
issue — that is exactly the kind of finding we would want to know about.

---

## Citation

```bibtex
@inproceedings{Hotta2026PrivatePublicGap,
  author    = {Hajime Hotta and Minh Tien Nguyen},
  title     = {From Private Beliefs to Public Silence:
               A Multi-Agent {LLM} Simulation of Psychological Safety},
  booktitle = {Proceedings of the 48th Annual Meeting of the Cognitive
               Science Society (CogSci 2026)},
  year      = {2026}
}
```

---

## License

Prompts and documentation in this repository are released under the
MIT License.

---

## Contact

- Hajime Hotta — `hotta@hajime.institute` (Hajime Institute, Singapore)
- Minh Tien Nguyen — `tiennm@utehy.edu.vn` (NLU Lab, Hung Yen
  University of Technology and Education, Vietnam)
