# Lesson 8 — Thumbnail, Tweaks and Improvements

## Video goal

Finish the pipeline with three things:
1. **`/produce-thumbnail`**: a command that makes on-brand thumbnails from your own footage
2. **The tweak loop**: a simple habit that makes the pipeline better with every video you make
3. **Ideas for what to add next**

🎬 At the end: your final video with every feature, plus its thumbnail.

⏱ About 1 hour.

---

## Before you start

- Lesson 7 is done: `/produce` works.
- Put 2–3 thumbnails you like in `examples/` (`thumbnail-1.png`, …), if you haven't already. No thumbnails yet? That's fine: Claude starts from your title card design.

Nothing new to install. HyperFrames already has the tools we need:
- **snapshot**: saves a still picture from a design (made for thumbnails)
- **remove-background**: cuts you out of the background

So a thumbnail is a one-frame HyperFrames design, made with the **same brand kit** as your graphics. That's what makes it match the video.

---

## Steps

### Step 1 — Set your thumbnail rules

**Send this to Claude:**

```text
Look at the thumbnails in examples/ and the Thumbnail section of my style guide. Make the
section specific. Interview me with simple questions and suggestions:
- sizes (1080x1920 cover for Shorts; also 1280x720 for YouTube's horizontal thumbnails)
- where my face goes and how big
- what expression works (excited, surprised, pointing…)
- how many words of text (usually 2–4) and which font and colours from my brand
- background style
- whether to include an icon or a snippet of the screen recording
- it must be readable as a tiny picture in a phone feed
- things to never do
```

**What you should see:** about 9 numbered questions, each with a suggestion. Answer with letters, e.g. *"1A, 2C, 3A, 4B, 5A, 6A, 7A, 8A, 9 all"*. Claude may suggest **no face on the Shorts cover** (so it looks like your title card) and **your face on the horizontal YouTube thumbnail**, where faces help most. Pick what suits your channel.

**Check it worked:** read the section. It should describe the thumbnails you like.

### Step 2 — Thumbnail template

**Send this to Claude:**

```text
Using the HyperFrames skills, create a thumbnail template in the kit: a single-frame design at
1080x1920 that also adapts to 1280x720. Fill-in-the-blanks: a cut-out photo of me, a headline
(with one highlighted word), optional icons, optional screen snippet. Use my brand kit and
thumbnail rules. Save it as a picture with HyperFrames' snapshot.
For the photo of me, cut me out with HyperFrames' remove-background. The first time, it needs an
AI engine and a cut-out model (about 170 MB): check for them first, and install them inside this
project, not system-wide.
Make a test with a frame from 01-sample and show it to me.
```

> **Approve the install:** Claude asks before installing the cut-out engine and downloading the model. Click **Allow**. Both stay inside your project folder.

