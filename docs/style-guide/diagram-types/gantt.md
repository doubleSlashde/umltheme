# Gantt-Diagramme

Gantt-Diagramme modellieren die **zeitliche Planung** von Aufgaben, Meilensteinen und Abhaengigkeiten in einem Projektplan. Sie nutzen die [Gantt-Syntax](https://plantuml.com/de/gantt-diagram) (`[Task] lasts N days`, `[Task] starts at …`, Meilensteine, Notizen). Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer Gantt-Elemente.

**Organismus:** `<style> ganttDiagram`, Selektoren `task`, `timeline`, `milestone`, `note`, `arrow`, `separator`; Autoren-Direktiven fuer Wochenend-Farben und `printscale`.

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

<!-- prettier-ignore-start -->
!!! note "To-be-Design"
    Die Tabellen auf dieser Seite beschreiben den **Soll-Standard (to-be)**. Die Umsetzung erfolgt in [`doubleslash/v3/puml-theme-gantt-mindmap-light.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/v3/puml-theme-gantt-mindmap-light.puml) und [`doubleslash/v3/puml-theme-gantt-mindmap-dark.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/v3/puml-theme-gantt-mindmap-dark.puml) — jeweils mit modusabhaengigen Farben (Light und Dark).
<!-- prettier-ignore-end -->

**Golden Samples:**

- [`gantt.v3-theme-light.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/gantt.v3-theme-light.puml)
- [`gantt.v3-theme-dark.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/gantt.v3-theme-dark.puml)
- [`gantt.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/gantt.puml) (Gen2)
- [`projectplan.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/projectplan.puml) (Gen2)

=== "light"

    ```puml
    @startgantt v3-theme-light-gantt
    !theme gantt-mindmap-light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    skinparam RoundCorner 6
    saturday are colored in #F8F8F8
    sunday are colored in #F8F8F8
    printscale weekly zoom 4

    title UML Theme v3 — Light Mode Gantt Smoke Test

    Project starts 2026-06-02

    [Prototype Design] lasts 7 days
    [Functional Testing] lasts 4 days
    [Performance Testing] lasts 4 days
    [Documentation] lasts 3 days

    [Functional Testing] starts at [Prototype Design]'s end
    [Performance Testing] starts at [Prototype Design]'s end
    [Documentation] starts at [Functional Testing]'s end

    [Functional Testing] is 0% complete
    [Performance Testing] is 80% complete
    [Documentation] is 100% complete

    -- Milestone --
    [Release 1.0] happens at [Documentation]'s end
    @endgantt
    ```

=== "dark"

    ```puml
    @startgantt v3-theme-dark-gantt
    !theme gantt-mindmap-dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    skinparam RoundCorner 6
    saturday are colored in #2D2D2D
    sunday are colored in #2D2D2D
    printscale weekly zoom 4

    title UML Theme v3 — Dark Mode Gantt Smoke Test

    Project starts 2026-06-02

    [Prototype Design] lasts 7 days
    [Functional Testing] lasts 4 days
    [Performance Testing] lasts 4 days
    [Documentation] lasts 3 days

    [Functional Testing] starts at [Prototype Design]'s end
    [Performance Testing] starts at [Prototype Design]'s end
    [Documentation] starts at [Functional Testing]'s end

    [Functional Testing] is 0% complete
    [Performance Testing] is 80% complete
    [Documentation] is 100% complete

    -- Milestone --
    [Release 1.0] happens at [Documentation]'s end
    @endgantt
    ```

## Geltende Werte

### Geltende Atome & Molekuele

<!-- markdownlint-disable MD060 -->

| Mechanismus              | Soll-Wert (Light)                                                                            | Soll-Wert (Dark)                                                                                  |
| ------------------------ | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Task (Standard)          | Hintergrund Blau-Tint `#D7E9F4`; Rahmen Blau-Tint; Label `#000000`; **12 pt**; Padding **3** | Hintergrund Dark Blau-Grau `#22303C`; Rahmen `#22303C`; Label `#D7E9F4`; **12 pt**; Padding **3** |
| Task (`unstarted`)       | Hintergrund Super Light Grey `#F8F8F8`                                                       | Hintergrund Dark Surface `#2D2D2D`                                                                |
| Task (`undone` / offen)  | Hintergrund Invalid Red `#C63328`; Label `#FFFFFF`                                           | Hintergrund Invalid Red Dark `#E85F63`; Label `#FFFFFF`                                           |
| Task (`closed` / fertig) | Hintergrund Valid Green `#6B9714`; Label `#FFFFFF`                                           | Hintergrund Valid Green Dark `#B9D478`; Label `#000000`                                           |
| Timeline                 | Hintergrund Super Light Grey `#F8F8F8`; Label `#000000`; **12 pt**                           | Hintergrund Dark Surface `#2D2D2D`; Label `#D7E9F4`; **12 pt**                                    |
| Milestone                | Akzent Primary `#00759E`; LineThickness **15**; Label `#000000`; **12 pt**                   | Akzent Bright Sky `#77DDFF`; LineThickness **15**; Label `#D7E9F4`; **12 pt**                     |
| Note                     | Label `#000000`; **10 pt**; Rahmen Light Grey `#C6C6C6`                                      | Label `#D7E9F4`; **10 pt**; Rahmen Medium Light Grey `#B6B6B6`                                    |
| Abhaengigkeit (`arrow`)  | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **12 pt**               | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **12 pt**                    |
| Separator                | Linie Medium Grey `#7A7A7A`; Staerke **1**; Label `#000000`; **12 pt**                       | Linie Medium Grey `#7A7A7A`; Staerke **1**; Label `#D7E9F4`; **12 pt**                            |
| Wochenende (Sa/So)       | Hintergrund Super Light Grey `#F8F8F8` (Autoren-Direktive)                                   | Hintergrund Dark Surface `#2D2D2D` (Autoren-Direktive)                                            |

Hinweis: Gantt-Tasks erben die Blau-Tint-Fuellung der Standard-Formen. Status-Farben (`unstarted`, `undone`, `closed`) nutzen semantische Container- bzw. Valid-/Invalid-Tokens, damit Fortschritt und Verzug auf einen Blick erkennbar sind.

### Element-Typen (Syntax)

| Zweck                  | Empfohlenes Element              | Hinweis                               |
| ---------------------- | -------------------------------- | ------------------------------------- |
| Aufgabe / Arbeitspaket | `[Name] lasts N days`            | Standard-Task; Dauer in Tagen         |
| Abhaengigkeit          | `[B] starts at [A]'s end`        | Sequenzielle oder parallele Planung   |
| Fortschritt            | `[Task] is N% complete`          | Steuert `undone`/`closed`-Darstellung |
| Meilenstein            | `[Name] happens at [Task]'s end` | Wird als `milestone` gerendert        |
| Phasentrenner          | `-- Label --`                    | Wird als `separator` gerendert        |
| Erlaeuterung           | `note bottom` / `note top`       | Erbt `ganttDiagram` → `note`-Styling  |
| Projektstart           | `Project starts YYYY-MM-DD`      | Setzt den Zeitachsen-Start            |

### Typografie

| Eigenschaft                | Soll-Wert                            | Geltung                          |
| -------------------------- | ------------------------------------ | -------------------------------- |
| **FontName**               | **Helvetica**                        | Task, Timeline, Arrow, Separator |
| **FontSize** (Task-Label)  | **12 pt**                            | Standard-Fliesstext              |
| **FontSize** (Note)        | **10 pt**                            | Gantt-Notizen                    |
| **FontSize** (Timeline)    | **12 pt**                            | Datumsachse                      |
| **FontColor** (Task-Label) | Element-Labels `#000000` / `#D7E9F4` | Beschriftung auf Task-Balken     |
| **FontStyle** (Milestone)  | normal                               | Meilenstein-Beschriftung         |

## Konfiguration

Gantt-Diagramme nutzen das dedizierte v3-Theme-Bundle `puml-theme-gantt-mindmap-light.puml` bzw. `puml-theme-gantt-mindmap-dark.puml` (`!theme gantt-mindmap-light` / `!theme gantt-mindmap-dark`). Globale Typografie- und Canvas-Defaults aus dem Haupt-Theme (`puml-theme-light` / `puml-theme-dark`) gelten hier nicht — das Bundle enthaelt eigene `root`-, `element`- und `ganttDiagram`-Regeln.

### [SG-46] Gantt `<style>`-Block

**Ebene:** Stil / Rendering  
**Geltung:** Gantt

**Regel:** Gantt-Styling **MUSS** ueber `<style> ganttDiagram { … }` in `puml-theme-gantt-mindmap-*.puml` erfolgen — nicht ueber verstreute `skinparam`-Eintraege (Ausnahme: siehe [SG-48](#sg-48-gantt-autoren-direktiven)).

```plantuml
<style>
ganttDiagram {
  task {
    BackGroundColor #D7E9F4
    unstarted { BackGroundColor #F8F8F8 }
    undone { BackGroundColor #C63328 }
  }
}
</style>
```

### [SG-47] `@startgantt`-Wrapper

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Gantt

**Regel:** Gantt-Quellen **MUSSEN** mit `@startgantt` … `@endgantt` umschlossen sein.

```plantuml
@startgantt
!theme gantt-mindmap-light from .../doubleslash/v3/
[Task] lasts 3 days
@endgantt
```

### [SG-48] Gantt-Autoren-Direktiven

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Gantt

**Regel:** Gantt-spezifische Layout-Direktiven **SOLLTEN** direkt in der Autoren-Datei gesetzt werden (nicht im `puml-theme-gantt-mindmap-*.puml`-Bundle):

| Direktive                 | Soll-Wert (Light) | Soll-Wert (Dark) |
| ------------------------- | ----------------- | ---------------- |
| `skinparam RoundCorner`   | **6**             | **6**            |
| `saturday are colored in` | `#F8F8F8`         | `#2D2D2D`        |
| `sunday are colored in`   | `#F8F8F8`         | `#2D2D2D`        |
| `printscale weekly zoom`  | **4**             | **4**            |

Der abweichende `RoundCorner`-Wert **6** (statt globalem **16**) ist die einzige dokumentierte Gantt-Ausnahme — siehe [Design Tokens — Abstaende & Form](../design-tokens.md#abstande--form).

**Siehe auch:** [Theme usage — Gantt](../../theme-usage.md#gantt-diagrams)
