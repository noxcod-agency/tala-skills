# Tala agent skills

[![skills.sh](https://skills.sh/b/noxcod-agency/tala-skills)](https://skills.sh/noxcod-agency/tala-skills)

Agent skills for [Tala](https://www.tala-assistant.com), AI phone agents that answer your business calls, qualify callers and transfer them.

With this skill, your coding or chat assistant knows how to:

- connect ChatGPT, Claude or Claude Code to Tala's read-only connector, then answer "show my latest calls" or "summarize this call";
- use the Tala public API to list agents, read call history and results, and start an outbound call only after your confirmation;
- receive post-call webhooks in a CRM, Zapier, Make or n8n, and handle repeated deliveries.

## Install

```bash
npx skills add noxcod-agency/tala-skills
```

The skill installs in Claude Code, Codex, Cursor and the other agents supported by the [skills CLI](https://github.com/vercel-labs/skills). Tala documents its read-only connector for ChatGPT, Claude and Claude Code.

## Skills

| Skill | What it does |
| --- | --- |
| [`tala-voice-agents`](skills/tala-voice-agents/SKILL.md) | Read-only connector, public API (agents, calls, results) and post-call webhooks |

## Links

- Website: <https://www.tala-assistant.com>
- Create an account: <https://app.tala-assistant.com/handler/sign-up>
- Documentation: <https://docs.tala-assistant.com>
- ChatGPT and Claude connector: <https://docs.tala-assistant.com/integrations/chatgpt-claude> (in French: <https://docs.tala-assistant.com/integrations/chatgpt-claude-fr>)
- Public API: <https://docs.tala-assistant.com/api/trigger-calls>
- Post-call webhooks: <https://docs.tala-assistant.com/features/webhooks>
- Support: <https://docs.tala-assistant.com/support>

## License

[MIT](LICENSE)
