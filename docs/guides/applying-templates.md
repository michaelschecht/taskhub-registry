<a id="applying-top"></a>

<h1 align="center">▶️ Applying Templates</h1>

<p align="center">
  <em>Turn a template into a real, running scheduled task by filling in its parameters.</em>
</p>

<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/↩-guides-6B7280?style=for-the-badge" alt="Back to guides"></a>
</p>

---

A template is just a blueprint. **Applying** it compiles the blueprint — with your values — into an actual scheduled task on a real target.

## Steps

1. In the **Templates** tab, find the template (built-in, or one you [imported](importing-templates.md)) and click **Apply**.
2. Pick the **target** — where the task will run:
   - **Windows** — creates a real Windows Task Scheduler entry via the local agent.
   - **TaskHub-native** — an HTTP job (webhook / health check) that TaskHub schedules and runs itself.
3. Give the task a **name** and confirm the **schedule** (the template's default cron is prefilled; presets and a human-readable preview help).
4. Fill in the **parameters** — the `{{placeholders}}` the template declares (paths, names, URLs, options). Required ones are marked.
5. Click **Create**. TaskHub substitutes your values server-side (per-token, no shell), registers the task on the target, and it shows up on your dashboard.

## Which targets can I apply to?

Only targets TaskHub can **actually create on today** are selectable: **Windows** and **TaskHub-native**.

A template may list other **compatible targets** (macOS, Claude Code, ChatGPT). Those are shown honestly as **"copy to set up manually"** — the Apply button is disabled with a note, because there's no compiler for them yet. You can still read the command and set it up yourself on that platform.

> [!IMPORTANT]
> Parameter values are substituted **per token** — a value is always exactly **one argument** to the intended program, no matter what spaces or quotes it contains. A template can't be tricked into launching a second command. Avoid single quotes inside values for PowerShell templates (they close the inline string — the parameter's help text will say so where it matters).

## After applying

- The new task appears on the **dashboard** with its platform + status.
- **Run Now** triggers it immediately; **Run history** records status, time, duration, and a log snippet.
- Applying the same template again creates **another** task — Apply makes tasks, it doesn't edit the template.

---

<p align="center">
  <a href="importing-templates.md">← Importing templates</a> ·
  <a href="README.md">Guides</a> ·
  <a href="exporting-templates.md">Next: Exporting templates →</a>
</p>

<p align="right">(<a href="#applying-top">back to top</a>)</p>
