<!-- WS_STATIC_START adapter=rules-v2 inputs=b59d6aee78ed202a6f00e252dd044ca45d6ba68b608f6fa9c096928314df8862 -->
<!-- Generated file: do not edit by hand. These rules are maintained in the owner's rule source and re-rendered here. -->

## Engineering discipline

- **Measure the physical system first.** Before an abstract architecture proposal, inspect the system with read-only probes such as `time cmd`, process chains, and file-descriptor locks. A conceptually neat story without physical evidence is insufficient. A probe must not write. Do not combine validation and action in one command: a POST permission probe can create a resource, and a trial commit can leave a real commit. Measure, read the result, then decide, with a stop point between these steps.
- **Green does not prove truth.** The tested system writes its own unit tests, CI, and issue states. Cross-check critical conclusions against two external sources not written by this repository.
- **Tests must be falsifiable.** Do not hide assertions in `if (exists)` or `if (code != 0)` so failures run zero assertions. Do not accept tautologies such as `typeof null === 'object'` or `result !== undefined || true`. Source-text `indexOf` matches against prose are not integration tests. Duplicate test function identifiers can silently shadow earlier tests (Python `def` and duplicate JS function/const/export names); duplicate string titles in `test()` or `it()` instead run both. A green count is not coverage evidence. Make a new test fail under a relevant mutation. A read-only reviewer treats such fake-test patterns as CRITICAL merge blockers.
- **Falsifiable documentation and assertions:** State test requirements, error messages, and specifications in concrete ASD-STE100 terms without vague qualifiers.
- **One source of truth:** Keep one authoritative definition per core fact. Repeated hardcoding and scattered configuration invite drift.
- **Clean up during migration:** After the new mechanism is live and equivalence is proved, remove its predecessor, obsolete files, and dead code in the same change. Define contracts first and derive CI from them.
- **Deletion can leave guards green and empty:** A guard for an old structure can stop checking anything after deletion. Check each guard and remove it or redirect it to the new structure; green tests alone do not prove safe deletion.
- **Define guard scope from what it must govern, not from today's passing tree.** Let the guard fail on existing violations, then repair them. A guard never seen failing is not yet evidence of protection.
- **Worktree self-sufficiency:** Every worktree must resolve its dependencies, toolchain, skills, and configuration internally. Tools and tests must not navigate upward with `../..` to locate files in parent checkouts.
- **Physical context verification:** Static file existence does not prove host runtime context injection. Junior runs non-interactive probes (`-p` or headless exec) with low-cost models, asserting visible specification text across root and deep subdirectories.
- **Host verification scope:** Official host CLIs are the primary execution environment. Regular testing covers Antigravity 2.0 project workspaces (`.agents/skills/` and project rules); standalone desktop chat apps without directory awareness are excluded.
- **Local and remote test segregation:** Inner-loop verification (Senior, Junior, Intern) runs only focused tests on changed files (`pytest <file>::<test> -x`). Full-suite regression runs on remote CI, or locally at most once before merge.
- **Bounded file reads:** Pass `StartLine` and `EndLine` (`<= 120` lines per call) when reading existing files with `view_file`.

## Production reservation

The single definition of the production reservation. Other tiers, skills and gates point here.

- **Only a production change returns to the owner.** A production change alters what production runs or stores. Examples: a deploy, promote or apply to production; a production secret write; a manual production data write or deletion. Also a production DNS, route or host change, and a release that cannot be recalled. Code that reaches production with no later owner approval, for example on a schedule, counts too. Each Repo tier names its production paths.
- **Approval:** the owner approves the exact commit SHA or release tag of each production change, and is present when it runs. A "deploy" reply covers only the release that it names. Immediately before a production dispatch, get a live reply from the owner.
- **Self-guard:** an edit that removes, narrows or redefines the production reservation needs the owner's approval of its head SHA. This includes an edit that makes fewer production runs wait for the owner. Examples: the owner-approval check of a deploy path, a production job classification, the settings of a production environment. It also includes an edit that removes or weakens a pin of this section or its dev_env pin test. The same holds for the required check that runs the test.
- **Everything else is the agent's:** in a repository that the owner owns, every merge, staging and canary deploy, and release tag. Also rule text, skills, gate code, data and tests, required-check workflows and release code. Before you merge gate or release code, a read-only reviewer that did not write it checks the head. The review states whether the gate gets stricter, stays equal or gets looser. A looser edit in the self-guard list follows the self-guard.
- **Every other hold is a defect:** a rule, skill, label or gate exit code that holds non-production work for the owner. Do the work, then fix the hold. The dev_env check `ws_owner_scope` fails on it.

# Muscle Pain Helper — Agent Guidelines

> **Repository Archetype**: `app` (Personal Health Tracking Application)
> **Rule Carrier**: `AGENTS.md` is generated; `CLAUDE.md` is a symlink to it. Do not edit either by hand.
> **Merge Authority**: Standard PRs with clean tests and review passing may be merged by agents per workspace standing grant.

## Overview

A lightweight personal application for tracking and managing muscle pain.

## Guidelines

1. **12-Factor Design**: Any future server or persistence logic should rely on standard environment variables.
<!-- WS_STATIC_END -->
