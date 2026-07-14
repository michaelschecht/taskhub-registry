<a id="updating-top"></a>

<h1 align="center">🔄 Updating &amp; Managing Templates</h1>

<p align="center">
  <em>How built-in and imported templates update, how to edit one, and how to grow your catalog.</em>
</p>

<p align="center">
  <a href="../README.md"><img src="https://img.shields.io/badge/↩-guides-6B7280?style=for-the-badge" alt="Back to guides"></a>
</p>

---

## Two kinds of templates

TaskHub's catalog is a mix of two things, and they update differently:

| Kind | Where it comes from | How it updates |
|:---|:---|:---|
| **Built-in (`core`)** | Ships with TaskHub; auto-synced from the registry. | **Automatically.** TaskHub re-syncs the curated core from the registry on a schedule — improvements land on their own, and a template dropped from core is removed. You don't manage these. |
| **Imported / custom** | You [imported](importing-templates.md) it, or used **Save as template**. | **You manage it.** It stays exactly as you left it and is never touched by the automatic sync. |

> [!NOTE]
> This is the safety guarantee: the automatic sync only ever touches **built-in** templates. Anything **you** added stays put until **you** change it.

## Updating an imported / custom template

There's no in-app template editor — you update by **re-importing**:

1. [**Export**](exporting-templates.md) the template you want to change: `GET /api/templates/export?id=<id>` (or grab a fresh copy from the [gallery](https://mikesailab.com/taskhub-registry/)).
2. Edit the JSON — the command, `parameters`, schedule, tags, etc. Keep the **same `id`**.
3. [**Import**](importing-templates.md) it again. Because import **upserts by `id`**, your edited version replaces the old one in place. The toast will say **`0 added, 1 updated, …`**.

> [!WARNING]
> Don't re-use a **built-in `core`** id for a custom edit — the next automatic sync would overwrite your changes with the authoritative version. Give custom templates their own id.

## Growing your catalog

| Action | How | Result |
|:---|:---|:---|
| **Add from the gallery** | [Import](importing-templates.md) a downloaded template. | A new template in your catalog. |
| **Save a real task as a template** | In a task's detail modal, click **Save as template**. | TaskHub derives a Registry v1 template from that task's command + schedule and adds it (with a fresh id). |
| **Favorite** | Click the ⭐ on a card / row. | Pins it to the top and to the **Favorites** filter (per-user; never changes the shared catalog). |

## Removing a template

- **Built-in** templates come and go with the registry — if one is retired from core, the next sync removes it automatically.
- **Imported / custom** templates persist by design (they're protected from the sync). A per-template delete control isn't in the UI yet — for now, the automatic prune only applies to built-ins.

## Proposing a change to the public registry

Found a bug in a built-in template, or want a new one added for everyone? **[Open an issue](https://github.com/michaelschecht/taskhub-registry/issues)** describing the automation (trigger, command, parameters, target) — or attach an [exported](exporting-templates.md) JSON. See also the [Template Resources](../../resources/README.md) for good sources to adapt.

---

<p align="center">
  <a href="exporting-templates.md">← Exporting templates</a> ·
  <a href="../README.md">Guides</a> ·
  <a href="../../../README.md">Registry root →</a>
</p>

<p align="right">(<a href="#updating-top">back to top</a>)</p>
