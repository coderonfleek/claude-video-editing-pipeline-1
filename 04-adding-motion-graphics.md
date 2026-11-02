# Lesson 4 — Adding Motion Graphics

## Video goal

Add **animated graphics** in your brand style:
- a **title card** near the start
- **concept graphics** that explain ideas (comparisons, lists, numbers), animating *as you say the words*
- an **end card** to finish

Claude makes them with **HyperFrames**, a free tool that turns web-page designs into video. You don't need to know anything about web design: Claude writes the designs, and you judge how they look.

Claude also turns your style guide into a **brand kit**: your fonts, colours and animation style packaged into templates, so every graphic matches.

🎬 At the end: the video with screen recordings *and* motion graphics.

⏱ About 1.5–2 hours, mostly Claude working. The brand kit and the final render take about 15–20 minutes each.

---

## Before you start

### 1. Install Node.js (needed by HyperFrames)

**Send this to Claude:**

```text
Check whether Node.js version 22 or newer is installed. If it is, leave it as it is. If it's
missing or older than 22, install the LTS version with Homebrew on Mac or winget on Windows (ask
me before upgrading an existing version). Then check it works and tell me the version.
```

**Check it worked:** Claude says Node.js is ready (already installed or newly installed) and the version is 22 or higher.

> **Windows:** close and reopen the Claude app afterwards, then ask Claude to check again.

### 2. Install the HyperFrames skills

**What this does:** skills are instruction packs that teach Claude how to use a tool well. We install the HyperFrames skills **for your whole computer (user scope)**, not just this project, so any project can use them.

**Send this to Claude:**

```text
Check whether the HyperFrames skills are already installed for Claude Code. If they are,
don't reinstall; just tell me which ones I have. If not, install them at user level (so every
project can use them) by running:
npx skills add heygen-com/hyperframes -g -a claude-code -s '*' -y
Then tell me which HyperFrames skills are installed.
```

**Then:** if anything was newly installed, **close the Claude app completely and reopen it** so Claude loads the new skills.

**Check it worked:** ask Claude: *"Which HyperFrames skills do you have?"* It should list several (hyperframes, hyperframes-core, hyperframes-animation and more).

### 3. Check HyperFrames is ready

**Send this to Claude:**

```text
Run the HyperFrames health check (npx hyperframes doctor) and fix anything it complains about.
Then lock the HyperFrames version for this project in the pipeline settings and note it in
CLAUDE.md, so future updates don't change how my videos look without me knowing.
```

**Check it worked:** Claude reports the health check passed.

---

## Steps

### Step 1 — Build your brand kit

**What this does:** turns your style guide's fonts, colours, spacing and animation style into reusable building blocks for every graphic.

**Send this to Claude:**

```text
Using the HyperFrames skills, create a brand kit in kit/ for my pipeline:
- every colour, font, size and spacing value from my style guide (use the font files in
  style/fonts/, never online fonts)
- small reusable animations for how things appear and disappear, as my style guide describes,
  and a way to trigger an animation exactly when I say a specific word
- sound effects: use HyperFrames' built-in sound library (the media-use skill) to pick sounds
  matching my style guide's Audio section (e.g. whoosh, pop), save the chosen files into the kit,
  and use them only in graphics and cards. If style/sfx/ has my own sounds, use those first.
  Only use the built-in library: don't download sounds from online libraries (they can need
  credits or have licence limits).
- text never goes in the safe-zone edges from my style guide
Then make a one-page preview showing my colours, fonts and a sample animation, and show me a picture of it.
```

**What you should see:** after about 20 minutes, a one-page preview picture with your colours (each with its role), your fonts in every weight, your type sizes, your motion and sound rules, and a sample card that builds up in time with your real words.

