# Course Overview — Build Your Own Video Editing Pipeline with Claude Code

## Who this course is for

**Anyone who makes videos and wants Claude to do the editing**, whether you've written code before or not.

You won't write any code. You'll **copy prompts into Claude**, look at what it makes, and tell it what to change in plain words, the same way you'd give notes to a human editor. Claude writes and runs all the code.

If you *are* technical, everything still applies. You'll just recognise more of what Claude is doing behind the scenes.

## What we're building

An editing **pipeline**: a set of steps Claude runs the same way every time.

You record a video, drop the files into a folder, and type one command: `/produce`. The pipeline then:

1. Cuts out mistakes, retakes and long pauses, and adds zooms
2. Colour-corrects your footage to match a look you choose
3. Cleans up your voice and adds background music
4. Places your screen recordings at the right moments
5. Adds animated graphics (titles, diagrams, an end screen) in your brand style
6. Adds captions where the word you're saying lights up
7. Gives you a project file you can open in your own editing app (DaVinci Resolve, Premiere Pro, Final Cut Pro or CapCut) to make final touches
8. Makes a thumbnail

You build it **once**, and then it edits every future video. Under the hood it's a real program (Claude writes it in Python), not a list of instructions Claude follows each time. That's why it's fast, repeatable and gives the same result every time.

**Each lesson adds one feature and ends with a finished video.** By the last lesson, your video has everything.

## How every lesson works

Each lesson has the same parts:

- **Video goal**: what you'll have at the end
- **Before you start**: anything to download or install, with step-by-step instructions
- **Steps**, and each step has:
  - **What this does**: in plain words
  - **Send this to Claude**: a prompt to copy and paste, or **Do this**: something you do yourself
  - **What you should see**
  - **Check it worked**: how to tell it went right
  - **If it's not right**: what to say to Claude
- **What you have now**: the finished video for the lesson

