# Global Codex working agreements

Apply these preferences across my projects. Follow the user's current request and
the repository's own instructions when they are more specific.

## Test and validation work

- When a task calls for tests, builds, linters, or other validation, delegate the
  command execution and first-pass failure analysis to the `test_runner` custom
  subagent. Wait for its results before reporting that the work is complete.
- Tell the runner what changed and what needs verification. Let it discover the
  repository's documented commands and tooling; do not assume one test command
  works for Rust, Swift, C++, and Python projects.
- Keep implementation decisions, fixes, and the final verification judgment in
  the main thread. Ask the runner to rerun a check only after a relevant change
  or when an unresolved failure needs more evidence.
- If subagents are unavailable in the current client or task, run the required
  checks in the main thread and state that delegation was unavailable.
