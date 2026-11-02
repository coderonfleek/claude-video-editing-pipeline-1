# Lesson 6 — Generating a Timeline for Your Editor

## Video goal

Get a **project file** you can open in your own editing app, showing the whole edit as separate clips on tracks: your face, the screen recordings, the graphics, the captions, and your voice, music and sound effects on their own audio tracks.

**Why this matters:** you get Claude's speed *and* full control. If you want to nudge a cut, swap a song or change one caption, open the project and do it by hand, just like any other edit.

🎬 At the end: the final video **plus** a project file that rebuilds it in your editing app.

⏱ About 30–45 minutes of Claude working (the project file export takes about 10 minutes), plus your time opening it in your app.

> **Don't use an editing app?** You can skip this lesson. The pipeline already makes a finished video. Come back if you ever want to fine-tune by hand.

---

## Before you start

- Lesson 5 is done: the full video with captions plays correctly.
- Install the editing app you want to use (one is enough):

| App | Cost | Mac | Windows | Download |
|-----|------|-----|---------|----------|
| **DaVinci Resolve** | Free (paid Studio version optional) | ✅ | ✅ | https://www.blackmagicdesign.com/products/davinciresolve |
| **Premiere Pro** | Subscription | ✅ | ✅ | Adobe Creative Cloud |
| **Final Cut Pro** | One-off purchase | ✅ | ❌ | Mac App Store |
| **CapCut** (desktop) | Free / Pro | ✅ | ✅ | https://www.capcut.com |

> **Not sure which?** DaVinci Resolve is free, works on Mac and Windows, and opens our project files very well. It's the recommended choice for this course.

### What file each app needs

You don't need to remember this. Claude makes the right file. It's just good to know:

| App | File type | How you open it |
|-----|-----------|-----------------|
| DaVinci Resolve | `.fcpxml` | **File → Import → Timeline…** and pick the file |
| Final Cut Pro | `.fcpxml` | **File → Import → XML…** |
| Premiere Pro | `.xml` (an older Final Cut format Premiere understands) | **File → Import…** and pick the file |
| CapCut | No project-file import | Claude gives you the layers as separate files plus a "where to put each one" sheet (more below) |

> **About CapCut:** CapCut can't open project files from other apps. Instead, Claude exports each layer (your graded face video, screen recordings, graphics, captions, audio) as separate files, plus a simple sheet listing which track each goes on and at what time. You drag them in. (Claude *can* attempt a real CapCut project file, but CapCut changes its format often, so treat that as experimental.)

---

## Steps

### Step 1 — Collect everything the editing app needs

**What this does:** Claude gathers every piece of the edit into one list: every clip, where it starts and ends, how it's zoomed, which track it's on. Then it double-checks the list is complete.

**Send this to Claude:**

```text
Prepare the edit for exporting to an editing app. Gather every piece into one list in
build/final/:
- Track V1, my face: each kept piece of the ORIGINAL camera file (so I can re-trim it), with
  its cropping and zooms as movement keyframes, plus my house colour look
- Track V2, screen recordings: original file, which part, speed, position in the split layout
- Track V3, motion graphics, title and end card: their rendered files (see-through where needed)
- Track V4, captions: the caption overlay, plus the .srt file
- Audio tracks: A1 my voice, A2 music, A3 sound effects
Then check: nothing overlaps on a track, every file exists, and the total length matches the
final video exactly. Tell me the result in plain words.
```

**What you should see:** a summary per track, e.g. *"V1 your face: 21 clips with 265 movement keyframes. V2 screen recordings: 6 clips. V3 graphics: 5. V4 captions. A1 voice, A2 music (empty), A3 sound effects: 13"*, then *"2,549 frames (1:24.97), the same as the finished video."*

Claude may mention small things, like *"your camera records at 30.003 fps, so an app may place a face clip a frame off"*. That's normal and nothing to fix.

### Step 2 — Make the project file for your app

**Send this to Claude** (pick your app):

**DaVinci Resolve or Final Cut Pro:**

