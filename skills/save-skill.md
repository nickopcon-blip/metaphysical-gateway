---
name: save
description: SAVE & CLOSE CHECK — protect a chat's work before it's lost, then say whether the chat is safe to close. Use whenever the user types /save or /s, or says anything like "save this", "save my work", "checkpoint", "I have to run", "wrap this up", "can I close this chat?", "are we done here?", "anything left to do?", or otherwise signals they're stepping away or ending the conversation. Sweeps the chat for anything worth keeping, writes it somewhere permanent, leaves a resume note so a later "continue" picks up where things left off, and ends with a clear ✅ safe-to-close / ⏳ not-yet verdict.
---

# /save — Save everything, then tell me if I can close this chat

Chats get closed, archived, and forgotten — but the work inside them shouldn't be. When this skill runs, your job is: get everything valuable OUT of this chat and into somewhere permanent, leave a trail so the user can resume later, and give an honest verdict on whether closing the chat loses anything.

## Step 1 — Park safely

If something is mid-flight, don't start anything new. Finish only what's already safe to finish; otherwise stop cleanly with no half-done state. Note the exact point reached: what was just done, and the single next concrete step.

## Step 2 — Sweep the chat

Walk back through the conversation and collect everything that exists ONLY here and still matters:

- **Decisions made** — anything the user decided or approved.
- **Facts learned** — durable things about the user, their projects, clients, or preferences.
- **Work produced** — drafts, files, code, plans, lists (make sure files were actually created/delivered, not just shown in chat).
- **Unfinished work** — things you said you'd do but didn't finish, and the next step for each.
- **Waiting on the user** — things only they can do (send something, approve something, decide something). These don't block closing — but list them so nothing is forgotten.
- **Lessons** — corrections or preferences that should change how Claude works from now on (see Step 4).

## Step 3 — Persist to the best available home

Save each item using the best option this account actually has, in this order. On the FIRST run ever, briefly tell the user which homes you found and are using.

1. **Claude memory** (if this account has the memory feature): store durable facts, preferences, and project status there — it's kept by Claude in the cloud and follows the user across chats and devices with zero setup. This is the preferred home for facts and preferences.
2. **A connected folder** (if one is connected, or the user connects one when you offer): keep a folder called `Claude HQ` with two files, and always read the current file before editing it — update in place, never blindly overwrite:
   - `RESUME.md` — one section per open topic: what's done, what's in progress, the exact next step, and any context (drafts, values, decisions) that would otherwise be lost. This is what makes "continue" work later.
   - `NOTES.md` — durable facts and reference info, one topic per section, newest updates replacing old ones in place.
3. **The user's own connected tools** (Notion, Google Drive, GitHub, etc.), if they've told you where things should live — honor their setup over the defaults above.
4. **No storage available at all?** Print a compact **💾 SAVE BLOCK** in the chat — a short fenced block with the resume section from `RESUME.md` format — and tell the user: "Copy this somewhere safe (notes app, doc, email to yourself). Paste it into any new chat to continue." Then offer to set up a `Claude HQ` folder so next time is automatic.

Do the saving yourself, immediately — don't ask "want me to save this?". Only pause for things that are genuinely the user's (sending messages, deleting things, judgment calls).

## Step 4 — Lesson check

If the chat surfaced a lasting preference, correction, or better way of working, propose it as a permanent instruction upgrade (the `learn` skill's 📚 format). One short proposal, never auto-applied.

## Step 5 — Verdict

End with one of:

- **✅ Safe to close.** — plus one line on where everything now lives, so any future chat can find it.
- **⏳ Not yet — N things:** — list only what remains, each tagged either *(done just now)* or *(yours — survives closing)*.

## Step 6 — Report format

Keep the whole response short: the verdict, a 3–5 line log of what was saved and where, and the single next step if work is unfinished. No recap of the conversation — the user was there. End with: **Say "continue" in a new chat to pick up where we left off.**

## Long or heavy chats — bonus handoff prompt

If this chat has been long or heavy (multi-hour, lots of steps, second+ save, or things feel slow), ALSO output a short ready-to-paste prompt under the header **"🆕 Fresh-chat prompt (paste into a new chat):"** — a fenced block that names the topic, says where the saved state lives (memory / `Claude HQ/RESUME.md` / the save block), lists the remaining tasks as a numbered queue, and ends with "Continue from where you left off." Long chats slow Claude down; a fresh chat with this prompt keeps full speed.

## Resuming

When the user says **"continue"** (or "resume", "pick up where we left off") in a fresh chat: check Claude memory and `Claude HQ/RESUME.md` (or ask for their save block). If exactly one topic is open, resume it and execute its next step. If several are open, list them and ask which.
