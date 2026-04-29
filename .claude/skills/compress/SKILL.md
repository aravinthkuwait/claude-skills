---
name: compress
description: Compress natural language memory files (CLAUDE.md, todos, preferences) into caveman format to save input tokens. Preserves all technical substance, code, URLs, and structure. Compressed version overwrites the original file. Human-readable backup saved as FILE.original.md. Trigger: /caveman:compress <filepath> or "compress memory file"
user-invocable: true
allowed-tools:
  - Bash(python3:*)
  - Read
  - Write
---

# Caveman Compress

## Purpose

Compress natural language files (CLAUDE.md, todos, preferences) into caveman-speak to reduce input tokens. Compressed version overwrites original. Human-readable backup saved as `<filename>.original.md`.

## Trigger

`/caveman:compress <filepath>` or when user asks to compress a memory file.

## Process

1. This SKILL.md lives alongside `scripts/` in the same directory. Find that directory.

2. Run:
```bash
cd <directory_containing_this_SKILL.md> && python3 -m scripts <absolute_filepath>
```

3. The CLI will:
   - detect file type (no tokens)
   - call Claude to compress
   - validate output (no tokens)
   - if valid: save `FILE.original.md` backup, overwrite FILE with compressed version
   - if invalid: keep original, report error

## Rules

- Preserve ALL technical content: code blocks, URLs, file paths, commands, version numbers
- Drop: articles, filler words, pleasantries, hedging, verbose explanations
- Compress natural language descriptions only
- Never compress code or structured data

---
Source: https://github.com/JuliusBrussee/caveman