**Check it worked:** compare the preview with your style guide and the graphics in your examples folder.
- Are the **fonts** right? (If text looks like Times New Roman or Arial, the font didn't load.)
- Are the **colours** right?

**If it's not right:** *"The heading font is wrong. It should be the bold one."* · *"The yellow is too pale."* Fix it now, because every graphic inherits from the kit.

### Step 2 — Title card and end card templates

**What this does:** creates fill-in-the-blank templates for your title card and end card, so every video just swaps the text.

**Send this to Claude:**

```text
Create title card and end card templates in the kit, following my style guide's Title card and
end card section. The text should be fill-in-the-blanks (title card: a small tag, 2–3 short
headline lines with one highlighted, a subtitle; end card: a call to action). If there's a
reference in examples/, match its animation and timing.
Make a sample of each with placeholder text and show me pictures from the start, middle and end.
```

**What you should see:** a picture of each card at its start, middle and end. Claude measures your example videos frame by frame, so the cards' timing (when the highlight wipes in, when each piece appears) should match your published videos. It may also update your style guide where your examples differ from what it says, and tell you what it changed.

> **No logo or icon files yet?** Claude draws simple stand-in icons in your style and leaves the logo out. Add your own files to `style/icons/` and `style/logo/` at any time, and the cards use them.

**Check it worked:** ask Claude to show you the sample videos too and watch them. Text stays away from the edges, the animation feels like your examples, and any sound effect plays exactly when something appears (not before).

### Step 3 — The graphic template and rules

**What this does:** creates the starting template for concept graphics, and adds rules to your style guide about when to use graphics and how.

**Send this to Claude:**

```text
Create a starter template in the kit for concept motion graphics. Its animations should trigger
on the words I say, it should fit my video size, and it should explain how to use it at the top
of the file.
Then add a "Motion graphic rules" section to my style guide. Interview me with simple questions
and suggestions. Cover: which lines get a graphic (ideas, comparisons, numbers, "this vs that",
takeaways), how long a graphic stays on screen, one idea per graphic, the maximum words in a
heading, revealing one thing at a time as I say it, and when the graphic should end.
```

**What you should see:** Claude first tests the template on one of your "needs a graphic" spots, then asks numbered questions with a ✅ suggestion each. Answer with letters (e.g. *"1A, 2A, 3A…"*). It ends with rules like *"Graphics last 3–8 seconds"*, *"Headings of 6 words max"*, *"Reveal one item each time it's mentioned"*, *"Never hold a finished graphic just to fill time"*.

### Step 4 — Plan the graphics

**What this does:** Claude adds graphics to the shot plan and writes a one-line description of each **before** making them. This is the cheapest moment to change your mind.

**Send this to Claude:**

```text
Add title, graphic and end card shots to the shot plan, then re-plan 01-sample using my Shot
planning rules, Motion graphic rules, plan.md's Motion graphic ideas and the script's sections.
The title card goes at the end of the hook, idea lines get graphics, the takeaway gets a graphic,
and the end card starts just after my last word and holds. Every spot marked "needs a graphic"
gets one. Keep screen recordings where they still make sense, and never use them as filler.
Now that graphics exist, face stretches longer than my rules allow count as errors again.
For each graphic, give me a one-line description: what it shows and which words make each
part appear. Run the checker and fix any warnings.
```

**What you should see:** a list like *"Connect your tools (1:03–1:08): heading on 'connect', then 'Your database', 'Notion', 'Figma' and 'GitHub', each on its own word."* With the sample pack (no plan.md), Claude picks the idea lines itself: a title card, 3 graphics and an end card, with every "needs a graphic" spot filled.

Claude may flag a judgement call, like *"the takeaway graphic ends before your last sentence, because running it longer would break your 8-second limit"*. Answer in plain words, e.g. *"That's right: end the graphic when its content is done and keep the closing line on my face."*

**Check it worked:** read the descriptions. Do they explain the right ideas? Is the mix sensible, with graphics separated by face or screen shots and never three in a row?

**If it's not right:** *"Skip graphic 3. That line is fine on my face."* · *"For the takeaway, show three short rules instead of a paragraph."*

### Step 5 — Make the graphics and add them to the video

**Send this to Claude:**

```text
Build the "visuals" step. For each title, graphic and end card in the plan: start from the
matching kit template, design it from its description using the HyperFrames skills, time the
animations to my spoken words, run HyperFrames' quality check, and render it to video. Render
several at once if my computer can handle it.
Add the graphics to the assemble step (they fill the screen, and their sound effects play under my
voice), then rebuild build/final/01-sample.mp4.
Before telling me it's done, look at a picture of each graphic yourself and fix anything that's off.
Then show me a sheet with one picture of each graphic, labelled with what I'm saying at that moment.
```

**What you should see:** after about 15 minutes, a picture sheet of every graphic (as a picture or a link to a private page) and an updated video. The video gets about 4 seconds longer because of the end card. Claude often fixes a card or two after looking at the pictures, e.g. a heading that wrapped onto an extra line, and adds a check so it can't happen again.

**Check it worked:** watch the video and, for each graphic, check:
- **Timing:** things appear *as* you say them, not before or after.
- **Brand:** right fonts, colours and spacing, with nothing at the very edges.
- **Spelling:** all the text is spelled correctly.

### Step 6 — Give notes

**Do this:** tell Claude what you'd change. It only re-makes the graphics you mention, so it's quick. Examples:

- *"Graphic 4 is too busy. Remove the icons and keep two words per column."*
- *"The title card highlight should be on 'pipeline', not 'build'."*
- *"End the takeaway graphic as soon as the last item appears. Don't hold it."*
- *"Everything animates too fast."*

> **Want to see a graphic up close?** Ask: *"Open graphic 4 in the HyperFrames preview."* It opens in your browser, where you can scrub through it frame by frame.

> **Tip:** if you give the same note more than once, say *"Add this to my Motion graphic rules."*

---

## What you have now

- ✅ HyperFrames installed, with its skills available to every project
- ✅ A **brand kit** with title card, end card and graphic templates
- 🎬 **Milestone video:** `build/final/01-sample.mp4`, now with a title card, animated graphics timed to your words, and an end card

## Landscape note

Ask Claude to make every template adapt to the video's shape, then test one horizontal render. In landscape, things usually sit side by side instead of stacked.

## Common problems

| What you see | What to tell Claude |
|---|---|
| Fonts look wrong in the video | *"The fonts in the video don't match my style guide. Can you check they're loading?"* |
| No sound effects in graphics | *"The graphics have no sound. Can you check the sound effects are set up correctly in HyperFrames?"* |
| Graphics take ages to make | *"Make graphics faster while we're testing. Use draft quality, and full quality only for the final build."* |
