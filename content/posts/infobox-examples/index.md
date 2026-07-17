+++
date = '2026-07-16T23:45:00+02:00'
draft = false
title = 'Infobox and Callout Examples'
toc = true
tags = ["guide", "callouts", "infoboxes", "design"]
+++

# Infobox and Callout Styles in Blowfish

This post showcases the various ways to display emphasized content, special boxes, and callouts in the Blowfish theme. These are perfect for definitions, lemmas, theorems, warnings, tips, and other specialized content.

---

## 1. Lead Shortcode

The `lead` shortcode emphasizes introductory paragraphs or key concepts with larger, muted text.

{{< lead >}}
A lead paragraph stands out visually and is perfect for introducing important concepts or article summaries. It uses a larger font and neutral color to draw the reader's eye.
{{< /lead >}}

---

## 2. Alert Shortcode (Customizable Boxes)

The `alert` shortcode creates styled boxes with optional icons and custom colors. Perfect for definitions, lemmas, theorems, and special notices.

### Parameters

| Parameter | Description | Example |
|-----------|-------------|---------|
| `icon` | Font Awesome icon name | `icon="book"` |
| `cardColor` | Light mode background color | `cardColor="#e3f2fd"` |
| `cardColorDark` | Dark mode background color (auto-generated if omitted) | `cardColorDark="#1a2847"` |
| `iconColor` | Light mode icon color | `iconColor="#1976d2"` |
| `iconColorDark` | Dark mode icon color (auto-generated if omitted) | `iconColorDark="#64b5f6"` |
| `textColor` | Light mode text color | `textColor="#0d47a1"` |
| `textColorDark` | Dark mode text color (auto-generated if omitted) | `textColorDark="#e3f2fd"` |

**Note:** Dark mode colors are optional. If omitted, they are automatically generated as lighter/brighter variants of the light mode colors.

### Basic Alert

{{< alert >}}
This is a basic alert with the default warning icon and styling.
{{< /alert >}}

### Definition Box

{{< alert icon="book" cardColor="#e3f2fd" cardColorDark="#1e3a5f" iconColor="#1976d2" iconColorDark="#60a5fa" textColor="#0d47a1" textColorDark="#e0e7ff" >}}
**Definition:** A *metric space* is an ordered pair $(X, d)$ where $X$ is a set and $d: X \times X \to \mathbb{R}_{\geq 0}$ is a distance function satisfying:
1. $d(x, y) = 0 \iff x = y$ (identity of indiscernibles)
2. $d(x, y) = d(y, x)$ (symmetry)
3. $d(x, z) \leq d(x, y) + d(y, z)$ (triangle inequality)
{{< /alert >}}

### Lemma Box

{{< alert icon="lightbulb" cardColor="#f3e5f5" cardColorDark="#3f2555" iconColor="#7b1fa2" iconColorDark="#d8b4fe" textColor="#4a148c" textColorDark="#f3e5f5" >}}
**Lemma:** If $f: X \to Y$ is a continuous function between metric spaces, then for any open set $U \subseteq Y$, the preimage $f^{-1}(U)$ is open in $X$.
{{< /alert >}}

### Theorem Box

{{< alert icon="star" cardColor="#fff3e0" cardColorDark="#5a3a1a" iconColor="#e65100" iconColorDark="#fdba74" textColor="#bf360c" textColorDark="#fed7aa" >}}
**Theorem (Bolzano-Weierstrass):** Every bounded sequence in $\mathbb{R}^n$ has a convergent subsequence.

*Proof idea:* Use nested intervals and the compactness of closed bounded sets.
{{< /alert >}}

### Corollary Box

{{< alert icon="check" cardColor="#e8f5e9" cardColorDark="#1b4d2b" iconColor="#2e7d32" iconColorDark="#86efac" textColor="#1b5e20" textColorDark="#dcfce7" >}}
**Corollary:** A closed bounded subset of $\mathbb{R}^n$ is compact.
{{< /alert >}}

### Example Box

{{< alert icon="list" cardColor="#fce4ec" cardColorDark="#4a1c3a" iconColor="#c2185b" iconColorDark="#f472b6" textColor="#880e4f" textColorDark="#fce7f3" >}}
**Example:** Consider the metric space $(\mathbb{R}, d)$ where $d(x, y) = |x - y|$. The open ball $B_1(0) = (-1, 1)$ is the set of all points at distance less than 1 from 0.
{{< /alert >}}

---

## 3. Admonition Blockquotes

The blockquote syntax `> [!TYPE]` creates admonitions compatible with GitHub and Obsidian. This is the most flexible approach.

### GitHub-Compatible Types

> [!NOTE]
> **Note** boxes are for general information and clarifications.

> [!TIP]
> **Tip** boxes provide helpful suggestions and best practices.

> [!IMPORTANT]
> **Important** information that shouldn't be missed.

> [!WARNING]
> **Warning** boxes alert readers to potential pitfalls.

> [!CAUTION]
> **Caution** boxes indicate dangerous or destructive actions.

### Obsidian Extended Types

> [!ABSTRACT]
> A summary or overview of the main concepts discussed in this section.

> [!BUG]
> A known issue or bug in the system being described.

> [!EXAMPLE]
> An example demonstration of the concept.

> [!SUCCESS]
> A successful outcome or positive result.

> [!FAILURE]
> A failed outcome or negative result.

