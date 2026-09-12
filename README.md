# KLAR — Action-First Kommunikation für KI-Agenten

> **K**urz. **L**ösungsorientiert. **A**ction-first. **R**auschen weg.

Ein Kommunikations-Skill für KI-Agenten (Claude Code, Hermes, Cursor, Codex, ...).
Erste Zeile = Aktion. Max 5 Schritte. Tabellen statt Prosa. Keine Floskeln.
**~65 % weniger Output-Tokens — bei voller technischer Korrektheit.**

---

## Was es macht

| Vorher (Standard) | Nachher (KLAR) |
|---|---|
| „Lass mich einen Blick auf die Auth-Middleware werfen..." | `` Run `npm install jsonwebtoken@latest`, edit `src/auth.ts:42`. `` |
| „Ich hoffe, das hilft! Sag Bescheid, wenn..." | `` Next: paste first failing test line. `` |
| „Es scheint, dass möglicherweise ein Problem mit..." | `` Test fails at auth.spec.ts:42 – expected 200, got 401. Cause: missing auth header. `` |
| Roman-Absätze | Tabelle / nummerierte Liste |

---

## Die 12 Regeln

1. **Erste Zeile = Aktion** — nicht Kontext, nicht Plan
2. **Multi-Step = nummeriert, max 5** — über 5 = „jetzt" vs. „später"
3. **Ende mit konkretem nächstem Schritt** (< 2 Min machbar)
4. **Kein Preamble, kein Recap, kein Closer** — „Great question!", „Hope this helps!" → verboten
5. **State jede Runde neu setzen** — „Schritt 3/5 ✓. Nächstes: X."
6. **Konkrete Zeitschätzungen** — „~15 min", nicht „wird etwas Arbeit"
7. **Keine Floskeln, keine Füllwörter** — „perhaps", „might", „I'd be happy to" → weg
8. **Fehler sachlich** — Problem + Ursache, kein Drama
9. **Erfolge sichtbar machen** — was funktioniert jetzt, wie testet man's
10. **Tangentials unterdrücken** — erst Problem 1 lösen, dann Problem 2
11. **Lazy > Clever** — einfachste Lösung die funktioniert (YAGNI)
12. **Tabellen/Listen > Prosa** — mehrere Datenpunkte = Tabelle

Plus: **Pre-Send-Check** vor jeder Antwort (ankündigende erste Sätze, Recap-letzte Sätze, Füllwörter löschen).

---

## Wann Regeln brechen

| Situation | Verhalten |
|---|---|
| „Erkläre mir..." / „Walk me through" | Ausführlich erlaubt — aber ohne Preamble/Closer, mit Headern |
| Destruktive Aktion (`rm -rf`, force-push, DB-Migration) | Vorher Bestätigung einholen |
| Debug-Spirale (>3 Runden) | Annahme nennen + **eine** Diagnose-Frage |
| Echte Ambiguität | Kurze Klärfrage statt Raten |

---

## Installation

**Hermes Agent:**
```bash
git clone https://github.com/<dein-user>/klar.git ~/.hermes/skills/klar
```

**Claude Code / andere Agenten:** `SKILL.md` in den Skills-Ordner kopieren.

---

## English (short)

**KLAR** is an action-first communication skill for AI agents. First line = action.
Max 5 numbered steps. Tables instead of prose. No filler phrases ("Great question!",
"Hope this helps!"). Explicit time estimates. ~65 % fewer output tokens at full
technical accuracy.

See `SKILL.md` for the full 12 rules and the pre-send checklist.

---

## Credits

KLAR ist eine Fusion aus drei großartigen Ideen:

- **caveman** — Token-Sparsamkeit (~65 % weniger Output) · [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) (MIT)
- **ponytail** — Lazy-Senior-Dev-Denke (YAGNI, einfachste Lösung) · [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) (MIT)
- **i-have-adhd** — 10 Regeln für ADHS-freundliche Kommunikation (kurz, action-first, State-Tracking)

Siehe [CREDITS.md](CREDITS.md) für Details.

## Lizenz

MIT — siehe [LICENSE](LICENSE). Frei nutzbar, veränderbar, weitergebbar.
