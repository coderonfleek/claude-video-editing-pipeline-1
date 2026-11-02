# Lesson 3 — Adding B-rolls

## Video goal

Add your **screen recordings** (b-roll) to the video at the right moments. Claude watches each recording, works out what happens on screen and when, and places it where you talk about it. The screen recording shows at the **top** of the video with your face **below**: a split layout.

**What's new here:** this is the first time Claude makes **editing decisions** for you. It writes them down in a **shot plan** (a list of every shot, what's in it and why) *before* making the video, so you can read it, question it and change it. Lessons 4 and 5 build on the same plan.

🎬 At the end: your rough cut, now with screen recordings.

⏱ About 1 hour, most of it Claude working. Building the split layout takes about 15–20 minutes.

---

## Before you start

- Lesson 2 is done: `build/final/01-sample.mp4` plays correctly.
- Your screen recordings are in `projects/01-sample/b-roll/`. Listing them in `plan.md` under **B-rolls** helps, but isn't required: with no plan, Claude matches recordings to what you say.

> **Tip for recording b-roll:** make the editor font bigger before you record, and record each thing you'll talk about. B-roll only appears where you talk about what it shows. The rest of the video is your face and (from Lesson 4) motion graphics.
- Your style guide's **Screen recording layout** section is filled in. If you're not sure, ask Claude: *"Is my Screen recording layout section complete enough to place b-rolls?"*

Nothing new to install.

---

## Steps

### Step 1 — Let Claude watch your screen recordings

**What this does:** Claude looks through each screen recording and notes what happens and when, like a script for each recording, and which part of the screen matters.

**Send this to Claude:**

```text
Look at every screen recording in projects/01-sample/b-roll/. For each one, take still frames
every couple of seconds so you can see it, and write down what happens and when, e.g.
"0–3s: settings page opens. 3–7s: typing in the search box. 7s: the result appears".
Also note which part of the screen matters (e.g. "the action is all in the left third").
Save your notes in the build folder and show me a picture sheet of frames for each recording.
```

**What you should see:** for each recording, a timeline like *"0–3.9 s: nothing happens. 3.9 s: zooms in on the top of the file. 9.3 s: selects lines 1–10"*, which part of the screen matters, and which of your lines it fits. Claude also points out things like *"your recordings already zoom in by themselves"* and *"the last 11 seconds are idle"*.

**Check it worked:** look at the picture sheets. Do Claude's notes match? If it says "the result appears at 7 seconds", check the frame at 7 seconds.

**If it's not right:** *"In 02-run-command, the result appears at 9 seconds, not 7."*

### Step 2 — Teach Claude your editing rules

**What this does:** you only do this once. These rules let Claude make the same choices you would, on every video.

**Send this to Claude:**

```text
Add a "Shot planning rules" section to my style guide. Interview me with simple questions
and give me sensible suggestions to choose from (I'm not a professional editor). Cover:
- how long the video opens on just my face (the hook)
- which lines should show a screen recording (e.g. any line that names a setting, button,
  command or file)
- how long a screen recording can stay on screen, and whether one can cover several lines
- the longest stretch of just my face allowed in the FINISHED video (motion graphics come in
  Lesson 4 and will fill those gaps, so screen recordings must never be used as filler)
- whether to put a short shot of my face between big visuals
- what to do when a recording is shorter than what I'm saying (freeze the last frame? slow it down?)
  or longer (trim it? speed it up? by how much at most?)
- that the screen should show the action AT THE MOMENT I describe it
- a screen recording is only used where the line is about what it shows. Never reuse a
  recording or stretch one just to fill time.
```

**What you should see:** Claude first checks what your style guide already says, then asks numbered questions with options and a ⭐ suggestion. Answer with letters, e.g. *"1B, 2B, 3: up to 15 s if the screen keeps changing, 4B…"*, or say *"go with your suggestions"*. Then it writes a new section with clear rules like *"Open on your face for 3–6 seconds"*, *"Screen recordings up to 15 seconds"*, *"Never more than 6 seconds of just your face"*, *"Screen recordings can be sped up to 1.5×; your face never".*

**Check it worked:** read the new section. Does it sound like how *you* would edit? Compare it with the finished Shorts in your examples folder.

### Step 3 — Make the shot plan

**What this does:** Claude plans the video shot by shot: when it's your face, when it's a screen recording, which recording, and which part of it. It ties each shot to **the words you say**, so it stays correct even if the cut changes later.

**Send this to Claude:**

