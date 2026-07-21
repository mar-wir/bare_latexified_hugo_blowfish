# Custom Shortcodes & Additions Documentation

This guide documents all the custom shortcodes and additions in this Hugo Blowfish project.

## Basic Dependencies

```bash
sudo apt install nodejs
sudo apt install npm 
sudo npm install -g blowfish-tools
```

Or use brew on mac.

## This repostory

```bash
git clone https://github.com/mar-wir/bare_latexified_hugo_blowfish.git
cd bare_latexified_hugo_blowfish
git submodule update --init --recursive

```

## JavaScript Dependencies

Following depenencies must be installed manually via npm:

### JavaScript Libraries

- **Tippy.js** v6.x (CDN) - Tooltip/popover library for interactive references

```bash
npm i tippy.js
```

## Shortcodes Overview

Here is the updated table with the `{{< bibliography >}}` shortcode separated into its own row for clarity, using standard Markdown table syntax with clear column separators:

| Definition Shortcode | Reference Shortcode | Description |
| --- | --- | --- |
| `{{< equation >}}` | `{{< eq >}}` | Defines and cross-references numbered mathematical equations using LaTeX syntax.

 |
| `{{< figdef >}}` | `{{< fig >}}` | Defines and cross-references numbered image figures with captions and responsive styling.

 |
| `{{< tabdef >}}` | `{{< tab >}}` | Defines and cross-references numbered tables containing Markdown content and styled captions.

 |
| `{{< htmlfigdef >}}` | `{{< htmlfig >}}` | Defines and cross-references embedded HTML content (like custom diagrams or widgets) wrapped as a figure.

 |
| `{{< codelistingdef >}}` | `{{< codelisting >}}` | Defines and cross-references numbered Markdown code blocks with centered captions. |
| `{{< manimdef >}}` | `{{< manim >}}` | Embeds and cross-references interactive presentations (like Manim slides) within a 16:9 iframe featuring a custom controls popup. |
| N/A (Uses YAML file) | `{{< citep >}}`, `{{< citet >}}` | Generates inline parenthetical or textual citations based on a CSL JSON/YAML database.

 |
| N/A | `{{< bibliography >}}` | Automatically generates a formatted bibliography section (typically placed at the end of the post) containing all cited references.

 |
| `{{< alert >}}` | N/A | Creates styled alert boxes with customizable light/dark mode colors and Font Awesome icons.

 |

## Mathematical Equations

### Equation Definition

**Shortcode:** `{{< equation >}}`

Define numbered equations with LaTeX syntax. Equations are automatically assigned IDs for cross-referencing.

**Usage:**

```markdown
{{< equation "1.1" >}}
E = mc^2
{{< /equation >}}

{{< equation "schrodinger" >}}
-\frac{\hbar^2}{2m}\nabla^2\psi + V\psi = E\psi
{{< /equation >}}
```

**Output:**

- Displays the equation with a tag showing the number
- LaTeX math is rendered in a math-container div
- The equation ID is generated from the parameter: `eq-1-1` or `eq-schrodinger`

### Equation References

**Shortcode:** `{{< eq >}}`

Create clickable references to equations defined elsewhere in the post.

**Usage:**

```markdown
As shown in {{< eq "1.1" >}}, we can see that energy equals mass times the speed of light squared.

More complex equations like {{< eq "schrodinger" >}} govern quantum mechanics.
```

**Features:**
- Creates a clickable link to the equation
- Shows a popover preview on hover
- Links directly to the equation ID defined with `{{< equation >}}`
- Works across the same page

---

## Figures & References

### Figure Definition

**Shortcode:** `{{< figdef >}}`

Define numbered figures with captions and images.

**Parameters:**
- **num** (required): Figure number/identifier (e.g., "1", "2.1", "diagram-a")
- **src** (required): Image source URL
- **caption** (required): Figure caption text

**Usage:**

```markdown
{{< figdef num="1" src="/images/architecture.png" caption="System architecture diagram" >}}

{{< figdef 
  num="2.1" 
  src="/images/workflow.jpg" 
  caption="Multi-step workflow showing data processing pipeline"
>}}
```

**Features:**
- Creates centered figure with styled caption
- Responsive image sizing
- Rounded corners and auto height
- Figure ID is generated: `fig-1`, `fig-2-1`, `fig-diagram-a`

### Figure References

**Shortcode:** `{{< fig >}}`

Create clickable references to figures.

**Usage:**

```markdown
The architecture is shown in {{< fig "1" >}}. 

As described in {{< fig "2.1" >}}, the workflow consists of multiple stages.
```

**Features:**
- Creates a clickable link (e.g., "Figure 1")
- Popover preview on hover
- Links to the figure defined with `{{< figdef >}}`

---

## Tables & References

### Table Definition

**Shortcode:** `{{< tabdef >}}`

Define numbered tables with Markdown-formatted content and captions.

**Parameters:**
- **num** (required): Table number/identifier
- **caption** (required): Table caption

