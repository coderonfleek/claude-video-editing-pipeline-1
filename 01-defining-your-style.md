# Lesson 1 — Defining Your Style

## Video goal

By the end of this lesson you'll have:
- every basic tool installed
- a project folder for your pipeline
- a **style guide**: a document describing how *your* videos look and sound
- an **examples** folder: videos and pictures you want to look like
- your first **video folder** with a recording, screen recordings, audio and a script

…and your first video out of the pipeline: your raw recording **fitted to the Shorts frame** (whether you filmed horizontally or vertically) with your face framed properly and the good microphone audio lined up with your lips. Nothing is cut yet. That's Lesson 2.

**Why this lesson matters most:** the pipeline can only be as good as what you give it here. A clear style guide and good examples are the difference between "looks like a generic AI edit" and "looks like *your* channel".

⏱ About 1.5 hours. Claude works for about 45 minutes of that: the first pipeline step alone takes 15–20 minutes to build and run on a 7-minute 4K recording. The rest is you answering style questions.

> **Usage note:** this lesson is the heaviest one for Claude usage, because of the style-guide interview and building the first step. On a Pro plan you may hit your usage limit partway through. If you do, just continue in the same chat when it resets.

---

## Before you start

### 1. Install the Claude desktop app

If you haven't yet: download it from **https://claude.ai/download**, install it and sign in. See the course overview for a quick tour.

### 2. Windows only: install Git

Claude Code on Windows uses a program called Git behind the scenes to run commands, so it has to be installed. You won't need to use it yourself.
1. Go to **https://git-scm.com/download/win** and download the installer.
2. Run it and click **Next** through every screen. The default options are fine.
3. Restart the Claude app.

### 3. Create your pipeline folder

1. In Finder (Mac) or File Explorer (Windows), go to your **Documents** folder.
2. Create a new folder called **`my-edit-pipeline`**. Use dashes, not spaces: some video tools have trouble with spaces in folder names.
3. In the Claude app, open the **Code** tab and choose this folder.

---

## Steps

### Step 1 — Let Claude install the basic tools

**What this does:** installs the "engine room" of your pipeline: Python (the language Claude writes the pipeline in) and FFmpeg (the video engine).

**Send this to Claude:**

```text
I'm a beginner and I'm setting up my computer for a video editing pipeline that you'll build
with me. Please check what's already installed and install whatever is missing:
- Python 3.12
- FFmpeg (it needs the lut3d, loudnorm and sidechaincompress filters; the standard version has them)
Use Homebrew on Mac or winget on Windows. On a Mac, first check whether Homebrew is installed.
If it isn't, its installer needs my Mac password, so give me the exact line to paste into
Terminal and walk me through it step by step, then continue once I say it's done.
If a tool is already installed and works, leave it as it is. Never replace, unlink or upgrade something I already have without asking me first.
Explain each step in one simple sentence before you do it, and tell me if I need to click
anything or type a password.
When you're done, check each one works and tell me in plain words.
```

**What you should see:** Claude explains each install, asks permission to run it (click **Allow**), and finishes with something like *"Both are installed and working."*

**If Claude asks you to install Homebrew (Mac only):** Homebrew is an "app store" Claude uses to install tools. It needs your password, so you run it yourself:
1. Open **Terminal** (`Cmd + Space`, type *Terminal*, press Enter).
2. Paste the line Claude gave you and press Enter.
3. Type your Mac password when asked. **You won't see it as you type. That's normal.** Press Enter.
4. Press Enter again when it asks to continue. It takes a few minutes.
5. At the end it prints **"Next steps"** with two or three lines. **Copy those lines, paste them into Terminal and press Enter.** This is easy to miss.
6. Go back to Claude and say *"Done."* Claude checks it worked and carries on.

**Check it worked:** ask Claude: *"Is everything installed correctly?"* It should confirm both.

**If it's not right:**
- **Windows** sometimes shows a pop-up asking *"Do you want to allow this app to make changes?"* Click **Yes**.
- **Windows:** if Claude says a tool "isn't found" right after installing, close the Claude app completely, reopen it, and tell Claude: *"I restarted the app. Please check again."*

### Step 2 — Set up the project

**What this does:** Claude creates the folders, a notes file for itself (`CLAUDE.md`) and a change diary (`CHANGELOG.md`). Think of it as setting up a tidy studio before you start.

**Send this to Claude:**

