[![Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-Install-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/appointrac-studio/cgmhhafpjnooleooijnfjndmmcecjoji)
<!-- Version tracks the extension's manifest.json, not this guide's own history - bump both together. -->
![Version](https://img.shields.io/badge/version-1.0.0-informational?style=for-the-badge)
![Platform](https://img.shields.io/badge/platform-Chrome-yellow?style=for-the-badge)

# 🎬 Appointrac Studio — Batch Prompt Automation for Google Flow

**Appointrac Studio** is a Chrome extension for batch-running prompts on
[Google Flow](https://labs.google/fx/tools/flow). Queue up a list of
prompts, click Run, and walk away — Appointrac Studio submits them one by one and
downloads the finished videos/images automatically, instead of you
clicking through Flow's UI by hand for every single prompt.

Appointrac Studio is an independent project built by [Appointrac](https://appointrac.in).
It is not affiliated with, endorsed by, or sponsored by Google.

> [!NOTE]
> Appointrac Studio is live on the
> [Chrome Web Store](https://chromewebstore.google.com/detail/appointrac-studio/cgmhhafpjnooleooijnfjndmmcecjoji).
> Free to try (20 prompts/day), with paid plans for unlimited use — see
> [Account & Plans](#-account--plans). This guide documents what's actually
> built today, not what's planned.

### ⚡ Quick start

1. [Install the extension](#-installation) from the Chrome Web Store.
2. [Log in](#-account--plans) with Google — the free plan needs no payment.
3. Open a Google Flow project and open Appointrac Studio's side panel.
4. Pick a mode, paste in some prompts, hit **Run**.

That's it for a first try — the rest of this guide covers everything
else in more depth.

## 📑 Contents

- [Key Features](#-key-features)
- [Installation](#-installation)
- [Account & Plans](#-account--plans)
- [User Guide](#-user-guide)
  - [Text → Video](#1-text--video)
  - [Text → Image](#2-text--image)
  - [Image → Image](#3-image--image)
- [File Saving & Naming](#-file-saving--naming)
- [Settings](#️-settings)
- [Tips](#-tips)
- [Troubleshooting](#-troubleshooting)
- [Privacy](#-privacy)
- [Support](#-support)

-----

## ✨ Key Features

* **🚀 Queue support** — add a whole batch of prompts and let them run
  one at a time, instead of manually submitting each one in Flow.
* **📝 Text → Video** — generate videos from plain text prompts, imported
  from a text box, a `.txt` file, or a spreadsheet.
* **🖼️ Text → Image** — generate images from text prompts, same queue and
  import options.
* **🔄 Image → Image** — attach an already-uploaded Flow image as a
  reference, then describe the change you want as a prompt. (Flow itself
  has no dedicated mode for this — Appointrac Studio builds it on top of
  Text→Image by attaching the reference image first.)
* **🧑‍🤝‍🧑 Character & image auto-attach** — mention a Flow Character or an
  uploaded reference image by name (`@Alex`, `@storefront.jpeg`) and
  Appointrac Studio attaches it automatically before the prompt runs.
* **📂 Spreadsheet import** — pull prompts from `.xlsx` / `.csv` files,
  with a preview to pick the right sheet and column first.
* **💾 Auto download** — save finished outputs straight to a named
  subfolder, with automatic file renaming based on each prompt's label.
* **🛡️ Retry on failure** — failed prompts retry automatically with
  increasing delay between attempts, up to a configurable limit.
* **🐛 Debug Logs tab** — a live log of what the extension is doing,
  copyable or one click away from a pre-filled bug report email.

**Not built yet** (visible in the mode selector, intentionally disabled
until they're real): Frame → Video, Ingredients → Video, Agent Automation.

-----

## 📥 Installation

1. Open the [Appointrac Studio listing](https://chromewebstore.google.com/detail/appointrac-studio/cgmhhafpjnooleooijnfjndmmcecjoji)
   on the Chrome Web Store.
2. Click **Add to Chrome**.
3. Pin the extension icon to your toolbar for easy access.

-----

## 👤 Account & Plans

Appointrac Studio needs a Google account to run prompts — a **Log in** button sits at the top
of the side panel until you sign in, then shows your email and current plan instead.

| Plan | Prompts | Price |
|---|---|---|
| Free | 20/day, resets every 24 hours | No payment required |
| 1 Month / 3 Months / 1 Year | Unlimited (unless an admin-configured daily cap applies) | One-time payment, no auto-renewal |

- Paid plans are a **single upfront payment for a fixed period** — not a subscription, nothing
  re-bills automatically. When a paid plan's period ends, you're back on the free plan's daily
  limit, not locked out.
- See [current pricing and to upgrade](https://appointrac.in/studio).
- Full terms: [Terms of Service](https://appointrac.in/studio/terms) ·
  [Privacy Policy](https://appointrac.in/studio/privacy).

-----

## 📖 User Guide

### Getting started

1. **Open a Google Flow project** — Appointrac Studio only activates on Flow
   project pages (`labs.google/fx/tools/flow/project/...`).
2. **Open the side panel** from the extension icon.
3. **Pick a mode** — choose a category (Video / Image / Agent) first,
   then the specific sub-mode underneath it.

### 1. Text → Video

1. Select **Video → Text → Video**.
2. Enter prompts in the box (blank line between each) or click **Upload
   .txt file** / **Upload .xlsx / .csv** to import them.
3. Optionally set a **Model**, **Default Aspect Ratio**, and **Default
   Video Option** (duration) in Settings — these get applied to Flow
   automatically before each prompt runs.
4. Click **Run**.

**Example prompt:**

```
A serene sunset over a calm ocean with gentle waves.
The camera slowly pans across the horizon.

A bustling city street at night with neon lights.
Cars and pedestrians moving through the scene.
```

### 2. Text → Image

1. Select **Image → Text → Image**.
2. Enter image descriptions the same way as Text→Video prompts.
3. Optionally set an **Image Model** and **Default Aspect Ratio** in
   Settings.
4. Click **Run**.

### 3. Image → Image

1. Upload your reference image(s) to Flow directly, via Flow's own site,
   first — Appointrac Studio selects from images already in your Flow account,
   it doesn't upload new files itself.
2. Select **Image → Image → Image**.
3. Click **Scan Uploads** in the Image References section so Appointrac Studio
   knows what's available.
4. Write prompts that mention the reference image by filename, e.g.
   `@storefront.jpeg but at night with warm lighting`.
5. Turn on **Auto-add image by @mention** to have matches attach
   automatically, or set a **Default reference image** to attach to
   every prompt regardless of mentions.
6. Click **Run**.

> [!NOTE]
> A prompt with a `@mention` that doesn't match anything scanned shows a
> clearly marked "not found" warning in the queue preview before you run
> it, rather than silently attaching nothing.

### Coming soon

**Frame → Video**, **Ingredients → Video**, and **Agent Automation** are
visible in the mode selector but currently disabled — they'll be
documented here once built.

-----

### 📁 File saving & naming

* **Save to folder** — a subfolder name (under Chrome's default
  Downloads folder) that finished files get organized into.
* **Auto change file name** — renames downloads after each prompt's
  label, or a `PROMPT-001`-style number when it has none, instead of
  keeping Flow's own default file name.
* **Open folder** — reveals the most recently downloaded file directly
  in your OS file browser.

### 📂 Spreadsheet & file import

* Click **Upload .xlsx / .csv** or **Upload .txt file** inside the
  Prompts box.
* For spreadsheets, a preview appears letting you pick the target
  **Sheet** and **Column** before importing.

### Queue management

* Pending/running/finished prompts are grouped by batch in the queue
  list below the Run button.
* **Stop** cancels a currently running batch; **Clear** removes a
  finished one.
* **Retry** re-runs just the failed/cancelled items from a batch,
  without starting the whole thing over.

-----

## ⚙️ Settings

Settings apply as defaults for the whole tool, independent of whichever
mode is currently selected in Control — organized into **Video**,
**Image**, and **General** sections.

### Video settings

| Setting | Options |
|---|---|
| Auto Download Quality (Video) | No Download, 270p, 720p, 1080p, 4K |
| Model | Omni Flash, Veo 3.1 – Lite, Veo 3.1 – Fast, Veo 3.1 – Quality |
| Default Aspect Ratio | 16:9, 9:16 |
| Default Video Option (duration) | 4s, 6s, 8s, 10s |

### Image settings

| Setting | Options |
|---|---|
| Auto Download Quality (Image) | No Download, 1k, 2k, 4k |
| Image Model | 🍌 Nano Banana Pro, 🍌 Nano Banana 2, 🍌 Nano Banana 2 Lite |
| Default Aspect Ratio | 16:9, 4:3, 1:1, 3:4, 9:16 |

### General

* **Default Mode** — the category + sub-mode the Control tab starts on
  when the panel opens.
* **Max Retries on Failure** — how many times (0–5) a failed prompt
  retries automatically, with a longer wait between each attempt. If
  Flow's UI itself has changed and Appointrac Studio can't find something it
  expects, that's never retried — retrying can't fix that kind of
  problem.
* **Language** — English only for now; present so the layout won't need
  to change once more languages are added.
* **Reset Defaults** / **Save Settings** — restore built-in defaults, or
  explicitly confirm the current values are saved (every field already
  saves as you change it — this is a convenience, not a required step).

> [!NOTE]
> Prompts always run one at a time, never in parallel. That's a Flow
> limitation, not a Appointrac Studio setting — Flow only allows one active
> generation per account at a time.

-----

## 💡 Tips

* **Rate limits** — increase the random delay between prompts if you're
  running a large batch; if Appointrac Studio detects a likely rate-limit or
  CAPTCHA, the whole queue pauses and shows a **Resume** button rather
  than continuing to hammer Flow.
* **Naming for auto-match** — name uploaded reference images and Flow
  Characters something you'll actually type, then mention that exact
  name with `@` in your prompt (e.g. `hero_pose.png` → `@hero_pose.png`).
* **Check Debug Logs first** — before reporting an issue, the Debug Logs
  tab usually shows exactly which step failed and why.

-----

## 🔧 Troubleshooting

| Issue | What to check |
|---|---|
| Nothing happens when you click Run | Confirm you're on a Flow *project* page, not the Flow home/dashboard. |
| A prompt fails with an "automation issue" warning | Flow's own UI likely changed since this was built — check Debug Logs for the specific step that failed, and report it. |
| Chrome keeps asking where to save every download | Turn off *"Ask where to save each file before downloading"* in `chrome://settings/downloads` — Appointrac Studio's folder/naming settings need this off to take effect. |
| A `@mention` isn't attaching | Click **Scan Characters** / **Scan Uploads** again — the cached list may be stale, or the name doesn't exactly match what's scanned. |
| A "started debugging this browser" banner appears on the Flow tab | Expected — Appointrac Studio uses Chrome's DevTools Protocol to produce trusted clicks/keystrokes. It clears once the current step finishes. |
| The whole queue stops with a "blocked" message | A likely rate-limit/CAPTCHA was detected. Resolve it in the Flow tab directly, then click **Resume** in Appointrac Studio. |
| "Daily free limit reached" / "Your plan has expired" | You're on the free plan's 20/day limit, or a paid plan's period ended. Click **Upgrade** in the banner, or see [Account & Plans](#-account--plans). |
| "Your session expired" | Click **Log in** again — sessions can expire after time away; your queue and settings aren't affected. |

-----

## 🔒 Privacy

**Your prompts never leave your browser.** They're sent directly to Google Flow's own page to
run, never to Appointrac's servers — settings and scanned Character/image names likewise stay
in Chrome's local extension storage on your machine.

Signing in does send your Google email/name and plan/usage counts (e.g. "one more prompt run
today") to Appointrac's backend, to run your account and enforce plan limits — never the content
of what you typed. Full details, including what's deliberately *not* collected:
[Privacy Policy](https://appointrac.in/studio/privacy).

-----

## 📞 Support

* **Report a bug** — use the **Report Bug** button in the Debug Logs
  tab, or email [info@appointrac.in](mailto:info@appointrac.in) directly.
* **Billing/refund questions** — see the
  [Terms of Service](https://appointrac.in/studio/terms), or email the address above.
* **Maintained by** — [Appointrac](https://appointrac.in)

_This guide describes Appointrac Studio's current, real feature set — it gets
updated as new modes and settings actually ship, not ahead of them._
