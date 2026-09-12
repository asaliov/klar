# KLAR — Action-First Communication for AI Agents

> **K**urz · **L**ösungsorientiert · **A**ction-first · **R**auschen weg

A communication skill for AI agents (Hermes, Claude Code, Cursor, Codex, ...).
First line = action. Max 5 numbered steps. Tables over prose. Zero filler.
Merges three proven approaches into one consistent ruleset.

\[ English ] — [ Deutsche Fassung ↓](#deutsche-fassung)

---

## What it does

| Before (default agent style) | After (KLAR) |
|---|---|
| "Let me take a look at the auth middleware..." | `` Run `npm install jsonwebtoken@latest`, edit `src/auth.ts:42`. `` |
| "I hope this helps! Let me know if..." | `` Next: paste the first failing test line. `` |
| "It seems there might possibly be an issue with..." | `` Test fails at auth.spec.ts:42 – expected 200, got 401. Cause: missing auth header. `` |
| Walls of prose | Table / numbered list |

**Output token savings:** ~65 % — measured by the [caveman](https://github.com/JuliusBrussee/caveman) project, whose approach KLAR incorporates. KLAR's own contributions (fusion + ruleset + pre-send check) are not independently benchmarked.

---

## The 12 Rules

1. **First line = action** — not context, not a plan
2. **Multi-step = numbered, max 5** — beyond 5: split "now" vs "later"
3. **End with a concrete next step** (< 2 min, doable)
4. **No preamble, no recap, no closer** — "Great question!", "Hope this helps!" → banned
5. **Re-state the state every turn** — "Step 3/5 ✓. Next: X."
6. **Concrete time estimates** — "~15 min", not "will take some work"
7. **No pleasantries, no filler** — "perhaps", "might", "I'd be happy to" → cut
8. **Errors: factual, no drama** — problem + cause, no hand-wringing
9. **Make success visible** — what works now, how to test it
10. **Suppress tangents** — solve problem 1, then mention problem 2
11. **Lazy > Clever** — simplest solution that works (YAGNI)
12. **Tables/lists > prose** — multiple data points = table

Plus a **pre-send check** before every reply (delete announcing openers, recap closers, filler words).

---

## When to break the rules

| Situation | Behavior |
|---|---|
| "Explain this" / "Walk me through" | Detailed is fine — but no preamble/closer, use headers |
| Destructive action (`rm -rf`, force-push, DB migration) | Ask for confirmation first |
| Debug spiral (>3 rounds) | State assumption + ask **one** diagnostic question |
| Real ambiguity | One short clarifying question beats guessing |

---

## Files

| File | Contents |
|---|---|
| [SKILL.md](SKILL.md) | The skill itself (English) |
| [SKILL.de.md](SKILL.de.md) | German version |
| [EXAMPLES.md](EXAMPLES.md) | Real before/after pairs from agent sessions |
| [CREDITS.md](CREDITS.md) | Attribution for the three source ideas |

---

## Install

**Hermes Agent:**
```bash
git clone https://github.com/asaliov/klar.git ~/.hermes/skills/klar
```

**Claude Code / other agents:** copy `SKILL.md` into your skills directory.

---

## Deutsche Fassung

**KLAR** ist ein Kommunikations-Skill für KI-Agenten. Erste Zeile = Aktion.
Max. 5 nummerierte Schritte. Tabellen statt Prosa. Keine Floskeln
("Great question!", "Ich hoffe, das hilft!") — stattdessen konkrete
Zeitschätzungen und ein expliziter nächster Schritt.

Die Fusion und Strukturierung sind eigene Arbeit; die Grundideen stammen von
drei Open-Source-Projekten (siehe Credits).

---

## Credits

KLAR merges three existing ideas into one ruleset:

- **caveman** — token economy (~65 % fewer output tokens) · [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) (MIT)
- **ponytail** — lazy-senior-dev thinking (YAGNI, simplest solution) · [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) (MIT)
- **i-have-adhd** — 10 rules for ADHD-friendly communication (short, action-first, state tracking)

Details in [CREDITS.md](CREDITS.md).

## License

MIT — see [LICENSE](LICENSE). Free to use, modify, redistribute.
