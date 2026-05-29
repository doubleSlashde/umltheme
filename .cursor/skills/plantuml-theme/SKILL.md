---
name: plantuml-theme
description: Erstellt und pflegt PlantUML-Themes mit CSS-<style>-Blöcken und Legacy-skinparam. Nutzt https://plantuml.com/de/style als Autorität für Selektoren und Properties. Verwenden bei Theme-Dateien (doubleslash/, puml-theme-*, doubleslash-gen2.puml), skinparam, style-Tag, Corporate Theme, umltheme, Gen2/v3.
---

# PlantUML Theme (umltheme)

## Wann dieser Skill gilt

- Bearbeiten von `doubleslash/**/*.puml`, insbesondere `v3/puml-theme-*.puml` und `doubleslash-gen2.puml`
- Neue Styling-Regeln, Stereotyp-Klassen (`.external`, `.interface`), diagrammspezifische Overrides
- Abgleich Theme ↔ Style-Guide (`docs/style-guide/`)

## Autoritative Quelle (extern)

**Primär:** [PlantUML CSS Styles (DE)](https://plantuml.com/de/style)

Wenn Selektoren, Properties oder Diagrammtyp-Blöcke unklar sind:

1. `WebFetch` auf `https://plantuml.com/de/style` (englisch: `https://plantuml.com/style`)
2. Lokale Kurzreferenz: [reference.md](reference.md)
3. Offizielle Beispiele auf der Seite nachbauen und mit `examples/gen2/local_testing/` vergleichen

PlantUML positioniert `<style>` als Nachfolger von `skinparam` (deprecated). Neue Regeln **CSS-first**; Legacy-`skinparam` nur parallel pflegen, solange das Repo Legacy-Support dokumentiert.

## Theme bearbeiten — Workflow

```
1. Anforderung klassifizieren (global / diagrammspezifisch / Stereotyp / Legacy-only)
2. Betroffene Selektoren in reference.md oder plantuml.com/de/style nachschlagen
3. Änderung
4. Golden Samples: examples/gen2/local_testing/ rendern (light und dark)
5. Style-Guide + CHANGELOG bei Token-/Soll-Wert-Änderung
```

## Syntax-Konventionen (dieses Repo)

Im Repo **ohne Doppelpunkt** nach Property-Namen (PlantUML akzeptiert beides; bestehende Themes nutzen Leerzeichen):

```plantuml
<style>
  element {
    BackGroundColor #D7E9F4
    LineColor #00759E
  }
  sequenceDiagram {
    participant { Padding 16 16 }
    .external { BackGroundColor #F8F8F8 }
  }
</style>
```

Stereotyp-Styling: Klasse per `<<external>>` → Selektor `.external`

v3-Theme-Struktur (Kopfzeile → Legacy-skinparam → globales `<style>`):

```1:20:doubleslash/v3/puml-theme-light.puml
---
name: light
...
---
skinparam useBetaStyle false
...
<style>
  root { ... }
  element { ... }
  sequenceDiagram { ... }
</style>
```

## Property-Schnellwahl

| Ziel                 | Typische Selektoren / Properties                            |
| -------------------- | ----------------------------------------------------------- |
| Canvas               | `root` → `BackGroundColor`                                  |
| Alle Formen          | `element`                                                   |
| Pfeile global        | `arrow`                                                     |
| Sequence-Participant | `sequenceDiagram` → `participant`, `lifeLine` / `lifeline`  |
| Stereotyp            | `.stereotypeName` innerhalb des Diagramm-Blocks oder global |
| Klassen-Stereotyp    | `classDiagram` → `.mystyle` + `<<mystyle>>`                 |
| Gantt-Status         | `ganttDiagram` → `task` → `unstarted`, `undone`             |
| WBS-Tiefe            | `wbsDiagram` → `:depth(n)`                                  |

Vollständige Property-Liste: [reference.md](reference.md).

## Nicht tun

- Hardcoded-Hex außerhalb zentraler Token-Definition
- Nur light **oder** nur dark ändern ohne Gegenstück
- `skinparam useBetaStyle true` ohne Absprache (v3 nutzt `false`)
- Diagramm-Autoren-`.puml` mit Theme-Tokens überschreiben (Scope: Maintainer-Dateien unter `doubleslash/`)

## Zusätzliche Ressourcen

- [reference.md](reference.md) — PlantUML CSS (aus plantuml.com/de/style)
- [umltheme-project.md](umltheme-project.md) — Repo-Layout, SemVer, PR-Checkliste
- `docs/style-guide/theme-development.md` — Maintainer-Governance im Repo
