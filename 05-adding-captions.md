# Lesson 5 — Adding Captions

## Video goal

Add **captions** where the word you're saying **lights up** as you say it (karaoke-style). Captions are made from a very accurate transcription, spell-checked against your script, and placed so they **never cover** your graphics or the important part of a screen recording.

🎬 At the end: the full video with captions. Every feature is in place except the editing-app project file (Lesson 6).

⏱ About 1–1.5 hours, mostly Claude working. Making the captions takes about 20 minutes.

---

## Before you start

- Lesson 4 is done.
- **Vibe** is already set up from Lesson 2. Captions use the same transcriber and model, so there's nothing new to install.

### Check your caption style

Ask Claude:

```text
Is the Captions section of my style guide complete? It needs: font and weight, size, how many
words per caption, background (none, box or rounded), text colour, the HIGHLIGHT colour and style
for the word being spoken, position on screen, and what to do when a graphic or screen
recording is showing. Compare it with the captions in my examples and ask me about anything missing.
```

**What you should see:** Claude measures the captions in your example videos to the pixel and lists where your style guide disagrees with them, e.g. *"the guide says 64 px, your videos use about 74 px"*, *"the highlight yellow in your videos is #FDE200, slightly warmer than the guide's"*, plus anything missing (what happens to punctuation, what shows during pauses). Each comes with a ✅ suggestion. Answer with letters, e.g. *"1A, 2A, 3A…"*.

---

## Steps

### Step 1 — Get accurate words for the edited video

**What this does:** transcribes only the parts you **kept** in the edit, word by word, then fixes spelling using your script.

**Send this to Claude:**

```text
Build the "captions" step, part 1, and run it on 01-sample. Transcribe only the kept parts of the
cut with Vibe and line up each word with its time in the EDITED video.
Then fix the words:
- WITH a script: use the script's spelling and punctuation (names, product names, commands,
  capital letters) but keep the real timings. Keep genuine ad-libs as I said them. Fix obvious
  typos from my script in the pipeline's copy, never in my plan.md.
- WITHOUT a script: use what was heard, but correct names and special terms using
  style/glossary.txt (from Lesson 2) and the video's "Words to spell right" in plan.md.
Show me a list of every correction you made.
```

**What you should see:** a short table of every correction, e.g. *"0:01.49 Cloud (Code) → Claude (Code), glossary"*. With the sample pack, about 12 of 211 words get fixed, mostly "Cloud Code" → "Claude Code".

Claude is careful with ordinary words: "cloud" on its own stays "cloud", and only the full phrase "Cloud Code" becomes "Claude Code".

**Check it worked:** read the corrections. Each one should be right.

> **Try it without a script:** ask *"Run captions once without the script and show me the difference."* You'll see exactly why a script helps.

### Step 2 — Split words into captions

**What this does:** groups the words into short captions that are easy to read.

**Send this to Claude:**

```text
Captions part 2: group the words into short captions following my style guide (words per
caption). Break at natural pauses and punctuation, never split a name or command across two
captions, and don't flash a caption too quickly to read. Show me the first 15 captions.
```

**What you should see:** a table of the first 15 captions with their start time, how long each stays up, and whether it sits at the bottom or the top (captions move to the top while the title card shows). For example: `Three main files` · `give Claude Code` · `90% of` · `its power.`

Claude may also fix timing it doesn't trust, e.g. *"the transcriber put the first word of some sentences too early, so I moved 13 words to where your voice actually starts"*. That's what keeps the highlight in sync.

**Check it worked:** read the 15 captions out loud. They should break where you'd naturally pause.

**If it's not right:** *"Max 3 words per caption."* · *"Don't leave single words on their own unless they're important."*

### Step 3 — Make the captions with the moving highlight

**What this does:** creates the captions as a see-through layer that sits on top of the video, with the current word highlighted. It also makes a standard subtitle file (`.srt`) for YouTube, TikTok and editing apps.

**Send this to Claude:**

```text
Captions part 3: make the captions as a see-through overlay video using HyperFrames, with a
captions template in the kit that uses my brand fonts and colours. Follow my style guide. The
word I'm saying gets the highlight, moving word by word exactly in time with my voice.
Placement: use my style guide's normal position, but when a graphic is on screen, look at where
its content is and move the captions to free space. Never put them in the safe-zone edges, and keep them
off the important part of screen recordings.
Add the captions as the top layer in the assemble step, and also save a .srt subtitle file.
Rebuild build/final/01-sample.mp4, then show me a picture of every graphic and every split shot
with its captions visible.
```

**What you should see:** after about 20 minutes, a rebuilt video with captions and a sheet of frames (as a picture or a link to a private page), one for each graphic and screen-recording shot, showing where the caption sits and which word is yellow. Claude checks every highlight change against your voice. In the course test, all 112 landed on the right frame. It also explains any placement it chose differently from your guide, e.g. *"on the title card, the captions sit in the gap above the icons so they don't cover the watermark"*.

**Check it worked:**
1. **Highlight timing:** watch 3 different moments, slowed down if your player allows. The highlight moves *with* your voice, never ahead or behind.
2. **Placement:** in the pictures, captions never cover graphic text or the important part of a screen recording.
3. **Spelling:** read through the captions. Names and terms are correct.
4. **Phone test:** watch it full screen on your phone. That's how your viewers will see it.

### Step 4 — Fine-tune the look

**Do this:** give notes in plain words. Claude updates your style guide and re-makes only the captions. Examples:
- *"The highlight is too subtle. Put a solid coloured box behind the current word."*
- *"Captions sit too high on face shots. Move them down a bit."*
- *"Make the text slightly bigger."*
- *"Keep words coloured after they've been said."*

> **Optional:** want your name or channel watermark on face shots? Ask: *"Add a subtle [channel name] watermark on face shots and split shots, top-right, never on graphics or cards."*

---

## What you have now

- ✅ Captions powered by the same Vibe setup from Lesson 2
- ✅ Captions spell-checked against your script, with the current word highlighted, placed around graphics, plus a `.srt` file
- 🎬 **Milestone video:** `build/final/01-sample.mp4`, the full edit with captions

## Landscape note

In horizontal videos, captions are usually one wider line near the bottom. Add a horizontal version to your style guide's Captions section.

## Common problems

| What you see | What to tell Claude |
|---|---|
| The highlight gets later as the video goes on | *"The highlight is in sync at the start but drifts later. Can you check the timings match the edited video?"* |
| A word is missing from the captions | *"At 0:34 the word 'really' is missing from the captions."* |
| Captions flicker | *"Captions flicker between each other. Can you smooth the changeovers?"* |
