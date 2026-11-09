# infinitum-build-progress

Automated hourly snapshots of Infinitum Corporation product build and development progress.

## Purpose

This repository maintains a living record of the current development status across **all Infinitum products** (SCALVS.ai, :\ARCHITECT\, ODIN°, [HRVST], FabriC++, ei·det·ic, Cumulus, Firmament, VEIL, military editions, etc.).

- `PROGRESS.md` — current snapshot (updated hourly)
- `.github/workflows/hourly-progress.yml` — scheduled workflow that regenerates the snapshot

## Constraints

- **Never change anything on the website** (infinitum-corporation-site or live deployments) unless explicitly instructed.
- This repo only records progress; it does not modify product source code.

## Manual trigger

You can run the workflow manually from the Actions tab, or update PROGRESS.md directly.

Created: 2026-11-09
