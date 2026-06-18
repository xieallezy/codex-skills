---
name: reading-card
description: Create or update weekly Chinese companion-reading learning-card PowerPoint decks from an existing weekly PPT template. Use when the user asks to make the next week of 5 daily reading cards, replace story/quiz/vocabulary/progress text, preserve the original PPT layout/fonts/styles, prepare image requirements, or continue work on files named like L1-01周伴读.pptx, L1-02周伴读.pptx, L1-03周伴读学习.pptx.
---

# 伴读学习卡 PPT

## Core Rule

Only change the content that the user asks to change. Do not rebuild the template.

- Keep all template layout, text boxes, positions, alignments, margins, fills, borders, icons, reward blocks, and decorative elements unchanged.
- Keep all original font sizes and fonts unchanged.
- Font names, font sizes, paragraph styles, run styles, and existing text-box formatting are strict invariants. When editing PPT text, modify the text inside existing runs whenever possible; do not clear paragraphs or recreate text boxes. If a run must be split or rebuilt, copy the original run formatting exactly and validate against the source/template before reporting completion.
- For PowerPoint font validation, do not rely on `font.name` alone. Chinese rendering depends on DrawingML font slots. When setting or validating fonts, check or set `latin`, `ea`, and `cs` font slots for every non-empty run.
- Preserve the existing text box formatting by editing existing text runs where possible. Avoid clearing and recreating text boxes unless there is no alternative.
- Never shrink fonts to make new content fit. If text does not fit, first lengthen or widen the existing text box within the original card/panel. If a decorative illustration blocks or crowds the text area, delete that illustration rather than reducing font size or allowing text to wrap awkwardly.
- Main font rule: all normal Chinese text uses `方正粗圆简体`.
- Exception: pinyin inside `说一说` must use `微软雅黑` for readability. Keep the original pinyin font size and run styling otherwise; do not change the Chinese text font.
- Do not generate images unless the user explicitly asks for image generation. If image work is pending, describe the needed images and let the user provide them.
- Do not export all slides to images unless the user explicitly asks. The user may keep editing the PPT afterward.
- Before editing, list the skill rules that will be applied for the current task. After editing, validate each listed rule. Do not report completion until all validations pass.

## Standard Workflow

1. Inspect the folder and locate the latest/source weekly PPT.
2. If making a new week, copy the previous week’s PPT and rename it for the new week only after confirming the intended filename if unclear.
3. Read the existing PPT structure before editing. Identify per-slide text boxes and picture placeholders from the actual deck; do not assume every slide has identical shape indexes.
4. Ask for or use the user-provided 5-day content:
   - reading page range
   - companion-reading lesson number
   - story-train copy
   - quiz question, options, and correct answer
   - `说一说` page/word/pinyin items
   - progress titles and page ranges, if not already specified
   - image descriptions, if image placement will be needed later
5. First update text only. Do not work on images until text is accepted or the user requests image placement.
6. Validate the edited PPT structurally and visually before reporting completion. Visual validation may use single-slide or key-area previews; do not export all slides unless the user explicitly asks.
7. After validation passes, report that the PPT is updated. If validation fails, fix the PPT and validate again instead of reporting success.

## Text Rules

- Story-train copy should fit the existing story text box, usually about 5 visual lines.
- If the user’s story copy is too long, lightly compress it while preserving the original meaning and plot.
- Keep child-friendly, concise Chinese wording.
- Do not invent story facts, answer options, or vocabulary unless the user asks for help drafting.
- If the user omits pinyin and asks Codex to fill it, fill common Mandarin pinyin with tone marks.
- Keep page labels in the existing format, such as `1-10页`.
- Keep lesson labels in the existing format, such as `观看伴读第一讲`.

## Quiz Layout Rules

