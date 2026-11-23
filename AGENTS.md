# AGENTS.md

This repo holds *Think Python* (2nd Edition, Version 2.4.1) by Allen Downey, split for agent-assisted reading and reference. It is published under the Creative Commons Attribution-NonCommercial 3.0 Unported License (see front matter). Keep this repo **private** and never make it public.

## Orient cheaply
1. Read `outline.md` (one line per chapter) and `bible/style.md` first.
2. For context on any chapter, read `summaries/NN-*.md`, not the chapter.
3. Open a full chapter in `chapters/` only when you need exact prose or code. To read part of one, use line ranges.
4. Find mentions with grep rather than reading files:
   - `grep -rn "recursion" chapters/`
   - `grep -rln "dictionary" chapters/` (which chapters)
   - `grep -n "^#" chapters/06-*.md` (section map of one chapter)
5. Look up names, frameworks, terms and versions in `bible/` (`glossary.md`, `world.md`, `characters.md`, `timeline.md`).

## Layout
- `chapters/NN-kebab-title.md`: one chapter per file, starting with `# Chapter N: Title`.
- `front/`: preface and front matter. `back/`: appendices (A: Debugging, B: Analysis of Algorithms).
- `summaries/`: same file names as `chapters/`.
- `notes/todo.md`: suspected PDF extraction glitches. Read it before "fixing" anything.

## Editing rules
- **Never reword, correct or trim the prose unless explicitly asked.** That includes PDF extraction glitches: log them in `notes/todo.md` instead.
- **One sentence per line**, with a blank line between paragraphs (when editing summaries/bible, not extracted chapter text).
- Keep terms consistent with `bible/glossary.md`.

## After editing a chapter or summary
1. Update `summaries/NN-*.md` if the chapter summary is affected.
2. Update the chapter's line in `outline.md`.
3. Update the bible entries it affects (new terms, versions, tools).
4. Commit after each logical change with a clear message, e.g. `ch06: fix summary of fruitful functions` or `bible: add memoization to glossary`.
