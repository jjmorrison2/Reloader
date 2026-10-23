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
3. A **Load Library** tab lets you add, edit, import, and export load data transcribed from
   published sources. Your library is saved in the browser (localStorage). When a new version
   of the built-in library ships, your own and imported loads are carried over automatically.
4. A **Load Log** tab records your range sessions per load — charge fired, chronograph string
   (average/SD/ES computed), group size, temperature, pressure signs, notes. Entries appear on the
   recipe card and are plotted against the published curve; export/import as JSON. A logged
   charge above the published maximum (or below the published start) is flagged wherever it appears.
5. A **Ballistics** tab runs a point-mass trajectory (standard G1/G7 drag curves) from your muzzle
   velocity and the bullet maker's BC: drop, MOA, wind drift, velocity, energy, time of flight.
   "Fill from selected recipe" uses your logged average velocity when you have one.
6. An optional **Your rifle & conditions** panel (barrel length, twist, temperature) applies
   rule-of-thumb estimates (default 25 fps/inch, 1.0 fps/°F vs 70°F) to expected velocity.
   Barrel length is remembered per cartridge, so a rifle barrel never skews handgun data.
   Your target is converted to each load's test-barrel equivalent before interpolating —
   charges never leave the published range. Twist is reference-only (stability, not pressure).

Built-in library v5: **26 cartridges, 130 loads** — 9mm Luger, .38 Special, .44 Rem Mag, .45 ACP,
.22-250 Rem, .223 Rem, .243 Win, .25-06 Rem, .260 Rem, 6.5 Creedmoor, 6.5 PRC, .270 Win, 7mm-08 Rem,
7mm PRC, 7mm Rem Mag, .280 Rem, .30-30 Win, .300 Blackout (supersonic), .30-06 Springfield, .300 WSM,
.308 Win, .300 Win Mag, .35 Rem, .350 Legend, .45-70 Govt (SAAMI-level table, not Trapdoor),
.450 Bushmaster — transcribed live from Hodgdon's
Reloading Data Center, Vihtavuori's Reloading Data Tool, and Nosler's official load-data
PDFs — every load independently re-fetched and number-for-number verified.

## What it deliberately refuses to do

- It will **not** compute a charge above a published maximum or below a published start.
- It contains **no internal-ballistics simulation** — only interpolation of published points.
- It never presents the interpolated charge as a load to jump to; the ladder always starts
  at the published starting charge.

## Data

The built-in library was transcribed from powder manufacturers' free published load data
(each entry links its source URL). Entries marked **✓ verified** were independently
re-fetched and every number compared against the source at build time; **⚠ unverified**
entries could not be re-checked automatically.

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
