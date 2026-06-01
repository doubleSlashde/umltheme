# Mindmap & WBS

Mindmaps und Work-Breakdown-Structures (WBS) modellieren **hierarchische Wissens- und Projektstrukturen** als Baumdiagramme. Mindmaps eignen sich fuer Brainstorming und Themencluster; WBS fuer Arbeitspakete und Projektzerlegung. Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer beide Diagrammtypen.

**Organismus:** `<style> mindmapDiagram`, `<style> wbsDiagram` — Selektoren `node`, `rootNode`, `leafNode`, `arrow`; WBS zusaetzlich `:depth(n)` und Stereotyp-Klassen.

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

<!-- prettier-ignore-start -->
!!! note "To-be-Design"
    Die Tabellen auf dieser Seite beschreiben den **Soll-Standard (to-be)**. Die Umsetzung erfolgt in [`doubleslash/v3/puml-theme-light.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/v3/puml-theme-light.puml) und [`doubleslash/v3/puml-theme-dark.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/v3/puml-theme-dark.puml) — jeweils mit modusabhaengigen Farben (Light und Dark).
<!-- prettier-ignore-end -->

**Golden Samples:**

- [`mindmap.v3-theme-light.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/mindmap.v3-theme-light.puml)
- [`mindmap.v3-theme-dark.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/mindmap.v3-theme-dark.puml)
- [`wbs.v3-theme-light.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/wbs.v3-theme-light.puml)
- [`wbs.v3-theme-dark.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/wbs.v3-theme-dark.puml)
- [`mindmap.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/mindmap.puml) (Gen2)
- [`wbs.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/wbs.puml) (Gen2)

=== "light"

    ```puml
    @startmindmap v3-theme-light-mindmap
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    title UML Theme v3 — Light Mode Mindmap Smoke Test

    * Renovation project
    ** Planning
    *** Budget & deadlines
    ** Execution
    *** Team coordination
    @endmindmap
    ```

=== "dark"

    ```puml
    @startmindmap v3-theme-dark-mindmap
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    title UML Theme v3 — Dark Mode Mindmap Smoke Test

    * Renovation project
    ** Planning
    *** Budget & deadlines
    ** Execution
    *** Team coordination
    @endmindmap
    ```

## Geltende Werte

### Mindmap — Geltende Atome & Molekuele

<!-- markdownlint-disable MD060 -->

| Mechanismus          | Soll-Wert (Light)                                                                                      | Soll-Wert (Dark)                                                                              |
| -------------------- | ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| Knoten (`node`)      | Hintergrund Blau-Tint `#D7E9F4`; kein Rahmen (transparent); Label `#000000`; **12 pt**; Padding **10** | Hintergrund Dark Blau-Grau `#22303C`; kein Rahmen; Label `#D7E9F4`; **12 pt**; Padding **10** |
| Wurzel (`rootNode`)  | Hintergrund Primary Cyan `#00A5E1`; kein Rahmen; Label `#FFFFFF`; **bold**; **12 pt**                  | Hintergrund Primary Cyan `#00A5E1`; kein Rahmen; Label `#FFFFFF`; **bold**; **12 pt**         |
| Blatt (`leafNode`)   | Hintergrund Canvas `#FFFFFF`; kein Rahmen; Label `#000000`; **11 pt**; Padding **5**                   | Hintergrund Dark Surface `#2D2D2D`; kein Rahmen; Label `#D7E9F4`; **11 pt**; Padding **5**    |
| Verbindung (`arrow`) | Linie Medium Grey `#7A7A7A`; Staerke **1.5**                                                           | Linie Medium Grey `#7A7A7A`; Staerke **1.5**                                                  |

Hinweis: Mindmap-Knoten haben **keinen sichtbaren Rahmen** (`LineColor transparent`, `LineThickness 0`) — die Hierarchie wird allein ueber Hintergrundtints und Verbindungslinien lesbar.

### WBS — Geltende Atome & Molekuele

