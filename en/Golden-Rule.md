# AI Coordinator Pattern – Golden Rule

As of 2026-11-09 · belongs to [AI-Coordinator-Pattern.md](AI-Coordinator-Pattern.md) (version 4.9)

> **Every computer with its own workbench is a building site of its own, not just a test site.
> Spread the integration work across all building sites – and with every "done", release the next block.**

A **workbench** is everything a computer needs to integrate work: its own editor or its own runtime and test environment,
and its own agents working there.

**Why:** If you use a second computer only for cross-checks, the one editor on the main computer becomes the bottleneck for
everything. Finished offline results then queue up, although a second workbench is free. Yet the second computer was set up
for exactly this: with its own editor and its own agents.

---

## The eight points

1. **Only the real exclusive resource is limited.** On each computer, exactly one agent at a time works in the editor
   (window protocol, pattern 5.1). Offline work – reading, planning, writing patches, compiling offline, background tools –
   runs in parallel, as long as no two agents change the same file. How many helpers work at the same time is limited by
   the budget (pattern 5.10), not by an artificial cap.
2. **No artificial limit that hides a coordination fault.** A cap on the number of work sites is often a plaster over
   another cause: a coordinator without its own rhythm, sleeping helpers, assignments without "done means". Fix the cause
   first, then limit only what is exclusive. From practice: a limit of "at most two work sites" came from a phase in which
   the coordinator's rhythm was accidentally switched off. After that, things ran much better, and the limit only slowed
   them down.
3. **What stays on a building site and what moves.** Work stays on a computer if it needs that computer's not yet integrated
   state or touches the same non-mergeable files as an integration running there (e.g. binary files, large files in LFS,
   shared configuration or schema files). Everything else goes to the other building sites on its own branches. The
   coordinator merges and assigns the shared numbers (pattern 5.2 and 9).
4. **All building sites on the same main line.** After every integration, the coordinator supplies all building sites with
   the same state (e.g. push to all remotes, then pull on every computer). Before every assignment, it checks what is
   already done offline or running elsewhere, so nothing is built twice.
5. **A free workbench with a waiting block is an alarm.** If a workbench is free and an agreed block is waiting, the block
   starts at once. If the block only waits for the human's yes and the human is around, the coordinator asks right away,
   with a recommendation, instead of leaving it as "with the human". **Do not invent work:** a free workbench without a
   waiting block may rest. From practice: as long as every free workbench counted as an alarm, one night produced 37
   cross-reads and many plans that nobody needed, and the quota melted away. An idle watcher reports a free workbench with
   a waiting block after an adjustable idle time (pattern 5.12).
6. **"Done" means: release the next block in the same turn.** A pending test by the human does not block work on the
   branch; only integrating and acceptance wait for it. Known bugs for the next build are not parked "until after the
   test". From practice: the human asked "is someone already working on this?", and both workbenches were free.
7. **Priority and pauses have an end.** "Topic X has priority" means X gets the workbench first. The other tasks keep an
   owner and a next step and continue offline or on the other building site. Every pause names its reason; when the reason
   is gone (morning comes, the test is over, the quota is back), the pause ends. From practice: a night rule was not lifted
   in the morning, and a workbench stood idle for almost seven hours.
8. **The block goes to the lead in charge.** Before every block, the coordinator asks or assigns the lead session in charge
   of that field, not just any free helper. If it cannot be reached, the coordinator asks the human to open it, or says
   openly who takes the block instead.

---

## Quick check before every assignment

- Is a workbench free, and is an agreed block waiting? Then assign it at once – but do not invent a block.
- Does the block only wait for the human's yes? Then ask now, with a recommendation.
- Has the lead in charge been asked or assigned?
- Which building sites are free, and is the editor there free?
- Does the package need a not yet integrated state, or does it touch non-mergeable files of a running integration?
  Then it stays on that building site.
- Is it already done, built or running elsewhere? Look in the history and on the board first – also before asking the
  human.
- Is every building site on the current main line?

## Related sections in the pattern

5.1 Window protocol · 5.2 Shared files and numbers · 5.5 Reviews · 5.11 Delegate instead of implementing yourself ·
5.12 Leave no task lying idle · 7 Day and night mode · 9 Several computers · 11 Proven lessons (its own rhythm, define
"done" up front)
