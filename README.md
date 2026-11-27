<!--
SPDX-FileCopyrightText: 2026 Paolo Ungari and the Eiraman contributors
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Eiraman extended framework

Status: **skeleton with first content**. The first pages are [guidance/VALUES.md](guidance/VALUES.md), the
values the maintainers suggest where the Guide leaves a number to the mandate, and
[guidance/BENCH.md](guidance/BENCH.md), the Guidance for the test bench (draft, not measured). The folders
below are still planned.

The extended framework holds what the Eiraman Guide deliberately leaves out of its stable core:
practices and worked guidance that change faster than the Guide, owned by the working groups.

Planned content, from the split of specification 0.3 into Guide, extended framework, tools and cases:

| Folder | Content | Owner (working group) |
|---|---|---|
| `levels/` | Applicability levels 0–2 in detail: requirements, evidence, step-up and automatic step-down | Security, with Privacy and Legal & Compliance |
| `templates/` | Document templates used by Waves and Work Packages | Owning working group |
| `gate/` | The gate checklist and its exclusion criteria | Legal & Compliance, with Privacy |
| `seniority/` | The Digital Seniority map explained for each tool, and the local engine (Gemma 4, to be qualified) next to the cloud engines | DevSecOps & Tooling |
| `guidance/` | **Draft:** the suggested values for the rules whose value the mandate sets (`VALUES.md`) and the Guidance for the test bench: baseline, pilots, indicators, repetitions, limits (`BENCH.md`) | Steward, until the owning working groups are formed |

The Guide is in the [`guide`](https://github.com/eiraman/guide) repository and decides in case of
conflict. Changes that would alter the Guide need a Guide RFC (GOVERNANCE §2).

## Licence

CC BY-SA 4.0 for texts derived from the Guide ([LICENSE.md](LICENSE.md)); licence per file in its SPDX
header or in `REUSE.toml`. Contributions need a DCO sign-off on every commit.
