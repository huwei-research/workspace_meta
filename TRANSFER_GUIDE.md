# Manual Transfer Guide

This guide complements Git synchronization. It covers private documents,
ignored research outputs, local archives, experimental packages, and user
skills that are intentionally outside normal repository cloning.

## What is synchronized by Git

`workspace-repos.json` is the current repository and branch registry. It now includes the workspace and all 29 project repositories. Clone only the registered branches; a clean Git checkout does not include ignored local evidence or private delivery assets.

Current research rules and eight skills are maintained in the private `research_harness` repository; use its deployment guide. The old `math-paper-writer` and `research-orchestrator` entries remain retired. The private `weihu-resume-writer` source belongs to `Personal/weihu_resume`.

## What requires a trusted drive

- `Personal/PrivateDocuments/`
- `Personal/AIContext/`
- `Personal/SkillBackups/`
- `Archive/`
- ignored data and results in `Experimental/metricized_muon_p0/`
- ignored data, weights, results, and notes in `Experimental/jev_feasibility/`
- ignored workbooks, archives, results, and private deliverables in `Experimental/railway_maintenance/`
- ignored raw or expensive-to-regenerate outputs inside managed repositories
- optional external Lean toolchains and checkouts under
  `Experimental/lean-libraries/`
- user-installed skills from `%USERPROFILE%\.codex\skills`, excluding the
  version-managed `.system` directory

Do not copy Codex authentication files, browser sessions, or plugin credentials.
Reauthenticate plugins and connectors on the destination computer.

## Recommended exact-drive transfer

Generate a path inventory first:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File ./inventory_transfer.ps1 -IncludeGitMetadata
```

Copy everything, including repository metadata and rebuildable environments:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File ./export_workspace.ps1 `
  -Destination 'E:\CodexTransfer' -Mode Exact
```

One ignored pytest cache at `Research/memotro/codes/.pytest_cache` has an
inherited ACL that denies the current user access. Both inventory and export
skip this rebuildable cache; it contains no project source or research result.

For a smaller but still usable workspace, omit virtual environments, package
caches, Lean build directories, and Python caches:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File ./export_workspace.ps1 `
  -Destination 'E:\CodexTransfer' -Mode Portable
```

Both modes retain Git metadata. `Portable` may need dependency and LFS restores
before experiments run.

The read-only size probe on 2026-07-14 reported approximately 38.21 GB for
`Exact` and 31.82 GB for `Portable`; both already include the dated 108.4 MB
skill snapshot under `Personal/SkillBackups/`. Add `-IncludeGlobalSkills` only
when a second, live copy under `CodexProfile/user-skills` is useful. Allow at
least 50 GB of free space; a 64 GB or larger encrypted drive is recommended.

## Verify the drive copy

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File ./verify_transfer.ps1 `
  -Destination 'E:\CodexTransfer' -Mode Exact
```

Use the same mode for export and verification.

## Restore on another computer

1. Copy `E:\CodexTransfer\2026Projects` to the intended local path.
2. Run `setup.ps1 -SkipVenv`; existing repositories will be checked rather than
   cloned again.
3. Run `sync_all.ps1 -Action Status`.
4. Restore user skills:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File ./restore_codex_skills.ps1 `
  -BackupPath 'E:\CodexTransfer\2026Projects\Personal\SkillBackups\2026-07-14\user-skills'
```

If `-IncludeGlobalSkills` was used during export, the alternative restore path
is `E:\CodexTransfer\CodexProfile\user-skills`.

5. Reinstall plugins through Codex and sign in again where required.
6. Rebuild omitted environments when `Portable` mode was used.

Never delete the source copy until `verify_transfer.ps1` succeeds and several
important private PDFs and research outputs open correctly on the destination.
