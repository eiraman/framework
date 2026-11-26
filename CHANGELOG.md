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

[Unreleased]: https://github.com/eiraman/framework/compare/v0.1.2...main
[0.1.2]: https://github.com/eiraman/framework/compare/v0.1.1...v0.1.2
[0.1.1]: https://github.com/eiraman/framework/compare/v0.1.0...v0.1.1
[0.1.0]: https://github.com/eiraman/framework/releases/tag/v0.1.0
