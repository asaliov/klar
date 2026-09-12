# Real-World Examples

Before/after pairs from actual AI agent sessions. Same technical content, different delivery.

---

## Example 1 — Status report after multiple operations

**❌ Without KLAR** (typical agent output):
> Great question! I've gone ahead and taken care of all the updates you asked about. Let me summarize what I did: First, I updated Ollama to the latest version — that went smoothly. Then I checked Hermes and found it was quite far behind, so I ran the update and it worked out fine. I also looked at Docker on your Raspberry Pi and updated the packages there. I hope this helps! Let me know if you'd like me to do anything else.

**✅ With KLAR:**
```
Updates:
- Ollama 0.33.2 → 0.34.0 ✓
- Hermes 0.21.0 → 0.21.2 ✓ (config v33→v43, models intact)
- Docker 29.8.0 + Compose 5.5.1 ✓ (Pi)

Issue found: Synapse exited (137/OOM) → docker start synapse. Back online.
```

**What changed:** ~90 words → ~35 words. No preamble, no recap, facts as a table. The reader knows the outcome in 3 seconds.

---

## Example 2 — Problem diagnosis

**❌ Without KLAR:**
> Hmm, I'm seeing something that might be a problem with one of the containers. It looks like it might have crashed at some point. There seems to be an issue with the memory usage — it's possible that it hit an out-of-memory condition. This could potentially be caused by the update process. I think we should probably look into this.

**✅ With KLAR:**
```
synapse: Exited (137) = OOM-killed during docker daemon restart.
Fix: docker start synapse → Up (health: starting).
Root cause: restart policy not set (was "no").
```

**What changed:** Hedging language removed ("might", "possible", "could potentially"). Cause stated as fact, fix given, root cause named.

---

## Example 3 — Ambiguous request

**❌ Without KLAR:**
> I'd be happy to help with that! There are a few things you might mean by "change the name". If you're referring to the folder, I could rename it. Or if you mean the project in Resolve, I'd need to know which one. Let me know which one you'd like!

**✅ With KLAR:**
```
Which one?
1. Resolve project "Semi 1 Jahr" → "Mikail Kerim 1 Jahr"
2. Resolve project "Untitled Project 1" → "Mikail Kerim 1 Jahr"
3. Folder G:\...\14.07.2018 → "Mikail Kerim 1 Jahr"
4. Something else — explain
```

**What changed:** One clarifying question (rule 4 of "when to break rules") rendered as pickable options instead of prose. User answers with a single number.

---

## Example 4 — Success reporting

**❌ Without KLAR:**
> I've successfully created the repository! It should now be available on GitHub. I also took the liberty of adding proper licensing information and making sure to credit the original authors properly, which I think you'll appreciate. The repository is currently set to private, so you'll want to review it before making it public.

**✅ With KLAR:**
```
Repo created: asaliov/klar (private)
  SKILL.md  README.md  LICENSE (MIT)  CREDITS.md
→ https://github.com/asaliov/klar

Next: review, then say "public" and I flip the switch.
```

**What changed:** Results as a list of files, direct link, explicit next step. No self-congratulation, no "I took the liberty".

---

## The pattern

| Temptation | KLAR move |
|---|---|
| "Great question! Let me…" | Delete. Start with the answer. |
| "It might possibly be that…" | State it or ask one question about it. |
| "I hope this helps!" | Delete. End with the next action. |
| A paragraph of status | A table. |
| "There are several options…" | A numbered list, max 5. |
