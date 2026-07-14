<a id="importing-top"></a>

<h1 align="center">📥 Importing Templates</h1>

<p align="center">
  <em>Find a template in the gallery and add it to your TaskHub — no reseed, no redeploy.</em>
</p>

<p align="center">
  <a href="../README.md"><img src="https://img.shields.io/badge/↩-guides-6B7280?style=for-the-badge" alt="Back to guides"></a>
</p>

---

## 1. Find a template in the gallery

Open the **[Template Gallery](https://mikesailab.com/taskhub-registry/)** and browse or filter by **category, platform, runtime, tag**, or **availability** (Built-in vs. Import on demand). Click any card to see its full details — schedule, command, parameters, and which targets it can run on.

> [!NOTE]
> Cards badged **Built-in** already ship with TaskHub — you don't need to import those. The **Import** flow is for the rest.

## 2. Get the template JSON

On a card or its detail page:

- **Download** → saves a single `<id>.json` file (Registry v1 format).
- **Copy** → copies the JSON to your clipboard (handy for hand-editing or the API).

## 3. Import it into TaskHub

In the TaskHub app:

1. Go to the **Templates** tab.
2. Click **Import**.
3. Select the `<id>.json` file you downloaded.

TaskHub validates the file the same way it validates every built-in template — the [Registry v1 schema](../../../README.md#-template-schema-registry-v1) **plus** a `{{placeholder}}` resolvability check — then adds it to your catalog. You'll see a toast like **`1 added, 0 updated, 0 skipped`**. The template now appears in your Templates tab, ready to [**Apply**](applying-templates.md).

> [!TIP]
> The import accepts a **single template**, an **array**, or a full **`{ templates: [...] }` bundle** — so you can import many at once (e.g. a whole [export](exporting-templates.md) from another machine).

## What to expect

| | |
|:---|:---|
| **It's yours to keep** | Imported templates persist in your catalog. They're never removed by the automatic registry sync (only auto-managed built-ins are). |
| **Safe by design** | A bad entry in a multi-template file is reported and skipped — the rest still import. A malformed or unfillable template is rejected with a clear reason. |
| **Re-import = update** | Importing a template whose `id` you already have **updates it in place** (see [Updating](updating-and-managing-templates.md)). Avoid re-using a built-in `core` id — the next sync would overwrite your copy. |
| **No shell surprises** | Every command is validated as untrusted content and structured no-shell — a placeholder value is always exactly one argument to the intended program. |

## Troubleshooting

- **"Import failed — that file is not valid JSON."** — You picked a non-JSON file, or it was edited into invalid JSON. Re-download from the gallery.
- **"K skipped"** — One or more entries failed validation (unknown field, undeclared `{{placeholder}}`, empty command). The toast names the first issue; fix it and re-import.
- **Nothing happens / backend error** — Make sure the TaskHub backend is running.

---

<p align="center">
  <a href="../README.md">← Guides</a> ·
  <a href="applying-templates.md">Next: Applying templates →</a>
</p>

<p align="right">(<a href="#importing-top">back to top</a>)</p>
