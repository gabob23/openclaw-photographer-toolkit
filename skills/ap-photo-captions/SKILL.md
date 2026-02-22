---
name: ap-photo-captions
description: Write AP-style photo captions for editorial photography assignments. Use when a photographer sends photos, subject details, or voice notes during a shoot and needs captions drafted in standard wire-service format for filing to publications like WSJ, NYT, AFP, etc.
---

# AP Photo Captions

## Setup — Caption Log

At the start of an assignment, create a caption log file with this header:

```markdown
# [Publication] [Assignment Name] — Caption Log
## [Day of week], [Full date]

**Assignment:** [SLUG]
**Client:** [Publication]
**Credit line:** [Photographer Name] for [Publication]

### Caption Format (AP Style)
**Description field:**
[Who], [age/title/affiliation], [what they're doing] [event context: during/ahead of/at...], in [City], [Country], [Day of week], [Abbreviated month]. [Day], [Year]. [Additional context sentence]. CREDIT: [Photographer] for [Publication]
[SLUG]

**Credit field:** [Photographer] for [Publication]

---

### Photo Log

| # | Time | Subject | Details | Caption Draft |
|---|------|---------|---------|---------------|
```

## Writing Captions

Each caption goes in the **Description field** of the image metadata (Photoshop/Lightroom).

### Structure

```
[Who], [age/title if known], [what they're doing] [when/where context], in [City], [Country], [Day], [Month] [Date], [Year]. [1–2 sentences of context]. CREDIT: [Photographer] for [Publication]
[SLUG on next line]
```

### Rules

1. **First sentence** = Who + What + When + Where. Present tense for actions ("addresses," "holds," "marches"), past participle for states ("is seen," "was fatally beaten").
2. **Identify** people by full name, age, title/occupation when available.
3. **Translate** any non-English text in quotes with the original in parentheses, or vice versa.
4. **Context sentences** add newsworthy background — keep factual and neutral.
5. **Credit line** always ends the caption: `CREDIT: [Name] for [Publication]`
6. **Slug** goes on the line after the credit.
7. **Detail shots** (tattoos, signs, clothing): describe what's visible, then tie to the event.
8. **Quotes** from subjects can be included after the context sentence when provided.
9. Use **AP style** for dates (Saturday, Feb. 21, 2026), titles (lowercase after name), ages (numeral, comma-set: "Jean Dupont, 42, a baker,").

### Workflow

1. Photographer sends a photo or voice note with subject info (name, age, role, quote, what's happening).
2. Draft the caption in the log table — increment the `#` column.
3. If info is incomplete, ask for specifics (name spelling, age, title, what they're doing).
4. When the photographer says "show me the caption," output the clean caption text ready to paste.
5. Correct any details immediately when the photographer sends updates.

### Embedding Captions in Files

If asked to embed captions into image files, use exiftool:

```bash
exiftool -Description="[caption text]" -Credit="[Photographer] for [Publication]" image.jpg
```

## Reference

See `references/ap-style-cheatsheet.md` for AP style date/title/number formatting rules.
