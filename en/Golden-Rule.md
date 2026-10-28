# AI Coordinator Pattern – Golden Rule

As of 2026-10-28 · belongs to [AI-Coordinator-Pattern.md](AI-Coordinator-Pattern.md) (version 4.6)

> **Every computer with its own workbench is a building site of its own, not just a test site.
> Spread the integration work across all building sites.**

A **workbench** is everything a computer needs to integrate work: its own editor or its own runtime and test environment,
and its own agents working there.

**Why:** If you use a second computer only for cross-checks, the one editor on the main computer becomes the bottleneck for
everything. Finished offline results then queue up, although a second workbench is free. Yet the second computer was set up
for exactly this: with its own editor and its own agents.

---

## The four points

1. **Only the real exclusive resource is limited.** On each computer, exactly one agent at a time works in the editor
   (window protocol, pattern 5.1). Offline work – reading, planning, writing patches, compiling offline, background tools –
   runs in parallel without a cap, as long as no two agents change the same file.
2. **No artificial limit that hides a coordination fault.** A cap on the number of work sites is often a plaster over
   another cause: a coordinator without its own rhythm, sleeping helpers, assignments without "done means". Fix the cause
   first, then limit only what is exclusive. From practice: a limit of "at most two work sites" came from a phase in which
   the coordinator's rhythm was accidentally switched off. After that, things ran much better, and the limit only slowed
   them down.
3. **What stays on a building site and what moves.** Work stays on a computer if it needs that computer's not yet integrated
   state or touches the same non-mergeable files as an integration running there (e.g. binary files, large files in LFS,
   shared save or network files). Everything else goes to the other building sites on its own branches. The coordinator
   merges and assigns the shared numbers (pattern 5.2 and 9).
4. **All building sites on the same main line.** After every integration, the coordinator supplies all building sites with
   the same state (e.g. push to all remotes, then pull on every computer). Before every assignment, it checks what is
   already done offline or running elsewhere, so nothing is built twice.

---

## Quick check before every assignment

- Which building sites are free, and is the editor there free?
- Does the package need a not yet integrated state, or does it touch non-mergeable files of a running integration?
  Then it stays on that building site.
- Is it already done offline or running elsewhere? Then do not assign it again.
- Is every building site on the current main line?

## Related sections in the pattern

5.1 Window protocol · 5.2 Shared files and numbers · 5.11 Delegate instead of implementing yourself · 9 Several computers ·
11 Proven lessons (its own rhythm, define "done" up front)
