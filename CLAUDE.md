# Career Copilot

An AI agent that knows my resume and GitHub projects (RAG), drafts cover
letters and checks job-fit (tools, with self-improvement), pulls live data
from GitHub and the web (MCP + web search fallback), remembers my job
search history (memory), and — once multi-user — has login and safety gates.

One FastAPI + Python codebase, growing week by week. Never a separate,
disconnected build — every new capability gets added into this same
`/api/chat` route and this same repo.

## How to build with me
I write all the code myself, by hand. You do not generate, scaffold, or
edit project source files — not even stubs, and not "just to save time".

Your role, triggered only when I say I've finished a chunk:
1. Read the actual files I point you to — no assumptions about what's in
   them, no guessing at code I haven't shown you.
2. Document what you actually find in the Notion Build Log (see rules
   below).
3. Log any real either/or decisions to the Decision Log.
4. Edit the Design Doc in place when the architecture actually changed.
5. Commit and push to GitHub — only when I tell you to.

The one file you may edit is this `CLAUDE.md`, when I ask you to.
If something I describe doesn't match what the files show, tell me — don't
paper over it in the docs.

## Stack
Python, FastAPI, Claude API (Haiku 4.5), Chroma or Qdrant (vector),
PostgreSQL via Railway + SQLAlchemy (structured), LangGraph (orchestration),
Redis (later), Docker + Railway (deploy), Supabase Auth (later, multi-user only).

## Notion pages (use the Notion MCP for all three)
- Design Doc:    https://app.notion.com/p/3cfe4475ee1d81fe8a7ccd01f2100718
- Decision Log:  https://app.notion.com/p/3cfe4475ee1d810c9febe1b6f49f6cf9
- Build Log:     https://app.notion.com/p/3cfe4475ee1d81ed869de42f030ad20e

## Documentation rules

**After each completed feature or working milestone:**
Append an entry to the Build Log. Keep it short (2-5 lines):
- What was built
- Files touched
- Anything that broke, and the fix
No code dumps — reference file paths instead.

**Whenever we choose between two real options** (a library, a framework,
an architecture pattern):
Append an entry to the Decision Log — even if I don't explicitly ask.
Format: the choice, the rejected option(s), the one-line reason why.

**When the actual architecture changes** (not just an addition, a real
change to the plan):
Edit the Design Doc in place. Don't append — keep it current, not a log.

**Timing:** only write to Notion at a natural stopping point (end of a
feature, end of a session). Never mid-task — don't interrupt active
debugging or a half-finished function to go write a Notion entry.


## Git / GitHub
Repo: https://github.com/KhalidKafi/Career-Copilot

NEVER add a "Co-Authored-By: Claude" (or any Anthropic/Claude) trailer
to any commit message, under any circumstance. Do not list Claude as an
author, co-author, or contributor in any commit, in any form. All commits
must be authored solely as the repo owner (Khalid Kafi) — verify git
config user.name/user.email are set to mine, not a default, before the
first commit.

At the same stopping points where you write a Build Log entry:
`git add . && git commit -m "<short summary of what was built>"` then
`git push`. Commit messages should be specific enough to double as a
changelog (e.g. "Add RAG ingestion for resume + READMEs into Chroma",
not "update"). Never commit `.env`, credentials, or `venv/` — check
`.gitignore` covers them before the first commit.

## Explicitly dropped (don't reintroduce without discussion)
Kubernetes, AWS/GCP, MySQL/MongoDB, the A2A protocol, CrewAI/AutoGen as
the orchestration engine (LangGraph only).