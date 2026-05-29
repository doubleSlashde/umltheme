# Activity-Diagramme

Activity-Diagramme modellieren die **Ablauf- und Prozesssicht**: Aktionen, ihre Reihenfolge, Entscheidungen, parallele Pfade und die Zustaendigkeit (Swimlanes / Partitions). Sie nutzen die [Activity-Beta-Syntax](https://plantuml.com/de/activity-diagram-beta) (`start`, `:Aktion;`, `if/else`, `repeat`, `fork`, `|Swimlane|`). Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer Activity-Elemente.

**Organismus:** `:Aktion;` (Aktionsknoten), `diamond` (Entscheidungen aus `if`/`repeat`/`while`), `start` / `stop` / `end` (Start-/End-Knoten), `fork`/`join` (Synchronisationsbalken), `partition` (Gruppierung), `swimlane` (Verantwortungsspalten ueber `|Name|`).

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

**Golden Samples:**

- [`activity_model.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/activity_model.puml)
- [`piprocess.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/piprocess.puml)

=== "light"

    ```puml
    @startuml activitymodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    title Activity-Diagramm

    |Swimlane 1|
    start
    :Aktion 1;
    :Aktion 2;
    note right
    Diese Notiz erlaeutert
    den Zwischenzustand
    end note

    |Swimlane 2|
    if (Alles OKAY?) then (nur zum Teil)
      :do more research;
    else (Ja)
      :do action;
    endif

    |Swimlane 1|
    partition Abschluss {
      :final execution;
    }
    stop
    @enduml
    ```

=== "dark"

    ```puml
    @startuml activitymodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    title Activity-Diagramm

    |Swimlane 1|
    start
    :Aktion 1;
    :Aktion 2;
    note right
    Diese Notiz erlaeutert
    den Zwischenzustand
    end note

    |Swimlane 2|
    if (Alles OKAY?) then (nur zum Teil)
      :do more research;
    else (Ja)
      :do action;
    endif

    |Swimlane 1|
    partition Abschluss {
      :final execution;
    }
    stop
    @enduml
    ```

## Geltende Werte

### Geltende Atome & Molekuele

<!-- markdownlint-disable MD060 -->

| Mechanismus                         | Soll-Wert (Light)                                                                                                      | Soll-Wert (Dark)                                                                                                          |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Aktion (`:Text;`)                   | Hintergrund Blau-Tint `#D7E9F4`; BorderThickness 0; RoundCorner 16; Label Element-Labels `#000000`                     | Hintergrund Dark Blau-Grau `#22303C`; BorderThickness 0; RoundCorner 16; Label Element-Labels `#D7E9F4`                   |
| Entscheidung (`diamond`)            | Hintergrund Primary Cyan `#00A5E1`; Rahmen Primaer `#00759E`; Label `#000000`; FontSize **11 pt**                      | Hintergrund Primary Cyan `#00A5E1`; Rahmen Primaer (Bright Sky) `#77DDFF`; Label `#000000`; FontSize **11 pt**            |
| Start / Stop / End                  | Gefuellter Knoten Dark Grey `#515151` (gen2 `StartColor`/`EndColor`)                                                   | Gefuellter Knoten Light Grey `#CCCCCC`                                                                                    |
| Synchronisation (`fork`/`join`-Bar) | Balken Valid Green `#6B9714` (gen2 `BarColor` = Success)                                                               | Balken Valid Green `#B9D478`                                                                                              |
| Partition (`partition`/`group`)     | Rahmen Primaer `#00759E`; FontColor Primaer `#00759E`; Hintergrund Canvas (transparent); RoundCorner 16                | Rahmen Primaer (Bright Sky) `#77DDFF`; FontColor `#77DDFF`; Hintergrund Canvas (transparent); RoundCorner 16              |
| Swimlane-Titel                      | Hintergrund Super Light Grey `#F8F8F8`; FontColor `#000000`; **16 pt**; Rahmen Light Grey `#C6C6C6`; BorderThickness 1 | Hintergrund Dark Surface `#2D2D2D`; FontColor `#D7E9F4`; **16 pt**; Rahmen Medium Light Grey `#B6B6B6`; BorderThickness 1 |
| Pfeile (Kontrollfluss)              | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **11 pt** (globales `arrow`)                      | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **11 pt**                                            |
| Notiz (`note`)                      | Hintergrund transparent; Rahmen Medium Grey `#7A7A7A`; **11 pt**; linksbuendig (globales `note`)                       | Hintergrund transparent; Rahmen Medium Grey `#7A7A7A`; **11 pt**; linksbuendig                                            |

Hinweis: Aktionsknoten erben die globale Form-Fuellung (Blau-Tint / Dark Blau-Grau) und den dezenten Rahmen (BorderThickness 0) — identisch zu `class`, `state`, `usecase`. Die Entscheidung (`diamond`) ist der einzige farblich hervorgehobene Akzent (Primary Cyan), damit Verzweigungen sofort lesbar sind.

### Element-Typen (Syntax)

| Zweck                    | Empfohlenes Element                | Hinweis                                                                         |
| ------------------------ | ---------------------------------- | ------------------------------------------------------------------------------- |
| Aktion / Prozessschritt  | `:Text;`                           | Beta-Syntax; ein Schritt pro Zeile, abgeschlossen mit `;`                       |
| Start / Ende des Flusses | `start` / `stop`/`end`             | `start` einmal am Anfang; `stop` oder `end` an jedem terminierenden Pfad        |
| Entscheidung             | `if/else/endif`, `repeat`, `while` | Wird als `diamond` gerendert (siehe [SG-36](#sg-36-entscheidungen-als-diamond)) |
| Parallelitaet            | `fork` / `fork again` / `end fork` | Synchronisationsbalken                                                          |
| Verantwortung / Rolle    | `\|Swimlane\|`                     | Spalte pro Rolle; Reihenfolge der Deklaration bestimmt Spaltenfolge             |
| Logische Gruppierung     | `partition` / `group`              | Rahmt zusammengehoerige Aktionen; `partition` traegt sichtbaren Titel           |
| Zwischenkommentar        | `note left` / `note right`         | Erbt globales `note`-Styling                                                    |

### Typografie

| Eigenschaft                     | Soll-Wert                            | Geltung                                  |
| ------------------------------- | ------------------------------------ | ---------------------------------------- |
| **FontSize** (Aktion-Label)     | **12 pt**                            | Standard-Fliesstext (globales `element`) |
| **FontSize** (Diamond-Label)    | **11 pt**                            | Beschriftung der Entscheidungsraute      |
| **FontSize** (Swimlane-Titel)   | **16 pt**                            | Spaltenkopf der Swimlane                 |
| **FontColor** (Aktion-Label)    | Element-Labels `#000000` / `#D7E9F4` | Beschriftung auf Blau-Tint-Fuellung      |
| **FontColor** (Partition-Label) | Primaer `#00759E` / `#77DDFF`        | Partition-Titel in Primaerfarbe          |
| **ArrowFontSize**               | **11 pt**                            | Beschriftungen an Kontrollfluss-Pfeilen  |

## Konfiguration

### [SG-33] Beta-Syntax verwenden

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Activity

**Regel:** Activity-Diagramme **SOLLEN** die [Activity-Beta-Syntax](https://plantuml.com/de/activity-diagram-beta) nutzen (`start`, `:Aktion;`, `if/else`, `\|Swimlane\|`) — nicht die veraltete Syntax mit `(*)` und `-->`. Nur so greifen `activityDiagram`-Stylings korrekt.

```plantuml
start
:Aktion;
stop
```

### [SG-34] Layout-Richtung

**Ebene:** Page  
**Geltung:** Activity

**Regel:** Activity-Diagramme **SOLLEN** die globale Leserichtung **top to bottom** beibehalten — der Kontrollfluss laeuft von oben nach unten, Swimlanes rendern als vertikale Spalten. `left to right direction` **SOLLTE NICHT** gesetzt werden, da es den Fluss-Lesefluss bricht.

Globaler Default ist **top to bottom** — siehe [Globale Defaults — Richtung](../global-defaults.md#richtung-layout-logik).

### [SG-35] Swimlanes und Partitions

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Activity

**Regel:** Verantwortlichkeiten **SOLLTEN** ueber Swimlanes (`|Name|`) modelliert werden; thematisch zusammengehoerige Schritte **DUERFEN** zusaetzlich in einer `partition` gebuendelt werden. Swimlane-Farben **SOLLEN** dem Theme-Token folgen (Titel Super Light Grey / Dark Surface); individuelle Lane-Farben nur bei fachlicher Notwendigkeit ueber `|#Farbe|Name|`.

```plantuml
|Planung|
:Angebot erstellen;
|Entwicklung|
:Umsetzung;
```

### [SG-36] Entscheidungen als `diamond`

**Ebene:** Stil / Rendering  
**Geltung:** Activity

**Regel:** Entscheidungen (`if`/`repeat`/`while`) **SOLLEN** als Raute (`diamond`) dargestellt werden. Das Theme setzt dafuer `skinparam conditionStyle diamond`; in Autoren-Diagrammen ist keine zusaetzliche Direktive noetig. Die Raute nutzt als einziges Element die Akzentfarbe Primary Cyan.

```plantuml
skinparam conditionStyle diamond
```

### [SG-37] Keine Hardcoded-Farben

**Ebene:** Domain / Governance  
**Geltung:** Activity

**Regel:** Aktionen, Entscheidungen und Partitions **SOLLEN** die Theme-Defaults nutzen. Inline-Farben (`:Aktion; #red`, `<<#blue>>`) **SOLLTEN** nur fuer bewusste fachliche Hervorhebung (z. B. kritische Pfade) eingesetzt werden — nicht zur generellen Umfaerbung. Farbwerte folgen den [Design Tokens](../design-tokens.md), nicht beliebigen Hex-Werten.
