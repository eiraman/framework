<!--
SPDX-FileCopyrightText: 2026 Paolo Ungari and the Eiraman contributors
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Guidance values

Written against: Eiraman Guide 1.0.0-rc.5. Status: **draft**, proposed by the Steward until the working
groups that own these values are formed.

The Guide states no numbers: where a rule needs a value, the mandate of each project sets it. This page
gives the values the maintainers suggest as a starting point. They are **Guidance**, not obligations: a
mandate may set different values, and a project conforms to the Guide whatever value its mandate sets. Each
row names the rule of the Guide, the suggested value and the decision it comes from.

## Values

| Rule of the Guide | What the mandate sets | Suggested value | Source |
|---|---|---|---|
| §7.1, Fallback | The Digital Seniority level at which a task outside the catalogue runs | **SD3**. Exception: a task that by its nature belongs to the Lead level (architecture, security, effects hard to undo) starts at **SD4** | Decision D4 of the Human Manager on the critical review of specification 0.3, 26 November 2026; RFC 0003, item 10 |
| §6, K6, type of package | What counts as a type of package when the competitive mechanism is compared with a single executor | One task of the catalogue of a Role Profile | Correction R14, approved by the Human Manager on 26 November 2026; RFC 0003, item 7 |
| §6, K6, minimum number of packages | How many packages of a type are needed before the comparison counts | At least **10** | As above |
| §6, K6, minimum margin | The margin over a single executor below which the type returns to a single executor | No suggested value yet | — |
| §5, E6 Measurement, sample size | How many decisions the process reviewer examines: reserved decisions for under-escalation, Do escalations for over-escalation | No suggested value yet; see the note below | — |
| §5, E6 Measurement, confidence level | The confidence level of the interval the process reviewer reports | No suggested value yet; see the note below | — |

The same fallback value and exception are in the Digital Seniority map of the Role Profile registry
(`_seniority/seniority.json`, fields `fallback`, `fallback_indicativo` and `fallback_eccezione`), from which
the tools generate the task catalogue of every profile. The fixed SD4 fallback of the early releases of the
registry is superseded. The Guide adds, as a rule and not as Guidance, that a task outside the catalogue is
raised to the next level at its first failure for lack of capability (§7.1, "Promotion and reduction").

## Note on the sample for E6

The Guide requires under-escalation and over-escalation to be reported as estimates, with the number of
decisions examined and their confidence interval, and counts a threshold as met only if the unfavourable
bound of the interval stays within it (§5, E6). It does not set the confidence level, and no value has been
decided for it.

The figures below are arithmetic, not a suggested value. They assume that no error is found in the sample
and that the decisions examined are independent. The number of decisions depends on how the interval is
built, which the Guide does not say either:

| Threshold to demonstrate | One-sided bound at 95% | Two-sided interval at 95% |
|---|---|---|
| Below 10% | 29 decisions (about 30) | 36 decisions (about 37) |
| Below 5% | 59 decisions (about 60) | 72 decisions (about 74) |

The exact numbers come from the binomial distribution; the rounded ones from the approximations 3/n and
3.7/n. With errors in the sample, or at a higher confidence level, more decisions are needed. As an example,
a project in which three reserved decisions per governance cycle are examined would need
about ten cycles to show a rate below 10% with the one-sided bound: the evidence for level 1 (Guide §14.1)
takes that long to collect.

## Indicative values of specification 0.3

Specification 0.3, now historical, marked some values as "Indicazione" (a recommended value that the
mandate may change) and gave other figures without the mark. The Guide keeps the mechanism and leaves the
value to the mandate (§0, "Values and Guidance"); the values are carried here as Guidance, with the section
of the Guide that governs the mechanism and the section of specification 0.3 they come from. Each value has
its own heading, so that other pages can link to it. A mandate may set a different value.

### Deadlines of a Do

- **Ordinary Do:** 3 working days for the Human Manager to answer, then a reminder, then another 3 working
  days.
- **Urgent Do:** 4 hours.

