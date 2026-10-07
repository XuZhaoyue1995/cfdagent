# CFDAgent

![CFDAgent](assets/logo.png)

A lightweight research companion for computational fluid dynamics (CFD) that works in Claude and Codex. Author: **Zhaoyue Xu**.

Affiliation: [Experimental Zoology Group, Wageningen University & Research (WUR)](https://www.wur.nl/en/chair-groups/experimental-zoology/contact), Netherlands.

CFDAgent adds on-demand CFD expertise to the agent's own conversation, coding and execution abilities: physical modeling and solver choice, case setup, computation, validation, post-processing and reproducible delivery. It is a single plugin that stays lightweight by default. How deep the computation goes depends on your task and the evidence already available.

## What you can ask

Once it is installed, just talk about your CFD problem. For example:

> I have a set of insect wing kinematics. Let's first discuss suitable computational methods, compare a few solvers, and then decide how to set up the case.

> Check the mesh in this directory. Tell me the problems you actually find and the evidence for each. Don't modify the mesh.

> Read the working notes and continue yesterday's case. Verify the current run status first.

> Check how these lift and pressure coefficients are defined, then judge what conclusions the existing mesh study can support.

You can also call the skill explicitly: `/cfdagent:cfdagent` in Claude Code, or `$cfdagent` in Codex.

## How it works

- **Discussion, recommendations and execution interleave freely.** A pure discussion gets a direct answer; nothing is set up unless the work needs it.
- **You choose the solver.** For a new case with no solver chosen yet, CFDAgent briefly compares suitable candidates: why each fits, what setup and computation would cost, and what validation evidence exists. You then pick one solver or a cross-solver comparison. If you have already chosen, or you say "you decide", it goes ahead directly.
- **Setup, runs and analysis can overlap.** The first steps check whether the setup and execution are feasible; startup transients alone are not treated as failure. Before a long production run, it states measured resource and time estimates, stopping criteria and a monitoring plan. Plans you have approved go ahead; significant new costs are discussed with you first.
- **"Done" is judged against your goal and the actual evidence.** Gaps that affect the goal are worked on within what you have authorized. Not every question is expanded into paper-level validation.
- **Working notes only when useful.** In a real project, CFDAgent keeps a working log, usually `CFD_WORKLOG.md`, and reuses existing notes.

## What's inside

The [skill entry point](skills/cfdagent/SKILL.md) reads only the references the current task needs. It does not load everything at once, and it does not turn the references into fixed workflow steps.

| When you need to | Reference used on demand |
| --- | --- |
| Discuss methods and choose a solver | [Solver map: 12 external solver families and PyIB](skills/cfdagent/references/solver-selection.md) |
| Set up physics, units and coordinates, case consistency and numerics | [Case setup](skills/cfdagent/references/case-setup.md) |
| Check volume meshes, high-order, IB, SPH, LBM or adaptive discretizations | [Mesh quality](skills/cfdagent/references/mesh-quality.md) |
| Record the environment; handle Slurm, resource estimates and failures | [Execution](skills/cfdagent/references/execution.md) |
| Judge results; plan spatial and temporal sensitivity studies or cross-solver comparisons | [Result validation](skills/cfdagent/references/result-validation.md) |
| Find classic cases and validation data | [Benchmark library: 8 curated official sources and how to cite them](skills/cfdagent/references/benchmark-library.md) |
| Extract quantities, compare coefficients, build figures, reports and reproducibility packages | [Post-processing and delivery](skills/cfdagent/references/postprocess-and-delivery.md) |
| Resume a project; keep input versions, run evidence and lessons from failures | [Working notes](skills/cfdagent/references/working-notes.md) |
| Compare a plain agent with the plugin (plugin development only) | [Plugin evaluation](skills/cfdagent/references/agent-evaluation.md) |

PyIB is the author's own immersed-boundary solver. It sits in the solver map on equal terms with the other families and is not preferred by default.

The skill and reference notes are currently written in Chinese. You can discuss your project in English or Chinese; responses depend on the host model.

## What the plugin runs, sends and stores

- CFDAgent contains instructions, reference notes, manifests, documentation, license text, and a PNG icon. The package has no executable code, hooks, MCP server, background jobs, or telemetry client. Installing the package does not itself send project data to the author; host tools and external services process data under their own settings and policies.
- It relies on the host application's own tools. When your work calls for it, and within the permissions you grant, the agent may read and write files in your project, write helper scripts, run solvers, and use a scheduler such as Slurm on systems you have set up.
- For substantive case work, it may create or update a working-notes file (usually `CFD_WORKLOG.md`) in your project.
- The reference notes link to official documentation of third-party solvers and benchmark sources. The agent may open these links when it needs version-specific details.

## Scope and limitations

- CFDAgent provides professional guidance and pointers to sources. It does not bundle solvers or a hosted computation service. Actual simulation needs host file and command tools, a suitable solver, and the required computing environment.
- The benchmark library indexes official upstream sources. It is not a pre-installed or locally validated case library.
- Validation is specific to the case and intended use. The agent should relate convergence, reference comparisons, and mesh or time sensitivity to the conclusions you need.

## Install

CFDAgent is submitted to the Claude and Codex plugin directories; availability there depends on each directory's review.

- **Claude:** find CFDAgent in the plugin directory on the Customize page in claude.ai or the Claude desktop app. A plugin added there is also available in Claude Code.
- **Codex:** find CFDAgent in the Codex plugin directory.
- **Local use:** in Claude Code, run `claude --plugin-dir ./cfdagent` from the parent of the `cfdagent` folder; in Codex, add this folder through the plugin installation flow.

Both `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json` live at the repository root and share the same `skills/` folder.

## How to cite

The following papers describe earlier CFDAgent research systems. This release is a lightweight shared skills plugin, rather than a distribution of the full implementations in those papers. If the work contributes to your research, please cite the relevant papers:

1. Zhaoyue Xu, Long Wang, Chunyu Wang, Yixin Chen, Qingyong Luo, Hua-Dong Yao, Shizhao Wang and Guowei He. CFDAgent: A language-guided, zero-shot multi-agent system for complex flow simulation. *Physics of Fluids* **37**, 117124 (2025). <https://doi.org/10.1063/5.0294696>
2. Zhaoyue Xu, Hua-Dong Yao, Shizhao Wang and Guowei He. CFDAgent with a general kinematics module: Driving biological flapping flight simulation. *Theoretical and Applied Mechanics Letters* **16**, 100734 (2026). <https://doi.org/10.1016/j.taml.2026.100734>

```bibtex
@article{Xu2025CFDAgent,
  author  = {Xu, Zhaoyue and Wang, Long and Wang, Chunyu and Chen, Yixin and Luo, Qingyong and Yao, Hua-Dong and Wang, Shizhao and He, Guowei},
  title   = {{CFDAgent}: A language-guided, zero-shot multi-agent system for complex flow simulation},
  journal = {Physics of Fluids},
  volume  = {37},
  number  = {11},
  pages   = {117124},
  year    = {2025},
  doi     = {10.1063/5.0294696}
}

@article{Xu2026CFDAgentKinematics,
  author  = {Xu, Zhaoyue and Yao, Hua-Dong and Wang, Shizhao and He, Guowei},
  title   = {{CFDAgent} with a general kinematics module: Driving biological flapping flight simulation},
  journal = {Theoretical and Applied Mechanics Letters},
  volume  = {16},
  number  = {5},
  pages   = {100734},
  year    = {2026},
  doi     = {10.1016/j.taml.2026.100734}
}
```

## License

Copyright © 2026 Zhaoyue Xu.

CFDAgent is licensed under the [Creative Commons Attribution 4.0 International License (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/); the full legal code is in [LICENSE](LICENSE). You may use, adapt and share it for any purpose, including commercially, as long as you give appropriate credit. When you share CFDAgent or material adapted from it, please credit it as:

> CFDAgent by Zhaoyue Xu (https://github.com/XuZhaoyue1995/cfdagent), licensed under CC BY 4.0.

## Privacy, terms and support

- [Privacy policy](PRIVACY.md): package behavior, host processing, and voluntary support correspondence.
- [Terms of use](TERMS.md)
- Questions and bug reports: [GitHub issues](https://github.com/XuZhaoyue1995/cfdagent/issues)
- [Changelog](CHANGELOG.md)
