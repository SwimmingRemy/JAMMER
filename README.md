# JAMMER — a radar jammer for BeamNG.drive

**BETA — v0.3.3.** Bugs are expected. Please report them.

Author: **SwimmingRemy** · Written with Claude (Anthropic) · Free

Switch it on and the police stop ticketing you for speed. No speeding reports, no racing reports.
The panel keeps score of every ticket you did not get.

The price is that you are **exposed** for 60 seconds every time you switch it off.

It works on any map. It does **not** need BeamNG.Earth, and it does **not** need RLS Career Overhaul
or any other career mod.

**One case where it cannot keep that promise.** The police decide whether to report you through a
function attached to your own car, and JAMMER replaces that function with one that throws the report
away. If another mod has already replaced the same function, JAMMER refuses to fight it and backs off —
and then nothing is being suppressed and the police ticket you normally. It does not hide this: the
panel reads **POLICE REPORTING** instead of ARMED, and it says so once in the log. If you see that
badge, a mod you have installed owns that hook and JAMMER's speeding half is not protecting you.

> ### About the speed cameras — read this before you expect CAMERAS JAMMED to move
>
> On BeamNG.Earth, JAMMER also beats France's real fixed speed cameras. Two things decide whether you
> will ever see that count move.
>
> **1. Earth's French roads are off unless you turn them on.** The speed cameras come with Earth's
> French road scenery, and that scenery is opt-in. If you have not set `BNE_FR_ROADS` yourself, your
> Earth has **no speed cameras at all** — not even in France. CAMERAS JAMMED sits at zero because
> there is nothing there to beat. That is not a fault in this mod. See
> [Turning the cameras on](#turning-earths-speed-cameras-on) below.
>
> **2. Earth's camera list is French only.** It is a surveyed catalogue of 2,565 real sites in France
> and its overseas départements, and that is Earth's only source today. Outside those places there is
> nothing to beat either.
>
> **This mod carries no camera list of its own.** It reads whatever Earth serves it, so as Earth adds
> other countries JAMMER will work with those too, with no update needed here.
>
> **None of this affects the police half.** Stopping them ticketing you for speed works everywhere,
> on any map, with or without Earth. For most players that is the whole mod.

---

## Install

1. Download the `.zip` from [Releases](../../releases). **Do not unzip it.**
2. Close the game first.
3. Put the zip in your mods folder:
   `%LOCALAPPDATA%\BeamNG\BeamNG.drive\current\mods\`
4. Start the game.

## Requirements

| | |
|---|---|
| BeamNG.drive | 0.40.4 or newer |
| BeamNG.Earth | Optional, and only for the speed-camera half. Built against the 1.9.x betas. |
| RLS Career Overhaul | Not required. Not used at all. |

## Switching it on

The panel has an **ARM / DISARM** button. That is the whole setup — you can play without binding
anything.

If you would rather use a key or a controller button:

> Options → Controls → Gameplay → **"Radar Jammer: Toggle"**

No key is bound for you on purpose. A default binding would stamp on something you already use.

## Finding the panel

Open the apps bar and look under **Gameplay** for **JAMMER**.

BeamNG does not place a newly installed app for you. It waits in the apps picker until you drag it
onto your HUD. That is normal and is not a bug.

The panel is sized to stay readable when you crop it out of a screenshot.

## What it does

**While it is ON:**

- The police stop ticketing you for speed. Speeding and racing are not reported.
- Everything else still is. Reckless driving, driving the wrong way and red-light cameras all count
  exactly as before. **It is a radar jammer, not an invincibility switch.**
- Fixed speed cameras in the map do not catch you.
- On BeamNG.Earth, its real speed cameras do not flash you, and every one you get past is added to
  your **CAMERAS JAMMED** count.

**While it is OFF**, everything behaves as it would without the mod.

### The two numbers on the panel

**POLICE JAMMED** — how many tickets you did not get. This is the headline number, because it works
everywhere.

It counts **one per pass**. Blast past a patrol car and that is one, however long you stay on the
throttle. It only moves when police can genuinely see you — speeding down an empty road counts
nothing, because there was nothing to save you from. It never moves while the jammer is off.

**CAMERAS JAMMED** — how many of Earth's speed cameras you got past while armed. Second on the panel,
because on a default install there are no cameras at all and it correctly reads zero.

The panel shows **counts only, no money.** Earth's camera fine is a simulated one that never touches
your career balance (see *A note on the money* below), so a euro total sitting beside a
Beam Bucks economy invited exactly one wrong conclusion — that it was money you saved. It is not. The
figures are still recorded in the score file and still quoted in the mod's own notifications, where
naming the French amount is the honest thing to do; they are simply not kept as a scoreboard.

### The words beside the title

The panel says **ARMED** or **OFF**, and beside that it speaks up **only when something is wrong**.
There is deliberately no badge for everything working — ARMED already says that. So any of these means
read it:

| Badge | What it means |
|---|---|
| **POLICE REPORTING** | Another mod owns the speed-offence hook on your vehicle, so JAMMER backed off and your speeding **is** being reported. See the note at the top. |
| **FINES LANDING** | Earth's cameras are live and currently able to fine you — the jammer is not blocking them. **EXPOSED · FINES LANDING** means that *and* you are inside the 60-second window after switching off. |
| **NO EARTH CAMERAS** | Earth has no camera data for where you are, so there is nothing to beat and CAMERAS JAMMED correctly stays at zero. |
| **LAST KNOWN** | The numbers on screen have stopped updating. They are dimmed rather than quietly shown as current, because a stale number that looks live is worse than no number. |
| **NO SIGNAL** | The panel is not hearing from the jammer at all, and the numerals show dashes. |

The small strip beside **RESET SCORE** says the same two things about the score line itself:
**WAITING FOR JAMMER** before the first reply arrives, and **RE-READING SCORE FROM JAMMER** while a
reset is being confirmed. Both clear on their own.

The counts and both euro totals live in `settings/srcl_jammer_earth.json`. It is written when you
switch the jammer off, change level, quit, or clear your score with **RESET SCORE** on the panel.
Deleting the file resets your score too.

## The catch

- **Switch the jammer off and you are EXPOSED for 60 seconds.** The cameras are live again and will
  flash you. Switching back on during those 60 seconds does not help you.
- **Changing vehicle** switches it off, and exposes you if it was on.
- **Opening the World Editor** switches it off and exposes you, the same as doing it yourself.
- It does not work on foot, and it will not arm while the World Editor is open.

## Turning Earth's speed cameras on

This is a BeamNG.Earth setting, not a JAMMER one. Earth's French road scenery — and every speed
camera with it — only appears if the environment variable `BNE_FR_ROADS` is set.

To set it once, so it sticks for every future launch, open Command Prompt and run:

```
setx BNE_FR_ROADS on
```

Then close and reopen any program that needs it, Steam included. You only do this once.

**JAMMER does not set this for you, and will not.** A mod that quietly writes a permanent setting into
your system is a mod behaving like something you would not want installed. If you would rather this
were a normal in-game Earth setting, that is a fair thing to ask the Earth project for.

With the cameras off, the panel says **NO EARTH CAMERAS** and CAMERAS JAMMED correctly stays at zero.
POLICE JAMMED still works.

## What it changes while it is running — please read

This mod is open about being intrusive, because two of the things it does reach outside its own files.

**1. While armed it rewrites the callback on the map's fixed speed-camera triggers**, so your car's
camera hits come to this mod instead of to the game. It saves the exact value it found on each one and
puts it back when you switch the jammer off, change vehicle, change level, or when the mod unloads. If
another mod has taken one of those triggers over in the meantime, this mod leaves it alone rather than
overwriting it. **Nothing is written to any map file on disk.**

Those triggers live in memory, not on disk, so there is nothing to clean up afterwards. The one way it
could go wrong is saving the level in the World Editor while the jammer is on, which would write the
redirect into your own level file permanently. The mod does not rely on you remembering that: it
refuses to arm while the editor is open, and if you open the editor with the jammer on, it switches
itself off first.

**2. On BeamNG.Earth it replaces a few functions on Earth's own speed-camera module while in use**, and
puts every one of them back. If a future Earth update changes that module, this mod notices, turns its
camera feature off, says so once in the log, leaves Earth untouched, and carries on doing everything
else.

**3. It takes over the speed-offence check on your own traffic entry** — the hook the police read to
decide whether you get reported — and gives it back on disarm, vehicle change, level change and unload.
It takes it over **only if nothing else owns it**. If another mod got there first, JAMMER leaves that
mod's version exactly where it is: replacing another mod's work is not this mod's business. That is the
POLICE REPORTING case above.

It writes two files: its own score file, named above, and `settings/srcl_diary.txt` — a
rolling 300-line event log, shared with my other mods, which append to it as well. It claims exactly one global name, `JAMMER_speedTrapTrigger`, and releases it when
unloaded.

## Your career save is safe

This mod does not touch your career save, your vehicles, your money or your progress. The two files it
writes are its own score file and a shared event log
(`settings/srcl_diary.txt`). Neither is part of your career save.

## A note on the money

**No money changes hands.** BeamNG.Earth does not charge you for a speed camera. Its own message calls
it a *simulated fine*, and there is no career, wallet or balance anywhere in that code. The euro
figures are a score, not a transaction. They are **not** Beam Bucks and not your career currency.

They are in euros because Earth's camera model follows French law.

First the legal tolerance comes off your measured speed: 5 km/h below 100 km/h, 5% above that. Then
the fine lands on one of three fixed amounts:

| Over the limit by, after the tolerance | Fine |
|---|---|
| Under 20 km/h, where the limit is over 50 | €68 |
| Under 20 km/h, where the limit is 50 or under | €135 |
| 20 km/h up to 50 | €135, whatever the limit |
| 50 km/h or more | €300, plus a criminal offence |

Those amounts are not adjusted to wherever you happen to be driving, and this mod does not pretend
otherwise. It reports Earth's own numbers.

## Known issues

- **With `BNE_FR_ROADS` unset, CAMERAS JAMMED stays at zero.** Not a bug. See the box at the top.
- **Outside France CAMERAS JAMMED stays at zero** even with the cameras on. Earth's catalogue is French
  only today. This mod will pick up new countries as Earth adds them.
- **If the panel reads POLICE REPORTING, another mod owns the speed-offence hook** on your vehicle
  and speeding is not being suppressed. JAMMER will not take the hook off another mod. The cameras
  half, on Earth, is unaffected.
- This is a beta and has had no public testing yet.

## Reporting a bug

Please open an [issue](../../issues) and include your game version, your BeamNG.Earth version if you
run it (the dev number, or the version string — either is fine), and which map you were on. There is a template that asks for exactly that.

## Credits and licences

This mod interoperates with BeamNG.Earth and calls its public speed-camera functions.
BeamNG.Earth is used under the MIT License:

```
MIT License

Copyright (c) 2026 TecnaGamer

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

No other third-party code, art, sound or data is included in this mod.

BeamNG.drive is a trademark of BeamNG GmbH. This is an unofficial fan project and is not affiliated
with or endorsed by BeamNG GmbH, or by the BeamNG.Earth project.

## This mod's own licence: MIT

JAMMER's own code is released under the **MIT License** — the full text is in
[LICENSE](LICENSE), copyright © 2026 SwimmingRemy.

In plain terms: **other modders are welcome to use it.** You may bundle JAMMER in your own mod,
fork it, change it, or ship it as part of something you charge for. You do not need to ask me, and
you do not owe me anything. The only condition MIT puts on you is the usual one — keep the copyright
notice and the licence text with the code when you redistribute it.

Building a crime or pursuit mod? The police half of JAMMER would probably suit it. That half needs
no BeamNG.Earth and no career overhaul, and works on any map, so you can lift it on its own without
taking the rest.

I would enjoy hearing about it if you do. That is a request, not a condition.
