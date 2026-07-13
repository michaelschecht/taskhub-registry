<a id="readme-top"></a>

<h1 align="center">TaskHub Template Registry</h1>

<p align="center">
  <em>The public, versioned catalog of automation templates for TaskHub —<br>served as static JSON over a CDN, integrity-checked, and fetched at runtime.</em>
</p>

<p align="center">
  <a href="#-template-schema-registry-v1"><strong>Explore the schema »</strong></a>
</p>

<p align="center">
  <a href="https://mikesailab.com/taskhub-registry/index.json">Browse the catalog</a>
  ·
  <a href="https://github.com/michaelschecht/taskhub-registry/issues">Report an issue</a>
  ·
  <a href="https://github.com/michaelschecht/taskhub-registry/issues">Request a template</a>
</p>

<p align="center">
  <a href="https://mikesailab.com/taskhub-registry/index.json"><img src="https://img.shields.io/badge/served_via-GitHub_Pages-2ea44f?style=for-the-badge&logo=githubpages&logoColor=white" alt="Served via GitHub Pages"></a>
  <img src="https://img.shields.io/badge/schema-Registry_v1-8B5CF6?style=for-the-badge" alt="Schema: Registry v1">
  <img src="https://img.shields.io/badge/templates-24-0078D4?style=for-the-badge" alt="24 templates">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/format-JSON-000000?style=flat-square&logo=json&logoColor=white" alt="JSON">
  <img src="https://img.shields.io/badge/integrity-sha256-16A34A?style=flat-square&logo=letsencrypt&logoColor=white" alt="sha256-verified">
  <img src="https://img.shields.io/badge/line_endings-LF_pinned-6B7280?style=flat-square" alt="LF pinned">
</p>

---

## 🧩 What this is

