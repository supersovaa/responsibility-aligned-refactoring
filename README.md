# Responsibility-Aligned Refactoring

A lightweight skill for implementing and reviewing refactoring that redistributes existing responsibilities across modules, packages, crates, or layers.

## Core idea

Move each responsibility to its settled owner and keep one authoritative implementation path. Connect consumers through the smallest boundary that preserves the required behavior, contracts, and dependency direction. Compare the whole affected path with the pre-refactor structure to identify duplicated processing, state, compatibility layers, and recurring work.

## Skill and activation

- [`responsibility-aligned-refactoring`](SKILL.md) — use when implementing or reviewing a refactoring that moves, splits, or consolidates existing responsibilities across implementation boundaries.

## Responsibility boundaries

This skill owns the coherence of implementation paths after responsibility moves. [`responsibility-driven-crates`](https://github.com/supersovaa/responsibility-driven-crates/blob/main/SKILL.md) owns choosing Rust crate boundaries; [`concept-introduction-threshold`](https://github.com/supersovaa/concept-introduction-threshold/blob/main/SKILL.md) owns named abstraction justification; [`prefer-static-decisions`](https://github.com/supersovaa/prefer-static-decisions/blob/main/SKILL.md) owns static versus runtime decisions.

[`test-evidence-preservation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/preservation/SKILL.md) owns preserving and verifying executable test evidence after restructuring. Implementation and review workflows own the changes and acceptance decisions.

## Setup

Link [`SKILL.md`](SKILL.md) directly from the applicable implementation and review work-type entries in the target repository, such as `AGENTS.md` or a task-specific skill. Read and apply it when that work type begins. Keep detailed operational rules in the public `SKILL.md`.

## Files

- `SKILL.md` — skill definition.
- `README.md` — activation, boundaries, and setup.
- `LICENSE` — MIT License.
