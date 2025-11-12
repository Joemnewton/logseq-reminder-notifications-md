# Reminder Notifications (Markdown)

> Desktop + in-app reminders for scheduled blocks living in Logseq's **Markdown/file-based graphs**.  
> Works anywhere Markdown graphs run on Desktop, Web, and Mobile clients.

| Feature Pack | Highlights |
| --- | --- |
| ✅ Desktop & mobile notifications | Native OS toasts (desktop) + Logseq in-app banners everywhere |
| ✅ Multiple warning times | Comma-separated intervals (`15,5,0`) |
| ✅ Quiet hours | Silence reminders overnight or during focus time |
| ✅ All-day support | Convert `scheduled:: 2025-10-14` into a reminder at your preferred time |

> Need the Database build instead? Use the [DB version of Reminder Notifications](https://github.com/Joemnewton/logseq-reminder-notifications-db).

---

## Compatibility Cheat Sheet

| Supported | Not Supported |
| --- | --- |
| Logseq Desktop/Web/Mobile using **Markdown/file-based graphs** | Logseq Database (DB) graphs |
| `/reminders: rescan` command | DB plugin settings or DB-only properties |
| In-app + desktop/mobile notifications | Automatic support for SQLite graphs (install the DB build above) |

> **Tip:** Markdown graphs are folders of `.md` files you open directly. If your graph path ends in `db.sqlite`, you're on the DB format.

---

## Screenshots

![Desktop Notification](./screenshots/Desktop_Notification.png)
*Native OS toast fired from a scheduled block*

![In-App Message](./screenshots/In_App_Notification.png)
*Matching in-app reminder when you're already inside Logseq*

---

## Quick Start

1. **Clone or download**
   ```bash
   git clone https://github.com/Joemnewton/logseq-reminder-notifications-md.git
   ```
2. **Load in Logseq**
   - `Settings → Plugins → Load unpacked plugin`
   - Select the `logseq-reminder-plugin-md` folder
3. **Reload on mobile/web**
   - Use the same folder (or zip) synced via iCloud/Drive/Git to run the plugin across your Markdown graphs.

---

## Using Reminders

### Recommended format (Markdown graphs)

```
- Prep project retro
  scheduled:: 2025-02-10 15:00
```

### Journal style (classic Logseq)

```
SCHEDULED: <2025-02-10 Mon 15:00> Prep project retro
```

### Manual rescan

- Slash command: `/reminders: rescan`
- Command palette entry: “Reminder Notifications → Rescan now”

---

## Settings Reference

| Setting | Description |
| --- | --- |
| Default reminder intervals | Comma-separated minutes before the event (`15,5,0`) sorted automatically |
| Enable all-day reminders / time | Convert `scheduled:: 2025-02-10` into a reminder at e.g. `09:00` |
| Polling interval (seconds) | How frequently to check for upcoming reminders (10–300) |
| Daily rescan hour | Force a full graph rescan every day at the chosen hour |
| Quiet hours (start/end) | Silence notifications between the times you specify |
| Notification durations | Tune how long desktop / overdue / in-app banners stay on screen |

Access everything in `Settings → Plugins → Reminder Notifications`.

---

## Troubleshooting

1. **No notifications?**
   - Verify you opened a Markdown graph (folder of `.md` files).
   - Make sure the block uses `scheduled::` or a `SCHEDULED: <timestamp>` marker.
   - Run `/reminders: rescan` and watch the developer console for parsing logs.
2. **Getting duplicates?**
   - Confirm your OS/phone clock and timezone are correct.
   - Keep the polling interval around 10–30 seconds for reliability.
3. **Swapping between DB and Markdown graphs?**
   - Install both versions of the plugin and disable whichever doesn't match the active graph format.

---

## Development Notes

- Targets Markdown/file graphs (`:block/content`) and uses Logseq's standard datascript queries.
- Everything lives in `index.js`-no bundler required.
- `npm install` is only needed if you add tooling; the plugin ships as plain JS.

PRs and issues are welcome!

---

## License

MIT © Joemnewton