This repository is the **decoupled catalog** for [TaskHub](https://mikesailab.com) — the unified scheduled-task manager. Instead of baking its template library into the app (and needing a redeploy to change it), TaskHub reads the catalog from **here**, at runtime.

It's just data: an `index.json` manifest plus one JSON file per template. It is served as static files over **GitHub Pages** at:

> **`https://mikesailab.com/taskhub-registry`**

A running TaskHub backend points `TEMPLATE_REGISTRY_URL` at that address, fetches the catalog, verifies every file, and syncs it in — so publishing a template is a push to this repo, never an app deploy.

## 📦 What's inside

| File | What it holds |
|:---|:---|
| [**`index.json`**](https://mikesailab.com/taskhub-registry/index.json) | The manifest: `registryVersion`, `updatedAt`, and one lightweight entry per template (id, name, description, category, tags, runtime, os, `compatibleTargets`, the file `path`, and its `sha256`). Enough to render a catalog without fetching every file. |
| **`templates/<id>.json`** | One full [Registry v1](#-template-schema-registry-v1) template per file — the abstract Trigger → Action definition plus its `{{placeholder}}` parameters. |
| `.nojekyll` | Tells GitHub Pages to serve the files raw (no Jekyll processing). |
| `.gitattributes` | Pins every file to **LF** line endings — the `sha256` is computed over exact bytes, so a CRLF rewrite would break every checksum. |

Today the catalog holds **24 templates** — 20 parameterized script starters (PowerShell / Bash / Python / Node / executable / HTTP / …) and 4 use-case patterns (database backup, system cleanup, news digest, PR triage).

## 🔌 How TaskHub consumes it

The backend's `RegistryCatalogSource` treats this catalog as **untrusted, executable content** and defends accordingly:

1. Fetch `index.json`.
2. Fetch each `templates/<id>.json`.
3. **Verify each file's bytes against the index `sha256`** — any mismatch aborts the whole fetch (no partial or unverified seeding).
4. Validate each template against the Registry v1 schema.
5. Cache the result, and **fall back to the app's compiled-in bundled snapshot** on any failure (offline, 404, bad checksum) — so TaskHub always has a working catalog.

> [!NOTE]
> A template is **target-agnostic**. It describes the automation abstractly (a trigger + an action) and is *compiled* to a target's native config at apply time. Only Windows Task Scheduler and TaskHub-native targets have real compilers today; a declared-but-uncompiled target is an honest "copy to set up manually" path, never a silent failure.

<a id="-template-schema-registry-v1"></a>

## 🧬 Template schema (Registry v1)

Each `templates/<id>.json` is a self-contained template:

```json
{
  "schemaVersion": "1.0",
  "id": "tpl_starter_powershell_script",
  "name": "PowerShell Script",
  "description": "Run a PowerShell script on a schedule.",
  "runtime": "powershell",
  "os": "windows",
  "category": "system",
  "tags": ["windows", "powershell", "script"],
  "trigger": { "kind": "schedule", "cron": "0 9 * * *" },
  "commandTemplate": "powershell.exe -NoProfile -File \"{{scriptPath}}\"",
  "parameters": [
    { "key": "scriptPath", "label": "Script file path", "type": "path", "required": true }
  ],
  "compatibleTargets": ["windows"]
}
```

| Field | Meaning |
|:---|:---|
| `schemaVersion` | Always `"1.0"` for this registry. |
| `id` | Stable unique id (kebab / `tpl_*`). Favorites and applied tasks key off it, so it never changes. |
| `runtime` / `os` / `category` / `tags` | Classification for search, filtering, and grouping. |
| `trigger` | The abstract schedule — `{ "kind": "schedule", "cron": "<5-field UTC cron>" }`. |
| `commandTemplate` **or** `action` | What runs. `commandTemplate` is a command string with `{{placeholders}}`; the structured `action` form (`{ "kind": "exec", "program", "args": [] }`) is **no-shell** by design. |
| `parameters` | The `{{placeholder}}` inputs a user fills in (key, label, type, required, options…). |
| `compatibleTargets` | Where it *can* run (`windows`, `taskhub-native`, `macos`, `linux`, `claude-code`, `chatgpt`). Real only where a compiler exists. |

> [!IMPORTANT]
> Placeholders are substituted **server-side, per token**, and structured actions never touch a shell — a `{{placeholder}}` value is always exactly one argument to the intended program, so it can't inject a second command.

## 🛠️ How this repo is maintained

This repo is a **published mirror**. The source of truth is the TaskHub app's `registry/` folder (generated from a bundled catalog and drift-tested in CI); a publish script copies `index.json` + `templates/` here and pushes, and GitHub Pages rebuilds within about a minute.

That means **template content here is generated, not hand-edited** — an edit to `index.json` or a `templates/*.json` file would be overwritten on the next publish (and would break its `sha256`). This repo *does* own its own `README.md`, `.nojekyll`, and `.gitattributes`.

To propose a new template or a change, **[open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** describing the automation (trigger, command, parameters, target).

## 🗺️ Where this is heading

Right now a TaskHub install auto-syncs this whole catalog. As the catalog grows toward hundreds of templates (developer, AI/agent, and the full automation taxonomy), the plan is a **browsable gallery site** over this registry — search and filter the catalog, then **import** just the templates you want into your local TaskHub (the app already supports importing template JSON). This repo is the backing store for that gallery, and the natural home for community-contributed templates once TaskHub goes public.

## 🔗 Links

| | |
|:---|:---|
| [**Live catalog (index.json)**](https://mikesailab.com/taskhub-registry/index.json) | The manifest this registry serves. |
| [**Issues**](https://github.com/michaelschecht/taskhub-registry/issues) | Report a problem or request/propose a template. |
| [**TaskHub**](https://mikesailab.com) | The app this catalog powers. |

---

<p align="center">
  <sub>Static template registry for <a href="https://mikesailab.com">TaskHub</a> · served via GitHub Pages · content-addressed with sha256</sub>
</p>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