**Usage:**

```markdown
{{< tabdef num="1" caption="Comparison of different approaches" >}}
| Method | Pros | Cons |
|--------|------|------|
| Approach A | Fast | Less accurate |
| Approach B | Accurate | Slow |
| Approach C | Balanced | Moderate complexity |
{{< /tabdef >}}
```

**Features:**
- Renders Markdown content inside table wrapper
- Automatic numbering and IDs
- Styled caption below table
- Table ID: `tab-1`, `tab-comparison`, etc.

### Table References

**Shortcode:** `{{< tab >}}`

Create clickable references to tables.

**Usage:**

```markdown
The comparison in {{< tab "1" >}} shows that Approach C offers the best balance.

As seen in {{< tab "results" >}}, our findings confirm the hypothesis.
```

---

## Code Listings & References

### Code Listing Definition

**Shortcode:** `{{< codelistingdef >}}`

Define numbered code blocks with captions. This shortcode provides a structured wrapper around standard Markdown code fences.

**Parameters:**

* **num** (required): Listing number or identifier (e.g., "1", "2.1", "auth-script")
* **caption** (required): Descriptive text displayed below the code

**Usage:**

```markdown
{{< codelistingdef num="1" caption="A simple Python function" >}}
```python
def hello_world():
    print("Hello, World!")
_```
{{< /codelistingdef >}}
```

**Features:**

* Wraps inner Markdown code blocks inside a styled `<figure>` element.
* Maintains left-aligned formatting for the code while perfectly centering the caption below it.
* Automatically generates a unique ID for cross-referencing (e.g., `code-1`).

### Code Listing References

**Shortcode:** `{{< codelisting >}}`

Create clickable references to code listings defined elsewhere on the page.

**Usage:**

```markdown
As demonstrated in {{< codelisting "1" >}}, the print function outputs text to the console.

The authentication flow is handled by {{< codelisting "auth-script" >}}.

```

**Features:**

* Creates a clickable internal link (e.g., "Listing 1").
* Triggers a Tippy.js popover preview on hover, displaying the entire code block and its caption in a scrollable window.
* Links directly to the identifier defined in `{{< codelistingdef >}}`.

---

## Presentations & Manim Slides

### Presentation Definition

**Shortcode:** `{{< manim-slidedef >}}` 

