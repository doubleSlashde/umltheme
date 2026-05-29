# Barrierefreiheit & Export

Kontrast, Lesbarkeit und Export-Anforderungen für doubleSlash PlantUML-Diagramme.

## Kontrast (WCAG AA)

Ziel: **mindestens WCAG 2.1 Level AA** (4.5:1 für normalen Text) wo prüfbar.

| Token-Paar (Light)        | Vordergrund           | Hintergrund           | Einschätzung         |
| ------------------------- | --------------------- | --------------------- | -------------------- |
| Body-Text                 | `$FGCOLOR` `#515151`  | `$PUML_BGCOLOR` white | ✅ ausreichend       |
| Class auf `$DS_LIGHTBLUE` | `$BLACK`              | `#D7E9F4`             | ✅ ausreichend       |
| Code-Level C4             | `$WHITE`              | `$CODE_BG` `#84999F`  | ✅ geprüft in v2.0.0 |
| Orange Warning-Text       | `$WARNING_TEXT` white | `$WARNING` `#DB6A00`  | ✅ Theme-Default     |

| Token-Paar (Dark) | Vordergrund                  | Hintergrund               | Einschätzung         |
| ----------------- | ---------------------------- | ------------------------- | -------------------- |
| Body-Text         | `$FGCOLOR` `#FFFFFF`         | `$PUML_BGCOLOR` `#1E1E1E` | ✅ ausreichend       |
| Participant       | `$BLACK` auf `$DS_LIGHTBLUE` | Dark-Tint `#2A5B7A`       | ⚠️ prüfen bei Export |

!!! warning "Mindmap/WBS Dark-Mode"
Hardcoded Light-Farben brechen Kontrast auf dunklem Hintergrund — siehe [Anti-Patterns](anti-patterns.md#ap-02-hardcoded-style-bloecke).

## Design-Regeln für Lesbarkeit

### [SG-58] Keine Schattierung

**Ebene:** Atom  
**Geltung:** Global  
**Status:** ✅ implementiert

**Regel:** `shadowing false` **MUSS** aktiv bleiben — Schatten reduzieren Kontrast und Druckqualität.

### [SG-59] Mindest-Schriftgrößen

**Ebene:** Atom  
**Geltung:** Global  
**Status:** ✅ implementiert

**Regel:** Body **MUSS** ≥ 11 pt sein; Titel 28 pt; Notes 11 pt.

## Transparenter Hintergrund vs. `$PUML_BGCOLOR`

| Modus                               | Verhalten                               |
| ----------------------------------- | --------------------------------------- |
| `$PUML_BGCOLOR = white` / `#1E1E1E` | Undurchsichtiger Export-Hintergrund     |
| Transparent (CLI `-transparent`)    | `!assume transparent light/dark` greift |

**Regel:** Für MkDocs/PDF **SOLL** undurchsichtiger Hintergrund genutzt werden — bessere Konstanz mit Seitenhintergrund.

**Implementierung:** `!assume transparent light/dark` in `doubleslash-gen2.puml` Z. 137, 179

## Export & Druck

| Parameter       | Wert      | Zweck                       |
| --------------- | --------- | --------------------------- |
| `skinparam dpi` | 100       | Balance Größe/Schärfe       |
| `roundcorner`   | 16        | Weiche Ecken, drucktauglich |
| Vektor (SVG)    | bevorzugt | Skalierung in MkDocs/PDF    |

### [SG-60] SVG für Dokumentation

**Ebene:** Template  
**Geltung:** MkDocs  
**Status:** ✅ implementiert

**Regel:** Diagramme in MkDocs **SOLLTEN** als SVG gerendert werden (`mkdocs_puml`-Plugin).

```yaml
plugins:
  - plantuml:
      puml_url: https://www.plantuml.com/plantuml/
```

**Siehe auch:** [Theme usage — MkDocs](../theme-usage.md#consumption-from-mkdocs-mkdocs_puml)

## Outline-Modus für Präsentation

`$PUML_OUTLINE = "true"` vor Include:

- Füllfarben → Hintergrund
- Rahmen/Text in Light-Varianten der Semantik-Farben

Geeignet für Projektoren und Schwarz-Weiß-Druck.

## Tooling

| Tool                         | Empfehlung                                    |
| ---------------------------- | --------------------------------------------- |
| VS Code + PlantUML Extension | Lokale Vorschau (<kbd>Alt</kbd>+<kbd>D</kbd>) |
| PlantUML JAR ≥ 1.2026.3      | CSS-Padding-Pfad testen                       |
| PlantUML JAR Legacy          | skinparam-Fallback testen                     |
| `mkdocs serve`               | Docs-Build inkl. gerenderter Diagramme        |
