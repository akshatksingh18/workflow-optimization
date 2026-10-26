# AI Coding Workflow Tool Evaluation

This is the current decision document for optional tooling around Claude Code and Codex on
Windows 11. It is not an installation plan, wishlist, or research diary.

**Current state:** no optional workflow tool, memory layer, alternate agent runtime, or model
gateway is adopted. The baseline is Claude Code + Codex + the shared `CLAUDE.md` hierarchy.

## Decision rules

- Start with a concrete problem, not a tool. If the baseline handles the work well, install
  nothing.
- Trial only one overlapping tool at a time on a bounded real task. Define the success measure
  first: time saved, fewer missed dependencies, lower verified token cost, or fewer defects.
- Prefer tools that work with both Claude Code and Codex so the workspace behaves consistently.
- Before installation, verify Windows 11 support, privacy and telemetry, account/API cost,
  maintenance, permissions, generated-file footprint, and a clean uninstall path.
- Never let automatic memory replace durable project documentation. Current decisions,
  architecture, status, and TODOs still belong in the applicable workspace files.
- Replace statuses and conclusions in this document in place. Do not append dated trials,
  release histories, or session notes.

## Baseline workflow — already sufficient for now

1. Load the applicable `CLAUDE.md` chain and task-triggered rules/skills.
2. Inspect the smallest relevant set of files and identify the owning source of truth.
3. For non-trivial work, clarify the outcome and plan the change before editing.
4. Keep changes cohesive; review the diff as well as test output. Passing tests do not prove the
   implementation matches the request.
5. Verify in proportion to risk, then update current status/TODO/architecture in place.

These practices solve most workflow problems without another background service, memory store,
agent runtime, or generated documentation tree.

## Evaluation board

| Category | Candidate | Status | Current decision and adoption trigger |
|---|---|---|---|
| Development methodology | [Superpowers](https://github.com/obra/superpowers) | **Best first trial, not installed** | Offers structured design, planning, TDD, review, and verification for both Claude Code and Codex. Trial on one active feature only when a project reaches sustained implementation; keep it only if the added ceremony prevents real rework. |
| Codebase orientation | [lore-map](https://github.com/srihari7070/lore-map) | **Defer** | Useful for visual architecture and scoped prompts, but currently Claude-oriented and unnecessary for small or mostly-document projects. Revisit for a large unfamiliar codebase after cross-agent/Windows support is verified. |
| Generated repository docs | [OpenWiki](https://github.com/langchain-ai/openwiki) | **Defer** | Supports Claude Code and Codex integrations and Windows installation. Use only when an active repository is large enough that maintained architectural documentation saves more than its generated-file and update cost. Do not use alongside another generated wiki without choosing one owner. |
| Automatic session memory | [claude-mem](https://github.com/thedotmack/claude-mem) | **Not recommended by default** | Now supports multiple agents, including Codex, but captures and summarizes session history in a local service and can optionally sync it. That conflicts with the preference for compact current-state documentation unless repeated cross-session context loss becomes a measured problem. |
| Manual memory files | [Memory Bank](https://github.com/hudrazine/claude-code-memory-bank) | **Do not add** | Duplicates the existing `CLAUDE.md` hierarchy and tends to create growing progress/context files. Put durable current state in the owning project files instead. |
| Structural code memory | [memtrace](https://github.com/syncable-dev/memtrace-public) | **Watchlist** | Local code graph with Claude/Codex support and zero LLM calls for indexing, but currently private beta with proprietary/closed-source core components and telemetry/license traffic. Revisit only for a large codebase where dependency discovery or token use is demonstrably painful. |
| Structural code memory | [codebase-memory-mcp](https://github.com/DeusData/codebase-memory-mcp) | **Personal source copy; installation/adoption deferred** | [Checkout instructions](../codebase-memory-mcp/CLAUDE.md) own provenance, the standalone private personal repository, and recovery. Its persistent code graph complements canonical project documents with dependency discovery. Trial only for recurring navigation pain on one substantial repository; verify correctness, time, tokens, peak RAM, and idle CPU rather than assuming published benchmark savings apply locally. No installer or agent integration has been run for this copy. |
| Model gateway | [OpenRouter](https://openrouter.ai/) | **Defer; not configured** | Adds value only when multi-provider access or measured API cost justifies another account, key, billing path, and data processor. It is not the permanent gateway. |
| Local model proxy/router | [LiteLLM](https://github.com/BerriAI/litellm) | **Defer** | Useful after multiple providers are actively used and manual routing is a real problem. It adds operational complexity without value in the current baseline. |
| Alternate agent runtime | [Goose](https://github.com/block/goose) | **Parked** | Overlaps Claude Code and Codex. Revisit only for a specific provider-neutral or extension use case that neither current agent can handle. |
| Alternate terminal agent/UI | [Pi](https://github.com/badlogic/pi-mono) / [Pi setup](https://github.com/abhinand5/pi-setup) | **Parked** | A different interface is not a workflow improvement by itself. Revisit only if its minimal CLI or cost display solves a concrete daily friction. |
| Always-on autonomous agent | [Hermes Agent](https://github.com/NousResearch/hermes-agent) | **Separate future project** | Do not fold it into the normal coding workflow. Consider it only when an actual always-on automation has a defined owner, security boundary, budget, and hosting plan. |
| Discovery list | [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | **Reference only** | Use to discover candidates after a need is defined; inclusion is not evidence that a tool should be installed. |
| Instruction scaffold | [senior-engineering-partner](https://github.com/NeoLabHQ/context-engineering-kit) | **Reference only** | Extract an individual durable rule only if it fills a demonstrated gap. Do not import a second broad instruction system that competes with the workspace `CLAUDE.md` files. |

## Category boundaries

### Methodology

Methodology tools change how work is planned, tested, reviewed, and completed. If Superpowers is
trialled, install/enable the supported version separately in both agents and check that it does not
override project-specific `CLAUDE.md` instructions. Its value must come from fewer mistakes, not
from producing more planning files.

### Codebase orientation and generated documentation

lore-map, OpenWiki, and memtrace partly overlap, but are not interchangeable:

- lore-map is a visual/scoping aid.
- OpenWiki produces and maintains repository documentation.
- memtrace provides queryable structural relationships and change history.

Choose at most one first based on the observed problem. For a small repository, normal search and
the existing project docs remain the default.

### Memory and continuity

The workspace already has the portable memory layer both agents need: concise current-state files
plus the `CLAUDE.md` hierarchy. Automatic session capture is a different product—it retains the
story of prior work. That should remain off unless the benefit is proven, because it adds storage,
retrieval noise, privacy considerations, and another source that can disagree with the project.

### Model routing

Do not optimize routing before there is usage data. If API spend or provider availability later
becomes a problem, first compare a short manual trial through OpenRouter with the normal Claude
Code/Codex result. Add LiteLLM only if managing multiple active providers becomes recurring work.
Every generated change still requires diff review and appropriate tests, regardless of model.

## Next evaluation

There is no installation backlog. The next move depends on the first real bottleneck:

- Sustained coding work with preventable rework → trial Superpowers on one feature.
- Large unfamiliar repository with navigation pain → compare OpenWiki, lore-map, and memtrace for
  that specific repository, then trial one.
- Verified context/token waste across sessions → measure the existing baseline first; only then
  reconsider automatic or structural memory.
- Meaningful multi-provider cost or availability problem → trial OpenRouter manually before adding
  routing infrastructure.

Until one of those conditions exists, keep the baseline unchanged.