> **The golden rule:** if anything goes wrong (an error, a weird result, something you don't understand), **tell Claude what you see in your own words**. "It says 'command not found'" or "the captions are covering my face" is all Claude needs. You never have to figure out the fix yourself.

## The big ideas (why the pipeline works)

- **One pipeline per editing style.** Short vertical videos and long tutorials are edited differently, so they get separate pipelines. This course builds one for **vertical Shorts** (TikTok / Reels / YouTube Shorts). Each lesson has a *Landscape note* on what changes for horizontal videos.
- **A style guide gives it your personality.** Without one, Claude makes "safe" choices and your video looks like everyone else's.
- **Examples beat descriptions.** Showing Claude a frame with the colours you want works much better than describing them. Examples also stop Claude guessing.
- **A script helps a lot.** If Claude knows what you meant to say, it can spell captions correctly and time graphics to the right words. A list of sections still helps if you don't use a script.

## Before Lesson 1: get comfortable with the tools

### Claude desktop app (recommended)

We'll use **Claude Code inside the Claude desktop app**. It's the easiest way: no terminal needed for most of the course.

1. Download the Claude app from **https://claude.ai/download** (Mac or Windows) and install it like any other app.
2. Sign in. You need a paid Claude plan (Pro, Max, Team or Enterprise).
3. Open the **Code** tab. This is Claude Code: Claude can work with files on your computer and run programs for you.
4. When it asks for a folder, choose the folder you're working in (we create it in Lesson 1).

When Claude wants to do something on your computer (install a program, run a step), it **asks permission**. Read the short description and click **Allow**. If you're unsure what something is, ask: *"What does this do, in simple terms?"*

> **Prefer the terminal?** Claude Code also runs in a terminal window. Every prompt in this course works the same there.

### Terminal (only for one or two installs)

Occasionally you'll paste a single line into a **Terminal** (Mac) or **PowerShell** (Windows) window. That's a text window for typing commands to your computer.

- **Open it on Mac:** press `Cmd + Space`, type **Terminal**, press Enter.
- **Open it on Windows:** click Start, type **PowerShell**, press Enter.
- **Paste a command:** `Cmd + V` (Mac) or right-click (Windows), then press **Enter**.
- **Passwords on Mac:** when it asks for your password, type your Mac login password. **Nothing appears as you type.** That's normal. Press Enter.

## Words you'll hear (plain-English glossary)

| Word | What it means |
|------|---------------|
| **Pipeline** | The set of editing steps Claude runs in order, the same way every time |
| **Stage** | One step of the pipeline (e.g. "the captions stage") |
| **Main roll / A-roll** | The footage of you talking to the camera |
| **B-roll** | Extra footage shown over or beside the main roll. Here, your screen recordings |
| **Rough cut** | The first edit: mistakes and pauses removed |
| **Retake** | Saying a line again after a mistake |
| **Colour grade / LUT** | The colour "look" of the video. A LUT is a small file that stores that look so any app can apply it |
| **Motion graphics (MGs)** | Animated text, shapes and diagrams |
| **HyperFrames** | A free tool that turns web-page designs into video. Claude uses it to make the motion graphics |
| **Transcription** | Turning speech into text, with the time each word was said |
| **Render** | Turning the edit into an actual video file |
| **Timeline / project file** | A file your editing app opens to show the edit as clips on tracks |
| **Skill** | A saved set of instructions you can run with a slash command, like `/produce` |
| **Safe zone** | Edges of the screen where text shouldn't go, because the app's buttons cover them (TikTok, Shorts) |
| **Overrides** | Your manual corrections, saved so Claude respects them every time it re-runs |

## Lessons

| # | Lesson | What it adds | The video you'll have at the end |
|---|--------|--------------|----------------------------------|
| 1 | [Defining Your Style](01-defining-your-style.md) | Installs, project folder, style guide, examples, first video folder | Your raw recording, turned vertical, with good audio |
| 2 | [Rough Cuts and Audio](02-rough-cuts-and-audio.md) | Cuts mistakes, zooms, colour grade, clean audio + music | A clean, colour-graded rough cut |
| 3 | [Adding B-rolls](03-adding-b-rolls.md) | Screen recordings placed at the right moments | + screen recordings |
| 4 | [Adding Motion Graphics](04-adding-motion-graphics.md) | Title card, animated graphics, end screen | + motion graphics |
| 5 | [Adding Captions](05-adding-captions.md) | Captions with the current word highlighted | + captions |
| 6 | [Generating a Timeline](06-generating-a-timeline.md) | A project file for your editing app | Final video + editable project |
| 7 | [One Skill to Run It All](07-one-skill-to-run-the-pipeline.md) | The `/produce` command | A **brand-new** video, edited with one command |
| 8 | [Thumbnail, Tweaks and Improvements](08-thumbnail-tweaks-and-improvements.md) | `/produce-thumbnail`, improving the pipeline over time | Final video + thumbnail |

## Your folder at the end of the course

You don't need to understand every file. Claude creates and looks after almost all of them. The folders **you** put things in are marked ✋.

```
my-edit-pipeline/
├── CLAUDE.md          Claude's notes on how your pipeline works
├── CHANGELOG.md       A diary of every change and why
├── style/           ✋ Your style guide, fonts, logo, sounds, music
├── examples/        ✋ Videos, frames and screenshots you want to look like
├── kit/               Your brand templates for graphics (Claude makes these)
├── pipeline/          The editing program: Python code Claude writes, one part per step (you never need to open it)
└── projects/
    └── 01-sample/   ✋ One folder per video
        ├── main-roll/ ✋ Your camera recording
        ├── b-roll/    ✋ Your screen recordings
        ├── audio/     ✋ Your microphone recording (and music, if any)
        ├── plan.md    ✋ Your script and plan
        └── build/       Everything the pipeline makes. The final video is in build/final/
```

> **File names may differ slightly.** Claude decides the exact folder names inside `build/`, so your rough-cut preview might be in `build/4-cut/` rather than `build/3-cut/`. The final video always ends up in `build/final/`. If you can't find something, ask Claude: *"Where's the preview video?"*

## Sample footage

The course comes with a **sample pack**:
- a video folder with a camera recording, a separate mic recording and four screen recordings. There's deliberately **no script**, so you'll see the pipeline work without one.
- two finished example videos
- a brand style guide (PDF)

Follow along with it first. Once it works, try your own footage. Don't worry about matching the folder layout exactly: Claude checks the folder and offers to organise it for you.

## Tools that get installed along the way

You don't need to install anything ahead of time. Each lesson tells you what to install when you need it, and Claude does most of the installing.

| Tool | What it's for | Lesson |
|------|---------------|--------|
| Claude desktop app | Where you talk to Claude | Before Lesson 1 |
| Homebrew (Mac) / winget (Windows) | An "app store" for tools Claude installs | 1 |
| Git (Windows only) | Needed by Claude Code itself on Windows. Mac users don't need it. (Technical users can optionally use it to save versions of the pipeline.) | 1 |
| Python | The language Claude writes the pipeline in | 1 |
| FFmpeg | The video "engine" that cuts, colours and exports | 1 |
| Node.js + HyperFrames | Makes the motion graphics | 4 |
| Vibe | A free transcription app. Turns your speech into text with word timings, for cutting (Lesson 2) and captions (Lesson 5) | 2 |
| Your editing app | Opening the finished project (optional) | 6 |
