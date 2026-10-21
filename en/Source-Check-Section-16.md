# Source check for section 16 (comparison with cloud offerings)

As of 2026-10-21, 17:40 · belongs to [AI-Coordinator-Pattern.md](AI-Coordinator-Pattern.md) version 4.1, section 16

**Method:** An external worker (another model) had done the research; several of its links were wrong. On the evening
of 21 Oct, every claim was checked against official pages: first by a checking helper (read only), then the most
important points were opened again first-hand (column "own check"). Paraphrased, not quoted word for word.

**Rating:** verified = claim found on the page · partly = right at its core, note the limitation ·
not found = page opened, the claim is not there.

## Sources (each retrieved 2026-10-21)

| Code | Page | Date on the page |
|---|---|---|
| D1 | `https://code.claude.com/docs/en/claude-projects` (Projects in Claude Code) | none |
| D2 | `https://code.claude.com/docs/en/data-usage` (Claude Code data usage) | none |
| D3 | `https://code.claude.com/docs/en/routines` (Scheduled tasks) | none |
| B1 | `https://claude.com/blog/projects-redesigned` ("Projects redesigned: from folder to conversation") | 2026-09-17 |
| H1 | `https://support.claude.com/en/articles/11145838-use-claude-code-with-your-pro-or-max-plan` | "updated this week" |
| H2 | `https://support.claude.com/en/articles/11049741-what-is-the-max-plan` | "updated over a week ago" |
| P1 | `https://claude.com/pricing` (pricing) | none |
| P2 | `https://privacy.claude.com/en/articles/10023548-how-long-do-you-store-my-data` | 2026-07-01 |
| X1 | `https://learn.chatgpt.com/docs/cloud` (OpenAI Codex Cloud, redirected from developers.openai.com) | none |
| X2 | `https://jules.google/docs` (Google Jules) | none |

## Result per claim

| No. | Claim from the research | Result | What the source says | Source | Own check |
|---|---|---|---|---|---|
| 1 | Projects is a public beta for Pro and Max, rolled out step by step, not yet for Team/Enterprise | verified | exactly so; rolled out first to accounts with cloud sessions and without old projects in claude.ai | D1, B1 | yes |
| 2 | A coordinator conversation starts tasks as parallel cloud threads; single threads via Remote Control on your own computer | verified | one thread per task; locally from Claude Code v2.1.280, only while the computer is awake, not with "Require trusted devices" | D1 | yes |
| 3 | Own clone and branch per thread, a pull request at the end, the human merges | partly | own branch and own sandbox are right; pull request only if the work calls for it; merging by button ("Merge it"), the page does not say the human must do it | D1 | yes |
| 4 | Shared project memory and library | partly | memory as files with the index `MEMORY.md`, every cloud thread reads it at start; library = added files and files created by threads | D1 | yes |
| 5 | Parallel threads draw on the same 5-hour and weekly quota | verified | projects use the same plan limits as other Claude Code sessions and use them up faster; the limits are shared between Claude and Claude Code | D1, H1 | yes |
| 6 | Number of threads and model can be limited in the project settings | partly | model and reasoning effort of the threads: yes (Project settings > General). Number of threads: only as a request in the conversation, explicitly no upper limit; hard limit of 200 new threads per day | D1 | yes |
| 7 | Only Claude models | verified (in substance) | Anthropic is the model provider in both cases (cloud, Remote Control) | D1 | yes |
| 8 | Prices Pro $20, Max $100/200, Team per seat | verified | Pro $20/month ($17 with annual billing, $200 up front); Max 5x $100, Max 20x $200; Team Standard $25 ($20 annually), Premium $125 ($100 annually); prices may change | P1, H2 | yes (P1) |
| 9 | Privacy: personal accounts 5 years with training, otherwise 30 days; business accounts no training; /feedback 5 years | verified | exactly so; business accounts 30 days by default; `/feedback`, `/bug`, `/share` 5 years; cloud session: repository in an isolated VM, GitHub access stays on Anthropic servers | D2, P2 | yes (D2) |
| 10 | Announced on 2026-09-17 | verified | blog post from 2026-09-17 | B1 | yes |
| 11 | Scheduled tasks ("formerly routines") are a research preview and run in the cloud | verified | yes; also possible in a self-hosted environment; Pro, Max, Team, Enterprise | D3 | no |
| 12 | Similar offerings from other providers | spot check | Codex Cloud: own working environment per task, commit/PR by the user, no coordinator described. Jules: clones the repository into a VM; coordinator or parallel runs not found. Only one page checked for each | X1, X2 | no |

## Additional findings (important for context)

- **Cost default:** A new project runs all threads with the largest model and high reasoning effort; according to
  D1 this uses up the plan fastest. On Pro you reach the limit sooner on such days. (D1)
- **Blog and docs differ:** On 17 Sep the blog said local threads would come "soon"; the docs now describe them as
  available. The docs are authoritative. (B1, D1)
- **Same name:** The "Projects" row on the pricing page means the older projects in claude.ai (chats and project
  knowledge), not the Projects in Claude Code. (P1, D1)
- **Limits of the beta:** not in the terminal CLI, in VS Code or JetBrains; a project belongs to exactly one user and
  cannot be shared; no control at the organization level; local sessions you started yourself cannot be added;
  a cloud sandbox can restart, and uncommitted changes are then lost. (D1)
- **Max plans** also have their own weekly limit for a specific model. (H1)

## Not checked

- Launch dates of the other offerings (cloud sessions, Remote Control, Agent Teams, Managed Agents) from the research:
  not needed for section 16, so not checked.
- The older projects in claude.ai (since 2024-06-25) had already been checked against
  `https://www.anthropic.com/news/projects` before and were not opened again here.
