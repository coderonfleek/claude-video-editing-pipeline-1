# Lesson 2 — Rough Cuts and Audio

## Video goal

Turn your raw recording into a **rough cut**: Claude keeps your best take of every line, removes mistakes, retakes and long pauses, and adds zooms to keep it lively. Then it **colour-grades** your footage to match your reference picture and **cleans up the audio**: clearer voice, steady volume, background music that drops when you talk.

🎬 At the end you'll have your first real edited video in `build/final/`.

⏱ About 2–2.5 hours. Most of it is Claude working: the rough cut and zoom steps take about 20 minutes each to build. You only need to step in to check results between steps.

> **Keep going in the same chat as Lesson 1.** This lesson uses a lot of Claude usage. On a Pro plan you may hit the limit; just continue in the same chat when it resets.

---

## Before you start

- Lesson 1 is done: `build/1-ingest/preview.mp4` plays correctly.
- You need one new tool: **Vibe**, a free app that turns your speech into text and records exactly when each word was said. That's how Claude knows where to cut. The same setup powers your captions in Lesson 5, so it only happens once.

**Send this to Claude:**

```text
The pipeline needs Vibe to turn my speech into text with a timing for every word. We'll use it
for cutting now and for captions later. Please handle all of it:
1. Check whether Vibe is already installed. If it is, leave it as it is.
2. If it isn't, download the right version for my computer (Mac Apple chip, Intel Mac or
   Windows) from Vibe's official GitHub releases page (github.com/thewh1teagle/vibe/releases)
   and install it. Tell me if I need to click anything, for example a security prompt.
3. Check whether Vibe's large-v3-turbo model (ggml-large-v3-turbo.bin) is already downloaded
   (Vibe keeps models in its app data folder). If not, download it into that folder (about 1.6 GB).
4. Vibe includes a command-line transcriber inside the app (called sona). Use it with that model
   for the pipeline, so nothing else needs installing and no model is downloaded twice.
5. Save where everything is in the pipeline settings and in CLAUDE.md.
6. Test it on the first 30 seconds of my recording and show me the text it heard, with word timings.
Explain each step in one simple sentence, and tell me what was already there and what you added.
```

**What you should see:** Claude reports what it found, e.g. *"Vibe and its large-v3-turbo model were already installed, so nothing was downloaded."* Or, on a fresh computer, *"I installed Vibe and downloaded the model (1.6 GB)."* Then it shows the words from your first 30 seconds with their timings.

**Check it worked:** the text matches what you said in the first 30 seconds of your recording.

