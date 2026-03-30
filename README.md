# Quick Question (/q)

Don't you find it annoying that Claude will search your codebase, spin up a plan, edit files, and run half a dozen tools — but won't just *answer your question*? You ask "what port does Redis use?" and suddenly it's grepping through your entire project looking for Redis configs.

That's why I created `/q`. One simple slash command that tells Claude to skip everything and just give you a straight answer. No planning. No file edits. No tool use. No code search. Just the answer.

## Usage

```
/q what port does Redis use?
→ 6379

/q what's the difference between let and const in JavaScript?
→ let can be reassigned, const cannot. Both are block-scoped.

/q what is a Python decorator?
→ A wrapper that modifies a function's behavior without changing its code.

/q how do I reverse a list in JavaScript?
→ array.reverse() mutates in place, or [...array].reverse() for a copy.
```

## Install

```
/plugin install quick-question
```

Or manually copy the command file to use it right away:

```bash
# User-level (works in all projects)
mkdir -p ~/.claude/commands
cp .claude-plugin/commands/q.md ~/.claude/commands/q.md

# Project-level (works only in that project)
mkdir -p .claude/commands
cp .claude-plugin/commands/q.md .claude/commands/q.md
```

## How It Works

It's just a prompt template. The `/q` command prepends an instruction telling Claude to answer directly, then passes along your question. That's it — no magic, no dependencies, no config.

## License

MIT
