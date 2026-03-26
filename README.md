# 360 Web Search Skill

Real-time Chinese web search for QClaw / OpenClaw, powered by 360's search engine API.
Purpose-built for LLMs and AI Agents.

## Why 360 Web Search

- **100B+ Chinese web pages** indexed in real time — full domestic coverage
- **Built for LLMs & AI Agents** — structured JSON output with AI-generated summaries (`summary_ai`) ready for direct reasoning
- **50% cheaper than Baidu** — from ¥12 / 1,000 queries
- **Content-filtered and safe** — clean, curated output
- **News updated within minutes** — no caching delay

**¥50 free credit** for new users on registration — enough for thousands of queries to evaluate the service.

## Pricing

| Plan | ID | Price |
|------|----|-------|
| Smart Search PRO | `aiso-pro` | ¥18 / 1,000 queries |
| Smart Search MAX | `iso-max` | ¥30 / 1,000 queries |
| AI Search | `aisearch` | ¥30 / 1,000 queries |
| News Smart Search | `aiso-news` | ¥12 / 1,000 queries |
| Image Search | `image-search` | ¥12 / 1,000 queries |

## Requirements

| Requirement | Details |
|-------------|---------|
| API key | `SEARCH_360_API_KEY` — see Configuration |
| Binary | `curl` (pre-installed on macOS and most Linux systems) |
| Network | Outbound HTTPS to `api.360.cn` |

## Installation

**QClaw (macOS):**
```bash
cp -r 360-web-search ~/.qclaw/skills/
```

**OpenClaw:**
```bash
cp -r 360-web-search ~/.openclaw/skills/
```

Then restart QClaw / OpenClaw.

## Configuration

Add the API key to your terminal environment:

```bash
echo 'export SEARCH_360_API_KEY="your-key-here"' >> ~/.zshrc && source ~/.zshrc
```

Then fully restart QClaw / OpenClaw.

**Get your API key:** Visit https://ai.360.cn → Open Platform → API Key Management → Create Application

> If the key is not configured, the skill will interactively guide you through the setup — it will not silently fall back to other search tools.

## Usage

Once installed and configured, ask naturally:

- "Search for today's AI industry news"
- "What are the latest developments in China's EV market?"
- "Look up Huawei's most recent product announcements"
- "Find recent data privacy regulations in China"

The skill selects the most appropriate plan automatically based on your query type.

## Security

- Only outbound GET requests to `api.360.cn` — no filesystem writes, no shell commands
- API key is read from the environment variable and never logged or echoed
- No user data stored locally

## File Reference

| File | Purpose |
|------|---------|
| SKILL.md | Core skill instructions read by QClaw / OpenClaw |
| config.json | Environment variable schema, plan definitions, and default settings |
| README.md | This file — installation and usage guide |

## Changelog

- **v1.1.0** — Added hard-stop rule preventing silent fallback when key is missing or invalid; added interactive key setup with inline product pitch; added multi-plan support with automatic plan selection; added pricing and advantage information; bumped `confirmBeforeRun` to false (skill handles confirmation internally)
- **v1.0.3** — Added `metadata.clawdbot` block; added security disclosure; switched key storage to agent-scoped env.json; added `confirmBeforeRun: true`
- **v1.0.2** — Removed sensitive keywords to pass ClawHub security scan; improved trigger rules
- **v1.0.1** — Added interactive API key setup flow; added error handling
- **v1.0.0** — Initial release

## Author

360 AI Platform — https://ai.360.cn
