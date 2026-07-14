<a id="exporting-top"></a>

<h1 align="center">📤 Exporting Templates</h1>

<p align="center">
  <em>Download your templates as portable JSON to back up, share, move, or hand-edit.</em>
</p>

<p align="center">
  <a href="../README.md"><img src="https://img.shields.io/badge/↩-guides-6B7280?style=for-the-badge" alt="Back to guides"></a>
</p>

---

Export lowers your live catalog back into **[Registry v1](../../../README.md#-template-schema-registry-v1) JSON** — the same format the gallery serves and [Import](importing-templates.md) accepts. Anything you export round-trips straight back in.

## From the app

In the **Templates** tab, click **Export** — you get a JSON file of your whole catalog (a `{ taskhubCatalogVersion, exportedAt, templates: [...] }` bundle). Save it, edit it, or import it on another machine.

## Via the API

`GET /api/templates/export` (authenticated) supports three shapes:

| Request | Returns |
|:---|:---|
| `GET /api/templates/export` | The **whole catalog** as a bundle. |
| `GET /api/templates/export?ids=a,b,c` | Just those template ids, same bundle shape. |
| `GET /api/templates/export?id=x` | A **single** template as a bare v1 object — nicest to hand-edit. |

Each comes back as a `Content-Disposition` download.

## What it's for

| Use case | How |
|:---|:---|
| **Back up your catalog** | Export the whole thing and keep the JSON somewhere safe. |
| **Move to another machine** | Export on one TaskHub, [Import](importing-templates.md) on another. |
| **Hand-edit a template** | `?id=x` → tweak the command/parameters → re-import (see [Updating](updating-and-managing-templates.md)). |
| **Bulk-author with an agent** | Point an AI agent at the [schema](../../../README.md#-template-schema-registry-v1); it can draft or edit a bundle you then import. |
| **Propose it to the registry** | Export, then **[open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** with the JSON to add it to the public catalog. |

> [!NOTE]
> Export reads what you actually see (including templates you imported), and emits only round-trippable entries — so an export always re-imports cleanly.

---

<p align="center">
  <a href="applying-templates.md">← Applying templates</a> ·
  <a href="../README.md">Guides</a> ·
  <a href="updating-and-managing-templates.md">Next: Updating & managing →</a>
</p>

<p align="right">(<a href="#exporting-top">back to top</a>)</p>
