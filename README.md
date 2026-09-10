# ai-lab-notes

Open notes from an experiment in running a real drug-discovery campaign with a bounded
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

## Contact

Gianni De Fabritiis — g.defabritiis@acellera.com

## License

MIT — see [LICENSE](LICENSE).
