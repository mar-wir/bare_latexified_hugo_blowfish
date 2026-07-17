+++
date = '2026-07-17T12:00:00+02:00'
draft = false
title = 'Übersetzungs-Demo'
description = 'Eine Demonstration, wie mehrsprachige Inhalte in Hugo funktionieren'
toc = true
+++

Willkommen zu dieser Übersetzungs-Demo! Dieser Beitrag zeigt, wie Hugo mehrsprachige Inhalte mit sprachspezifischen Versionen verarbeitet.

## Was ist Mehrsprachige Unterstützung?

Hugo bietet integrierte Unterstützung für die Erstellung von Inhalten in mehreren Sprachen. Jede Sprachversion kann seinen eigenen URL-Pfad und unabhängigen Inhalt haben, während es das gleiche Theme und die gleiche Struktur verwendet.

## Wie es funktioniert

Das Blowfish-Theme verwendet sprachspezifische Dateiendungen zum Organisieren von übersetzten Inhalten:
- `index.en.md` für englische Inhalte
- `index.de.md` für deutsche Inhalte

Jede Datei enthält die gleiche Frontmatter-Struktur, aber mit übersetztem Text.

## Wichtigste Merkmale

### Automatische Spracherkennung
Hugo erkennt die Sprache automatisch anhand des Dateiendzeichens und stellt Benutzern die entsprechende Version basierend auf ihrer Spracheinstellung bereit.

### Unabhängige URLs
Jede Sprachversion erhält ihre eigene URL:
- Englisch: `/en/posts/translation-demo/`
- Deutsch: `/de/posts/translation-demo/`

### Sprachauswahl
Benutzer können leicht zwischen verschiedenen Sprachversionen desselben Inhalts über Sprachauswahllinks in der Sitenavigation wechseln.

## Vorteile

1. **Bessere Benutzererfahrung** - Benutzer lesen Inhalte in ihrer bevorzugten Sprache
2. **SEO-freundlich** - Suchmaschinen können jede Sprachversion richtig indexieren und bewerten
3. **Organisierte Inhalte** - Alle Versionen eines Beitrags bleiben im selben Ordner zusammen
4. **Leichte Wartung** - Fügen Sie Übersetzungen hinzu oder aktualisieren Sie diese, ohne Ihre Inhaltsstruktur zu reorganisieren

## Erste Schritte

Um mehrsprachige Inhalte zu erstellen:
1. Erstellen Sie Ihren Hauptinhalt als `index.en.md` (oder Ihre Standardsprache)
2. Erstellen Sie übersetzte Versionen als `index.de.md`, `index.fr.md` usw.
3. Aktualisieren Sie Ihre Sprachkonfiguration in `config/_default/languages.*.toml`
4. Verwenden Sie den gleichen Ordner für alle Sprachversionen

Schauen Sie sich die englische Version dieses Beitrags an, um ein vollständiges Übersetzungsbeispiel zu sehen!

## Gleichungen Test

{{< equation "1" >}}
\dot{\mathbf{x}}_i = (1 - S_i) \big[ -\Gamma (\mathbf{x}_i - \mathbf{x}_i^{(0)}) \big] + S_i \big[ \mathbf{K}_{snap} (\boldsymbol{\xi}_{winner} - \mathbf{x}_i) \big]
{{< /equation >}}

Mare aliquid cultosque Delius in altera putat soli nostrae sternere vate,
praestiteris canes. Erat ipse, **de** non tam capiti, pharetra nusquam furiisque
revertitur. Monuit hostem institerat cervice adsumpserat socios solet ore tecta
coniuge, alios erit Althaea nullus inmunitamque Thoactes diu et Melaneus?


Referenz zur {{< eq "1" >}}.

## Abbildungen Test

{{< figdef num="1" src="featured.de.png" caption="The organizational structure of the system." >}}

Mare aliquid cultosque Delius in altera putat soli nostrae sternere vate,
praestiteris canes. Erat ipse, **de** non tam capiti, pharetra nusquam furiisque
revertitur. Monuit hostem institerat cervice adsumpserat socios solet ore tecta
coniuge, alios erit Althaea nullus inmunitamque Thoactes diu et Melaneus?


Referenz zur {{< fig "1" >}}.