Embed interactive presentations, such as Manim slides or external slide decks, within a styled viewport. See [here](https://manim-slides.eertmans.be/latest/) for more information about manim slides.

The manim slides must be created as following:
1. Render slides with `--one-file` and `--offline` flags.

```bash
manim example.py SCENE # or manimgl example SCENE
manim-slides convert SCENE scene.html -ccontrols=true --one-file --offline
```
2. Place the resulting html file in the `static/slides/` directory. You might have to create those folders first.

**Parameters:**

* **num** (required): The presentation number or identifier used for cross-referencing.


* **src** (required): The URL source of the presentation (e.g., HTML file or external link) loaded into the iframe.


* **caption** (required): Descriptive text displayed beneath the presentation.



**Usage:**

```markdown
{{< manim-slidedef num="1" src="/slides/intro-presentation.html" caption="Introduction to Vector Mathematics" >}}
```

**Features:**

* Renders an embedded iframe with a responsive 16:9 aspect ratio, rounded corners, and a subtle drop shadow.


* Includes a dedicated **"Fullscreen"** button that requests fullscreen mode specifically for the presentation iframe.


* Features a **"Controls"** toggle button that reveals an interactive, glassmorphism-styled (blurred background) popup listing keyboard shortcuts.


* The controls popup automatically hides after 5 seconds of inactivity, when clicking away, or when an active presentation shortcut key (like Space, F, or arrow keys) is pressed.


* Automatically generates an HTML ID formatted as `pres-{num}` to allow for direct linking.


* Creates a centered `<figcaption>` that automatically pulls the localized "Presentation" string via Hugo's `i18n` function.



### Presentation References

**Shortcode:** `{{< manim-slide >}}`

Create standard, clickable internal anchor links to presentations defined elsewhere on the page.

**Usage:**

```markdown
As we can see in the interactive demonstration within {{< manim-slide "1" >}}, the vectors align perfectly.

```

**Features:**

* Generates a clickable link displaying "Presentation {num}" (localized via `i18n`).


* Navigates directly to the `pres-{num}` ID generated by the definition shortcode.


* *Note: Unlike figures and code listings, this reference shortcode currently outputs a standard `<a class="pres-ref">` link and does not trigger a Tippy.js popover preview*.

---

## Citations & Bibliography

### Citation Database

**File:** `/data/references.yaml`

Store all references in CSL (Citation Style Language) JSON format. The system reads from a YAML file containing a `references` array.

**Example Structure:**

```yaml
---
references:
- id: authorYear
  author:
    - family: Last Name
      given: First Name
    - family: Second Author
      given: First Name
  issued:
    - year: 2020
  title: "Article Title"
  type: article-journal
  container-title: "Journal Name"
  volume: 10
  issue: 2
  page: "100-120"
  publisher: "Publisher Name"
```

### Parenthetical Citations (citep)

**Shortcode:** `{{< citep >}}`

Create citations in parenthetical format: `(Author, Year)`

**Usage:**

```markdown
Machine learning has revolutionized many fields {{< citep "smithMachineLearningApplications2021" >}}.

According to recent research {{< citep "jonesDeepLearningAdvances2022" >}}, neural networks continue to improve.
```

**Output:**
- Displays as: `(Smith, 2021)`
- Adds reference to bibliography
- Clickable link with popover preview showing full citation

### Textual Citations (citet)

**Shortcode:** `{{< citet >}}`

Create citations in textual format: `Author (Year)`

**Usage:**

```markdown
{{< citet "smithMachineLearningApplications2021" >}} demonstrated that deep learning improves accuracy.

{{< citet "jonesDeepLearningAdvances2022" >}} built upon this work to create more efficient models.
```

**Output:**
- Displays as: `Smith (2021)`
- Adds reference to bibliography
- Clickable link with popover preview

### Bibliography

**Shortcode:** `{{< bibliography >}}`

Automatically generates a bibliography section with all cited references. Place this at the end of your post.

**Usage:**

```markdown
# Main Content

Some text with citations {{< citep "ref1" >}} and {{< citep "ref2" >}}.

{{< bibliography >}}
```

**Features:**
- Only shows references that were actually cited in the post
- Automatically deduplicates citations
- Formats in hanging indent style (standard academic format)
- Shows full author names, year, title, and publication details
- Clickable links back to citation positions

**Citation Formats:**
- **Journal Articles:** Author (Year). Title. *Journal Name*, Volume(Issue), Pages.
- **Books:** Author (Year). *Title*. Publisher.

---

## HTML Figures

### HTML Figure Definition

**Shortcode:** `{{< htmlfigdef >}}`

Define figures with embedded HTML content instead of just images (useful for diagrams, code blocks, etc.).

**Parameters:**
- **num** (required): Figure number
- **caption** (required): Figure caption

**Usage:**

```markdown
{{< htmlfigdef num="1" caption="Code example in Python" >}}
```python
def hello_world():
    print("Hello, World!")
```
{{< /htmlfigdef >}}

{{< htmlfigdef num="2" caption="HTML embed example" >}}
<div style="border: 1px solid #ccc; padding: 10px;">
  <h4>Custom HTML Content</h4>
  <p>This is custom HTML inside a figure.</p>
</div>
{{< /htmlfigdef >}}
```

**Features:**
- Wraps inner content as figure
- Supports Markdown and HTML
- Styled with consistent figure formatting
- Figure ID: `fig-1`, `fig-2`, etc.

### HTML Figure References

**Shortcode:** `{{< htmlfig >}}`

Reference HTML figures (same as regular `{{< fig >}}`, included for consistency).

**Usage:**

```markdown
See the code example in {{< htmlfig "1" >}}.
```

---

## Data Structure

### References File Format

The `/data/references.yaml` file uses the CSL (Citation Style Language) standard. Key fields include:

| Field | Type | Description |
|-------|------|-------------|
| `id` | string | Unique identifier for the reference (used in citations) |
| `author` | array | List of authors with `family` and `given` names |
| `issued` | array | Publication date with `year` field |
| `title` | string | Reference title |
| `type` | string | Reference type (e.g., `article-journal`, `book`, `webpage`) |
| `container-title` | string | Journal/collection name (for articles) |
| `publisher` | string | Publisher name |
| `volume` | string | Volume number (for journals) |
| `issue` | string | Issue number (for journals) |
| `page` | string | Page range |
| `DOI` | string | Digital Object Identifier |
| `URL` | string | Website URL |

---

## Alerts

**Shortcode:** `{{< alert >}}`

Create styled alert boxes with customizable icons and colors.

### Basic Usage

```markdown
{{< alert >}}
This is a basic alert with a default warning icon.
{{< /alert >}}
```

### Parameters

- **icon** (optional): Font Awesome icon name (default: `triangle-exclamation`)
- **cardColor** (optional): Light mode background color (hex, rgb, etc.)
- **cardColorDark** (optional): Dark mode background color
- **iconColor** (optional): Light mode icon color
- **iconColorDark** (optional): Dark mode icon color
- **textColor** (optional): Light mode text color
- **textColorDark** (optional): Dark mode text color

### Examples

```markdown
{{< alert icon="circle-info" >}}
This is an info alert with a custom icon.
{{< /alert >}}

{{< alert 
  icon="heart" 
  cardColor="#fff3cd" 
  cardColorDark="#664d03"
  iconColor="#ff0000"
  textColor="#333333"
>}}
Custom styled alert with all parameters.
{{< /alert >}}
```

---

For more information about the Blowfish theme, visit: https://blowfish.page/