> [!QUESTION]
> Questions and frequently asked answers.

> [!QUOTE]
> A notable quote or citation.

### Collapsible Admonitions

Admonitions can be collapsible by using `+` (collapsed by default) or `-` (expanded by default).

> [!WARNING]+ Collapsible Warning
> This warning starts collapsed. Click to expand and read the details about potential issues.

> [!NOTE]- Expanded Note
> This note starts expanded by default and can be collapsed if needed.

### Custom Icons in Admonitions

You can specify custom icons using the `{icon="name"}` syntax:

> [!NOTE]
> Using a custom icon for this note.
{icon="sparkles"}

**Usage:**
```markdown
> [!NOTE]
> Your note text here.

> [!WARNING]+ Collapsible Title
> Content here
{icon="custom-icon-name"}
```

---

## 4. Specialized Content Examples

### Definition and Lemma with Admonitions

For a lighter, more integrated look, you can use admonitions for mathematical content:

> [!ABSTRACT] Definition: Continuity
> A function $f: X \to Y$ between metric spaces is *continuous at a point* $x_0 \in X$ if for every $\epsilon > 0$, there exists $\delta > 0$ such that:
> $$d_X(x, x_0) < \delta \implies d_Y(f(x), f(x_0)) < \epsilon$$

> [!IMPORTANT] Lemma: Compactness Preservation
> If $f: X \to Y$ is a continuous function and $X$ is compact, then $f(X)$ is compact.

> [!SUCCESS] Theorem: Intermediate Value
> If $f: [a, b] \to \mathbb{R}$ is continuous and $k$ is between $f(a)$ and $f(b)$, then there exists $c \in (a, b)$ such that $f(c) = k$.

### Proof Blocks

> [!EXAMPLE]
> **Proof:** Consider the set $S = \{x \in [a, b] : f(x) \leq k\}$. This set is closed and bounded, hence compact. By the extreme value theorem, $S$ achieves its maximum at some point $c \in [a, b]$...

### Counterexample

> [!BUG] Counterexample
> While every continuous function on a compact set is uniformly continuous, this does not hold for non-compact sets. For instance, $f(x) = x^2$ on $(0, \infty)$ is continuous but not uniformly continuous.

---

## 5. Quick Reference: Icon Options

When using alerts or custom icons, you can use Font Awesome icon names. Common choices for academic content:

| Content Type | Icon | Light Color | Dark Background | Dark Icon | Dark Text |
|---|---|---|---|---|---|
| Definition | `book` | #1976d2 | #1e3a5f | #60a5fa | #e0e7ff |
| Lemma | `lightbulb` | #7b1fa2 | #3f2555 | #d8b4fe | #f3e5f5 |
| Theorem | `star` | #e65100 | #5a3a1a | #fdba74 | #fed7aa |
| Corollary | `check` | #2e7d32 | #1b4d2b | #86efac | #dcfce7 |
| Example | `list` | #c2185b | #4a1c3a | #f472b6 | #fce7f3 |
| Proof | `pen-fancy` | #00796b | #1a4d45 | #7ee8c0 | #ccf8e8 |
| Remark | `circle-info` | #424242 | #2d2d2d | #a3a3a3 | #e5e5e5 |
| Exercise | `dumbbell` | #3f51b5 | #1e293b | #818cf8 | #e0e7ff |

---

## 6. Complete Color Palette: Light and Dark Modes

For consistent, readable styling across themes:

**Light Mode Background** → **Dark Mode Background** pairings:
- Light blue `#e3f2fd` → Dark blue `#1e3a5f`
- Light purple `#f3e5f5` → Dark purple `#3f2555`
- Light orange `#fff3e0` → Dark orange `#5a3a1a`
- Light green `#e8f5e9` → Dark green `#1b4d2b`
- Light pink `#fce4ec` → Dark pink `#4a1c3a`
- Light teal `#e0f2f1` → Dark teal `#1a4d45`
- Light gray `#f5f5f5` → Dark gray `#2d2d2d`
- Light indigo `#e8eaf6` → Dark indigo `#2d3748`

**Icon Colors** (should be bright in dark mode):
- Blue icon: Light `#1976d2` → Dark `#60a5fa`
- Purple icon: Light `#7b1fa2` → Dark `#d8b4fe`
- Orange icon: Light `#e65100` → Dark `#fdba74`
- Green icon: Light `#2e7d32` → Dark `#86efac`
- Red icon: Light `#c2185b` → Dark `#f472b6`
- Teal icon: Light `#00796b` → Dark `#7ee8c0`
- Gray icon: Light `#424242` → Dark `#a3a3a3`

**Text Colors** (should be very light in dark mode):
- Dark text: Light `#0d47a1` → Dark `#e0e7ff`
- Dark text: Light `#4a148c` → Dark `#f3e5f5`
- Dark text: Light `#bf360c` → Dark `#fed7aa`
- Dark text: Light `#1b5e20` → Dark `#dcfce7`

---

## Summary

| Component | Best For | Customizable |
|-----------|----------|--------------|
| **Lead** | Introductions, summaries | Limited (text size/color only) |
| **Alert** | Definitions, special cases, custom styling | High (colors, icons, text) |
| **Admonition** | Notes, tips, warnings, integrated content | Medium (icon via attribute) |

Choose **Alert** for maximum visual control and structured definitions, and **Admonition** for seamless integration with surrounding text and semantic meaning.
