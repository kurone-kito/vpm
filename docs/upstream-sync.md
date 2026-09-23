# Upstream template sync

This repository was created from the GitHub template
[`vrchat-community/template-package-listing`](https://github.com/vrchat-community/template-package-listing)
on 2024-02-01. Because it is a template instantiation and not a fork,
there is no `parent` remote and no upstream lineage recorded anywhere
in git history — this document is that record.

## Last synced upstream commit

`0c6013555c9566a1658320e5495576f48a4424a0` (2026-09-01).

## Diff procedure

```bash
git remote add upstream https://github.com/vrchat-community/template-package-listing.git
git fetch upstream
git log f249c6fda149e593b1c29c2d01264bed04a8008f..upstream/main
```

Update the "Last synced upstream commit" section above once the
resulting commits have been triaged (imported, or recorded below as
already-covered / not applicable).

## Deliberately diverged surfaces

A sync should never try to revert these; they are intentional,
permanent differences from the upstream template:

- `README.md` — fully rewritten for this repository.
- `.github/workflows/*` — split into `build-common.yml`,
  `build-listing.yml`, and `build-on-push.yml` with an artifact
  hand-off, instead of upstream's single workflow.
- `Website/*` — Prettier formatting, OGP meta tags, and the banner
  image implementation are local additions.
- `source.json` — this repository's package listing data, never
  upstream content.

## Upstream commits already resolved

Commits between the previous sync and `f249c6fda149e593b1c29c2d01264bed04a8008f`
that needed no import, so they should not be re-evaluated on the next
sync:

- `1dd2a82` (2026-06-30, "Pin @fluentui/web-components CDN imports to
  v2.6.1") — imported by this change.
- `3e54dd1` (GitHub Actions version bumps) — already covered
  independently by this repository's own workflow refactor
  (`build-common.yml` / `build-listing.yml` already use
  `actions/checkout@v4`, `actions/cache@v4`, `actions/configure-pages@v5`,
  `actions/upload-pages-artifact@v3`, and `actions/deploy-pages@v4`).
- `064c066` (`packageInfoVccUrlField` should be `{{ listingInfo.Url }}`)
  — already applied; see `Website/index.html`.
- `83a6950` and `3f6f64a` (upstream README link polish) — not
  applicable; this repository's `README.md` is fully rewritten.
- `d218b20` (set head title to use the listing name) and `592db45`
  (add favicon link to `index.html`), merged as `0c60135` — imported by
  this change.

## Automated drift detection

`.github/workflows/upstream-drift.yml` checks this file's recorded
commit against the upstream default branch on a monthly schedule (and
on demand via `workflow_dispatch`) and files an issue when upstream has
moved. It only reads the repository and writes issues — it never
pushes a commit or edits this file. Advancing the "Last synced upstream
commit" section above is always a reviewed, manual outcome of actually
importing the change it flags.