Mechanism: Guide §5, "Silence never approves a Do" (reminder at the deadline, the package leaves the Wave
when the reminder's deadline also passes) and "Urgent containment" (the mandate sets the deadlines).
Source: specification 0.3 §3, marked "Indicazione".

### Wave spending thresholds

- **Early warning:** at **80%** of the Wave spending cap the AI Coordinator flags the Wave.
- **Deny on new work:** at **100%** of the cap the environment denies new work and the Wave closes with a
  checkpoint.

Mechanism: Guide §8, "Wave" (the mandate sets both thresholds; the cap and the maximum duration apply
whichever is reached first). Source: specification 0.3 §5, not marked "Indicazione" but stated as a figure.

### Cadence of the governance cycle

**Weekly.** Mechanism: Guide §8, "Governance cycle" and "Declared and observed values" (the mandate sets
cadence and reference values; a declared value changes only at a cycle review). Source: specification 0.3
§5, marked "Indicazione".

### Reference for the escalation load

**3 ordinary Do escalations (and K9 escalations) per cycle.** Mechanism: Guide §8, "Escalation load" (urgent Do escalations and
decisions planned by the phases are not counted; the indicator never blocks a due Do) and "Declared and
observed values". Source: specification 0.3 §5, marked "Indicazione".

### Attention of the Human Manager

**About 30 minutes a week.** A reference for the attention the Human Manager gives to the project, to be
declared in the mandate and shown next to the observed value in the cycle review. Mechanism: Guide §8,
"Declared and observed values" (the mandate sets cadence and reference values). The Guide has no rule that
measures reading minutes: the measure of specification 0.3 §8 ("Misura") has no counterpart in the Guide, so
the observed value is whatever the project records. Source: specification 0.3 §5, marked "Indicazione".

### Number of candidates (K3)

**One candidate by default; 2 to 3 for generative packages of high variability or with a costly error**,
within the spending cap. Mechanism: Guide §6, "K3 · Number of candidates" (the mandate sets the default).
Source: specification 0.3 §4, K3.

### Calibration sample of E6

**About 20 autonomous decisions**, reviewed once by the Human Manager in the first project of every new
adoption, to calibrate the process reviewer. It is not the sample of the measurement (see the note on E6
below, which has no suggested value). Mechanism: Guide §5, "E6 · Calibration" (the mandate sets the sample
size). Source: specification 0.3 §3, E6. Specification 0.3 tied the review also to the NUR pilot; the Guide
keeps the first project of every new adoption.

### Attempts before promotion

**Two failed attempts** for lack of capability before the AI Coordinator raises the agent to the next
Digital Seniority level. Mechanism: Guide §7.1, "Promotion and reduction" (the mandate sets the number; the
attempts allowed by the Work Package record, §9, still apply). Source: specification 0.3 §4 bis.

### Calibration set of the comprehension test

**About 5 documents**, on which the Human Manager calibrates once the agent that tests each document for
comprehension. Mechanism: Guide §12, "Comprehension test" (the mandate sets the size of the set). Source:
specification 0.3 §8.

### Not carried

- The fixed SD4 fallback of specification 0.3 (§4 bis) is not carried: it conflicts with the fallback value
  above (SD3, decision D4), which supersedes it.
- "For security and personal data, at least a different model" (specification 0.3 §4, marked "Indicazione")
  is not a value of the mandate any more: the Guide states it as a SHOULD (recording is a MUST) (§6, "Security and personal data").

## Local engine

The Guide lets the mandate decide which local engines run the agents of a project (§14, "Local engines in
the informative mode") and allows a local model without retrieval as hard blinding (§7, "Hard blinding").
The Role Profile registry declares one local engine, Gemma 4 (dense version, 31 billion parameters, open
weights, run on the device), with status **to be qualified**: no task has passed qualification yet, and
until it does, the engine is not used for that task and the fallback applies. The engine is not a Digital
Seniority level: each task carries in the catalogue of its profile the level of its fallback. The rules are
in the registry (`_seniority/MOTORE-LOCALE.md`, declaration in `_seniority/motori-locali.json`, both
drafts).

The registry gives, for each task, a **maximum length of input**, counted with a deterministic tool and
not by the model. The values are indicative and still to be calibrated; a longer text is split into parts
that respect the limit, or the task goes back to the fallback.

| Task (profile) | Maximum input |
|---|---|
| Check of the message before it goes to the Human Manager (AI Coordinator) | 1,500 words |
| Comparison of the original risk profile with the business-language version (AI Coordinator) | 3,000 words per pair of points |
| Summaries of the registers for the Human Manager's view (AI Coordinator) | 2,000 words of register per summary |
| Reading of real files for the checklist, T11 (Security Officer) | 3,000 words or 200 rows per part |
| Check of residues after masking, T12 (Security Officer) | 3,000 words or 200 rows per part |
| Needs, answers and observations on a mock-up in Discovery, T01-T03 (User Persona) | 4,000 words |

The qualification threshold of each task is "to be set before the test": there is no suggested value.
Source: role-profiles registry, `_seniority/motori-locali.json` 0.1.0 in registry v0.10.0.

## Open points

- The minimum margin of K6, and the sample size and confidence level of E6, have no suggested value. Until
  they have one, each mandate sets its own.
- The qualification thresholds of the local engine, and the maximum input of each of its tasks, have no
  tested value yet.
- The values on this page have not been tested on real projects. The share of tasks run outside the
  catalogue, which the Guide requires in every cycle review (§7.1, §8), is the evidence for revising the
  fallback value.
