---
name: dependency-update-web
description: Workflow command scaffold for dependency-update-web in RD-Agent.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /dependency-update-web

Use this workflow when working on **dependency-update-web** in `RD-Agent`.

## Goal

Automated update of JavaScript/TypeScript dependencies for the web frontend, typically via Dependabot. Updates package.json and package-lock.json, sometimes for specific packages.

## Common Files

- `web/package.json`
- `web/package-lock.json`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Update web/package.json with new dependency version(s)
- Update web/package-lock.json to lock new versions
- Commit both files with a message referencing the dependency and version

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.