```text
Build the "plan" step and run it on 01-sample. Write a shot plan: a list of shots in order,
each with an id, a type (face or split for now), which script lines it covers, where it starts
and ends (tied to the spoken WORDS, not fixed times, so it survives re-cuts), and for split
shots: which recording, which part of it, and any speed change or freeze.
Use plan.md's B-rolls as suggestions, your notes on what happens in each recording, and my
Shot planning rules. Line up on-screen moments with the words that describe them (the click
happens on "click").
Only put a screen recording where the line is about what it shows. Never reuse a recording or
stretch one just to fill time. Everywhere else is my face for now. Where a face stretch is longer
than my rules allow, don't fill it with b-roll: mark it "needs a graphic" (motion graphics come
in Lesson 4).
Also build a checker that turns the plan into exact times and warns about anything that breaks
my rules (gaps, overlaps, recordings too short or too long, b-roll that doesn't match its line).
Fix every warning. Long face stretches are listed as "needs a graphic", not as errors.
Then explain the plan to me in a simple list, one line per shot.
```

**What you should see:** a list like:
- *Shot 1: face, hook (0:00–0:05)*
- *Shot 2: split with 01-open-settings, 0:05–0:12. The settings page opens as you say "open your settings".*
- …

Claude also tells you where the plan file is, in case you ever want to edit it by hand (you don't have to).

> **Some lines say "needs a graphic".** That's expected. Those are face stretches longer than your rules allow, where no screen recording fits. Lesson 4 fills them with motion graphics. Claude never pads them with b-roll.

**Check it worked:**
- Every screen recording appears when you talk about it.
- Claude says there are **no warnings** left. "Needs a graphic" notes are fine.
- **No recording is used just to fill time.** Each one appears only where you're talking about it.
- Question one decision: *"Why is there no screen recording on line 9?"* A good answer points to one of your rules. If the answer doesn't make sense, your rules need a tweak. Tell Claude what you'd prefer.

### Step 4 — Make the video with the split layout

**What this does:** builds the screen recordings into the video: the recording on top, your face below.

**Send this to Claude:**

```text
Add screen recordings to the assemble step, following my style guide's Screen recording layout:
- the recording sits at the top, cropped to the part of the screen that matters (from your
  notes); never squash or stretch it
- my face is reframed into the bottom part, with the same colour look as the rest of the video
- face-only shots stay full screen
- don't apply my face colour look to the screen recordings
- save the crop for each shot in the plan so I can adjust it
Rebuild build/final/01-sample.mp4, then show me a still frame from the middle of each shot,
labelled with what I'm saying at that moment.
```

**What you should see:** after about 15–20 minutes, a list of every split shot with what's on screen and what you're saying. Claude may also tell you it fixed its own crops after looking at the stills (e.g. *"the deny list was missing from the 'deleting' shot, so I moved the crop"*). That's normal. It may show the stills as a picture or as a link to a private page.

**Check it worked:**
- **Look at the stills:** each split shot shows what you're talking about at that moment.
- **Watch it on your phone** (AirDrop it on a Mac, or send it to yourself). Can you read the text in the screen recordings? That's how viewers will see it.
- Your face isn't cut off in the bottom half, and its colour matches the full-screen shots.

### Step 5 — Give notes like you would to an editor

**Do this:** watch the whole video and tell Claude what to change in plain words. Claude updates the shot plan and re-makes the video. Examples:

- *"Shot 3 starts too early. The screen changes before I say it."*
- *"Freeze the last frame of recording 02 instead of cutting back to my face for one second."*
- *"Line 11 needs a screen recording. Use the end of 04-terminal."*
- *"The text in shot 5 is too small. Zoom in on the top-left of the screen."*
- *"At about 0:28 the whole editor window is squeezed in and I can't read anything. Zoom in on the file tree instead."* (This one came up in the course test with the sample pack.)

> **Tip:** if you find yourself giving the same note twice, say *"Add this to my Shot planning rules."* The pipeline remembers it for every future video.

---

## What you have now

- ✅ A **shot plan** you can read and change, plus a checker that enforces your rules
- ✅ **Shot planning rules** in your style guide
- 🎬 **Milestone video:** `build/final/01-sample.mp4`, your graded rough cut with screen recordings at the top at the right moments

## Landscape note

Horizontal videos don't have a "top half". The usual options are a **full-screen recording with your face in a small corner box**, or **side by side**. Add your choice to the style guide's Screen recording layout section. The shot plan works the same.
