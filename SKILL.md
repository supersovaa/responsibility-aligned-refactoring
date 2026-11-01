---
name: responsibility-aligned-refactoring
description: Keep implementation ownership coherent when implementing or reviewing refactoring that moves, splits, or consolidates existing responsibilities across modules, packages, crates, or layers.
---

# Responsibility-Aligned Refactoring

Use this skill when implementing or reviewing a refactoring that moves, splits, or consolidates existing responsibilities across implementation boundaries.

## Core rule

Align each moved responsibility with its settled owner. Keep one authoritative path for its behavior, state, and invariants, and connect consumers through the smallest interface justified by the new boundary.

## Trace responsibility moves

1. Identify the affected responsibilities, their existing implementations, and the settled design and behavior to preserve.
2. Identify the new owner of each operation, validation rule, event ordering rule, and piece of retained state.
3. Trace the affected calls, data, events, and diagnostic paths from producers to consumers before and after the move.
4. Preserve adapters and distinct representations when they express an actual public contract, dependency direction, or independently meaningful responsibility.

## Consolidate the resulting paths

- Let the owner perform each operation and maintain its invariants. Have consumers use the owner's results instead of duplicating validation, event ordering, cursors, counters, or synchronization.
- Reconcile moved code with its former location. Remove obsolete copies and connect each retained implementation to its actual callers.
- Prefer direct access through the intended boundary over forwarding methods, re-export chains, aliases, and wrappers that merely reproduce another path. Retain compatibility layers where a settled contract or migration requires them.
- Align test support with the new owner. Prefer updating test imports and helpers to their canonical paths over reproducing the previous module hierarchy through forwarding fixtures.
- When a consumer knows before an operation whether optional data is needed, pass that need to the producer before it captures expensive snapshots or diagnostic data. Compare enabled and disabled execution paths with the pre-refactor behavior.

## Verify the resulting implementation

Compare the complete affected paths with the pre-refactor implementation. Examine duplicated logic, state, data conversions, indirection, obsolete files, and recurring runtime cost. Use net code growth and repeated code shapes as investigation signals, then distinguish code required by real new boundaries from incidental reconstruction of old ones.

Apply [`concept-introduction-threshold`](https://github.com/supersovaa/concept-introduction-threshold/blob/main/SKILL.md) to the value of named wrappers and intermediate models, and [`prefer-static-decisions`](https://github.com/supersovaa/prefer-static-decisions/blob/main/SKILL.md) to decisions already known before execution.

## Responsibility boundaries

This skill owns implementation-path coherence after a responsibility move, during both implementation and review.

[`responsibility-driven-crates`](https://github.com/supersovaa/responsibility-driven-crates/blob/main/SKILL.md) owns choosing Rust crate boundaries. [`concept-introduction-threshold`](https://github.com/supersovaa/concept-introduction-threshold/blob/main/SKILL.md) owns the justification for named implementation concepts. [`prefer-static-decisions`](https://github.com/supersovaa/prefer-static-decisions/blob/main/SKILL.md) owns static versus runtime representation choices.

[`test-evidence-preservation`](https://github.com/supersovaa/requirement-driven-testing/blob/main/skills/preservation/SKILL.md) owns preservation and executable discovery of test evidence after restructuring. The surrounding implementation and review workflows retain ownership of code changes, test execution, findings, and acceptance.
