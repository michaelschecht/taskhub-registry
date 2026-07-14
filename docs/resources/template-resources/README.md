<a id="template-resources-top"></a>

<h1 align="center">🧰 Template Resources</h1>

<p align="center">
  <em>Where to find, adapt, and collect automation templates for the TaskHub registry —<br>scheduling references, script libraries, workflow galleries, and community sources.</em>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/type-curated_links-8B5CF6?style=for-the-badge" alt="Curated links">
  <a href="../../../README.md"><img src="https://img.shields.io/badge/↩-registry_root-6B7280?style=for-the-badge" alt="Back to registry root"></a>
</p>

---

## 🧭 What this is

A curated map of **places to source scheduled-task and automation ideas** — cron jobs, PowerShell/Bash/Python scripts, AI-agent routines, and workflow patterns — that can be adapted into [Registry v1](../../../README.md#-template-schema-registry-v1) templates for TaskHub.

> [!NOTE]
> A TaskHub template is **target-agnostic** (a trigger + an action + `{{placeholders}}`) and runs **no-shell** by design. When adapting anything below, keep the command structured (`{executable, args[]}` or an explicit `cmd.exe /c` / `powershell -Command` opt-in) and pull user-specific bits out into parameters. See the [schema](../../../README.md#-template-schema-registry-v1) before authoring, and **[open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** to propose one.

## 📅 Scheduling & cron references

| Resource | What you'll find |
|:---|:---|
| [**crontab.guru**](https://crontab.guru/) | Sanity-check and design 5-field cron expressions (TaskHub stores cron in UTC). |
| [**Windows Task Scheduler docs**](https://learn.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page) | The platform the Windows agent wraps — triggers, actions, principals. |
| [**systemd timers (Arch Wiki)**](https://wiki.archlinux.org/title/Systemd/Timers) | Linux scheduling patterns (`OnCalendar`) — good source of interval/calendar ideas. |
| [**launchd.info**](https://www.launchd.info/) | macOS `launchd` reference — the target for the (planned) macOS agent. |

## 🐚 Script & command libraries

| Resource | What you'll find |
|:---|:---|
| [**PowerShell Gallery**](https://www.powershellgallery.com/) | Thousands of PowerShell scripts & modules — a rich source of Windows automations. |
| [**SS64**](https://ss64.com/) | Concise command references for [PowerShell](https://ss64.com/ps/), [CMD](https://ss64.com/nt/), [Bash](https://ss64.com/bash/), and macOS — ideal for getting a one-liner exactly right. |
| [**Microsoft Learn — PowerShell**](https://learn.microsoft.com/en-us/powershell/) | Official cmdlet docs and scripting samples. |
| [**GitHub Gist (search)**](https://gist.github.com/search?q=cron+OR+scheduled+task) | Single-file scripts people share — search `cron`, `scheduled task`, `powershell`, etc. |

## ⭐ Curated "awesome" lists

| List | Focus |
|:---|:---|
| [**awesome-powershell**](https://github.com/janikvonrotz/awesome-powershell) | Modules, scripts, and tools for Windows automation. |
| [**awesome-shell**](https://github.com/alebcay/awesome-shell) | Shell frameworks, utilities, and command-line goodies. |
| [**awesome-bash**](https://github.com/awesome-lists/awesome-bash) | Bash-specific scripts, snippets, and references. |
| [**awesome-cli-apps**](https://github.com/agarrharr/awesome-cli-apps) | Command-line apps worth scheduling (backups, sync, media, dev). |
| [**awesome-selfhosted**](https://github.com/awesome-selfhosted/awesome-selfhosted) | Self-hosted software — a wellspring of homelab cron/backup/monitoring jobs. |

## 🔗 Automation platform template galleries

Adapt the *idea* (trigger + steps) into a scheduled command; these are mostly SaaS-flow galleries, not scripts.

| Gallery | What you'll find |
|:---|:---|
| [**n8n workflow templates**](https://n8n.io/workflows/) | Thousands of open workflow templates — great for AI/agent and integration patterns. |
| [**Node-RED flows library**](https://flows.nodered.org/) | Community flows for IoT, monitoring, and home automation. |
| [**Windmill Hub**](https://hub.windmill.dev/) | Scripts and flows (TypeScript / Python / Bash) built for scheduling. |
| [**Home Assistant blueprints**](https://community.home-assistant.io/c/blueprints-exchange/53) | Automation blueprints — many map cleanly to scheduled triggers. |
| [**Zapier templates**](https://zapier.com/templates) · [**Make templates**](https://www.make.com/en/templates) · [**IFTTT**](https://ifttt.com/explore) | No-code automation catalogs — useful for discovering *what* people automate. |
| [**Pipedream**](https://pipedream.com/apps) · [**Activepieces**](https://www.activepieces.com/) | Developer-first workflow platforms with open component/template libraries. |

## ⚙️ CI / workflow templates

| Resource | What you'll find |
|:---|:---|
| [**GitHub Actions starter workflows**](https://github.com/actions/starter-workflows) | Official CI/CD workflow templates — build/test/deploy patterns. |
| [**GitHub Marketplace (Actions)**](https://github.com/marketplace?type=actions) | Reusable actions; the scheduled (`on: schedule`) ones are cron-job inspiration. |
| [**Ofelia**](https://github.com/mcuadros/ofelia) | A Docker job scheduler — good reference for container-based scheduled tasks. |

## 🤖 AI-agent & LLM workflows

| Resource | What you'll find |
|:---|:---|
| [**Claude Code docs**](https://docs.claude.com/en/docs/claude-code) | Headless/`-p` runs, permission modes, allowed-tools — the basis of the AI Pack. |
| [**Anthropic Prompt Library**](https://docs.claude.com/en/resources/prompt-library/library) | Ready-made prompts to schedule as digest/triage/report jobs. |
| [**OpenAI Codex CLI**](https://github.com/openai/codex) | `codex exec` non-interactive runs — the basis of the Codex templates. |
| [**ChatGPT Tasks**](https://chatgpt.com/) · [**Gemini Scheduled**](https://gemini.google.com/) | Native AI schedulers — quick-link targets and pattern inspiration. |

## 💬 Communities

| Community | Why it's useful |
|:---|:---|
| [**r/PowerShell**](https://www.reddit.com/r/PowerShell/) · [**r/sysadmin**](https://www.reddit.com/r/sysadmin/) | Real-world Windows automation scripts and scheduled-task war stories. |
| [**r/selfhosted**](https://www.reddit.com/r/selfhosted/) · [**r/homelab**](https://www.reddit.com/r/homelab/) | Backup, monitoring, and maintenance cron jobs from self-hosters. |
| [**Stack Overflow**](https://stackoverflow.com/questions/tagged/scheduled-tasks) | Tags: [`scheduled-tasks`](https://stackoverflow.com/questions/tagged/scheduled-tasks), [`cron`](https://stackoverflow.com/questions/tagged/cron), [`powershell`](https://stackoverflow.com/questions/tagged/powershell). |

## ➕ Turn a resource into a template

1. Pick an automation and reduce it to a **command** + a **schedule**.
2. Pull the machine-specific bits (paths, names, URLs) out into **`{{placeholders}}`** with `parameters`.
3. Keep it **no-shell** where possible (`{executable, args[]}`); opt into a shell explicitly only for redirection/pipes (`cmd.exe /c "…"`, `powershell.exe -Command "…"`).
4. Match the [Registry v1 schema](../../../README.md#-template-schema-registry-v1), then **[open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** to propose it — or import it straight into your own TaskHub via the [gallery](https://mikesailab.com/taskhub-registry/).

---

<p align="center">
  <a href="../../../README.md">← TaskHub Template Registry</a> ·
  <a href="https://mikesailab.com/taskhub-registry/">Browse the gallery</a> ·
  <a href="https://github.com/michaelschecht/taskhub-registry/issues">Propose a template</a>
</p>

<p align="right">(<a href="#template-resources-top">back to top</a>)</p>
