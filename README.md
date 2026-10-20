# ai-lab-notes

Open notes from a series of experiments in running a real drug-discovery campaign with a bounded
virtual lab of AI scientists, supervised by a single human, on
[PlayMolecule AI](https://www.playmolecule.com).

**Research question:** can one human supervisor operate a bounded lab of AI scientists and
obtain useful, traceable work on a real molecular discovery program?

The experiment tests scientific usefulness, evidence quality, failure behaviour, escalation,
human intervention, compute use, and prospective decision value. It does **not** assume that
AI scientists are faster, more accurate, more autonomous, or better than a human team.

The target program is IL23R-p19 for psoriasis, an existing Acellera internal program. The
official program continues independently under its own scientific leadership; this repository
is a separate computational experiment and cannot authorize synthesis, assays, or program
decisions.

## Repository layout

| Path | Contents |
| --- | --- |
| [experiment-0/](experiment-0/) | Exploratory starting artifacts — seven IL23R-p19 target assessments and their comparison |
| [experiment-1/](experiment-1/) | First full AI-Lab campaign — autonomous agent team run at the IL23R-p19 interface, written up as a manuscript |
| [LICENSE](LICENSE) | MIT |

## experiment-0 — seven reports from one prompt

Seven systems were given the [same prompt](experiment-0/PROMPT.md): produce a validated,
publicly-sourced report on IL23R with structural information, small-molecule discovery
strategies, and a preclinical TPP for a small-molecule inhibitor of the IL23R-p19 interaction
in psoriasis.

The outputs were scored blind against a ten-criterion rubric (five TPP, five strategy, 0–4
each) with targeted primary-source, structural, and numerical checks. Full scoring, rubric,
and audit: [IL23R_report_comparison_named.pdf](experiment-0/IL23R_report_comparison_named.pdf).

| Report | System | TPP /20 | Strategy /20 | Total /40 |
| --- | --- | --- | --- | --- |
| [report_3693.pdf](experiment-0/report_3693.pdf) | PlayMolecule AI on Astra-high | 18 | 19 | 37 |
| [report_b577.pdf](experiment-0/report_b577.pdf) | ChatGPT 6 Astra-high | 18 | 18 | 36 |
| [report_68bd.pdf](experiment-0/report_68bd.pdf) | ChatGPT 5.6-Sol-ultra | 15 | 16 | 31 |
| [report_edea.pdf](experiment-0/report_edea.pdf) | Claude-Opus5-extra | 10 | 12 | 22 |
| [report_cbe0.pdf](experiment-0/report_cbe0.pdf) | PlayMolecule AI on Gemini-3.8-flash | 8 | 9 | 17 |
| [report_327e.pdf](experiment-0/report_327e.pdf) | PlayMolecule AI on GLM5.3-flash | 7 | 10 | 17 |
| [report_750e.pdf](experiment-0/report_750e.pdf) | PlayMolecule AI on Qwen3.8-27B, local, RTX 5090 | 5 | 6 | 11 |

[deck_750e.pdf](experiment-0/deck_750e.pdf) is the slide version of report_750e.
[models.md](experiment-0/models.md) is the code-to-system key used during blind scoring.

### What the comparison found

- The **PlayMolecule AI on Astra-high** report gives the strongest starting experimental
  framework; **ChatGPT 6 Astra-high** gives the strongest dose-feasibility analysis.
- Recurring weaknesses across systems: unsupported binding-to-inhibition assumptions, and
  disconnected potency, exposure, and dose targets.
- The evidence supports a *gated* feasibility campaign — reproducible binding to native
  interaction blockade, to selective human-cell activity, to achievable unbound skin exposure.
- Safety and mechanism errors can override an attractive total score. Two reports contain
  mechanism errors that must be repaired before their experimental instructions are reused.

### How to read the scores

Scores are editorial judgments under the rubric, **not** measurements of success probability.
Differences of one or two points are not meaningful; the tier separation is more robust than
the exact totals. Scores assess the supplied reports as decision documents, not the underlying
LLMs or harnesses — inputs, tools, context, and execution conditions differ materially between
systems and are not controlled.

These are proposed starting points, not results or accepted program decisions. They were not
preregistered and cannot be described as such.

## experiment-1 — one campaign run by a bounded lab of AI scientists

Where experiment-0 compared single reports, experiment-1 let a team of agents actually run a
campaign. The write-up is
[il23_full_project_report.pdf](experiment-1/il23_full_project_report.pdf) (21 pages).

**Setup.** A short goal-based prompt (kept in an `AGENTS.md` that drifted during the run) asked
the team to engineer the best small molecules against a preclinical TPP and to keep working
until stopped. A frontend agent created the other agents and handled all communication; the
independent agents picked their own next steps and tested their own ideas. Shared memory was a
linked HTML wiki the agents maintained themselves. Budget: 4 GPUs, 10 concurrent agents.
Total consumption: ~7 billion tokens.

**Supervision.** The human supervisor read the wiki and asked the frontend to display the
leading molecules with their supporting evidence — very little guidance on individual
calculations, and only two decisions retained: when to stop, and which compounds to review for
purchase.

**What the lab did.** Two binding sites were pursued — the peptide-induced pocket on p19
(from 8UUI) and the receptor contact surface (from 6WDQ). Across two phases the agents built
and curated libraries (~2.4k records), designed analogues and grafted fragments, docked at both
sites, ran repeated molecular dynamics, and attempted relative binding free energies. Candidates
had to stay in their pose across repeat runs *and* occupy space the natural partner needs.

**Outcome.** Three pocket candidates (W5_004, PS2B_013, W5_003) held their poses across
3 × 40 ns runs each and became priorities 1–3; two receptor-side compounds (C_0918,
CONT_CAT_R013) were added as exploratory probes of a different mechanism. PS_010 is the
reserve. No compound passed the combined contact-plus-overlap test, so the proposed experiments
measure binding and interference with complex formation **separately**.

### What this run actually shows

- **Nothing was measured.** There are no binding, inhibition, or cell data for any prioritized
  compound, and no verified physical material. The output is a testable panel, not a result.
- **The failures are the content.** A unit error comparing nm distances against Å cutoffs, a
  selectivity rule that passed every compound, docking labels assigned to the wrong molecules,
  and a stale summary reporting failures for runs that had since completed — each one changed
  what the results supported, and each was caught by review rather than by the agent that made it.
- **Three practices carried the campaign:** every result traceable to the exact molecule and
  prepared state behind it; analysis rules reviewed alongside the calculations they score; and
  progress checked against input files and real outputs, not against summaries.
- **No baseline.** There was no controlled comparison with a manual workflow and no complete
  GPU/CPU accounting, so this says nothing yet about time, cost, or success rate. The finding
  register (F01–F45, Appendix A) states the limits of each claim.

## Contact

Gianni De Fabritiis — g.defabritiis@acellera.com

## License

MIT — see [LICENSE](LICENSE).
