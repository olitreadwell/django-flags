# cfpb/django-flags context
> refreshed 2026-09-05 | upstream default: main @ d5362bb8ee1fab45d12e925c1a7350f01d848e37

## Identity & policies
- upstream: cfpb/django-flags, default branch main, primary language Python, English-first yes
- CLA/DCO: none (CC0 public-domain dedication in CONTRIBUTING/TERMS; no CLA bot, no DCO)
- AI-assisted PR policy: unstated (no AI ban/disclosure in repo or org cfpb/.github)
- signed commits required: no
- PR template: none (repo has no PULL_REQUEST_TEMPLATE; org cfpb/.github has none either) -> fallback 3-section body
- external tracker: github

## Conventions (verified from merged PRs)
- branch naming: mixed; dominant `fix/...`, `docs/...`, `feature/...`, `chore/...`; fall back to `type/desc`
- commit style: plain imperative / conventional-ish ("Pin our GitHub actions...", "docs: Update django & python version...")
- test command: `DJANGO_SETTINGS_MODULE=flags.tests.settings django-admin test` (tox envs: python3.10/3.13-django4.2, 3.12/3.13-django5.2, 3.12/3.13-django6.0)
- lint command: `ruff format --check`, `ruff check flags`, `bandit -c pyproject.toml -r flags` (tox -e lint)
- CI: GitHub Actions test.yml (tox matrix), docs.yml, release.yml
- how outside PRs get merged: responsive; recent external merges (bengerman13, chosak, sergei-maertens, andy-isoc, fourfridays, dancergraham, dimaqq, adamchainz)

## Maintainer picture
- active maintainers: willbarton (primary), chosak; responsive to external PRs
- areas actively worked: packaging/tooling, Django/Python version support, docs

## Issue-area health
- 12 open issues, none labelled (no good-first-issue/help-wanted labels)
- #96 "Setting user based flag conditions prevents migrations running on a fresh database" - open, unassigned, maintainer willbarton confirmed bug ("we should be handling model errors in the checks better than we are"), cristobalmackenzie proposed fix approach (catch ProgrammingError in validate_user), gudmundurp asked for status 2025-08-18 (no response). Real, verifiable bug.

## Gap ledger (dedupe — READ FIRST, never re-pick)
- `2026-09-05` issue #96 — outcome: pr-opened (https://github.com/olitreadwell/django-flags/pull/1) — validate_user crashed with raw OperationalError/ProgrammingError when user table missing during migrate; fixed by catching DB errors and raising ValidationError; check now reports flags.E002 warning instead of crashing. Verified: 181 tests pass, ruff/bandit clean.

## Mined gaps (discovered, not yet attempted)
- none
