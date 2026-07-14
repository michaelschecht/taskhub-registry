<a id="scheduling-top"></a>

<h1 align="center">📅 Scheduling &amp; Cron References</h1>

<p align="center">
  <em>Design and sanity-check the schedules behind your templates.</em>
</p>

<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/↩-template_resources-6B7280?style=for-the-badge" alt="Back to Template Resources"></a>
</p>

---

| Resource | What you'll find |
|:---|:---|
| [**crontab.guru**](https://crontab.guru/) | Sanity-check and design 5-field cron expressions (TaskHub stores cron in UTC). |
| [**Windows Task Scheduler docs**](https://learn.microsoft.com/en-us/windows/win32/taskschd/task-scheduler-start-page) | The platform the Windows agent wraps — triggers, actions, principals. |
| [**systemd timers (Arch Wiki)**](https://wiki.archlinux.org/title/Systemd/Timers) | Linux scheduling patterns (`OnCalendar`) — good source of interval/calendar ideas. |
| [**launchd.info**](https://www.launchd.info/) | macOS `launchd` reference — the target for the (planned) macOS agent. |

> [!TIP]
> TaskHub stores every schedule as a **5-field UTC cron** and translates it to each platform's native trigger at apply time. Design in cron, verify with crontab.guru.

---

<p align="center">
  <a href="README.md">← Template Resources</a> ·
  <a href="../../../README.md">Registry root</a> ·
  <a href="https://mikesailab.com/taskhub-registry/">Browse the gallery</a>
</p>

<p align="right">(<a href="#scheduling-top">back to top</a>)</p>
