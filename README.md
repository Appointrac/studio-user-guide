# FlowQueue — User Guide

FlowQueue is a Chrome extension that batches prompt submission on Google
Flow (labs.google): queue up dozens of prompts, let them run one after
another, and have the finished videos/images download and organize
themselves automatically — instead of babysitting Flow's own UI one
prompt at a time.

FlowQueue is an independent project, built and maintained by
[Appointrac](https://appointrac.in). It is not affiliated with, endorsed
by, or sponsored by Google — it automates the same Flow web UI a human
would otherwise click through by hand, using Chrome's own DevTools
Protocol to drive trusted input.

> **Status:** early / personal-use phase. There's no account system,
> billing, or license tiers, and no Chrome Web Store listing yet — this
> guide will be made public once the extension is ready for wider use.

## What actually works today

FlowQueue's mode selector shows six generation modes, grouped as
Video / Image / Agent. Only the three below are functional right now —
the rest are visible but intentionally disabled, so the UI is honest
about what it can and can't do rather than pretending everything works:

| Mode | Status |
|---|---|
| Text → Video | ✅ Live |
| Text → Image | ✅ Live |
| Image → Image | ✅ Live (see note below) |
| Frame → Video | 🚧 Not yet built |
| Ingredients → Video | 🚧 Not yet built |
| Agent Automation | 🚧 Not yet built |

**A note on Image → Image**: Google Flow has no native Image-to-Image
generation mode of its own. FlowQueue provides the effect of one by
running these prompts through Flow's ordinary Text→Image pipeline with a
reference image attached first — so the image you want to use as a
reference has to already be uploaded to your Flow account (via Flow's own
site) before FlowQueue can select and attach it. FlowQueue doesn't upload
new files on your behalf.

## Getting started

1. **Open a Google Flow project.** FlowQueue only activates on Flow
   project pages (`labs.google/fx/tools/flow/project/...`).
2. **Open the extension's side panel** from the Chrome toolbar.
3. **Pick a mode** in the Control tab's mode selector — choose a category
   (Video / Image / Agent) first, then the specific sub-mode.

## Running a batch

1. Type your prompts into the Prompts box, one per blank-line-separated
   paragraph — or click **Upload .txt file** / **Upload .xlsx / .csv** to
   import a list instead (spreadsheet imports let you pick which sheet and
   column holds the prompt text before confirming).
2. Give a prompt a label by starting it with `SCENE-001:` (or similar) —
   labels get used for the downloaded file name instead of a generic
   number.
3. Click **Run**. Prompts process one at a time, with a short random delay
   between each (configurable) to avoid hammering Flow. You can **Stop** a
   running batch or **Clear** a finished one from the queue list.
4. If something fails partway through, use **Retry** to re-run just the
   failed/cancelled items rather than the whole batch again.

### Attaching Characters or reference images automatically

If your Flow project has Characters, or you've uploaded reference images
to Flow directly, FlowQueue can auto-attach them to a prompt just by
mentioning them by name:

```
@Alex walking through @streetfork.jpeg at golden hour
```

- Click **Scan Characters** / **Scan Uploads** first, so FlowQueue knows
  what's available to match against.
- Turn on **Auto-add character by @mention** / **Auto-add image by
  @mention** to enable the matching.
- A prompt is checked against every scanned name before it runs; a
  mismatched or unscanned `@mention` shows up as a clearly-marked "not
  found" warning in the queue preview instead of silently doing nothing.
- Each toggle also has an optional **default** fallback, used when
  auto-add is on but a particular prompt has no `@mention` at all.

## Output handling

Below the prompt box:

- **Save to folder** — a subfolder name (under your default Downloads
  folder) that finished files get organized into.
- **Auto change file name** — renames downloads after each prompt's label
  (or a `PROMPT-001`-style number when it has none), instead of keeping
  whatever name Flow itself gives the file.
- **Open folder** reveals the most recently downloaded file directly in
  your OS file browser.

## Settings tab

Settings apply as defaults for the whole tool, independent of whatever
mode happens to be selected in Control — organized into Video, Image, and
General sections.

- **Default Mode** — which category + sub-mode the Control tab starts on.
- **Model / Default Aspect Ratio / Default Video Option** (Video) and
  **Image Model / Default Aspect Ratio** (Image) — these are read from
  Flow's own settings panel and applied to Flow automatically before each
  prompt submits, so a batch doesn't drift onto whatever mode/model the
  previous run happened to leave Flow in.
- **Auto Download Quality** — separate tiers for Image and Video outputs,
  matching whatever quality options Flow's own download menu actually
  offers for that mode.
- **Max Retries on Failure** — how many times a failed prompt automatically
  retries (with increasing delay between attempts) before being marked
  permanently failed. Automation failures — Flow's UI not matching what
  FlowQueue expects — are never retried, since retrying can't fix that
  category of problem.
- **Language** — English only for now; the control is present so the
  layout won't need to change once more languages are added.

## Debug Logs tab

A running log of what the extension is doing under the hood — useful when
something doesn't behave as expected. **Copy** grabs the full log to your
clipboard, **Clear** empties it, and **Report Bug** opens a pre-filled
email (with the most recent log entries attached) to the maintainer.

## Troubleshooting

| Symptom | What to check |
|---|---|
| Nothing happens when you click Run | Confirm you're on a Flow *project* page, not the Flow home/dashboard. |
| A prompt fails immediately with an "automation issue" warning | Flow's own UI likely changed since this was built — check Debug Logs for the specific selector/step that failed, and report it. |
| Chrome keeps asking where to save every download | Turn off Chrome's "Ask where to save each file" setting (`chrome://settings/downloads`) — FlowQueue's own folder/naming settings need this off to take effect. |
| A `@mention` isn't attaching | Click **Scan Characters** / **Scan Uploads** again — the cached list may be stale, or the name in your prompt doesn't exactly match what's scanned (check the "Show" list). |
| A "started debugging this browser" banner appears on the Flow tab | Expected — FlowQueue uses Chrome's DevTools Protocol to produce trusted clicks/keystrokes, which requires this. It clears once the current step finishes. |

## Privacy

Everything runs locally inside your own browser. Prompts, settings, and
scanned Character/image names are stored in Chrome's local extension
storage on your machine — nothing is sent to an external server.

## Support

- **Report a bug**: use the **Report Bug** button in the Debug Logs tab,
  or email [info@appointrac.in](mailto:info@appointrac.in) directly.
- **Maintainer**: [Appointrac](https://appointrac.in)

---

*This guide describes FlowQueue's current, real feature set as of this
writing — it will be updated as new modes and settings actually ship,
not ahead of them.*
