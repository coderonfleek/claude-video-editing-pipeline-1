# Lesson 7 — One Skill to Run the Pipeline (`/produce`)

## Video goal

So far you've run each step by asking Claude. In this lesson, everything gets packaged into **one command**:

```text
/produce 02-my-next-video
```

Point it at a video folder and Claude runs every step, makes the editing decisions using your style guide, checks its own work, and hands you the finished video and project file.

🎬 At the end: a **brand-new video**, edited with one command. That's the proof you've built a real pipeline and not a one-off edit.

⏱ About 30 minutes of your time, plus about 45 minutes while `/produce` edits the video on its own.

---

## Before you start

- Lessons 1–6 are done.
- **A second video folder:** `projects/02-<name>/`, set up exactly like `01-sample`:
  - `main-roll/`: your camera footage
  - `audio/`: your microphone recording (if it's separate)
  - `b-roll/`: your screen recordings, as video files
  - `extras/`: anything else, such as Screen Studio project folders
  - `plan.md` (optional): copy `projects/_plan-template.md` and fill in what you know

  Use the second video from the sample pack, or record a new one yourself. The sample pack's second video comes as loose files, so sort them into these folders in Finder (File Explorer on Windows) first.

Nothing new to install.

> **What's a skill?** A skill is a saved set of instructions Claude can follow on command. You run it by typing `/` and its name, like `/produce`. It's like a recipe card: the same steps, done the same way, every time.

---

## Steps

### Step 1 — Write down everything you taught Claude

**What this does:** over the last few lessons you gave Claude lots of notes. Before packaging the pipeline, Claude makes sure none of them get lost.

**Send this to Claude:**

```text
Look back through CHANGELOG.md, CLAUDE.md, my style guide and the fixes we made on 01-sample.
List every rule or lesson we learned that ISN'T written down yet where the pipeline will find it,
for example "always check the cut report for uncertain lines", "end a graphic as soon as its
content is done", "look at every graphic before saying it's finished".
For each one, suggest where it belongs:
- my style guide (how things should LOOK and SOUND)
- CLAUDE.md (how to RUN the pipeline)
- the /produce skill (the STEPS and CHECKS of an edit)
Show me the list in plain words.
```

**Check it worked:** read the list. Say yes, no or change for each item, e.g. *"Yes to all, except number 4. That was just for this video."* Claude puts them in place.

### Step 2 — Create the `/produce` skill

**Send this to Claude:**

```text
Create a skill called "produce" for this project, so I can type /produce <video folder name>.
It should be used when I say things like "produce <video>", "edit <video>", or when I add a new
folder to projects/.
The skill is the full editing workflow, step by step:
1. Check the video folder has everything it needs. If something's missing, stop and tell me
   what, in plain words.
2. Prepare: ingest, script, transcribe, cut. Read the cut report and sort out uncertain or
   missing lines yourself (search the transcript, use overrides). Only ask me about lines I
   really didn't record. Never invent a line.
3. Plan: write the shot plan using my style guide's rules, run the checker and fix every warning.
4. Make the title card, graphics and end card from the kit, timed to my words.
5. Build everything: colour, audio, screen recordings, graphics, captions, final video and
   project file.
6. Check your own work before showing me: look at a picture from the middle of every shot.
   The right screen is showing for what I'm saying, nothing important is cut off, captions are
   spelled right and don't cover graphics, nothing is in the safe-zone edges, loudness is on
   target, and the project file matches. Fix anything wrong and re-run only the step that needs it.
7. Tell me in plain words: where the video and project file are, how long the video is, and
   anything I should double-check.
Point to my style guide and CLAUDE.md for the rules instead of copying them, so there's only
one place to update them.
```

**Check it worked:**
1. Close the Claude app and reopen it, then click this same chat in the sidebar to carry on in it.
2. Type `/` in the message box. `produce` should appear in the list.
3. Ask: *"Check every step and file in the produce skill really exists."* Claude should confirm it all does.

### Step 3 — Stop the permission pop-ups

**What this does:** a full edit runs dozens of small steps. Without this, Claude asks your permission for every single one. You'll allow the routine ones once, permanently. Anything risky (installing or deleting) still asks.

**Send this to Claude:**

```text
I want /produce to run without asking me permission for routine steps. Add project settings
that always allow: running the pipeline's own Python steps, FFmpeg, HyperFrames, and the
transcriber. Installing and deleting things should still ask me.
Also add a rule to CLAUDE.md: keep each command simple (one command at a time; for anything
complicated, write a small script in the build folder and run it), because complicated commands
can't be pre-approved and will keep asking.
Explain in plain words what you allowed.
```

**Check it worked:** in the next step, you should only be asked about genuinely new things.

### Step 4 — Edit your second video with one command

**Do this:** in the same chat, type:

```text
/produce 02-<name>
```

(Use your folder's actual name.)

**What you should see:** Claude first checks the folder. If files are in the wrong place, it stops and tells you which ones to move. Move them, then say *"Done, go ahead."*

Then it works through every step on its own for about 45 minutes. It may ask you a question if a line seems missing or a screen recording isn't in your plan. It finishes with a short report:
- where the video, project file and subtitles are, how long the video is, and its loudness
- what's in the video (title, number of graphics, where screen recordings are used)
- what it checked (e.g. *"all 122 caption highlights land on their exact frame"*)
- a numbered **Please double-check** list: places it couldn't fix (e.g. your face near the edge of the camera's view), lines it wasn't sure it heard right, two rules that clash (e.g. a long name that's slightly too wide for one caption), and choices it made without a `plan.md`
- fixes it made to the pipeline itself, logged in `CHANGELOG.md`, so every future video benefits

Answer the double-check items in plain words, e.g. *"1: leave them. 3: split it into two captions."*

> **If it stops with a connection error** (for example *"API Error: Couldn't connect…"*), nothing is lost. Say: *"The connection dropped. Please carry on from where you stopped and finish the whole edit."* It picks up from the last finished step.

**Check it worked:**
- **Watch the video.** It should look like **the same channel** as `01-sample`: same colour, captions, graphic style, title and end cards, and pacing. And Claude has never seen this footage before.
- **Open the project file** in your editing app (Lesson 6's checks).
- **Note anything you had to correct.** Each one is a rule to add in Lesson 8.

### Step 5 — Make a quick change

**What this does:** shows that fixing one thing doesn't mean re-editing everything.

**Send this to Claude:**

```text
In 02-<name>, change the title card headline to "<your new headline>", with "<one word>" highlighted.
Re-make just that and rebuild.
```

For example: *In 02-disable-skills, change the title card headline to "Turn off auto-firing skills", with "auto-firing" highlighted.*

**What you should see:** after about 10 minutes, the new headline is in the video and the project file is updated. Claude re-runs only the steps after the change (graphics, captions, final video, project file). It doesn't re-cut, re-grade or re-transcribe, so it's much quicker than the 45-minute full edit. If your headline is long, Claude splits it over lines to follow your style guide's words-per-line rule and tells you.

---

## What you have now

- ✅ `/produce`: your whole pipeline in one command
- ✅ Routine steps pre-approved, so edits run without constant pop-ups
- 🎬 **Milestone video:** `projects/02-<name>/build/final/02-<name>.mp4` plus its project file, a new video in your style from one command

## Landscape note

Want horizontal videos as well? Remember: **one pipeline per style**. Ask Claude: *"Make a copy of this whole pipeline for horizontal 1920x1080 videos, and update the style guide's Format, Screen recording layout and Captions sections."* Then run `/produce` on a horizontal video in the copy. If anything breaks, ask Claude to fix it in both copies.