**If it's not right:**
- **Claude asks to access a folder outside your project** (like Applications, or Vibe's app data folder): click **Allow**. Vibe lives there, and the pipeline needs to use it. If Claude says it's *blocked* from looking outside the project folder, tell it: *"Please tell me exactly how to give you access to Vibe's folders."*
- **Mac:** if a message says Vibe "can't be opened because Apple cannot check it", go to **System Settings → Privacy & Security**, scroll down and click **Open Anyway**, then tell Claude *"Done."*
- **Windows:** if a pop-up asks *"Do you want to allow this app to make changes?"*, click **Yes**.
- If the download fails or stalls, tell Claude: *"The download didn't work. Can you try again?"*

---

## Steps

### Step 1 — Read your script

**What this does:** Claude turns your `plan.md` into a structured list the pipeline can use: numbered script lines, sections, b-roll notes and graphic ideas.

**Send this to Claude:**

```text
Build the "script" step: read projects/<video>/plan.md (in the format of
projects/_plan-template.md) and save its parts (aim, words to spell right, sections, numbered
script lines, b-roll notes, motion graphic ideas) in the build folder. If there's no plan.md or
no script, save an empty plan and make sure later steps still work. Run it on 01-sample and tell me
how many script lines you found, plus the first and last line.
```

**Check it worked:** the number of lines and the first and last lines match your `plan.md`. No plan for this video? Claude should say it found 0 lines and that later steps will work from the recording alone.

### Step 2 — Transcribe the recording

**What this does:** turns all your speech, including every retake, into text with a timing for each word.

**Send this to Claude:**

```text
Build the "transcribe" step and run it on 01-sample. Turn the synced audio into text with a
timing for every word.
Important: long recordings with lots of retakes can confuse the transcriber (it repeats
phrases or makes words up), so split the audio at the pauses first, transcribe each piece, and
put the timings back together. Keep a version transcribed without the script as a hint, so we
can double-check later.
To get names and special terms right, create style/glossary.txt (words that come up in all my
videos, like my channel name and product names) and also use the video's "Words to spell
right" from plan.md. Pass them to the transcriber as hints.
When done, show me the text from 3 random moments with their times, so I can compare them with the video.
```

**What you should see:** three short snippets, each with a time like *"at 1:42: 'and that's when I realised…'"*.

**Check it worked:** jump to those times in `preview.mp4` (drag the playhead). The words should match what you hear.

**If it's not right:** misheard names are the most common problem (e.g. "Claude Code" heard as "clock code"). Tell Claude: *"Add 'Claude Code' to my glossary and transcribe again."*

### Step 3 — Make the rough cut

**What this does:** this is where the editing starts. Claude matches each script line to your recording, picks your best take (usually the last complete one, since people restart after mistakes), and cuts everything else.

**Send this to Claude:**

```text
Build the "cut" step and run it on 01-sample. For each script line:
- find every time I said it, and keep the best take (usually the last complete, smooth one)
- remove retakes, false starts and long silences, keeping pauses within my style guide's limits
- never speed up my footage
If I said something that isn't in the script but clearly meant it (an ad-lib), keep it and mention it.
If there's no script, cut based on what I said: remove repeated phrases, false starts and long pauses.

Also:
- write a simple report (report.md, in the cut's build folder) listing each line, which take you chose, how
  confident you are, and anything MISSING or uncertain
- let me make manual corrections that are saved and respected every time this step runs
  (an "overrides" file)
- re-check each kept piece without the script as a hint, and flag any that sound different
  from the script. These might hide a stumble.
Make a preview video of the cut. Then tell me where it is, and give me a plain-English
summary: how long the cut is, and anything I should check.
```

**What you should see:** after about 20–25 minutes, a summary like *"The cut is 1 minute 21 seconds, down from 7 minutes. I found 16 sentences and kept your last good take of each. I removed 7 earlier takes, 3 false starts and 2 stray words. Please check line 11: the transcriber wasn't sure whether you said 'thankfully' or 'wrongfully'."*

With the sample pack (no script), the cut comes out at about 1:20 from the 7-minute recording.

**Check it worked:**
1. **Read the summary.** For anything flagged:
   - "MISSING": did you really skip that line? If you said it in other words, tell Claude: *"I said line 7 as '…'. Please use that."*
   - "Possible stumble" or "not sure": listen to that line in the preview. These are often false alarms (the transcriber misheard, but the take is fine). If it sounds right, tell Claude *"Line 11 is fine as it is."*
2. **Watch the cut preview all the way through** (Claude tells you where it is). Listen for:
   - words cut off at the start or end of a line
   - a sentence that repeats (a retake that slipped through)
   - a pause that feels too long or too short

**If it's not right:** describe it in plain words. Claude saves your correction and re-runs only this step.
- *"Line 4's last word is cut off."*
- *"At around 0:23 I say the same sentence twice. Keep only the second."*
- *"Drop line 9 completely."*
- *"The pause after line 3 is too long."*

### Step 4 — Add zooms

**What this does:** adds gentle zoom-ins (punch-ins) to keep the video lively and hide the jump where two takes join.

**Send this to Claude:**

```text
Add zooms to the cut, following the Framing and zooms section of my style guide:
- change the framing slightly at the joins between takes so the cut doesn't look like a jump
- zoom in on lines that deserve emphasis (the hook and the takeaway are good choices; use
  the script and sections to decide)
- keep my face nicely framed at every zoom level
My recording is higher quality than the final video, so zoom by cropping in, not by stretching.
Save the zooms so I can adjust them later, and update the preview.
Then show me one still frame from each zoom and tell me which line it's on.
If anything I've asked for here clashes with my style guide, tell me what you changed in the guide.
```

**Check it worked:** look at the still frames. Your face is never cut off, and the zooms are on lines you'd want to emphasise. Then watch the preview. Do the cuts between takes feel smoother now?

**If it's not right:**
- *"Too many zooms. Only zoom on the hook and the takeaway."*
- *"The zooms are too fast. Make them smoother."*
- *"Make this a rule in my style guide."* (Add this to any note you want to apply to every future video.)

### Step 5 — Colour-grade to match your reference

**What this does:** Claude creates a **LUT**, a small file that stores a colour look, so your footage matches the colours of your reference (your `grade-reference.png`, or frames of you from your finished example videos). This becomes your "house look" for every video.

**Send this to Claude:**

```text
Build the "grade" step. Create my house colour look from the colour reference in my style
guide's Colour section (examples/grade-reference.* if I have one, otherwise the frames of my
face from my finished example videos):
1. Take a few clear frames of my face from the recording.
2. Build a LUT (.cube file) that moves my footage's colours toward the reference: skin tone,
   contrast, how dark the shadows are, colour intensity. Keep my skin looking natural.
3. Save it as style/grades/house.cube and mention it in my style guide's Colour section.
4. Make a comparison picture: the same 3 frames side by side as original | graded | reference.
This is ONE look for every future video. Only use a different one if I ask for it on a specific video.
Show me the comparison picture.
```

**What you should see:** a side-by-side comparison picture, and a short explanation of what changed. For the sample pack, the graded footage gets a little darker and richer, with deeper blacks and a warm room, while skin stays natural.

> **Wearing different clothes from your reference?** That's fine. Claude matches your face, skin and room, not your outfit. In the sample, the reference shows a grey shirt and the recording a white one, and the white shirt stays white.

**Check it worked:** in the middle column, your skin looks natural and healthy, not orange, grey or plastic, and the overall feel is close to the reference.

**If it's not right:** describe it like you'd describe a photo filter:
- *"It's too orange."*
- *"The shadows look greenish."*
- *"I want it a bit brighter and softer."*
- *"Closer to the reference, but my skin is too red."*

> **Already have a colour look (LUT) you like?** Put the `.cube` file in `style/grades/` and tell Claude: *"Use this as my house look instead of making one."*

### Step 6 — Clean up and layer the audio

**What this does:** makes your voice clear and consistently loud, then adds background music that automatically gets quieter when you talk.

**Send this to Claude:**

```text
Build the "audio" step, following the Audio section of my style guide:
- My voice: remove rumble and background hiss gently, even out the volume, soften harsh "s"
  sounds if needed, and set the loudness to my style guide's target (if it doesn't have one, use
  -14 LUFS, the usual target for YouTube/TikTok). Smooth every cut so there are no clicks.
- Music: use the music in audio/ (or style/music/ if there's none), make it fit the video's
  length, set it to my style guide's volume, make it duck (get quieter) whenever I talk,
  and fade it in and out.
- Save my voice and the music as separate files as well as the final mix. We'll need the separate
  files in Lesson 6.
When done, tell me in plain words whether the loudness hit the target.
```

**What you should see:** Claude reports your loudness before and after (e.g. *"−25 LUFS → −14.1 LUFS"*) and what it did to your voice.

> **No music yet?** The sample pack has none, and that's fine. The video is voice only, and the music part kicks in automatically once you drop a track into `audio/` or `style/music/`.

**Check it worked:**
- Claude tells you the loudness is on target.
- **Listen with headphones:**
  - no clicks or pops where lines join
  - your voice sounds natural, not "underwater" or robotic
  - the music is clearly quieter when you speak and comes up a little in pauses, without obvious jumping

**If it's not right:** *"The music is too loud under my voice."* · *"My voice sounds robotic. Use less noise removal."* · *"I hear a click at 0:31."*

### Step 7 — Put it all together

**What this does:** builds the **assemble** step, which combines the cut, zooms, colour and audio into one finished video. Every later lesson adds a layer to it.

**Send this to Claude:**

```text
Build the "assemble" step: combine the cut, zooms, colour grade and mixed audio into
build/final/<video>.mp4, using the size, frame rate and format in my style guide.
Later lessons will add screen recordings, graphics and captions on top, so build it in layers.
Also give me one command that runs every step after ingest in order, while still letting any single step
be re-run on its own. Update CLAUDE.md and CHANGELOG.md, then build 01-sample.
```

**What you should see:** Claude lists the finished video's settings (1080×1920, 30 fps, loudness on target) and gives you the one command that rebuilds everything, something like `… pipeline edit 01-sample`. You'll rarely type it yourself. Asking Claude *"rebuild 01-sample"* does the same.

**Check it worked:** open `projects/01-sample/build/final/01-sample.mp4` and watch it all the way through. 🎉 With the sample pack it's about 1 minute 20 seconds.

---

## What you have now

- ✅ New steps: script → transcribe → cut → zooms → colour grade → audio → assemble
- ✅ Your **house colour look** (`style/grades/house.cube`), used on every future video
- 🎬 **Milestone video:** `build/final/01-sample.mp4`, a tight, colour-graded rough cut with clean voice (and background music, if you added any)

## Landscape note

Zooms work the same way. If you record horizontal video in 1080p (not 4K), keep zooms small (about 1.2×) so the picture stays sharp. Ask Claude to put that in the style guide.

## Common problems

| What you see | What to tell Claude |
|---|---|
| A line is missing from the cut | *"Line X is missing. I definitely said it around [time]."* |
| The cut feels rushed | *"The pauses are too short. Let me breathe a bit more."* (Claude updates the pacing rule.) |
| Colours look different in different shots | *"The colour changes between shots. Can you check the grade is applied the same everywhere?"* |
| **Windows:** an audio step errors | *"This error appeared: [paste it]. Is my FFmpeg missing something?"* |
