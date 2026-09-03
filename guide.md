# Time Klocks Guide

Everything here is a "how do I…" — short, task by task. Start with the
first three; the rest are there when you need them.

[← Back to Time Klocks](index.html)

---

## 1. Your first clock

Click the clock in your menu bar, then click **✏️** next to any time to
open the Format Editor. The **format line** is the clock's recipe: blue
chips are *tokens* (live values like hour, day-of-year, time zone), gray
chips are *text* you typed.

- **Click a token** to cycle its style — `Monday` → `Mon` → `M`,
  `2026` → `26`, `9` → `09`.
- **Click in the format line and type** to add text — spaces, dashes,
  words, emoji. Arrow keys move the cursor; delete works like a text
  field (whole tokens vanish in one press).
- **Click a token in the palette** to insert it at the cursor, or drag
  it exactly where you want it.
- The **Menu Bar Preview** at the top shows the result live.

Presets (**ISO 8601 (DOY)**, **Super Long**) are good starting points —
load one, then delete or restyle what you don't want.

<!-- image: guide-format-line.png — the format line with the caret between two chips -->

## 2. Fonts and colors

Under **Appearance**: **Font…** opens the standard macOS font panel
(any font, any size); **Text Color** is a color well. Each clock has its
own — mix a monospaced UTC with a bold red Mars sol if you like.

Leave the color on **Automatic** unless you have a reason: automatic
text flips with your light/dark menu bar by itself. Custom colors are
drawn literally, so pick ones that read on your usual menu bar.

Tip: proportional fonts don't jiggle. The menu bar reserves a fixed
width per clock so ticking seconds never shove your other icons around.

## 3. Flags and icons

Any image can sit in a format: **Image…** in the Text & Separators row
takes PNG, JPEG, GIF, TIFF, or HEIC, scales it to menu bar height, and
stores it inside the clock (transparent PNG looks best). A country flag
in front of each time zone is the classic use — emoji flags work too,
typed straight into the format line.

<!-- image: guide-flags.png — menu bar with flag-prefixed clocks -->

## 4. Time zones

The Time Zone list in the editor searches by city, zone name, or
abbreviation — try `IST`, `Bengaluru`, `Pasadena`, `zulu`. The
highlighted bar above the search shows the clock's current zone.

Want the zone shown as `IST` rather than `GMT+5:30`? Click the time
zone token until it reads the way you want (the styles include the
abbreviation, the long name, and numeric offsets), or just type `IST`
as text — it's your format.

## 5. Countdowns and count-ups

Switch the editor's tab to **Counter**. Set the zero point with the
date picker (seconds included) or type it as day-of-year:
`2026-186T09:00:00`. The counter reads **T−** until the moment, then
flips to **T+** and keeps counting. Tokens: sign, days, hours, minutes,
seconds, total hours — arrange them like any format
(`T- 002d 04:12:00` is the preset).

## 6. Mars time

Tab: **Mars**. Choose an asset — Perseverance, Curiosity, InSight,
Zhurong, the historic landers, or plain MTC (Mars Coordinated Time) —
and use the **Sol** and **Mars hour/minute/second** tokens. The math is
NASA's Mars24 algorithm (Allison & McEwen 2000), accurate to about a
second.

Rovers drive. If your LMST drifts a few seconds from NASA GISS's Mars24
tool, update the **Longitude** field to the rover's current position
(4 s of LMST ≈ 0.017° of longitude); **Preset** restores the built-in
value.

<!-- image: guide-mars-tab.png -->

## 7. Spacecraft clocks (SCLK)

Tab: **SCLK**. Time Klocks reads real NAIF SCLKSCET kernels — the same
`.tsc` files mission tools use — so the readout is mission-grade, no
SPICE installation needed. Get a kernel from your mission's ops team or
publicly from NAIF (`naif.jpl.nasa.gov/pub/naif/<MISSION>/kernels/sclk/`,
take the newest `.tsc`), then **Import SCLKSCET (.tsc)…**. The SCLK
token offers the raw count, count.fine, and partition/count.fine styles.

## 8. GPS time

In the **Clock** tab palette: **GPS Seconds** (continuous seconds since
the 1980 epoch — the LIGO-style integer), **GPS Week** (click for the
legacy mod-1024 form), and **GPS TOW** (time of week). GPS runs 18 s
ahead of UTC; Time Klocks verifies that offset monthly against the IETF
leap-second list (Settings → GPS shows the current value and lets you
check on demand).

## 9. The Time Kalculator

Menu bar panel → **Time Kalculator**. One row per time zone you use,
each with the same instant in ISO and day-of-year form, a day/night bar,
and a red line. **Drag any red line** and every zone moves together
(+1d / −1d markers show date rollovers). Type into any field — ISO, DOY,
or the GPS Week / TOW / seconds row at the bottom — and press ⏎; **Now**
snaps back to the present. "When is 21:00 Monday PDT in IST?" takes one
drag.

<!-- image: guide-kalculator.png -->

## 10. Managing the list

In the menu bar panel, each clock row has: copy the timestamp, ▲▼ to
reorder (the menu bar follows the list order), the eye to show/hide it
in the menu bar, edit, duplicate, and delete. Hidden clocks stay in the
list — handy for zones you only need sometimes.

## 11. Sharing a setup

Settings → **Configuration** → **Export Clocks…** writes a
`.timeklocks` file containing everything: formats, fonts, colors,
images, kernels, the separator. Send it to a colleague; they choose
**Import Clocks…** and pick **Append** (adds to their list) or
**Replace** (adopts your setup wholesale). Great for standardizing a
team on one set of mission clocks.

## 12. Troubleshooting

**My clocks vanished from the menu bar.** macOS hides menu bar items
when the bar is full — common on 13–14-inch laptops. Time Klocks
notices and shows a small **⚠︎ clock icon** instead; click it and the
panel explains what to do: hide a clock (eye), shorten a format, or
clear room (⌘-drag other icons off the bar, or quit their apps). The
clocks come back on their own once they fit. If you can't see even the
icon, **launch Time Klocks again** — launching the running app always
opens its window (also: Settings → General → Open Clock Manager).

**The trial ended — what do I keep?** Two fully custom clocks, forever.
Time Klocks Pro (one-time purchase) unlocks unlimited clocks and the
Time Kalculator; **Restore Purchases** is in Settings → Pro & About and
on the unlock screen.

**Clean reset.** Quit the app, then in Terminal:
`defaults delete com.tk.TimeKlocks` — next launch is a fresh install
(welcome window, starter clocks). Export first if you want your setup
back afterwards.

**Updates.** Delivered by the App Store like any Mac app; a running menu
bar app picks up an installed update after you quit and relaunch it.
Settings → Pro & About → **Check for Updates…** opens the App Store's
Updates page.

---

Something missing? Email **spacenewt@icloud.com** — a screenshot of the
format involved gets the fastest answer.
