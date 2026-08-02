<div align="center">

# 📬 Siftbox

**A free, local-first visual builder for Gmail filters and Outlook mail rules.**

No coding. No server. No account. Your data never leaves your browser.

[![Made with](https://img.shields.io/badge/made%20with-HTML%20%2F%20CSS%20%2F%20JS-22c3dd?style=flat-square)]()
[![100% Client-side](https://img.shields.io/badge/data-100%25%20local-2dd4bf?style=flat-square)]()
[![No backend](https://img.shields.io/badge/backend-none-9d8ce8?style=flat-square)]()
[![License](https://img.shields.io/badge/license-MIT-6bcf8f?style=flat-square)]()

[**🚀 Live Demo**](#) · [Features](#-features) · [How it works](#-how-it-works) · [Exporting](#-exporting-your-rules) · [Privacy](#-privacy--data)

</div>

---

## 📖 What is Siftbox?

Writing Gmail search operators or clicking through Outlook's rules wizard by hand gets old fast — especially once you have more than a handful of rules. **Siftbox** gives you a clean visual interface to build them instead:

- Define **conditions** (From, To, Subject, Body, attachments, size, advanced queries)
- Group multiple filters under one **label**
- Set **actions** (archive, star, mark important, delete, forward…)
- Export a file ready to drop into **Gmail**, or a structured reference for **Outlook**

Everything runs entirely in your browser. There's no backend, no analytics, no account — open the page, build your rules, download the file.

> [!TIP]
> New here? Open the app and click the **?** icon in the top bar — it has a full in-app guide covering every feature with examples.

---

## ✨ Features

| | |
|---|---|
| 🏷️ **Labels & sub-labels** | Organize rules hierarchically, just like Gmail's nested labels (`Finance/Banks`) |
| 🧩 **Multiple filters per label, each with its own actions** | One label, several independent rule combinations — each shown as `Filter (From & Subject)`, each with its own actions (one filter can delete, another can just star) |
| 🔀 **Drag-and-drop priority** | Reorder rules — matters for Outlook, informational for Gmail |
| 🧪 **Filter tester** | Simulate a fake email and see instantly which labels would fire, and why |
| ⚠️ **Conflict detector** | Flags labels with overlapping conditions before they surprise you |
| 🚫⭐ **Blocked & VIP senders** | Simple standalone lists, independent of your labels |
| 🔒 **Custom reserved words** | Block any label name yourself, on top of the built-in Gmail/Outlook system-name guard |
| 📤 **Import existing Gmail filters** | Re-import your real exported filters to edit them here |
| ↩️ **Undo** | Roll back the last destructive action |
| 💾 **Backup & restore** | Full JSON export/import of everything |
| 🌓 **Light / dark mode** | Persisted automatically |
| 👥 **Multiple accounts** | Personal, Work, or any custom account — fully separate data per account |

---

## 🧠 How it works

The single most important thing to understand:

> [!IMPORTANT]
> **Within one filter:** multiple values in the *same* field are combined with **OR**.
> **Across different fields:** From, Subject, Body, etc. are combined with **AND**.

**Example** — a filter with `From: nbe.com.eg` + `Subject: invoice`:

```
✅ Matches: an email FROM nbe.com.eg AND with "invoice" in the subject
❌ Does NOT match: an email from nbe.com.eg with a different subject
❌ Does NOT match: an email with "invoice" in the subject from a different sender
```

Need two genuinely different scenarios under the same label (e.g. "From nbe.com.eg" **or** "Subject contains invoice, regardless of sender")? That's exactly what **multiple filters per label** are for — add each as its own filter, and Siftbox names them automatically by their shape: `Filter (From)`, `Filter (Subject)`, `Filter (From & Body)`, etc. All filters under a label share the same actions.

<details>
<summary><b>How does the "shape" grouping work when adding a filter?</b></summary>
<br>

When you fill in the condition fields and click **➕ Add filter**, Siftbox looks at which fields you filled in (its "shape"). If a filter with that exact shape already exists on the label, your new values are merged into it (OR'd in). If not, a new filter is created. This means you can keep adding `Body` keywords one at a time and they'll all land in the same `Filter (Body)` — no duplicates.

</details>

---

## 📤 Exporting your rules

### Gmail — direct import ✅
Gmail supports real filter import.

1. Click **⤓ Gmail XML**
2. In Gmail: `Settings → Filters and Blocked Addresses → Import filters`
3. Select the downloaded file

### Outlook — manual, by design ⚠️

> [!WARNING]
> Neither **New Outlook** nor **Outlook on the web** support importing rules from a file — Microsoft removed this feature entirely (confirmed on Microsoft's own support forum). Classic desktop Outlook only exports to a proprietary `.rwz` format, not XML/CSV. This is a limitation of Outlook itself, not of Siftbox.

Click **⤓ Outlook CSV** for a structured reference sheet, then create each rule manually:

1. `Settings → Mail → Rules → + Add new rule`
2. Name it after the **Label / Folder Path** column
3. Add a condition for each filled column (From, Subject includes, Message body includes, Has attachment…)
4. Add the actions listed (Move to folder, Mark as read, Delete…)
5. Repeat per row — roughly 3–4 minutes per rule
6. Reorder rules using the **Priority** column (rule order is functionally meaningful in Outlook, unlike Gmail)

> [!TIP]
> Right-click a real email from the sender → **Rules → Create Rule** — it pre-fills the *From* condition for you.

---

## 🔐 Privacy & data

- Everything is stored in your browser's `localStorage` — nothing is ever transmitted anywhere.
- No cookies, no tracking, no third-party requests except loading the Google Fonts stylesheet.
- Clearing your browser data for this site will erase your saved labels — use **⤓ Backup** regularly if that matters to you.

---

## 🛠️ Tech stack

Plain **HTML + CSS + vanilla JavaScript** — a single self-contained file. No build step, no dependencies, no framework.

```
📁 your-repo/
 └── index.html   ← the entire app
```

## 🚀 Running it yourself

**Option 1 — GitHub Pages (recommended):** fork/clone this repo and enable Pages in Settings → Pages → Deploy from branch → `main` / root. Done — the app is live at `https://<you>.github.io/<repo>/`.

**Option 2 — Locally:** just download `index.html` and open it in any browser. No server needed.

---

## 📄 License

MIT — do whatever you'd like with it.

<div align="center">

Built for anyone tired of clicking through the same filter dialog for the tenth time.

</div>
