# Custom Shortcodes & Additions Documentation

This guide documents all the custom shortcodes and special additions in this Hugo Blowfish project.

## Table of Contents

1. [System Requirements & Installation](#system-requirements--installation)
2. [Alerts](#alerts)
3. [Mathematical Equations](#mathematical-equations)
4. [Figures & References](#figures--references)
5. [Tables & References](#tables--references)
6. [Citations & Bibliography](#citations--bibliography)
7. [HTML Figures](#html-figures)
8. [Data Structure](#data-structure)
9. [Multilingual Support](#multilingual-support)

---

## System Requirements & Installation

### Prerequisites

This project requires the following system dependencies to build and run:

#### Core Requirements

| Dependency | Version | Purpose |
|------------|---------|---------|
| **Hugo** | ≥ 0.158.0 (extended) | Static site generator |
| **Node.js** | ≥ 16.x | JavaScript runtime for build tools |
| **npm** | ≥ 8.x | Node package manager |

### Installation Steps

#### 1. Install Hugo

The **extended version** of Hugo is required (for SCSS/SASS support).

**macOS (Homebrew):**
```bash
brew install hugo
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get install hugo
```

**Windows (Chocolatey):**
```bash
choco install hugo-extended
```

**Verify installation:**
```bash
hugo version
# Output: hugo v0.164.0+extended+withdeploy darwin/arm64 BuildDate=2026-07-06...
```

#### 2. Install Node.js and npm

**macOS:**
```bash
brew install node
```

**Linux (Ubuntu/Debian):**
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**Windows:**
Download and install from [nodejs.org](https://nodejs.org/)

**Verify installation:**
```bash
node --version
npm --version
```

#### 3. Install Theme Dependencies

Navigate to the theme directory and install npm dependencies:

```bash
cd themes/blowfish
npm install
```

This installs the Blowfish theme's JavaScript and CSS dependencies.

### Theme Installation

The **Blowfish** theme is included as a Hugo module. It's automatically configured in your Hugo setup.

**Key theme files:**
- `/themes/blowfish/` - Theme directory
- `/themes/blowfish/theme.toml` - Theme configuration
- `/themes/blowfish/go.mod` - Go module definition (minVersion = "0.158.0")

### JavaScript & CSS Dependencies

The theme uses the following development dependencies (managed via npm):

#### CSS & Styling
- **Tailwind CSS** v4.3.2 - Utility-first CSS framework
- **Tailwind Scrollbar** v4.0.2 - Custom scrollbar styling
- **Tailwind Typography** v0.5.20 - Typography plugin

#### JavaScript Libraries
- **Tippy.js** v6.x (CDN) - Tooltip/popover library for interactive references
- **Popper.js** v2.x (CDN) - Positioning engine for Tippy
- **KaTeX** v0.17.0 - LaTeX math rendering
- **Mermaid** v11.16.0 - Diagram rendering
- **Chart.js** v4.5.1 - Data visualization
- **Medium Zoom** v1.1.0 - Image zoom effect
- **Fuse.js** v7.4.2 - Search functionality
- **TypeIt** v8.8.7 - Typing animation
- **Packery** v3.0.0 - Grid layout
- **Lite YouTube Embed** v0.3.4 - Lightweight YouTube embeds

#### Development Tools
- **Prettier** v3.9.4 - Code formatter
- **Rimraf** v6.1.3 - Cross-platform rm -rf
- **Vendor Copy** v3.0.1 - Copy vendor files
- **Puppeteer** v25.3.0 - Browser automation (Lighthouse testing)

### Building & Development

#### Development Mode (Watch Changes)

```bash
# In the theme directory
cd themes/blowfish

# macOS/Linux
npm run dev

# Windows
npm run dev-windows
```

This watches for CSS changes and recompiles Tailwind CSS automatically.

#### Production Build

```bash
# In the theme directory
cd themes/blowfish

# macOS/Linux
npm run build

# Windows
npm run build-windows
```

#### Run Hugo Server

```bash
# In the project root
hugo server

# With drafts and future posts visible
hugo server -D -F

# Specify port
hugo server -p 1313
```

#### Build Static Site

```bash
# Creates output in /public directory
hugo --minify
```

### Additional Tools

#### Blowfish Tools

Custom tools provided by the theme for enhanced functionality:

- **Citation Support** - CSL JSON format for bibliography management
- **Cross-referencing** - Automatic equation, figure, and table references
- **Multilingual Support** - Language-specific content and menus

#### External Services (CDN)

The following libraries are loaded from CDN (not npm dependencies):

```html
<!-- Tippy.js Popovers -->
<script src="https://unpkg.com/@popperjs/core@2"></script>
<script src="https://unpkg.com/tippy.js@6"></script>
<link rel="stylesheet" href="https://unpkg.com/tippy.js@6/dist/tippy.css" />
```

These provide the interactive popover functionality for citations, equation references, and figure references.

### Troubleshooting

**Hugo version incompatibility:**
```
WARN  Module "blowfish" is not compatible with this Hugo version
```
→ Update Hugo to v0.158.0 or higher

**Missing node_modules:**
```
npm install
```

**CSS not building:**
```bash
cd themes/blowfish
npm run build
# or for watch mode
npm run dev
```

**Port already in use:**
```bash
hugo server -p 2000  # Use different port
```

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

## Multilingual Support

This project supports multiple languages with language-specific content and configuration.

### Language Configuration

**Files:**
- `/config/_default/languages.en.toml` - English configuration
- `/config/_default/languages.de.toml` - German configuration
- Add more as needed: `languages.fr.toml`, `languages.es.toml`, etc.

### Language-Specific Content

Content files use language suffixes:

```
posts/
├── my-post/
│   ├── index.en.md    # English version
│   ├── index.de.md    # German version
│   └── featured.png
└── another-post/
    ├── index.en.md
    ├── index.de.md
    └── featured.png
```

### Language-Specific Menus

**Files:**
- `/config/_default/menus.en.toml` - English menu
- `/config/_default/menus.de.toml` - German menu

Menus automatically switch based on the user's language selection. The same `pageRef` values point to the appropriate language version.

### Language Switching

Users can switch languages through the language selector in the site navigation. The site automatically serves content in the selected language while maintaining the same URL structure with language codes:

- English: `/en/posts/my-post/`
- German: `/de/posts/my-post/`

---

## Tips & Best Practices

1. **Citations:** Always add `{{< bibliography >}}` at the end of posts that use citations
2. **Cross-references:** Use consistent numbering schemes (1, 2, 3 or 1.1, 1.2, 2.1, etc.)
3. **Figure captions:** Keep captions concise but descriptive
4. **Equations:** Use recognizable IDs like "einstein" or "pythag" for easy reference
5. **Multilingual:** Ensure all non-English content has corresponding translations
6. **Custom styling:** Use the alert's color parameters for emphasis instead of relying on colors alone

---

For more information about the Blowfish theme, visit: https://blowfish.page/
