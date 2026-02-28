# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.2.0] - 2026-02-28

### Added

- **Relations** — full CRUD for relations between work packages via 4 new tools:
  `list_relations`, `create_relation`, `update_relation`, `delete_relation`.
  Supports all 11 relation types (`relates`, `blocks`, `precedes`, `follows`, etc.)
  with optional `description` and `lag`. ([#5], closes [#3])

- **Categories** — new `list_categories(project_id)` tool; `category_id` parameter
  added to `create_work_package` and `update_work_package`; category name and ID
  are now included in all work package responses. ([#11], closes [#10])

- **Test infrastructure** — `pytest` + `responses` (mocked HTTP, no live server needed),
  `pytest-cov`, 38 unit tests covering all tools, GitHub Actions CI workflow. ([#6], closes [#4])

- **`OpenProjectClient.delete()`** — new HTTP method on the base client, required by
  relation deletion.

### Fixed

- `list_work_packages` now accepts `status='*'` to include closed work packages
  (previously all statuses were sent as literal equality filters). ([#2], closes [#1])

- `update_work_package` now accepts `parent_id` to move a work package under a new
  parent; use `parent_id=0` to detach from the current parent. ([#8], closes [#13])

- `update_work_package` now accepts `start_date` (`YYYY-MM-DD`), consistent with
  `create_work_package` and `due_date`. ([#9], closes [#14])

### Changed

- GitHub Actions CI trigger restricted to pushes on `main` and `dev` branches only
  (previously triggered on all branches); manual dispatch (`workflow_dispatch`) added.

### Chore

- `CLAUDE.md` added to `.gitignore` — contributor-specific AI assistant context should
  not be committed. ([#7], closes [#12])

## [0.1.0] - 2026-02-27

### Added

- Initial release: `list_projects`, `get_project`, `list_work_packages`,
  `get_work_package`, `create_work_package`, `update_work_package`,
  `add_comment`, `get_comments`, `list_users`, `list_statuses`,
  `list_types`, `list_priorities`.

[Unreleased]: https://github.com/Aqueum/openproject-mcp/compare/v0.2.0...HEAD
[0.2.0]: https://github.com/Aqueum/openproject-mcp/compare/v0.1.0...v0.2.0
[0.1.0]: https://github.com/Aqueum/openproject-mcp/releases/tag/v0.1.0

[#2]: https://github.com/Aqueum/openproject-mcp/pull/2
[#5]: https://github.com/Aqueum/openproject-mcp/pull/5
[#6]: https://github.com/Aqueum/openproject-mcp/pull/6
[#7]: https://github.com/Aqueum/openproject-mcp/pull/7
[#8]: https://github.com/Aqueum/openproject-mcp/pull/8
[#9]: https://github.com/Aqueum/openproject-mcp/pull/9
[#11]: https://github.com/Aqueum/openproject-mcp/pull/11

[#1]: https://github.com/Aqueum/openproject-mcp/issues/1
[#3]: https://github.com/Aqueum/openproject-mcp/issues/3
[#4]: https://github.com/Aqueum/openproject-mcp/issues/4
[#10]: https://github.com/Aqueum/openproject-mcp/issues/10
[#12]: https://github.com/Aqueum/openproject-mcp/issues/12
[#13]: https://github.com/Aqueum/openproject-mcp/issues/13
[#14]: https://github.com/Aqueum/openproject-mcp/issues/14