```text
This folder will become a reusable video editing pipeline for ONE editing style:
vertical talking-head Shorts (1080x1920) with screen recordings as b-roll.
Every future video will be edited by it, so build it like a product, not a one-off edit.
The pipeline is a real Python program in pipeline/: one module per step, run from one command,
and every step can be re-run on its own. CLAUDE.md only explains how to run and maintain it;
the editing itself must live in the code and the style guide, not in instructions to you.

Please set up:
- a private Python environment for the pipeline inside this folder
- folders: style/ (with fonts, icons, logo, sfx, music and grades inside), examples/, pipeline/,
  projects/
- CLAUDE.md: explain what this pipeline is, the folder layout, that every video lives in
  projects/<name>/ with main-roll/, b-roll/, audio/ and plan.md, that every step saves its
  results in projects/<name>/build/ and can be re-run on its own, that the finished video and
  anything delivered (timeline, thumbnail) ALWAYS go in projects/<name>/build/final/ (not a
  numbered folder, so adding steps never moves it), and that ALL visual and
  audio decisions come from style/style-guide.md (never hard-coded)
- CHANGELOG.md, where you'll log every change we make and why
Text, motion graphics and captions will be made with HyperFrames in later lessons, so note that
in CLAUDE.md. Don't plan to draw text with FFmpeg or Python.
Don't write any editing code yet. When you're done, describe what you made in simple terms.
```

**What you should see:** new folders appear in `my-edit-pipeline`, and Claude gives you a short summary.

> **Optional, for technical users:** if you use Git, add this line to the prompt: *"Also set up git, ignoring big video/audio files and anything the pipeline generates, but keeping style/ (including music and sound effects), and commit after each lesson."* Everyone else can skip this. If you ever want to undo a change, just ask Claude, and CHANGELOG.md records what changed and why.

**Check it worked:** open the folder in Finder or File Explorer. You should see `style`, `examples`, `pipeline` and `projects`, plus the `CLAUDE.md` and `CHANGELOG.md` files.

### Step 3 — Add your examples

**What this does:** gives Claude visual references, the fastest way to get the look you want. Without them, Claude guesses.

**Do this:** put files in the `examples` folder.

