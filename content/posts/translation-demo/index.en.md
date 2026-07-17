+++
date = '2026-07-17T12:00:00+02:00'
draft = false
title = 'Translation Demo'
description = 'A demonstration of how multilingual content works in Hugo'
toc = true
+++

Welcome to this translation demonstration! This post showcases how Hugo handles multilingual content with language-specific versions.

## What is Multilingual Support?

Hugo provides built-in support for creating content in multiple languages. Each language version can have its own URL path and independent content while sharing the same theme and structure.

## How It Works

The Blowfish theme uses language-specific file suffixes to organize translated content:
- `index.en.md` for English content
- `index.de.md` for German content

Each file contains the same frontmatter structure but with translated text.

## Key Features

### Automatic Language Detection
Hugo automatically detects the language based on the file suffix and serves the appropriate version to users based on their language preference.

### Independent URLs
Each language version gets its own URL:
- English: `/en/posts/translation-demo/`
- German: `/de/posts/translation-demo/`

### Language Switching
Users can easily switch between different language versions of the same content through language selector links in the site navigation.

## Benefits

1. **Better User Experience** - Users read content in their preferred language
2. **SEO Friendly** - Search engines can properly index and rank each language version
3. **Organized Content** - All versions of a post stay together in the same folder
4. **Easy Maintenance** - Add or update translations without reorganizing your content structure

## Getting Started

To create multilingual content:
1. Create your main content as `index.en.md` (or your default language)
2. Create translated versions as `index.de.md`, `index.fr.md`, etc.
3. Update your language configuration in `config/_default/languages.*.toml`
4. Use the same folder for all language versions

Check the German version of this post for a complete translation example!


## Figure Test

{{< figdef num="1" src="./featured.png" caption="The organizational structure of the system." >}}

Mare aliquid cultosque Delius in altera putat soli nostrae sternere vate,
praestiteris canes. Erat ipse, **de** non tam capiti, pharetra nusquam furiisque
revertitur. Monuit hostem institerat cervice adsumpserat socios solet ore tecta
coniuge, alios erit Althaea nullus inmunitamque Thoactes diu et Melaneus?


Reference for {{< fig "1" >}}.