# Quick Question (/q) — Development Notes

## What It Does

The `/q` command lets you ask Claude a question and get a direct answer — no planning, no file edits, no tool use, no code search. Just a concise answer.

```
/q what port does Redis use?
→ 6379

/q what's the difference between let and const in JavaScript?
→ let can be reassigned, const cannot. Both are block-scoped.
```

## Why

Claude Code defaults to being helpful with tools — searching files, editing code, running commands. Sometimes you just want a quick answer without all that. The `/q` command tells Claude to skip everything and just answer.

## How It Works

It's a custom slash command (`.claude-plugin/commands/q.md`) that prepends a system instruction before your question:

> Answer the following question directly and concisely. Do NOT plan, do NOT edit files, do NOT run tools, do NOT search code. Just answer the question with your existing knowledge.

The `$ARGUMENTS` variable gets replaced with whatever you type after `/q`.

## Plugin Structure

```
claude-quick-question/
  README.md              — User-facing docs
  DEVELOPMENT.md         — This file
  .claude-plugin/
    plugin.json           — Plugin metadata (name, version, author)
    commands/
      q.md                — The /q command template
```

## Installation Methods

### 1. Plugin marketplace (once submitted)
```
/plugin install quick-question
```

### 2. Manual — user-level (works in all projects)
```bash
mkdir -p ~/.claude/commands
cp .claude-plugin/commands/q.md ~/.claude/commands/q.md
```

### 3. Manual — project-level (works only in that project)
```bash
mkdir -p .claude/commands
cp .claude-plugin/commands/q.md .claude/commands/q.md
```

### 4. Test locally with plugin flag
```bash
claude --plugin-dir /opt/claude-quick-question
```

## GitHub Repo

https://github.com/nentrapper-g-rod/claude-quick-question

## Next Steps

- Push code to GitHub repo
- Submit to claude.com/plugins marketplace
- Consider adding more question modes (e.g. `/explain` for code explanations, `/tldr` for summaries)