**Required:** 2–3 **finished videos** in the style you want (yours or someone else's), e.g. `finished-short-1.mp4`. These alone are enough: Claude pulls frames and listens to the audio to learn your pacing, layout, colours, captions and sounds.

**Optional extras** (each one makes a specific part more accurate):

| File | What to put in it | Why |
|------|-------------------|-----|
| `grade-reference.png` | A screenshot with **the exact colours you want**, if they're different from your finished videos | The colour look to copy. Without it, Claude uses frames of you from the finished videos. |
| `captions.png` | A screenshot of captions you like | Caption style |
| `mg-1.png`, `mg-2.png` | Screenshots of animated graphics you like | Motion graphics style |
| `thumbnail-1.png`, `thumbnail-2.png` | Thumbnails in the style you want | Thumbnail style |

> **Using the sample pack?** Copy its finished videos into `examples/`, and its style guide PDF into `style/`.
> **How to screenshot a video:** pause it, then press `Cmd + Shift + 4` (Mac) or `Win + Shift + S` (Windows) and drag over the video.

**Send this to Claude:**

```text
Look at everything in the examples/ folder. For videos, take still frames so you can see them,
AND analyse the audio: how loud the voice is, and whether there's background music or sound
effects (and when they play). For each example, write down what we can learn from it for my
style: layout, pacing, colours, fonts, captions, animation style, sounds, thumbnail design.
Still frames can't show movement, so for anything that moves (how captions highlight, how
graphics animate), describe what you think happens and mark it "please confirm".
Save your notes in examples/NOTES.md and give me a short, plain-English summary.
Don't design anything yet.
```

**What you should see:** a summary like *"Both videos follow the same template: open on your face, then a title card, then face, cream graphic cards and split-screen screen recordings. Captions are 1–3 words, white on a black box, with one word in yellow (please confirm). Voice is at YouTube level; there's a soft whoosh when a card appears."*

**Check it worked:** read the summary. Does it describe what you like about the examples? Check every "please confirm" item against the actual video.

**If it's not right:** correct it now. Everything else is built from these notes. A common one:
- *"The yellow word isn't a key word. The highlight follows the word I'm saying, moving word by word like karaoke."*
- *"No, the captions sit low on the screen, not in the middle."*

### Step 4 — Create your style guide

**What this does:** Claude interviews you and writes your **style guide**, the rulebook the pipeline follows on every video. It's the most important file in the course.

**Do this first (if you have them):**
- Your **brand guide** (PDF, Notion page, anything) → put it in `style/`
- **Font files** (`.ttf` or `.otf`) → `style/fonts/`. If your fonts are free Google Fonts, Claude can download them for you. Just say yes when it offers.
- **Logo** → `style/logo/`
- **Music** you own or have a licence for → `style/music/` (optional)
- **Sound effects:** nothing to find. HyperFrames (Lesson 4) comes with its own library of sound effects (whoosh, pop, click and more). Just describe the sounds you want in the style guide. If you have your own signature sounds, you can put them in `style/sfx/`.

**Send this to Claude:**

```text
Help me write style/style-guide.md: the rulebook for every visual and audio decision the
pipeline makes. Use examples/NOTES.md and anything in style/.
Interview me to fill the gaps: ask 2–3 simple questions at a time, give me suggestions
or options to choose from, and explain any video terms you use. I'm not a professional editor.

The guide needs these sections, each with exact values (sizes, colour codes, seconds,
loudness), not vague words like "clean" or "modern":
1. Format: video size (1080x1920 now; note what would change for horizontal 1920x1080),
   frame rate, and safe zones (edges where text must not go)
2. Pacing: longest pause allowed, how to handle retakes, how long the hook is, longest stretch
   of just my face
3. Framing and zooms: where my face sits, when to zoom in, how much, how fast
4. Colour: the look we want (reference: examples/grade-reference.png if it exists, otherwise
   frames of my face from the finished example videos)
5. Fonts: which font, weight and size for headings, body text, code and captions
6. Colours: named brand colours with their colour codes and what each is used for
7. Screen recording layout: where screen recordings go and how big
8. Motion graphics: tone, one idea per graphic, word limits, how things appear and disappear,
   sound effects
9. Title card and end card: what they show and how long they stay
10. Captions: words per line, font, background box, highlight colour for the current word,
    position, what to do when a graphic is on screen
11. Audio: voice loudness, music volume, which sound effects go where
12. Thumbnail: size, layout, text rules
13. Never do: things that would make it look generic or off-brand
```

**What you should see:** Claude writes a first draft straight away from your examples and brand guide, marking anything undecided as **OPEN**. Then it asks you a few rounds of questions, each with options and a suggestion. Answer briefly, e.g. *"Q1: A. Q2: your suggestion. Q3: 0.5 seconds."*

It starts with places where your examples and your brand guide **disagree** (e.g. caption colours). Your published videos usually win, because they show what you actually do now.

> **Short on time?** After the first round, you can say: *"For the rest, go with your suggestions wherever my brand guide and examples agree. Only ask me about real conflicts. Then tell me which sections are complete and which are still OPEN."*

Some items stay OPEN until later lessons, e.g. the exact colour grade (made in Lesson 2 from your raw footage). That's fine. Sound effects don't need files: write down *which* sounds play *when* (e.g. "soft whoosh when a card appears, quiet pop as each item builds in"), and Lesson 4 picks matching ones from HyperFrames' sound library.

**Check it worked:**
- Open `style/style-guide.md` (double-click it, or ask Claude to show it to you).
- Ask Claude: *"Is any section still vague, using words instead of exact values?"* It should say no, or fix the ones it finds.
- Ask: *"What would change in the style guide for a horizontal video?"* You should get a short list (size, safe zones, layout, caption position). If it's long, say: *"Please move all the vertical-only settings into the Format and layout sections."*

> **You can change the style guide any time.** It's yours. Every future video follows the latest version.

### Step 5 — Create your first video folder

**What this does:** sets up the folder for the video we'll edit throughout the course.

**Do this:** inside `projects`, create a folder called `01-sample` with this inside (or copy it from the sample pack):

```
01-sample/
├── main-roll/   → your camera recording (all your takes, unedited)
├── b-roll/      → your screen recordings, numbered in order: 01-open-settings.mov, 02-…
├── audio/       → your microphone recording (optional: camera audio is used if there isn't one)
│                  and background music (optional)
└── plan.md      → your script and plan (optional, see below)
```

**Give the pipeline a plan template.** This saves a blank plan file in your pipeline, so every video uses the same format.

**Send this to Claude:**

```text
Save this as projects/_plan-template.md. It's the format of plan.md in every video folder,
and every part is optional. Note it in CLAUDE.md, and read plan.md files in this format from now on.

# Aim
One or two sentences: who this video is for and what they'll learn.

# Words to spell right
Names, products and special terms in this video (e.g. Claude Code, CLAUDE.md).

# Sections
- Hook
- Problem
- Demo
- Takeaway
- Call to action

# Script
Each sentence or short paragraph on its own line, in the order I say them.
Retakes in the recording are fine; the pipeline finds the best take of each line.

# B-rolls
- 01-open-settings.mov → "open your settings"

# Motion graphic ideas
- "There are two ways to do this" → side-by-side comparison
```

**Then, for each new video:** copy `projects/_plan-template.md` into the video folder, rename it `plan.md`, and fill in what you have. Open it with TextEdit (Mac) or Notepad (Windows). Or ask Claude: *"Make a plan.md for 01-sample from the template. Here's my script: …"*

> **No script or plan at all?** That's fine. Still send the template prompt above (so future videos can use it), but skip `plan.md` for this video and tell Claude *"I don't have a script or plan for this one."* The pipeline works from what you said in the recording. A script or a list of sections makes captions and graphics better, but it isn't required.

> **Files not in these folders?** (For example, the sample pack has the camera and mic files loose, plus a `b-rolls` folder.) Don't worry about it. Claude spots this in the check below and offers to move them for you. Say yes.

**Send this to Claude:**

```text
Check projects/01-sample against what a video folder should contain (see CLAUDE.md).
Look at every video and audio file and tell me, in plain words: how long each is, what size
it is, and anything that looks wrong. For example: a screen recording that isn't mentioned in
plan.md, a b-roll in plan.md with no file, or a recording that's missing audio.
```

**What you should see:** a table of your files (length, size, what each one is) and a list of anything to watch out for. Claude often spots useful things here, for example:
- *"Only 2 of the 7 minutes is you talking. The pauses will be cut."*
- *"Two screen recordings show the whole window, so the text is small. Next time, make the editor font bigger before recording."*
- *"The mic recording is quiet. That's fine, it'll be turned up in Lesson 2."*

**If it's not right:** fix what Claude points out (or ask it to: *"Yes, please move the files into the right folders"*), then ask it to check again.

### Step 6 — Your first pipeline step: fit it to the Shorts frame

**What this does:** Claude builds the first step of the pipeline, called **ingest** ("bring the footage in"). It:
1. lines up your microphone audio with the camera video (so your lips match the sound)
2. finds your face in every part of the video
3. crops the video to the Shorts frame and keeps your face where your style guide says it should be. This works whether you filmed horizontally or vertically.

**Send this to Claude:**

```text
Build the first pipeline step, "ingest", and run it on 01-sample. It should:
1. Line up the microphone recording in audio/ with the camera's sound and tell me how far
   apart they were. If there's no mic file, use the camera audio.
2. Find my face throughout the main roll (use MediaPipe face detection) and smooth the
   movement so the framing doesn't wobble.
3. Crop to the video size in my style guide and keep my face where the style guide says.
   Read those settings from the style guide (stored in a settings file the pipeline loads),
   so a horizontal version is just a settings change later.
4. Save a preview video of the full, uncut recording at build/1-ingest/preview.mp4.
Set up a single way to run steps that later lessons will extend. Log this in CHANGELOG.md
and keep CLAUDE.md up to date.
When it's done, show me a few still frames from the preview so I can check the framing.
```

**What you should see:** Claude works for **15–20 minutes**. This is the longest step so far, because it reads your whole recording frame by frame. It may ask to install a couple of Python add-ons; click **Allow**. Then it tells you something like *"Your mic started recording 6 seconds before the camera. I've lined them up. I found your face in 99.9% of frames."* and gives you a **framing check picture**: 8 moments from the video with lines showing where your eyes should sit.

**Check it worked:**
1. **Open the framing check picture** (`build/1-ingest/framing-check.jpg`). Your eyes should sit on the horizontal line, and your face should be centred in every frame.
2. **Open the video:** `projects/01-sample/build/1-ingest/preview.mp4`. Double-click it to play it in QuickTime or your video player. It's tall like a phone screen and plays the whole recording, uncut.
3. **Lip sync:** watch your mouth on words with "p" or "b" sounds (or a clap, if you clapped at the start). The sound should land exactly with your lips.
4. **Framing:** your face stays well framed and doesn't jump around.

**If it's not right:**
- *"The sound is slightly behind my lips."* Claude re-checks the sync.
- *"The framing wobbles when I move."* Claude smooths it more.
- *"My head is cut off at the top."* Claude adjusts the face position (and updates the style guide).

---

## What you have now

- ✅ All basic tools installed
- ✅ A project folder with your **style guide** and **examples**
- ✅ Your first video folder, `01-sample`
- 🎬 **Milestone video:** `build/1-ingest/preview.mp4`, your raw recording in the Shorts frame, well framed, with the mic audio in sync

## Landscape note

For horizontal videos, only the video size and face position in the style guide change. The face-finding works the same way.

## Common problems

| What you see | What to tell Claude |
|---|---|
| "command not found" after an install | *"I got 'command not found'. Can you check the install and fix it?"* (On Windows, restart the app first.) |
| The audio drifts out of sync over time | *"The sync is fine at the start but drifts later."* (Usually a camera setting; Claude handles it.) |
| An install fails with lots of red text | Copy the message and paste it to Claude with: *"This happened. What does it mean, and can you fix it?"* |
