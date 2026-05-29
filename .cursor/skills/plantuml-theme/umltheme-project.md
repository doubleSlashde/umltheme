# umltheme — Projekt-Konventionen

Repository: `doubleSlashde/umltheme`. Dieser Skill ergänzt [PlantUML CSS](https://plantuml.com/de/style) um team-interne Regeln.

## Dateien & Rollen

| Pfad                                   | Rolle                                                             |
| -------------------------------------- | ----------------------------------------------------------------- |
| `doubleslash/v3/puml-theme-light.puml` | Gen3 CSS-Theme Light (Hauptreferenz für globales `<style>`)       |
| `doubleslash/v3/puml-theme-dark.puml`  | Gen3 CSS-Theme Dark — **immer** parallel zu Light                 |
| `doubleslash/doubleslash-gen2.puml`    | Gen2 Legacy + Moleküle (`!startsub`), Variablen, großes `<style>` |
| `doubleslash/padding-apply-css.puml`   | Referenz CSS-Padding                                              |
| `examples/gen2/local_testing/`         | Golden Samples zum visuellen Diff                                 |
| `docs/style-guide/`                    | Verbindliche Soll-Werte für Autoren                               |

## Atomic Design (Änderungsentscheid)

```txt
Neues Styling?
├─ Neue Farbe?              → Token in Gen2 / colors
├─ Neues Element über Typen? → !startsub / Stereotyp (Gen2)
├─ Nur ein Diagrammtyp?     → Organismus (!startsub oder <style>-Block)
├─ Nur System/Gantt?        → Bundle-Override
└─ Nur Doku?                → docs/style-guide/
```

## Verbindliche Soll-Werte (Auszug)

Vollständig: `docs/style-guide/global-defaults.md`, `design-tokens.md`.

| Bereich         | Light (typ.)         | Dark (typ.) |
| --------------- | -------------------- | ----------- |
| Canvas          | `#FFFFFF`            | `#15202B`   |
| Element-Fill    | `#D7E9F4`            | `#22303C`   |
| Container/Group | `#F8F8F8`            | `#2D2D2D`   |
| Element-Rahmen  | `#00759E`            | `#77DDFF`   |
| Pfeile          | `#7A7A7A`, Dicke 1.5 | gleich      |
| RoundCorner     | 16 (Gantt: 6)        | 16          |
| Shadowing       | 0                    | 0           |
| FontName        | Helvetica            | Helvetica   |

Interface-Stereotyp: `#00A5E1`, `LineThickness` 2 (`.interface` in v3).

## PR-Checkliste (Theme-Maintainer)

- [ ] Token in `design-tokens.md` dokumentiert
- [ ] Betroffene `diagram-types/*.md` aktualisiert
- [ ] `examples/gen2/` light **und** dark gerendert, visuell geprüft
- [ ] PlantUML ≥ 1.2026.3 + Legacy getestet (Padding)
- [ ] `CHANGELOG.md`
- [ ] Keine neuen Hardcoded-Hex außerhalb Token-Definition
- [ ] Legacy-Includes funktionieren weiter

## SemVer (Breaking)

| Änderung                           | Version |
| ---------------------------------- | ------- |
| Bugfix, Kontrast                   | Patch   |
| Neues Stereotyp, neues `!startsub` | Minor   |
| Token-Umbenennung, Pfad-Entfernung | Major   |
| Entfernung Legacy-Root-Themes      | Major   |

## Include-Patterns für Autoren (nicht Theme-Dateien)

```plantuml
!include https://raw.githubusercontent.com/doubleSlashde/umltheme/main/doubleslash/doubleslash-gen2.puml
```

Autoren **dürfen** lokales `<style>` nur für diagrammspezifisches Padding/Layout — nicht für Corporate-Farben (Style-Guide `authoring-rules.md`).

## Theme-Metadaten (YAML-Kopf)

v3-Dateien beginnen mit PlantUML-Theme-Header (`name`, `display_name`, `version`, `inspiration: https://plantuml.com/de/style`). Bei Releases Version und CHANGELOG synchron halten.
