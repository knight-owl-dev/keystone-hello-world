# Markdown Formatting Capabilities

Keystone supports advanced formatting through [Pandoc's fenced div syntax](https://pandoc.org/MANUAL.html#extension-fenced_divs), using the form `::: div-name` and `:::`.

This lets you apply custom styling or behavior by wrapping sections of content in named blocks — like `::: dialog` for character conversations.

## Styled Dialog Blocks

Dialogs are useful for formatting conversations or character interactions in narrative text.
The `dialog` div works with standard Markdown bullet lists — each `-` line becomes a stylized dialog line in the output.

### Example Output Using Dialog Blocks

::: dialog

- Who’s there?
- Just the wind.
- The wind doesn’t knock.
:::

The door creaked open, but no one was there.

::: dialog

- Are you sure we should be here?
- It’s too late to turn back now.
:::

### Markdown Snippet Using Dialog Blocks

Here’s the Markdown you’d write:

```markdown
::: dialog

- Who’s there?
- Just the wind.
- The wind doesn’t knock.
:::

The door creaked open, but no one was there.

::: dialog

- Are you sure we should be here?
- It’s too late to turn back now.
:::
```

**Spacing and line breaks matter** — the dialog block must be separated from surrounding text to render correctly. If you need to insert regular prose between dialog lines, **close the dialog div** (`:::`), add your text, and then **reopen the dialog** with `::: dialog`.

## Unstyled Dialog

::: {.aside type="tip"}
Do not mix **styled** and **unstyled dialog** in the same text. Pick one style and stick with it for consistency.
:::

If you prefer not to use the dialog block, you can still format dialog in Markdown. This is useful for simple conversations or when you want to avoid the extra styling. Use double dashes (`--`) to indicate dialog lines, and separate them with line breaks or double spaces. This method is less visually distinct but can be more straightforward.

For example, you can write with double spaces or line breaks to separate dialog lines and use double dashes:

### Example Output Using Unstyled Dialog

-- Who’s there?  
-- Just the wind.  
-- The wind doesn’t knock.  

The door creaked open, but no one was there.

-- Are you sure we should be here?  
-- It’s too late to turn back now.  

## Dialog Prose

Prose-style dialog presents conversations in the flow of narrative paragraphs, rather than using bullet points or script formatting.

Each spoken line is wrapped in quotation marks and usually begins a new paragraph. This style is common in fiction, short stories, and novels. It allows dialog to blend naturally with narration, emotion, and pacing — ideal for immersive storytelling.

No special syntax is needed; just write your dialog using standard Markdown. The output will format it as prose.

::: {.aside type="tip"}
Markdown treats paragraphs as blocks separated by either a blank line or two spaces at the end of a line. To separate dialog lines from surrounding text, use a blank line — it’s more reliable across editors and avoids issues with trailing whitespace being trimmed automatically.
:::

### Example Output Using Line Breaks

The wind stirred the grass in slow, whispering waves.

"It's quiet," she said. "Too quiet."

He glanced at her, brow raised. "You always say that."

She smiled, the corners of her mouth tugged upward like a secret she'd just decided to share. "And I'm usually right."

The hilltop was empty. No birdsong. No trees creaking. Just the breeze, brushing past them like it had somewhere more important to be.

"Still think this is the right place?" he asked.

"For now," she said. "But stay close. Just in case."

They moved on.

Not quickly. Just... together.

::: pause
:::

The morning came slowly, as if the sun itself was reluctant.

::: pause
:::

By the time they reached the ridge, the light had changed.

### Example Output Using Double Spaces

The wind stirred the grass in slow, whispering waves.  
"It's quiet," she said. "Too quiet."  
He glanced at her, brow raised. "You always say that."  
She smiled, the corners of her mouth tugged upward like a secret she'd just decided to share. "And I'm usually right."  
The hilltop was empty. No birdsong. No trees creaking. Just the breeze, brushing past them like it had somewhere more important to be.  
"Still think this is the right place?" he asked.  
"For now," she said. "But stay close. Just in case."  
They moved on.  
Not quickly. Just... together.  

::: pagebreak
:::

## Using Custom LaTeX Inserts

::: {.aside type="tip"}
LaTeX inserts are rendered only in **PDF output**. They will not appear in EPUB or DOCX.
:::

Keystone supports embedded LaTeX for advanced formatting that goes beyond standard Markdown. This includes typesetting math, inserting symbols, and controlling layout — all inline with your content.

To restrict LaTeX content to PDF builds only, wrap it in a `::: latex-only` block. This ensures the content is excluded from other formats like EPUB or DOCX.

### Example Output Using LaTeX Inserts

::: {.aside type="tip"}
If you see no table here, you're viewing it in another format. The table will be rendered in PDF output only.
:::

::: latex-only
\begin{center}
\begin{tabular}{|c|c|}
  \hline
  \textbf{Feature} & \textbf{Supported?} \\
  \hline
  Markdown         & \tick \\
  LaTeX Inserts    & \tick \\
  Lua Filters      & \tick \\
  Dockerized Builds & \tick \\
  \hline
\end{tabular}
\end{center}
:::

### Markdown Snippet Using LaTeX Inserts

Here's the corresponding Markdown snippet for the LaTeX table:

```latex
::: latex-only
\begin{center}
\begin{tabular}{|c|c|}
  \hline
  \textbf{Feature} & \textbf{Supported?} \\
  \hline
  Markdown         & \tick \\
  LaTeX Inserts    & \tick \\
  Lua Filters      & \tick \\
  Dockerized Builds & \tick \\
  \hline
\end{tabular}
\end{center}
:::
```

The use of `::: latex-only` is a custom Keystone feature. It allows you to specify that the content inside the **div** should only be rendered in LaTeX output, not in other formats like DOCX or EPUB.

### Inline LaTeX-Only Spans

For short LaTeX expressions within a sentence, use the inline span syntax `[content]{.latex-only}` instead of a full block. The content appears only in PDF output — EPUB and HTML strip it entirely, so the surrounding sentence must read naturally without it.

### Example Output Using Inline LaTeX-Only

Pandoc[, powered by \LaTeX,]{.latex-only} makes publishing easy[\footnote{Via the XeLaTeX engine with full Unicode support.}]{.latex-only}.

> **Note:** In PDF, the sentence above reads "Pandoc, powered by LaTeX, makes
> publishing easy" with a footnote. In EPUB, it simply reads "Pandoc makes
> publishing easy" — both spans are removed.

### Markdown Snippet Using Inline LaTeX-Only

```markdown
Pandoc[, powered by \LaTeX,]{.latex-only}
makes publishing easy[\footnote{Via the
XeLaTeX engine with full Unicode support.}
]{.latex-only}.
```

Two spans are used here:

- `[, powered by \LaTeX,]{.latex-only}` — a parenthetical aside containing the `\LaTeX` command, which renders the stylized logo in PDF. Purely cosmetic.
- `[\footnote{...}]{.latex-only}` — a `\footnote` that adds a numbered footnote at the bottom of the page. EPUB has no fixed pages, so the span is stripped entirely.

::: pagebreak
:::

## Including Images in Markdown

Markdown makes it easy to include images in your content. Wrap images in a `::: figure` div for explicit control over sizing and alignment:

```markdown
::: {.figure width=25%}
![Keystone](assets/keystone-example.jpg)
:::
```

Which will render as:

::: {.figure width=25%}
![Keystone](assets/keystone-example.jpg)
:::

### Using a Shortcut for Figures

If you frequently use a specific figure size, define a shortcut in `shortcuts.yaml`:

```yaml
thumbnail:
  class: figure
  width: 25%
```

Then use the shortcut name directly:

```markdown
::: thumbnail
![Keystone](assets/keystone-example.jpg)
:::
```

Which will render as:

::: thumbnail
![Keystone](assets/keystone-example.jpg)
:::

::: pagebreak
:::

## Page Breaks

If you need to start a new page in your document, you can use the `::: pagebreak` directive. This is useful for separating sections or chapters in your output.

The page break will be rendered in PDF and EPUB output, but not in DOCX.

For example, to create a page break, you can write:

```markdown
::: pagebreak
:::

## My Sample Chapter

This is a new chapter that starts on a new page.
```

## Poem Dates

If you want to include dates in your poems, you can use the `::: poem-date` directive after defining a shortcut for the `align` handler. This is useful for indicating when a poem was written or published while maintaining consistent formatting.

For example, add this to your shortcuts file:

```yaml
poem-date:
  class: align
  interface:
    style:
      bind: class.style
      default: right
  body: |
    ::: {.font style="italic"}
    :::
```

Then, to include a date in your poem, you can write:

```markdown
Line of the poem  
Line of the poem

::: poem-date
2023-10-01
:::
```

Which renders as:

Line of the poem  
Line of the poem

::: poem-date
2023-10-01
:::

::: pagebreak
:::

## Font Size Overrides

Keystone supports font size overrides at both block and inline level using the `font` handler. Block-level overrides wrap entire paragraphs, while inline overrides change the size of individual words or phrases.

### Example Output Using Font Size Blocks

::: {.font size="small"}
This paragraph is rendered at a smaller size. Useful for legal text, footnotes, or any content that should be visually subordinate to the main body.
:::

::: {.font size="large"}
This paragraph is rendered at a larger size. Useful for emphasis or section openers.
:::

### Example Output Using Inline Font Sizes

Regular text with [a few small words]{.font size="small"} in the middle, followed by [something large]{.font size="large"} for emphasis.

### Markdown Snippet Using Font Sizes

Here's the Markdown you'd write for block-level overrides:

```markdown
::: {.font size="small"}
This paragraph is rendered at a smaller size.
:::

::: {.font size="large"}
This paragraph is rendered at a larger size.
:::
```

And for inline overrides:

```markdown
Regular text with [a few small words]{.font size="small"} in the
middle, followed by [something large]{.font size="large"} for emphasis.
```

::: pagebreak
:::

## Font Family Overrides

The `font` handler lets you switch typefaces for blocks or inline text. All registered fonts are available for both PDF and EPUB output.

### Example Output Using Font Family Blocks

::: {.font family="libertine"}
This paragraph is set in Linux Libertine, a classic serif typeface well-suited for book body text. It pairs naturally with Biolinum for headings.
:::

::: {.font family="dejavu-sans"}
This paragraph is set in DejaVu Sans, a clean sans-serif with broad Unicode coverage. It works well for technical content or a modern look.
:::

### Example Output Using Inline Font Families

A sentence with [a word in Libertine]{.font family="libertine"} and [another in DejaVu Sans]{.font family="dejavu-sans"} showing mid-sentence typeface switching.

### Markdown Snippet Using Font Families

Here's the Markdown you'd write for block-level overrides:

```markdown
::: {.font family="libertine"}
This paragraph is set in Linux Libertine.
:::

::: {.font family="dejavu-sans"}
This paragraph is set in DejaVu Sans.
:::
```

And for inline overrides:

```markdown
A sentence with [a word in Libertine]{.font family="libertine"}
and [another in DejaVu Sans]{.font family="dejavu-sans"}.
```

::: pagebreak
:::

## Combining Font Family and Size

The `font` handler accepts both `family` and `size` attributes on the same element, so there is no need to nest.

### Example Output Using Combined Blocks

::: {.font family="libertine" size="small"}
This paragraph is set in Linux Libertine at a smaller size — useful for footnotes or asides that should feel distinct from the main body.
:::

::: {.font family="dejavu-sans" size="large"}
This paragraph is set in DejaVu Sans at a larger size — a natural fit for callouts or section openers.
:::

### Example Output Using Combined Inline Spans

Regular text with [small Libertine]{.font family="libertine" size="small"} and [large DejaVu Sans]{.font family="dejavu-sans" size="large"} in the same sentence.

### Markdown Snippet Using Combined Overrides

For block-level:

```markdown
::: {.font family="libertine" size="small"}
Small Libertine text.
:::
```

For inline:

```markdown
Regular text with
[small Libertine]{.font family="libertine" size="small"}
in the same sentence.
```

::: pagebreak
:::

## Multi-Column Layouts

Keystone supports multi-column layouts using the `multicol` div. Content flows automatically across columns in both PDF and EPUB output.

### Example Output Using Default Two Columns

::: multicol
Multi-column layouts are ideal for content that benefits from narrower line lengths — reference lists, glossaries, or sidebars. The default two-column layout balances readability with efficient use of page width.

A second paragraph continues in the same two-column flow, demonstrating that block-level content distributes naturally across columns.
:::

### Example Output Using Three Columns

::: {.multicol cols=3}
Three columns work well for compact lists and index-style layouts where entries are short and scanning is more important than sustained reading.
:::

### Markdown Snippet Using Multicol

For a default two-column layout:

```markdown
::: multicol
Content flows across two columns automatically.
:::
```

For a custom column count:

```markdown
::: {.multicol cols=3}
Content flows across three columns.
:::
```
