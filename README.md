# Orkestr

Orkestr is an open-source Claude Code plugin that runs your software project like a small autonomous AI company: it plans, holds bounded meetings with decision records, builds tasks in safe parallel waves, reviews work against real evidence, and reports status and retrospectives. Everything lives in local files; no paid services are added.

Full documentation: [plugins/orkestr/README.md](plugins/orkestr/README.md)

## Quick install

Inside Claude Code:

```
/plugin marketplace add alperglcoglu/orkestr
/plugin install orkestr@orkestr
```

Then, in the project you want to manage:

```
/orkestr:run A simple to-do list app; free tools only; with tests
```

## Data and privacy

Orkestr sends no data anywhere. It has no server, no telemetry, and no MCP servers, and its scripts never open a network connection. Model calls are made by Claude Code itself, under your own Claude Code account.

- **What it stores:** project state (plans, tasks, meetings, decisions, reviews, reports) as local files in a `.orkestr/` folder inside the project you manage.
- **What it reads:** only that project's files and the tool calls Claude Code passes to its guard hook.
- **Credentials:** Orkestr never reads credentials, environment variables, or key files. It contains patterns for common secret formats (for example API keys and tokens) only to keep secrets *out* of its records: matching text is replaced with `[REDACTED]` before saving, and `validate` flags any secret it finds in `.orkestr/`.
- **Guard hook:** a local `PreToolUse` hook that asks for your confirmation before risky commands such as `git push`, publishing, deploying, or recursive deletes. It only inspects the command text; it never runs anything or sends it anywhere.

## License

[MIT](LICENSE)
