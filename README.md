# Claude Video Editing Automation

A short course on building your own **video editing pipeline with Claude Code**. You record a video, drop the files into a folder and type `/produce`, and the pipeline does the edit:

- cuts out mistakes, retakes and long pauses, and adds zooms
- colour-grades your footage to match a look you choose
- cleans up your voice and adds background music
- places your screen recordings at the right moments
- adds on-brand motion graphics made with HyperFrames
- adds captions where the word you're saying lights up
- exports a project file for DaVinci Resolve, Final Cut Pro, Premiere Pro or CapCut
- makes a thumbnail

It's for **technical and non-technical creators alike**. You don't write any code: you copy prompts into Claude, check what it makes, and give notes in plain words. Claude writes the pipeline, a real Python program that edits every future video the same way.

The course targets vertical Shorts (1080×1920). Each lesson notes what changes for landscape videos.

## Lessons

Each lesson adds one feature and ends with a finished video.

| # | Lesson | What it adds |
|---|--------|--------------|
| 0 | [Course overview](00-course-overview.md) | How the course works, setup tips, glossary |
| 1 | [Defining Your Style](01-defining-your-style.md) | Installs, project folder, style guide, examples |
| 2 | [Rough Cuts and Audio](02-rough-cuts-and-audio.md) | Script-matched rough cut, zooms, colour grade, clean audio |
| 3 | [Adding B-rolls](03-adding-b-rolls.md) | Screen recordings placed where you talk about them |
| 4 | [Adding Motion Graphics](04-adding-motion-graphics.md) | Brand kit, title card, graphics, end card |
| 5 | [Adding Captions](05-adding-captions.md) | Captions with the current word highlighted |
| 6 | [Generating a Timeline](06-generating-a-timeline.md) | A project file for your editing app |
| 7 | [One Skill to Run the Pipeline](07-one-skill-to-run-the-pipeline.md) | The `/produce` command |
| 8 | [Thumbnail, Tweaks and Improvements](08-thumbnail-tweaks-and-improvements.md) | `/produce-thumbnail`, and improving the pipeline over time |

## What you need

- A Mac or Windows computer
- The [Claude desktop app](https://claude.ai/download) with a paid Claude plan
- Your own footage, or the course sample pack

Everything else (Python, FFmpeg, Vibe, Node.js, HyperFrames) is installed by Claude as the lessons go. Start with the [course overview](00-course-overview.md).

## Sample pack

The sample footage, example videos and brand guide used in the lessons are distributed separately and aren't part of this repository.