**What you should see:** a test thumbnail at each size. If your style guide's thumbnail rules use your face, it's cut out cleanly with no box or oval around it. Claude may suggest small design changes (e.g. dropping a label that's unreadable at phone size); say if you agree.

**Check it worked:**
- Put the test next to your example thumbnails (or your title card, if you have none). Does it look like it belongs with them?
- Ask Claude to *"show it at the size it appears in a phone feed (about 200 pixels wide)"*. Can you still read the headline?

### Step 3 — Create the `/produce-thumbnail` skill

**Send this to Claude:**

```text
Create a skill called "produce-thumbnail" so I can type /produce-thumbnail <video folder name>.
Steps:
1. Read the video's plan.md (aim, title card text) and my thumbnail rules.
2. Find the best frames of my face in the recording: sharp, eyes open, a strong expression,
   good lighting, with my house colour look applied. Show me the top 6 as a picture sheet.
3. Cut me out of the background with HyperFrames' remove-background.
4. Write 3 headline options (within my word limit, not just the video title repeated).
5. Make 3 different thumbnails from the template (mixing frames, headlines and layouts) and
   save them as pictures with HyperFrames' snapshot, in the video's build/thumbnail/ folder.
6. Show me all 3 side by side, at full size AND at phone-feed size, and recommend one, with the reason.
7. When I pick one, copy it to build/final/<video>-thumbnail.jpg, next to the video.
Also add a last step to /produce: "Offer to make a thumbnail with /produce-thumbnail."
```

**What you should see:** after about 15 minutes, Claude has built the skill and **tested it on your second video straight away**: a sheet of your best face frames, then 3 thumbnail options side by side (full size and phone-feed size) and a recommendation. It may ask to download a small face-expression model (about 4 MB) to judge your expressions. Click **Allow**.

**Check it worked:** close and reopen the Claude app, click this same chat in the sidebar to carry on in it, then type `/` and check `produce-thumbnail` is in the list.

### Step 4 — Make your thumbnail

**Do this:** type:

```text
/produce-thumbnail 02-<name>
```

(If Claude already showed you 3 options while testing the skill in Step 3, skip typing this and go straight to picking one.)

**What you should see:** a sheet of your best face frames, then 3 thumbnails side by side and a recommendation. Pick one, e.g. *"Option 1, please."* Claude copies it next to your video: `build/final/02-<name>-thumbnail.jpg` (and `-thumbnail-cover.jpg` for the Shorts cover, if your rules make one).

**Check it worked:**
- The **cut-out is clean**, with no leftover background around your hair or shoulders.
- The **headline is readable** at phone-feed size.
- **Your skin colour** matches the video.

**If it's not right:** mix and match in plain words:
- *"Use the layout of number 2 with the headline from number 1, and make my face bigger."*
- *"Pick a frame where I'm smiling."*
- *"The headline is too long. Two words max."*
- *"There's a bit of the chair behind my head. Pick a frame where I'm clearly in front of the wall."* (The cut-out works best where you stand out from the background. Bits of furniture or a mic arm at the edge are the usual weak spots.)

### Step 5 — The tweak loop: make every note count

This is the habit that makes your pipeline great over time.

Every time you correct something, ask yourself: **"Is this just for this video, or should it always be like this?"**

| Type of note | Example | What to say to Claude |
|---|---|---|
| **Just this video** | "Drop line 6 from this video" | Just say it. Claude saves it for this video only. |
| **How it should look or sound** | "Captions should be max 3 words" | *"…and make it a rule in my style guide."* |
| **How to run the pipeline** | "Always double-check the last word of each line" | *"…and add it to CLAUDE.md."* |
| **A check before handing over** | "Make sure no graphic text is near the bottom edge" | *"…and add it to the checks in /produce."* |
| **Something broke** | "The captions drifted out of sync" | *"Fix it, and add a check so it can't happen again."* |

**After every video (for the first few weeks), send this:**

```text
Look at all the corrections I made in this chat. For each one, tell me if it was a one-off or
should become a rule. For the rules, update the right place (style guide, CLAUDE.md, the
produce skill or the pipeline) and note why in CHANGELOG.md. Summarise what you changed in plain words.
```

**How you'll know it's working:** each new `/produce` needs **fewer notes** than the last.

### Step 6 — Ideas to add next (pick any)

Each is one prompt away:

- **Compare colour looks:** *"Use HyperFrames' grade-compare to show my house look next to two variations on a frame from this video, so I can choose."* Handy when your lighting or outfit changes. Keep one house look by default.
- **Graphics on the beat:** *"Find the beats in my background music and line up graphic animations with them, where it doesn't fight my voice."*
- **Smarter screen recordings:** *"In split shots, follow my mouse with smooth zooms (max 1.5×) instead of a fixed crop."*
- **Highlight boxes:** *"When I point at something on screen, add a brand-coloured highlight box over it."*
- **A reuse library:** *"Make a library folder for recordings and graphics I can reuse in future videos, and check it before making new ones."*
- **Batch editing:** *"Let /produce take several video folders and edit them one after another, with one report at the end."*
- **Share for feedback:** *"After each edit, make a one-page summary with pictures of every shot that I can send to someone for feedback."*

---

## What you have now

- ✅ `/produce-thumbnail`: 3 on-brand thumbnail options from your own footage
- ✅ The tweak loop that turns your notes into permanent rules
- 🎬 **Final milestone:** `projects/02-<name>/build/final/02-<name>.mp4` with **every feature** (rough cut, colour grade, clean audio and music, screen recordings, motion graphics, highlighted captions, editing-app project file), plus your chosen thumbnail next to it in `build/final/`

## Course wrap-up (for the end of the video)

Show the journey: the raw recording from Lesson 1 → the rough cut → screen recordings → graphics → captions → today's finished video and thumbnail, all now made with **one command**.

Recap the big ideas:
- **One pipeline per editing style**
- **A style guide** gives it your personality
- **Examples** stop Claude guessing
- **A script** makes captions and graphics land on the right words
- **Every note you give** makes the next video better

## Landscape note

The thumbnail template already works at 1280×720. In a horizontal pipeline, make that the main size, with your face on one side and the text on the other.