- If the question or options are long, remove the small illustration from `选一选` and use the freed space for text.
- A/B/C markers are fixed structural elements. Never move, resize, or restyle the marker circles or the A/B/C letters; only the option content after the marker may change.
- Keep quiz option rows aligned to the normal template row anchor. Do not copy a one-off shifted position from another week/slide unless the user explicitly asks for that special layout.
- If answer options wrap or look crowded, widen the option text boxes and their pill backgrounds only as much as needed for the longest option among A/B/C on that slide; keep all three option rows the same width for visual alignment, but do not make them unnecessarily long.
- Do not distort the A/B/C circular markers or option-pill shapes.
- If there are only two options:
  - remove the third option’s marker, text, and background shape;
  - reposition the remaining A/B rows so the block looks balanced;
  - do not invent a third option just to fill the template.
- Keep quiz fonts and text styling from the original template.

## Vocabulary Layout Rules

- Hard validation rule for the vocabulary/say-one-say block: preserve the source paragraph line spacing exactly. Current weekly templates commonly use `2.0`; inspect the source deck and keep its actual value.
- Put word and pinyin on one line when they fit comfortably in the existing or carefully widened text box. Split into a word line plus a pinyin line only when the combined word+pinyin would wrap, crowd, or collide.
- For PowerPoint files, set and validate all font slots for each non-empty vocabulary run. Chinese page labels, Chinese words, Chinese punctuation, and full-width parentheses must use the template Chinese font in `latin`, `ea`, and `cs`. Pinyin letters and tone marks must use the template pinyin font in `latin`, `ea`, and `cs`.
- Keep every vocabulary run at the source run size. Never enlarge or shrink vocabulary text to solve layout problems.

- `说一说` usually contains page number, word, and pinyin.
- Preserve the original font styling for Chinese text. Pinyin runs must use `微软雅黑` while keeping their original size and other styling.
- When splitting `说一说` runs, explicitly set the Chinese/page/punctuation runs to `方正粗圆简体` and only the pinyin letters/tone marks to `微软雅黑`; do not let Chinese words before or after the pinyin inherit the pinyin font.
- If vocabulary text is long, remove the small illustration from `说一说` rather than shrinking text too much.
- Do not let small images cover pinyin or vocabulary text.
- If vocabulary text is crowded, widen or lengthen the existing `说一说` text box within the panel. Keep Chinese run styling exactly as the template uses it; keep pinyin in `微软雅黑`.

## Progress And Image Rules

- The bottom adventure progress has 5 nodes matching the 5 daily sections.
- Progress titles and page ranges may change, but the bottom structure, lock/check states, reward area, and layout should stay unchanged.
- The circular progress images should correspond to the story-train main image for each day.
- If the user has not provided images, leave image handling for later and report what images are needed.
- For future image placement:
  - story-train side image is a full scene for that day;
  - `选一选` and `说一说` images should be simple cutout-style elements, not full-background scenes;
  - examples include a tree, leaf sign, hourglass, coin, bicycle detail, or character/object cutouts;
  - keep the first/second-week style as reference.

## Validation Checklist

Before reporting completion, check:

- Confirm the task-specific skill rules were listed before editing and every listed rule is validated after editing.

- Titles, reading pages, and lesson numbers match the user’s content.
- Story copy fits without obvious overflow.
- Quiz options match the user’s answer set.
- Two-option quizzes do not leave an empty C row.
- Vocabulary font slots are correct: Chinese/page/punctuation/full-width parentheses use the template Chinese font in `latin`, `ea`, and `cs`; pinyin uses the template pinyin font in `latin`, `ea`, and `cs`.
- Vocabulary text preserves the source line spacing, font sizes, and paragraph styling. Words and pinyin are on one line when they fit, and split only when needed.
- Key-slide visual validation confirms no text overflow, no unexpected font fallback, no quiz option wrapping, and no image/text overlap. If a visual check fails, continue fixing and revalidate before reporting completion.
- `说一说` pinyin is correct and uses `微软雅黑`; surrounding Chinese text keeps the template font.
- Top reading/lesson boxes preserve template alignment.
- No template fonts, font sizes, or alignments were changed accidentally.
- No images were generated, inserted, or exported unless explicitly requested.
