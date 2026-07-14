<a id="resources-top"></a>

<h1 align="center">🧰 Resources</h1>

<p align="center">
  <em>Curated external sources for finding, adapting, and collecting<br>automation templates for the TaskHub registry.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/resources-curated-8B5CF6?style=for-the-badge" alt="Curated resources">
  <a href="../../README.md"><img src="https://img.shields.io/badge/↩-registry_root-6B7280?style=for-the-badge" alt="Back to registry root"></a>
</p>

---

## 🧭 What's here

Places to source scheduled-task and automation ideas — cron jobs, scripts, AI-agent routines, and workflow patterns — that can be adapted into [Registry v1](../../README.md#-template-schema-registry-v1) templates.

> [!NOTE]
> A TaskHub template is **target-agnostic** (a trigger + an action + `{{placeholders}}`) and runs **no-shell** by design. When adapting anything below, keep the command structured (`{executable, args[]}` or an explicit `cmd.exe /c` / `powershell -Command` opt-in) and pull user-specific bits out into parameters. See the [schema](../../README.md#-template-schema-registry-v1) before authoring, and **[open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** to propose one.

## 📂 Categories

| Category | What's inside |
|:---|:---|
| [**📅 Scheduling & cron references**](template-resources/scheduling-and-cron.md) | crontab.guru, Windows Task Scheduler, systemd timers, launchd. |
| [**🐚 Script & command libraries**](template-resources/script-libraries.md) | PowerShell Gallery, SS64, Microsoft Learn, GitHub Gists. |
| [**⭐ Curated "awesome" lists**](template-resources/awesome-lists.md) | awesome-powershell / -shell / -bash / -cli-apps / -selfhosted. |
| [**🔗 Automation platform galleries**](template-resources/automation-platforms.md) | n8n, Node-RED, Windmill, Home Assistant, Zapier / Make / IFTTT, Pipedream / Activepieces. |
| [**⚙️ CI / workflow templates**](template-resources/ci-workflow-templates.md) | GitHub Actions starter workflows, Marketplace, Ofelia. |
| [**🤖 AI-agent & LLM workflows**](template-resources/ai-agent-workflows.md) | Claude Code docs, Anthropic Prompt Library, Codex CLI, ChatGPT/Gemini. |
| [**💬 Communities**](template-resources/communities.md) | r/PowerShell, r/sysadmin, r/selfhosted, r/homelab, Stack Overflow. |

## ➕ Turn a resource into a template

1. Pick an automation and reduce it to a **command** + a **schedule**.
2. Pull the machine-specific bits (paths, names, URLs) out into **`{{placeholders}}`** with `parameters`.
3. Keep it **no-shell** where possible (`{executable, args[]}`); opt into a shell explicitly only for redirection/pipes (`cmd.exe /c "…"`, `powershell.exe -Command "…"`).
4. Match the [Registry v1 schema](../../README.md#-template-schema-registry-v1), then **[open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** to propose it — or import it into your own TaskHub via the [gallery](https://mikesailab.com/taskhub-registry/). See the [Template Guides](../guides/README.md) for the import/apply/export/update flow.

---

<p align="center">
  <a href="../../README.md">← TaskHub Template Registry</a> ·
  <a href="../guides/README.md">Template Guides</a> ·
  <a href="https://mikesailab.com/taskhub-registry/">Browse the gallery</a>
</p>

<p align="right">(<a href="#resources-top">back to top</a>)</p>
