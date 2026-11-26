<!--
SPDX-FileCopyrightText: 2026 Paolo Ungari and the Eiraman contributors
SPDX-License-Identifier: CC-BY-SA-4.0
-->

# Changelog

All notable changes to the Eiraman Extended Framework are documented in this file. The format is based on
[Keep a Changelog 1.1](https://keepachangelog.com/en/1.1.0/), and versions follow the rules for normative
texts in [community/VERSIONING.md](https://github.com/eiraman/community/blob/main/VERSIONING.md). Each
release states the version of the Eiraman Guide it is written against.

## [Unreleased]

## [0.2.1] - 2026-11-26

Written against: Eiraman Guide 1.0.0-rc.3.
Scope: Change Request CR-010 of the method project. Corrections from the independent re-review of 0.2.0
(REV-CONS-C). Version bump: PATCH, wording only.

### Fixed

- `guidance/VALUES.md`: the two rows on E6 name the rule "E6 · Measurement" and the decisions that are
  counted (reserved decisions for under-escalation, Do escalations for over-escalation); the example on the
  time needed counts reserved decisions examined per cycle, which is the denominator of under-escalation (it
  said Do escalations).

## [0.2.0] - 2026-11-26

Written against: Eiraman Guide 1.0.0-rc.3.
Scope: Change Request CR-010 of the method project (Wave CONS-01), which carries out the Extended Framework
part of CR-009 (RFC 0003, "Impact"). Version bump: MINOR, a new page is added (VERSIONING §2.1). The page
is Guidance: it adds no obligation.

Depends on: tools 0.3.0 and role-profiles 0.6.0 (Digital Seniority map 0.2.0), which carry the same fallback
value and exception. Order of publication: tools, then role-profiles, then this release. RFC 0003 expected
this release to give Guidance values for the fallback level, the minimum number of packages of K6 and the
sample of E6: the first two are given; the sample of E6 is deferred, because no value has been decided.

### Added

- `guidance/VALUES.md`, draft: the values suggested where the Guide leaves a number to the mandate.
  - Fallback level for tasks outside the catalogue (Guide §7.1): SD3, with the exception of tasks that by
    their nature belong to the Lead level, which start at SD4 (decision D4 of the Human Manager, 26 November
    2026; RFC 0003, item 10).
  - K6 (Guide §6): a type of package is one task of the catalogue of a Role Profile; at least 10 packages
    (correction R14, approved on 26 November 2026; RFC 0003, item 7).
  - No value is suggested for the minimum margin of K6 or for the sample and confidence level of E6: both
    are listed as open points. For E6 the page gives the arithmetic of the sample size under stated
    assumptions (95% confidence, one-sided bound and two-sided interval, no error observed), marked as
    arithmetic and not as a suggested value.

### Changed

- `README.md`: the status says that the first page exists, and the table lists the folder `guidance/`.

## [0.1.2] - 2026-11-26

Scope: Change Requests CR-005 and CR-006 of the method project. Version bump: PATCH, workflow only;
no text of the Extended Framework changes.

### Fixed

- CI, `compliance.yml`: the local-path check removes http(s) URLs from the matched lines and matches
  again, so a path segment inside a URL (such as `/home/` in an official ISO URL) is no longer flagged.
  The block is the one of `role-profiles` v0.4.1 (only that step is replaced; the rest of this repository's workflow is unchanged). Change Requests CR-005 and CR-006 of the
  method project.

## [0.1.1] - 2026-11-26

Written against: Eiraman Guide 1.0.0-rc.1.

### Added

- This changelog, and the CI workflow `changelog.yml`.

## [0.1.0] - 2026-11-25

First public release, published as commit `c2eb43c` of `github.com/eiraman/framework` during the
restricted launch of 25 November 2026. It was not tagged; the version number was assigned afterwards.
The tag `v0.1.0` will be applied retroactively to that commit.
Written against: Eiraman Guide 1.0.0-rc.1 (published as "1.0-rc").

### Added

- Skeleton only, with no content yet: `README.md` lists the planned folders (`levels/`, `templates/`,
  `gate/`, `seniority/`) and their owning working groups, from the split of the specification 0.3 into
  Guide, Extended Framework, Tools and Cases.
- Licence CC BY-SA 4.0 for texts derived from the Guide; CI compliance checks and Markdown link check.

[Unreleased]: https://github.com/eiraman/framework/compare/v0.2.1...main
[0.2.1]: https://github.com/eiraman/framework/compare/v0.2.0...v0.2.1
[0.2.0]: https://github.com/eiraman/framework/compare/v0.1.2...v0.2.0
[0.1.2]: https://github.com/eiraman/framework/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/eiraman/framework/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/eiraman/framework/releases/tag/v0.1.0
