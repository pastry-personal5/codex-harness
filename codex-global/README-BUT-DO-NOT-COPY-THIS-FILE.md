Codex on 2026-10-22 said:

```
I wrote a Codex setup kit for test delegation across your macOS projects:

- Global instructions (codex-global/AGENTS.global.md) tell Codex to delegate validation to test_runner.
- Test runner (codex-global/agents/test-runner.toml) uses model = "gpt-5.6-luna" and model_reasoning_effort = "medium". It discovers each project’s own Rust, Swift, C++, or Python commands.

Install the files from this repository:

cd /Volumes/Work_Volume/approve-hub-mac
codex_home="${CODEX_HOME:-$HOME/.codex}"
mkdir -p "$codex_home/agents"
install -m 600 codex-global/agents/test-runner.toml "$codex_home/agents/test-runner.toml"

if [ -f "$codex_home/AGENTS.md" ]; then
  if ! grep -Fxq '# Global Codex working agreements' "$codex_home/AGENTS.md"; then
    cp -p "$codex_home/AGENTS.md" "$codex_home/AGENTS.md.before-test-runner"
    printf '\n' >> "$codex_home/AGENTS.md"
    sed -n 'p' codex-global/AGENTS.global.md >> "$codex_home/AGENTS.md"
  fi
else
  install -m 600 codex-global/AGENTS.global.md "$codex_home/AGENTS.md"
fi

Start a new Codex session after installation. Check printenv CODEX_HOME first: this session uses /Users/user1/.codex-totonani, while a terminal without that variable uses ~/.codex. These files apply to every project opened with that Codex home. For separate macOS accounts, install them in each account; /etc/codex/config.toml supplies system defaults but is not the documented location for custom agents or global AGENTS.md. OpenAI Docs: subagents (https://learn.chatgpt.com/docs/agent-configuration/subagents), global instructions (https://learn.chatgpt.com/docs/agent-configuration/agents-md), config layers (https://learn.chatgpt.com/docs/config-file/config-basic).

The agent TOML parses, and Swift formatting and SwiftLint passed. The repository’s Swift test run stalled in its service test bundle and was stopped, so that test gate remains unverified.
```

