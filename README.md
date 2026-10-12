# Awesome Hermes Agent

> Skills, personalities, and recipes for [Hermes Agent](https://github.com/NousResearch/hermes-agent) — the self-improving AI agent runtime by Nous Research.

A community-curated collection of drop-in SKILL.md files, ready-made personalities, real-world recipes, and migration guides for Hermes. Maintained by [@mustafaergisi](https://x.com/mustafaergisi).

If you've installed Hermes and aren't sure what to build first, this repo is a starting library. Everything here is MIT-licensed, paste-ready, and tested on a real Hermes install.

## Contents

- [🛠 Skills](#-skills) — drop-in `SKILL.md` files for common workflows
- [🎭 Personalities](#-personalities) — pre-written `personality.md` files for typical roles
- [📖 Recipes](#-recipes) — real-world walkthroughs combining skills + personalities
- [🔌 Plugins & Extensions](#-plugins--extensions) — community Hermes plugins worth knowing
- [🧩 MCP Servers](#-mcp-servers) — MCP integrations that pair well with Hermes
- [📚 Migration Guides](#-migration-guides) — moving from OpenClaw, CrewAI, or LangChain
- [🌟 Showcases](#-showcases) — public Hermes deployments worth studying
- [Contributing](#contributing)

---

## 🛠 Skills

Drop-in `SKILL.md` files following the [agentskills.io](https://agentskills.io) standard. Each skill is in its own directory under [`skills/`](./skills) with a self-contained README and the SKILL.md itself.

| Skill | What it does | Best paired with |
|---|---|---|
| [`github-issue-triage`](./skills/github-issue-triage) | Auto-labels new issues, asks for repro on bug reports, closes obvious duplicates with a link to the canonical thread | `triager` personality |
| [`pr-first-review`](./skills/pr-first-review) | First-pass PR review covering OWASP Top 10, style, scope creep, and breaking-change detection. Comments before you look. | `triager` personality |
| [`weekly-mrr-digest`](./skills/weekly-mrr-digest) | Pulls Stripe + Mixpanel + GA4 once a week, computes MRR / churn / ARPU / activation, sends a digest to Slack | any analyst personality |
| [`competitor-landing-watch`](./skills/competitor-landing-watch) | Daily diff of competitor landing pages — pricing changes, hero copy swaps, new features mentioned. Flags meaningful changes only. | `closer` personality |
| [`cold-email-personalize`](./skills/cold-email-personalize) | Writes signal-driven first lines for cold outreach: leads with a recent hire, product launch, podcast quote, or funding round. Avoids generic "I noticed your company..." openers. | `closer` personality |

Install:

```bash
mkdir -p ~/.hermes/skills/<skill-name>
cp skills/<skill-name>/SKILL.md ~/.hermes/skills/<skill-name>/SKILL.md
hermes
> /<skill-name>
```

## 🎭 Personalities

Pre-written `personality.md` files. Drop into `~/.hermes/personalities/` and activate with `/personality <name>`.

| Personality | Voice | Use case |
|---|---|---|
| [`echo`](./personalities/echo.md) | Diplomatic but firm content writer; pro-Oxford-comma, anti-passive-voice | Blog posts, marketing copy, newsletters |
| [`closer`](./personalities/closer.md) | Direct, signal-driven sales assistant; refuses Mad-Libs templates | Cold outreach, follow-up sequences, pipeline triage |
| [`triager`](./personalities/triager.md) | Patient OSS maintainer; defers to humans on hard architectural calls | GitHub issue triage, PR review, changelog drafting |

Each one is calibrated for a specific job. Edit them — they're starting points, not finals.

Install:

```bash
mkdir -p ~/.hermes/personalities
cp personalities/<name>.md ~/.hermes/personalities/<name>.md
hermes
> /personality <name>
```

## 📖 Recipes

Long-form walkthroughs combining skills + personalities for a real workflow. Each recipe documents what to install, how to wire it together, and what the first week of running it actually looks like.

| Recipe | Scenario | Skills + personalities |
|---|---|---|
| _Coming soon_ — Solo OSS maintainer setup | Triage 200+ issues / month with 1 person | `triager` + `github-issue-triage` + `pr-first-review` |
| _Coming soon_ — Indie SaaS weekly metrics | Founder-grade analytics without a data hire | `weekly-mrr-digest` + custom dashboards |
| _Coming soon_ — Two-person sales outbound | 50-100 cold emails/week with reply rate >5% | `closer` + `cold-email-personalize` + `competitor-landing-watch` |

Recipes land as we ship them. PRs welcome.

## 🔌 Plugins & Extensions

Community Hermes plugins that extend the base runtime. (We track these but don't host them — links go to the maintainers' repos.)

- _Add your plugin here via PR._

## 🧩 MCP Servers

Hermes supports the [Model Context Protocol](https://modelcontextprotocol.io). MCP servers worth knowing:

- [Aident Loadout](https://aident.ai) — Remote MCP server that connects Hermes and other MCP clients to 1,000+ apps and 400+ expert-built Skills through one setup (OAuth in the browser; credentials stay in Aident Vault). Endpoint: `https://loadout.aident.ai/mcp`. Skill/repo: [Aident-AI/aident-skill](https://github.com/Aident-AI/aident-skill) (MIT).

## 📚 Migration Guides

Moving an existing agent setup to Hermes.

- **From OpenClaw**: `hermes claw migrate` imports your memories, API keys, and gateway settings automatically. For the agent definition itself (SOUL.md → personality.md + SKILL.md), use the [free converter](https://crewclaw.com/tools/soul-to-hermes) and follow the [migration walkthrough](https://crewclaw.com/blog/migrate-openclaw-soul-md-to-hermes).
- **From CrewAI / LangGraph / AutoGen**: _Coming soon._
- **From a single ChatGPT custom GPT**: _Coming soon._

## 🌟 Showcases

Public Hermes deployments worth studying — open-source agents people are actually running in production.

- _Add your showcase here via PR._ Include a one-liner about what it does and a link to the repo.

---

## Contributing

PRs welcome for:

- New skills (must include a `SKILL.md` with agentskills.io frontmatter and a directory `README.md` with install + use cases)
- New personalities (must include a `personality.md` with frontmatter and a clear voice)
- Recipes (real-world walkthroughs, must reference existing skills/personalities or contribute new ones in the same PR)
- Curated list additions (plugins, MCP servers, showcases)

Style guide:

- Write in plain English. No marketing fluff, no "delve into," no em-dashes inside dialogue.
- Each skill description should be falsifiable — "What it does" + "What it doesn't do."
- Don't claim "60 seconds" or "no coding required" — they're not true.
- License: MIT for everything in this repo.

## Want pre-built multi-agent crews?

If you'd rather buy a ready-to-use 4-5 agent team than wire up individual skills, [crewclaw.com/use-cases](https://crewclaw.com/use-cases) ships 17 multi-agent bundles (Sales Outreach, GitHub Maintainer, Content Pipeline, DevOps Automation, etc.). Each bundle is convertable to either OpenClaw or Hermes. Source code is yours.

## License

[MIT](./LICENSE) © 2026 Mustafa Ergisi and contributors.