```text
Create a .fcpxml project file for DaVinci Resolve (and Final Cut Pro) from that list, saved in
build/final/. Use my original footage for my face and screen recordings so I can re-trim them,
with the cropping, zooms and split layout applied. Put the graphics and captions on their own
tracks, and the audio on separate tracks. Match my style guide's video size and frame rate.
Copy my house colour look (.cube file) next to it, and give me simple step-by-step instructions
for opening the project and applying the colour look in my app.
```

**Premiere Pro:**

```text
Create a Premiere Pro project file (.xml, the Final Cut 7 XML format Premiere imports) from that list,
saved in build/final/, with the same tracks, cropping, zooms and layout. Match my video size
and frame rate. Copy my house colour look (.cube) next to it and give me simple steps to open the
project and apply the look with Lumetri Color.
```

**CapCut:**

```text
Export each layer as a separate file in build/final/layers/: my face video (colour graded,
cropped and zoomed), each screen recording already positioned for the split layout, the
graphics and captions as see-through videos, and my voice, music and sound effects as separate
audio files. Then write a simple sheet (PLACEMENT.md) listing each file, which track it goes on,
and its start time, with step-by-step instructions for putting it together in CapCut.
```

**What you should see:** the project file in `build/final/`, a copy of your colour look (`house.cube`), and an instructions file written for your app (e.g. `01-sample-open-in-editor.md`). Claude also lists what it checked, and what might still need a small fix once you open it (zoom units, a sideways face, a black caption background). Each comes with a fix in the instructions.

> **Claude says your editing app "isn't installed"?** It may not be able to see your Applications folder. That's harmless: the file is made the same way. Just open it in your app.

> **Don't move the project folder** after exporting. The project file points to your footage where it is now.

### Step 3 — Open it in your editing app and compare

**Do this:** follow Claude's instructions to open the project in your app. If it asks where the media is, point it at your `projects/01-sample/` folder.

**Check it worked:** the "does it match?" test.
1. **Tracks:** you see separate tracks for your face, screen recordings, graphics, captions and audio.
2. **Compare 5 moments.** Pick a face shot, a split shot, a graphic, the title card and the end card. Look at the same moments in the app and in `build/final/01-sample.mp4`. They should look the same: same framing, zoom, layout and timing.
3. **Colour:** apply the house look (`.cube` file) to your face clips as Claude explained. The colour should match the finished video.
4. **Audio:** voice, music and sound effects are on separate tracks and sound the same as the finished video. If you hear sound effects twice, mute the graphics track's own audio (the effects are also on their own track).

**If it's not right:** tell Claude exactly what you see, and **where** (the time shown in your app):
- *"In Resolve at 00:00:12, my face is zoomed in way too much."*
- *"The screen recording is in the middle of the screen, not at the top."*
- *"The graphics are on the timeline but show as black boxes."*

Every app handles zoom and position slightly differently. Claude adjusts the file for yours.

### Step 4 — Make it automatic

**Send this to Claude:**

```text
Add the project file export to the full build, so every build makes the final video AND the
project file for my app. After exporting, re-check the project file is complete and matches the
video's length. Add the steps for opening it in my app to CLAUDE.md, and log the change in CHANGELOG.md.
```

**What you should see:** after a full build (about 10 minutes), Claude lists everything it made: the video, the project file, the instructions and the subtitles. From now on, the build stops with a plain message if the project file doesn't match the video, instead of silently giving you a broken file.

**Check it worked:** ask Claude to run the full build again. `build/final/` should have both the video and the project file.

---

## What you have now

- ✅ A project file (or layered export) for your editing app, checked against the final video
- ✅ Your house colour look ready to apply in the app
- 🎬 **Milestone:** `build/final/01-sample.mp4` **plus** a project you can open and fine-tune in your editing app

## Landscape note

Nothing changes. The export reads the video size from your style guide.

## Windows note

Final Cut Pro is Mac-only. On Windows, use DaVinci Resolve (recommended), Premiere Pro or CapCut.