| Mechanismus          | Soll-Wert (Light)                                                                                    | Soll-Wert (Dark)                                                                                  |
| -------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Knoten (`node`)      | Hintergrund Blau-Tint `#D7E9F4`; Rahmen Primary `#00759E`; Staerke **1**; Label `#000000`; **12 pt** | Hintergrund Dark Blau-Grau `#22303C`; Rahmen Bright Sky `#77DDFF`; Staerke **1**; Label `#D7E9F4` |
| Wurzel (`rootNode`)  | Hintergrund Primary Cyan `#00A5E1`; Rahmen Primary `#00759E`; Label `#FFFFFF`; **bold**              | Hintergrund Primary Cyan `#00A5E1`; Rahmen Bright Sky `#77DDFF`; Label `#FFFFFF`; **bold**        |
| Blatt (`leafNode`)   | Hintergrund Canvas `#FFFFFF`; Rahmen Primary `#00759E`; Label `#000000`; **11 pt**                   | Hintergrund Dark Surface `#2D2D2D`; Rahmen Bright Sky `#77DDFF`; Label `#D7E9F4`; **11 pt**       |
| Verbindung (`arrow`) | Linie Medium Grey `#7A7A7A`; Staerke **1.5**                                                         | Linie Medium Grey `#7A7A7A`; Staerke **1.5**                                                      |

Hinweis: WBS unterscheidet sich von Mindmap durch **sichtbare Primary-Rahmen** an allen Knoten — das unterstreicht die formale Projektstruktur.

### Element-Typen (Syntax)

| Zweck                    | Mindmap                    | WBS                        | Hinweis                                        |
| ------------------------ | -------------------------- | -------------------------- | ---------------------------------------------- |
| Wurzelknoten             | `* Thema`                  | `* Projekt`                | Ein Stern = oberste Ebene                      |
| Unterebene               | `**`, `***`, …             | `**`, `***`, …             | Stern-Anzahl = Tiefe                           |
| Stereotyp / Klassenstyle | `<<stereotype>>` am Knoten | `<<stereotype>>` am Knoten | CSS-Selektor `.stereotypeName` im `wbsDiagram` |
| Tiefenstyling (WBS)      | —                          | `:depth(n) { … }` im Theme | Optionale Ueberschreibung pro Hierarchieebene  |

### Typografie

| Eigenschaft                     | Soll-Wert                            | Geltung                             |
| ------------------------------- | ------------------------------------ | ----------------------------------- |
| **FontSize** (Knoten-Label)     | **12 pt**                            | `node`, `rootNode`                  |
| **FontSize** (Blatt-Label)      | **11 pt**                            | `leafNode`                          |
| **FontColor** (Standard-Knoten) | Element-Labels `#000000` / `#D7E9F4` | Beschriftung auf Blau-Tint-Fuellung |
| **FontColor** (Wurzel)          | `#FFFFFF`                            | Kontrast auf Primary Cyan `#00A5E1` |
| **FontStyle** (Wurzel)          | **bold**                             | Wurzelknoten hervorheben            |

## Konfiguration

### [SG-49] Wrapper-Direktiven

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Mindmap & WBS

**Regel:** Mindmaps **MUSSEN** `@startmindmap` … `@endmindmap`; WBS **MUSS** `@startwbs` … `@endwbs` nutzen.

```plantuml
@startmindmap
!theme light from .../doubleslash/v3/
* Thema
** Unterthema
@endmindmap
```

```plantuml
@startwbs
!theme light from .../doubleslash/v3/
* Projekt
** Phase 1
*** Arbeitspaket
@endwbs
```

### [SG-50] Mindmap vs. WBS — Rahmen

**Ebene:** Stil / Rendering  
**Geltung:** Mindmap & WBS

**Regel:** Mindmap-Knoten **SOLLTEN** rahmenlos gerendert werden (`LineColor transparent`). WBS-Knoten **SOLLTEN** einen Primary-Rahmen tragen (`LineColor` `#00759E` / `#77DDFF`, `LineThickness 1`). Keine Inline-Farben in Autoren-Diagrammen — das Theme liefert die Defaults.

### [SG-51] WBS-Tiefen- und Stereotyp-Styling

**Ebene:** Stil / Rendering  
**Geltung:** WBS

**Regel:** Optionale Tiefen- oder Stereotyp-Ueberschreibungen **DUERFEN** im Theme unter `wbsDiagram` definiert werden — nach dem Muster der [PlantUML CSS Style-Spezifikation](https://plantuml.com/en/style):

```plantuml
<style>
wbsDiagram {
  :depth(1) {
    BackGroundColor #FFFFFF
  }
  .americaStyle * {
    FontColor red
    :depth(2) {
      BackGroundColor #D7E9F4
    }
  }
}
</style>
```

Autoren **SOLLTEN** Stereotyp-Klassen nur bei fachlicher Notwendigkeit setzen (`<<americaStyle>>` am Knoten).

**Siehe auch:** [Theme usage — Mindmap & WBS](../../theme-usage.md)
