---
name: html-building-blocks-skill
description: Build or edit single-file HTML pages and artifacts for analysis, comparison and explainer documents (comparison tables, notebook-style code chunks, architecture diagrams, collapsible sections, status tags). Use when asked to create, extend or restyle such a page, especially one that will be presented to experts or edited by several sessions.
---

# HTML building blocks

Reusable blocks and house rules for explainer and analysis pages. Layer this on top of any platform design skill that is available: load that first, then apply the rules here.

## Files in this skill

- `assets/components.css`: styles for every block, with light and dark themes.
- `assets/components.html`: markup for every block, as one demo page. Copy the block you need and keep its class names.
- `html-preferences.csv`: page design, diagram, table, code-sample and accuracy rules, with the user's own words. Read it when a rule below needs detail or a case is not covered.
- `communication-preferences.csv`: how the user wants replies written and work handled (style, tone, planning, scope, collaboration). Apply it to chat replies and working style, not to page content.

## Workflow

1. **Plan before building.** State the audience and the point of the page. When more than one design fits, offer two or three labeled options with trade-offs, mark a recommendation, and wait for the choice.
2. **Add only what was asked.** If the user numbers a list of suggestions, add only the numbers they name. Keep all other content and structure unchanged.
3. **Build from the blocks.** Copy blocks from `components.html`. Inline `components.css` in a `<style>` tag for a single-file artifact. New sections reuse the format of existing ones.
4. **Check claims.** The audience is often expert. Verify product claims against source or official docs. Scope each comparison column to one product and version, and say so on the page.
5. **Run what you show.** Run every code chunk in a scratch environment before publishing. Say plainly what was not run.
6. **Merge, never overwrite.** Other sessions may edit the same page. Read the live version first. If a publish is refused, merge onto the newer version and publish again.
7. **Give the link** in the reply once published, and confirm any shared copy (such as a repo) matches the latest version.

## Block rules

| Block | Rule |
|---|---|
| Comparison table | First on the page. Row per concept, column per product. Fits the viewport with `table-layout: fixed`, never a horizontal scroll. Row labels explain jargon. Tint the key-difference row with `class="key"`. |
| Notebook chunk | `In [ ]:` prompt, monospace cell, green italic comments. In hello-world examples, comments name the matching table row. |
| Two columns | Side by side, stacked at 760px or narrower. |
| Option cards | Rows are setup types, columns are products. Each card has a title, numbered steps, a one-line gist and an LOE tag. The featured product gets the green border. |
| Collapsible | Native `details`, closed by default, no JavaScript. One `details` per section. Show/Hide button on the left, lavender `#7a68c4`, bold white text. All collapsibles look identical. |
| Unverified tag | `[UNVERIFIED SLOP]`, small yellow tag, first in the heading, no emoji, no all caps. A flagged section must not also say it was checked. |
| LOE tags | `[LOE: High]` red, `[LOE: Med]` orange, `[LOE: Low]` pale yellow, `[LOE: XLow]` light green. Same shape as the unverified tag. |
| Placeholder | Dashed box with a `PLACEHOLDER` tag and one sentence on what will go there. |
| Diagram | Green user-facing column, gray backend column, dashed row dividers with zone labels, labels inside boxes, three labeled sub-boxes (INPUTS, RUNS IN, OUTPUTS) instead of bullet lists. Keep it minimal. Wide diagrams may scroll sideways on a phone. Tables may not. |
| Headings | One h1 for the page or key insight, h2 for sections, h3 for subsections. Use the user's exact wording. Key takeaways read `Key Insight A:`, `Key Insight B:` and so on. |

## Style defaults

- Start restrained: no emoji, no all caps, no loud colors unless asked. The user has asked for a louder version before and then asked to cut it back.
- Dark and light themes both work. Tokens live on `:root` in `components.css`.
- Stay within the width of the page at 360px, apart from the diagram wrapper.

## Before publishing

- Headings are in a logical order.
- Every collapsible button toggles only its own section.
- Tables fit the width with no sideways scroll.
- Code chunks were run, or the page says they were not.
- Sources are listed, and unverified material is tagged.
- The live version was read and merged.
