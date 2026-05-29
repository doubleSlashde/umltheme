# Sequence-Diagramme

Sequenzdiagramme modellieren den Nachrichtenaustausch zwischen Teilnehmern (`participant`, `actor`, `boundary`, `control`, `entity`, `database`, `collections`, `queue`) entlang einer Zeitachse. Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer Sequence-Elemente.

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md).

=== "light"

    ```puml
    @startuml sequencemodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    title Sequenzmodell

    Actor Alice
    Participant FrontEnd
    Participant API
    Participant Backend
    database DB

    == Initialization ==
    Alice -> FrontEnd: klick Button
    activate FrontEnd
    FrontEnd -> API: call Service
    API -> Backend : Call Backend

    activate Backend
    Backend -> API : return value
    deactivate Backend

    API -> FrontEnd : return value
    FrontEnd -> Alice: Show status
    deactivate FrontEnd

    == Processing ==
    Backend -> DB : read detail data
    activate Backend
    DB -> Backend : return
    Backend -> Backend : process result
    Backend -> Alice : send email
    deactivate Backend
    @enduml
    ```

=== "dark"

    ```puml
    @startuml sequencemodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    title Sequenzmodell

    Actor Alice
    Participant FrontEnd
    Participant API
    Participant Backend
    database DB

    == Initialization ==
    Alice -> FrontEnd: klick Button
    activate FrontEnd
    FrontEnd -> API: call Service
    API -> Backend : Call Backend

    activate Backend
    Backend -> API : return value
    deactivate Backend

    API -> FrontEnd : return value
    FrontEnd -> Alice: Show status
    deactivate FrontEnd

    == Processing ==
    Backend -> DB : read detail data
    activate Backend
    DB -> Backend : return
    Backend -> Backend : process result
    Backend -> Alice : send email
    deactivate Backend
    @enduml
    ```

## Geltende Werte

### Geltende Atome & Molekuele

<!-- markdownlint-disable MD060 -->

| Mechanismus              | Soll-Wert (Light)                                                                                                           | Soll-Wert (Dark)                                                                                   |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Participant              | Hintergrund Blau-Tint `#D7E9F4`; Rahmen Primaer (Clickable, Deep Ocean Blue) `#00759E`; Border 0                            | Hintergrund Blau-Tint `#22303C`; Rahmen Primaer (Clickable, Bright Sky) `#77DDFF`; Border 0        |
| Actor (`actor`)          | Hintergrund/Rahmen Light Grey `#C6C6C6`; BorderThickness 3; Label Tertiary Tint `#6D6D6D`                                   | Hintergrund/Rahmen Dark Grey `#B6B6B6`; BorderThickness 3; Label `#AFC1C7`                         |
| Lifeline                 | Primaer `#00759E`; gestrichelt (PlantUML-Default); `LifeLineBorderThickness` 0; **kein** CSS `lifeLine { LineThickness 0 }` | Primaer `#77DDFF`; gestrichelt; `LifeLineBorderThickness` 0; Lifeline nur per `skinparam Sequence` |
| Divider (`== ... ==`)    | Super Light Grey `#F8F8F8`; BorderThickness 1                                                                               | Dark Surface `#2D2D2D`; BorderThickness 1                                                          |
| Group / Box              | Super Light Grey `#F8F8F8`; Medium Grey `#7A7A7A`; Body Canvas-Hintergrund                                                  | Dark Surface `#2D2D2D`; Medium Grey `#7A7A7A`; Body Canvas-Hintergrund                             |
| Stereotyp `<<external>>` | Hintergrund Super Light Grey `#F8F8F8`, Border 0                                                                            | Hintergrund Dark Surface `#2D2D2D`, Border 0                                                       |
| Abstand                  | Horizontaler Participant-Abstand 32, CSS `participant { Margin ... }`                                                       | Horizontaler Participant-Abstand 32, CSS `participant { Margin ... }`                              |

Hinweis: Die Markenfarbe Primary Cyan (`#00A5E1`) ist in Light und Dark identisch. Die hier gezeigten Rahmenwerte fuer Participant/Lifeline sind die modusabhaengige Primaer-(Clickable)-Farbe.

### Teilnehmer-Typen (Syntax)

| Zweck                        | Empfohlener Typ |
| ---------------------------- | --------------- |
| Menschlicher Benutzer        | `actor`         |
| Interner Service/Komponente  | `participant`   |
| Externe API/Systemgrenze     | `boundary`      |
| Steuerungslogik/Orchestrator | `control`       |
| Fachobjekt/Nutzdaten         | `entity`        |
| Datenbank                    | `database`      |
| Dokument-/Collection-Store   | `collections`   |
| Warteschlange                | `queue`         |

Wichtig: Fuer Datenbanken und Queues **nicht** `participant` verwenden. Nur die passenden Typen (`database`, `collections`, `queue`) aktivieren die korrekte Form und Umrandung.

### Typografie

| Eigenschaft                                         | Soll-Wert                                           | Geltung                                              |
| --------------------------------------------------- | --------------------------------------------------- | ---------------------------------------------------- |
| **ArrowFontSize**                                   | **11 pt**                                           | Pfeilbeschriftungen in Sequence                      |
| **DividerFontSize** (Separator-Label `== ...`)      | **14 pt**                                           | Beschriftung von Trennern / Separatorn               |
| **DividerFontStyle**                                | **normal**                                          | Kein Fettdruck fuer Trenner-Beschriftung             |
| **DividerBackgroundColor** / **DividerBorderColor** | Super Light Grey `#F8F8F8` / Dark Surface `#2D2D2D` | Horizontale Trennlinie (`== ... ==`)                 |
| **DividerBorderThickness**                          | **1**                                               | Sichtbare, dezente Trennlinie                        |
| **TitleFontColor** (Sequence-spezifisch)            | Default/Darkmode Textfarbe                          | Sequence-Titel (`skinparam sequence TitleFontColor`) |

<!-- markdownlint-enable MD060 -->

### CSS-Soll (Participant-Abstand) { #css-soll-participant-abstand }

| Eigenschaft                               | Soll-Wert                        |
| ----------------------------------------- | -------------------------------- |
| **Padding** (Participant innen)           | **16** (vertikal und horizontal) |
| **Margin** (Participant aussen, vertikal) | **4**                            |
| **Margin** (Participants horizontal)      | **32**                           |
| **Padding** (Boxen / Groups)              | **32** (`BoxPadding`)            |

```code
  <style>
  participant {
    Margin $PUML_SEQ_MARGIN_V $PUML_SEQUENCE_GAP_H
    Padding $PUML_SEQ_INNER_V $PUML_SEQ_INNER_H
  }
  </style>
```

## Konfiguration

### [SG-20] Teilnehmer typgerecht deklarieren

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Sequence

**Regel:** Teilnehmer **SOLLTEN** semantisch passend deklariert werden (z. B. `database DB` statt `participant DB`), damit Form und Style korrekt gerendert werden.

```code
  @startuml
  actor Alice
  participant API
  database DB
  queue Jobs
  collections Archive
  @enduml
```

### [SG-21] Externe Participants

**Ebene:** Stereotyp/Domain  
**Geltung:** Sequence

**Regel:** Externe Systeme **SOLLTEN** den Stereotyp `<<external>>` (kanonisch, Kleinschreibung) tragen.
