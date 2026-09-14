# Changelog

User-facing changes for each released version of Appointrac Studio.

## v1.0.8 (current)

Google Flow moved from `labs.google/fx/tools/flow` to `flow.google.com`
— Appointrac Studio updated to follow. No visible feature changes.

## v1.0.7

The panel now shows a dismissible announcement banner (info/warning)
sent directly from Appointrac's backend, so a message — a new model, a
known issue — can reach you instantly instead of waiting on a Chrome Web
Store update. Dismissing one is remembered; a different, newer
announcement still shows up later. Also: video model matching is now
resilient to Flow renaming a model's version number again — v1.0.6
handled the specific "Omni Flash" → "Omni 1.1 Flash" rename, this
generalizes it so a future version bump won't need another release.

## v1.0.6

Video model selection is now resilient to Flow renaming a model's
version number — Flow renamed "Omni Flash" to "Omni 1.1 Flash" without
warning, which broke automation until this fix; a future rename like
"Omni 1.2 Flash" won't need another release. Also fixed a bug where a
plain Text→Video run could get left stuck on Flow's Ingredients tab
instead of switching to Frames.

## v1.0.5

Two new video modes: **Frame → Video** (attach a Start frame, and
optionally an End frame, then describe the motion in between) and
**Ingredients → Video** (attach any number of reference images as
ingredients). Prompt templates let you write `{red|blue|green}` inside a
prompt and Appointrac Studio expands it into every combination
automatically instead of writing each variant out by hand. Also: a
Clear button for the Prompts box.

## v1.0.4

Save your current prompts (plus mode/category/delay settings) as a
named, reusable set instead of re-pasting the same batch every time —
load or delete saved sets anytime. Scheduled runs let you turn on a
daily schedule, pick a saved set and a time, and Appointrac Studio runs
it automatically (won't double-fire if a run is already in progress).
Also: the Character picker, Save to Folder, Saved Sets, and Scheduled
Run now live in a collapsible "Advanced" section, keeping the main
Control tab focused on Mode, Delay, Prompts, and Run.

## v1.0.3

A pre-run estimate above the Run button shows how many generations a
batch will use and how many you have left before you click Run. Daily
usage/quota preview now shows for any capped plan, not just the free
plan, with an upgrade prompt when a paid plan hits its daily cap. Also:
a banner when no Flow tab is open, the default save-to-folder renamed
from `flowqueue-outputs` to `studio-outputs`, and a video generation
duration-selection bug fixed.

## v1.0.2

Subscribe to a plan for auto-renewal, alongside the existing one-time
purchase, with renewal status and a cancel action right in the Control
tab. Also: a "resets in Xh Ym" countdown on the free plan, account email
masked by default, and queue list polish (auto-scroll to the active run,
~7-row cap with internal scrolling).

## v1.0.1

Moved to a new domain, `studio.appointrac.in`. No visible feature
changes.

## v1.0.0

First public release on the Chrome Web Store.
