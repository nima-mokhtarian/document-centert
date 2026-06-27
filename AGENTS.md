# Neo-Bank Workspace Agent Guide
edited by me
maryam added

This workspace contains independent Git repositories. Before acting, identify the target
repository and read its `AGENTS.md`. Repository instructions supplement this workspace contract.

## Mandatory Workflow

For any request that changes code, build configuration, architecture, runtime behavior, APIs,
contracts, infrastructure, or substantial documentation, use Spec-Kit in this order:

1. `/speckit-constitution`
2. `/speckit-specify`
3. `/speckit-clarify` when material ambiguity exists
4. `/speckit-plan`
5. `/speckit-tasks`
6. `/speckit-implement`

Never implement before a specification and plan exist.

### When to skip Spec-Kit

Do **not** start a Spec-Kit flow for:

- Read-only requests: questions, explanations, reviews, status checks, diagnostics, README additions.
- Small, self-contained code changes that touch ≤ 3 files, involve no new abstractions, and carry
  no design decision (e.g. rename a variable, fix a typo, move a method, add a missing null check).
- Prompt is not asking for a code change at all (architecture discussion, documentation lookup,
  log analysis, etc.).

When in doubt, ask the user whether they want a full Spec-Kit flow before starting one.

### Where to store specs

`neo-bank-docs` is the platform Spec-Kit repository. **Always** store feature specs in
`neo-bank-docs/specs/` using the sequential numbering from `neo-bank-docs/.specify/init-options.json`.
A repository-local Spec-Kit installation may be used only when the change is strictly confined to
that single repository and `neo-bank-docs` is not available.

## Codebase Analysis

- For codebase or architecture questions, run `graphify query "<question>"` before raw search when
  the target repository has `graphify-out/graph.json`.
- Use `graphify path` for relationships and `graphify explain` for focused context.
- After code or documentation changes, run `graphify update .` in each changed repository.

## Tools and Changes

- Prefix shell commands with `rtk`.
- Preserve unrelated user changes and repository boundaries.
- Use the narrowest meaningful verification for each changed repository.
- Follow `neo-bank-docs/development/git-conventions.md` when committing.
