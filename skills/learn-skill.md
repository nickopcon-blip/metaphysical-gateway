---
name: learn
description: AUTO-LEARN — turn lessons from any chat into permanent Claude instructions. Runs two ways. (1) Always-on: the moment the user corrects Claude, states a preference ("from now on…", "always…", "never…", "I prefer…"), repeats a request they've clearly made before, or a useful workaround is discovered, immediately propose a 📚 instruction upgrade. (2) On demand: when the user types /learn or says "what did you learn?", "anything worth remembering?", "upgrade your instructions", sweep the whole chat for lessons and propose upgrades for everything found.
---

# /learn — Make Claude permanently smarter from this chat

By default, everything Claude learns in a chat dies with the chat. This skill fixes that: lessons become short, paste-ready instruction upgrades the user can make permanent in under a minute. Over weeks, this compounds into a Claude that works exactly the way they do.

## What counts as a lesson

- **Corrections** — the user fixed something Claude did ("no, shorter", "don't use bullet points", "that's the wrong account").
- **Stated preferences** — "from now on…", "always…", "never…", "I prefer…", "call it X not Y".
- **Repeated asks** — the user is clearly asking for something they've asked for before; that's a preference in disguise.
- **Workarounds and better ways** — a discovered fix, sequence, or setting that future chats should know without rediscovering it.
- **Standing facts** — durable context about the user, their work, tools, or people that keeps coming up.

Not lessons: one-off details, anything sensitive (passwords, keys, private data — never put these in instructions), and things that only mattered for this single task.

## The 📚 upgrade format

The moment you spot a lesson — mid-chat, don't wait for the end — output:

📚 **Instruction upgrade:** one line saying what was learned and why it's worth keeping.

Then a fenced code block containing 1–3 crisp instruction lines, written as direct commands to Claude, general enough to apply beyond today's task. Example:

```
When drafting emails for me, keep them under 100 words, open with the point (no pleasantries), and sign off with just my first name.
```

Then one line telling them how to make it stick:

> To make this permanent: open the Claude app → **Settings → Profile** → paste this into the *"What preferences should Claude consider in responses?"* box (add it below whatever's already there). Or just tell me **"remember this"** and I'll store it in memory.

## Rules

- **Propose, never apply.** Never edit their settings yourself; the user pastes it. If they say "remember this", store it in Claude memory (if available) as the fallback.
- **Short and general.** 1–3 lines per upgrade. If it only works for today's exact task, it's not an instruction — it's a note.
- **Don't nag.** At most one or two proposals per chat unless the user runs /learn. If they ignore a proposal, drop it.
- **The 📚 emoji is the marker.** Always use it so upgrades are easy to spot when scrolling.

## /learn on demand

When explicitly invoked, sweep the entire chat against the lesson list above and output every qualifying upgrade in one response — each with its own 📚 header and paste block, ordered most valuable first. If nothing qualifies, say so in one line.
