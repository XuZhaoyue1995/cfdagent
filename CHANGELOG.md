# Changelog

## 0.2.1 — 2026-10-07

- Replace the plugin icon with a closed fan outline without lettering.

## 0.2.0

First public release.

- One skill entry point (`cfdagent`) with nine references read on demand: solver selection, case setup, mesh quality, execution, result validation, benchmark library, post-processing and delivery, working notes, and plugin evaluation.
- A solver map covering 12 external solver families and PyIB, with guidance for recommending candidates and letting the user choose a single solver or a cross-solver comparison.
- Guidance on startup trial runs versus production runs: resource and time estimates, stopping criteria and monitoring.
- Completion judged against the user's goal and the evidence. Exported figures and reports are opened and checked for overflow, overlap, clipped text and illegibility before delivery.
- Manifests for Claude (`.claude-plugin/plugin.json`) and Codex (`.codex-plugin/plugin.json`) sharing one `skills/` folder.
