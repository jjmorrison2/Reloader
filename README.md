# Reloading Calculator

A single-file, offline reloading reference calculator. Open `index.html` in any browser —
no install, no server, no internet required.

## What it does

1. Pick a **cartridge**, the **exact bullet** (from published data), and a **target muzzle velocity**.
2. It shows every powder in the library with published data for that bullet, and for each one:
   - an **estimated charge** for your target velocity, linearly interpolated **between the
     published starting load and the published maximum** — never outside them;
   - where your target sits inside the published velocity band;
   - a full **recipe card** (components, COAL, primer, case, source link) with a
     **work-up ladder** from the published starting charge to the estimated charge.
   Picking a powder jumps straight to its recipe card; **↑ All N powders** takes you back to the list.
   A **Case fill** box on the recipe card shows what percent of the case a charge fills (load
   density), and the ladder gains a % case fill column. Where Hodgdon or Nosler publish load
   density for that load, it is used directly (scaled with the charge). Otherwise, enter your
   fired case's water capacity and the powder's bulk density (or the weight of that powder that
   fills the case to the mouth); bullet and case length account for the seated bullet. Your own
   measurements, remembered per case and powder, take priority over the published figure.
   Nothing is guessed when neither is available.
3. A **Load Library** tab lets you add, edit, import, and export load data transcribed from
   published sources. Your library is saved in the browser (localStorage). When a new version
   of the built-in library ships, your own and imported loads are carried over automatically.
   Saved data is never silently discarded: a value the app cannot read is kept with its load
   and listed on the recipe card, and a record it cannot use at all is set aside in storage.
4. A **Load Log** tab records your range sessions per load — charge fired, chronograph string
   (average/SD/ES computed), group size, temperature, pressure signs, notes. Entries appear on the
   recipe card and are plotted against the published curve; export/import as JSON. A logged
   charge above the published maximum is flagged in the log tables, on the recipe chart, and
   when the Ballistics tab uses that session's velocity; one below the published start is
   flagged in the log tables.
   **Target photo:** take or choose a photo of your target and mark it on screen instead of
   measuring by hand. Three steps: set the scale (tap two points a known distance apart, such as
   two 1″ grid lines, or the four corners of a known rectangle for a photo taken at an angle), tap
   your aim point (optional), then tap each bullet hole. Pinch or scroll to zoom; press and hold
   for a magnifier; drag a mark to fine-tune it. It computes group size (center to center), mean
   radius, width × height, and where the group sits relative to your aim, in inches, MOA and
   mils, and fills the group size into the log entry. The shot positions are saved with the log
   entry and included in its JSON export; the photo itself stays on this device (browser storage)
   and is not exported. When you're
   working up a ladder, after saving it offers to mark the next charge's group on the same sheet,
   with the earlier groups shown dimmed.
5. A **Ballistics** tab runs a point-mass trajectory (standard G1/G7 drag curves) from your muzzle
   velocity and the bullet maker's BC: drop, MOA, wind drift, velocity, energy, time of flight.
   "Fill from selected recipe" uses your logged average velocity when you have one.
6. An optional **Your rifle & conditions** panel (barrel length, twist, temperature) applies
   rule-of-thumb estimates (default 25 fps/inch, 1.0 fps/°F vs 70°F) to expected velocity.
   Barrel length is remembered per cartridge, so a rifle barrel never skews handgun data.
   Your target is converted to each load's test-barrel equivalent before interpolating —
   charges never leave the published range. Twist is reference-only (stability, not pressure).

Built-in library v6: **26 cartridges, 341 loads** — 9mm Luger, .38 Special, .44 Rem Mag, .45 ACP,
.22-250 Rem, .223 Rem, .243 Win, .25-06 Rem, .260 Rem, 6.5 Creedmoor, 6.5 PRC, .270 Win, 7mm-08 Rem,
7mm PRC, 7mm Rem Mag, .280 Rem, .30-30 Win, .300 Blackout (supersonic), .30-06 Springfield, .300 WSM,
.308 Win, .300 Win Mag, .35 Rem, .350 Legend, .45-70 Govt (SAAMI-level table, not Trapdoor),
.450 Bushmaster — transcribed live from Hodgdon's
Reloading Data Center, Vihtavuori's Reloading Data Tool, Nosler's official load-data
PDFs, and Barnes' load-data PDFs — every load independently re-fetched and number-for-number verified.

Version 6 added 211 loads for hunting bullets in .308 Win, .30-06, .300 WSM, .300 Win Mag and
7mm PRC: Hornady 165 gr CX and SST, Barnes 165 gr TTSX BT and 175 gr LRX BT (.30 cal),
Barnes 160 gr LRX BT (7mm PRC), and Nosler 165 gr AccuBond. Nosler and Barnes print one table
for several bullets of similar weight; each such load's notes say so.

## What it deliberately refuses to do

- It will **not** compute a charge above a published maximum or below a published start.
- It contains **no internal-ballistics simulation** — only interpolation of published points.
- It never presents the interpolated charge as a load to jump to; the ladder always starts
  at the published starting charge.

## Data

The built-in library was transcribed from powder and bullet makers' free published load data
(each entry links its source URL). Every built-in entry is marked **✓ verified**: it was
independently re-fetched and every number compared against the source at build time.
**your entry** marks loads you added or edited, and **⚠ imported — verify** marks loads from
an imported file that don't match the built-in data; check those yourself.
Where Hodgdon or Nosler publish load density (case fill), it is included and shown on the
recipe card's Case fill box.

**Always cross-check every load against the publisher's current data or a current printed
manual before loading a single round.** Published data changes, and transcription errors
are possible anywhere — including here.

**Personal use only.** The publishers (notably Hodgdon) license their load data for
personal, non-commercial use. Keep this tool and its built-in data private — don't
republish, redistribute, or bundle it into anything you share.

## Safety

Handloading ammunition is inherently dangerous. This tool is a reference aid, not a
substitute for a published reloading manual or for careful load work-up. Read the
**Safety & About** tab in the app. You assume all risk.
