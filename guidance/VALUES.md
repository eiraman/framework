<!--
SPDX-FileCopyrightText: 2026 Paolo Ungari and the Eiraman contributors
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Guidance values

Written against: Eiraman Guide 1.0.0-rc.3. Status: **draft**, proposed by the Steward until the working
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
| §5, E6, sample | How many decisions the process reviewer examines, and at which confidence level | No suggested value yet; see the note below | — |

The same fallback value and exception are in the Digital Seniority map of the Role Profile registry
(`_seniority/seniority.json`, fields `fallback`, `fallback_indicativo` and `fallback_eccezione`), from which
the task catalogue of every profile is generated. The Guide adds, as a rule and not as Guidance, that a task
outside the catalogue is raised to the next level at its first failure for lack of capability (§7.1,
"Promotion and reduction").

## Note on the sample for E6

The Guide requires under-escalation and over-escalation to be reported as estimates, with the number of
decisions examined and their confidence interval, and counts a threshold as met only if the unfavourable
bound of the interval stays within it (§5, E6). It does not set the confidence level, and no value has been
decided for it.

The figures below are arithmetic, not a suggested value. They assume a confidence level of 95% and no
error observed in the sample, and use the approximation that the upper bound is three divided by the number
of decisions examined:

| Threshold to demonstrate | Decisions to examine, with no error found |
|---|---|
| Below 10% | About 30 |
| Below 5% | About 60 |

With errors in the sample, or at a higher confidence level, more decisions are needed. At a few Do
escalations per governance cycle, this means several cycles at level 0 before the evidence for level 1 can
be shown (Guide §14.1).

## Open points

- The minimum margin of K6 and the confidence level of E6 have no suggested value. Until they have one, each
  mandate sets them and records the reason.
- The values on this page have not been tested on real projects. The share of tasks run outside the
  catalogue, which the Guide requires in every cycle review (§7.1, §8), is the evidence for revising the
  fallback value.
