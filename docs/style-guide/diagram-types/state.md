# State-Diagramme

State-Diagramme modellieren das **Verhalten** eines Systems oder einer Komponente: Zustaende, Uebergaenge zwischen ihnen, Verzweigungen und parallele Regionen. Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer State-Elemente.

**Organismus:** `state` (Zustand), `[*]` (Initial-/Final-Pseudo-Zustand), `<<choice>>` (Verzweigung), `<<fork>>` / `<<join>>` (Synchronisation), `<<history>>` (History-Pseudo-Zustand), zusammengesetzte Zustaende (composite state mit Regionen).

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

**Golden Sample:** [`state.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/state.puml)

=== "light"

    ```puml
    @startuml statemodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    hide empty description

    title State-Diagramm

    state "Auftrag" as Auftrag {
      [*] --> Entwurf
      Entwurf --> Freigegeben : freigeben
      Freigegeben --> Storniert : stornieren
      Freigegeben --> [*]
      Storniert --> [*]
    }

    [*] --> Auftrag : anlegen

    state choice1 <<choice>>
    state fork1 <<fork>>
    state join1 <<join>>

    Auftrag --> choice1 : abschliessen
    choice1 --> fork1 : parallel starten
    choice1 --> join1 : direkt
    fork1 --> Bearbeitung
    fork1 --> Versand
    Bearbeitung --> join1
    Versand --> join1
    join1 --> [*]

    note right of Auftrag
      Zustandsbeschreibung
      und interne Aktivitaeten
    end note
    @enduml
    ```

=== "dark"

    ```puml
    @startuml statemodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    hide empty description

    title State-Diagramm

    state "Auftrag" as Auftrag {
      [*] --> Entwurf
      Entwurf --> Freigegeben : freigeben
      Freigegeben --> Storniert : stornieren
      Freigegeben --> [*]
      Storniert --> [*]
    }

    [*] --> Auftrag : anlegen

    state choice1 <<choice>>
    state fork1 <<fork>>
    state join1 <<join>>

    Auftrag --> choice1 : abschliessen
    choice1 --> fork1 : parallel starten
    choice1 --> join1 : direkt
    fork1 --> Bearbeitung
    fork1 --> Versand
    Bearbeitung --> join1
    Versand --> join1
    join1 --> [*]

    note right of Auftrag
      Zustandsbeschreibung
      und interne Aktivitaeten
    end note
    @enduml
    ```

## Geltende Werte

### Geltende Atome & Molekuele

<!-- markdownlint-disable MD060 -->

| Mechanismus                                | Soll-Wert (Light)                                                                                                   | Soll-Wert (Dark)                                                                                                                      |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Zustand (`state`)                          | Hintergrund Blau-Tint `#D7E9F4`; Rahmen Primaer `#00759E`; LineThickness **1**; RoundCorner **16**; Label `#000000` | Hintergrund Dark Blau-Grau `#22303C`; Rahmen Primaer (Bright Sky) `#77DDFF`; LineThickness **1**; RoundCorner **16**; Label `#D7E9F4` |
| Zusammengesetzter Zustand (composite)      | Gleiche Fuellung/Rahmen wie `state`; Header = Zustandsname; Regionen mit `--` trennbar                              | Gleiche Fuellung/Rahmen wie `state`                                                                                                   |
| Initial / Final (`[*]`)                    | Gefuellter Knoten Dark Grey `#515151` (wie Activity `StartColor`/`EndColor`)                                          | Gefuellter Knoten Light Grey `#CCCCCC` (wie Activity `StartColor`/`EndColor`)                                                         |
| Choice (`<<choice>>`)                      | Raute; Hintergrund Primary Cyan `#00A5E1`; Rahmen Primaer `#00759E` (konsistent zu Activity-`diamond`)              | Raute; Hintergrund Primary Cyan `#00A5E1`; Rahmen Primaer (Bright Sky) `#77DDFF`                                                      |
| Fork / Join (`<<fork>>` / `<<join>>`)      | Synchronisationsbalken Valid Green `#6B9714` (konsistent zu Activity `BarColor`)                                    | Synchronisationsbalken Valid Green `#B9D478`                                                                                          |
| History (`<<history>>`)                    | Pseudo-Knoten wie Initial/Final; Dark Grey `#515151` / Light Grey `#CCCCCC`                                          | Pseudo-Knoten wie Initial/Final                                                                                                       |
| Zustands-Beschreibung / interne Aktivitaet | `AttributeFontColor` `#000000`; `AttributeFontSize` **11 pt** (gen2 `skinparam state`)                              | `AttributeFontColor` `#D7E9F4`; `AttributeFontSize` **11 pt**                                                                         |
| Transition (Pfeil)                         | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **11 pt** (globales `arrow`)                   | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **11 pt**                                                        |
| Notiz (`note`)                             | Hintergrund transparent; Rahmen Medium Grey `#7A7A7A`; **11 pt**; linksbuendig (globales `note`)                    | Hintergrund transparent; Rahmen Medium Grey `#7A7A7A`; **11 pt**; linksbuendig                                                        |

<!-- prettier-ignore-start -->

!!! info
    Hinweis: Zustaende erben die globale Form-Fuellung (Blau-Tint / Dark Blau-Grau) und den Primaer-Rahmen — identisch zu `class`, `usecase` und Activity-Aktionen. Initial/Final (`[*]`) und History-Pseudo-Zustaende sind wie Activity Start/End **dunkel bzw. hell gefuellt** (Dark Grey / Light Grey), nicht Primary Cyan. Choice-Punkte nutzen wie Activity-Entscheidungen die Akzentfarbe Primary Cyan.

!!! note "Theme-Implementierung (v3)"
    In `doubleslash/v3/puml-theme-*.puml`:  
    - `stateDiagram` → `state` (nur `BackGroundColor`)  
    - `diamond` (Choice)  
    - `activityBar` (Fork/Join)  
    Rahmen, Typografie und Transitionen kommen von globalem `element` bzw. `arrow`.  
    `StartColor`, `EndColor`, `AttributeFontColor` und `AttributeFontSize` per Legacy-`skinparam state`.  
    Smoke Tests: [`state.v3-theme-light.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/state.v3-theme-light.puml) · [`state.v3-theme-dark.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/local_testing/state.v3-theme-dark.puml).
<!-- prettier-ignore-end -->

### Standard-Settings

Diese Direktive ist **kein Theme-Styling**, sondern eine verbindliche **Autor-Setting** fuer State-Diagramme. Sie gehoert **nach** dem Theme-Include und **vor** den Zustandsdeklarationen (wie in den Golden Samples).

| Setting                  | Soll       | Wirkung                                                                                                                                           | Ausnahme                                                                                  |
| ------------------------ | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `hide empty description` | **setzen** | Zustaende ohne Beschreibungstext werden als **kompakte Box** gerendert (ohne leeren Beschreibungsbereich). Diagramm wirkt ruhiger und CI-konform. | `show empty description`, wenn der leere Beschreibungsbereich bewusst sichtbar sein soll. |

**Empfohlene Reihenfolge** (direkt nach `!theme` / `!include`):

    hide empty description

    title [Projekt] — State: [Subject]

`title` darf vor oder nach weiteren Direktiven stehen; `hide empty description` **SOLL** vor dem Diagramminhalt gesetzt werden.

### Element-Typen (Syntax)

| Zweck                           | Empfohlenes Element / Stereotyp   | Hinweis                                                                                                                                   |
| ------------------------------- | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Zustand im Lebenszyklus         | `state "Name" as Id`              | Abgerundetes Rechteck; Kurzbeschriftung; optional Beschreibung im Zustandskoerper (siehe [SG-45](#sg-45-leere-beschreibungen-ausblenden)) |
| Start / Ende des Automaten      | `[*]`                             | Initial: eingehende Transition von `[*]`; Final: ausgehend zu `[*]`                                                                       |
| Bedingte Verzweigung            | `<<choice>>`                      | Raute; mehrere ausgehende Transitionen mit Guard-Bedingungen                                                                              |
| Parallele Aufspaltung/-fuehrung | `<<fork>>` / `<<join>>`           | Synchronisationsbalken; nicht mit Activity-`fork`-Syntax verwechseln                                                                      |
| History-Pseudo-Zustand          | `<<history>>` / `<<deepHistory>>` | Ruecksprung in uebergeordneten Zustand; sparsam einsetzen                                                                                 |
| Zusammengesetzter Zustand       | `state Name { ... }`              | Gruppiert Unterzustaende; Regionen mit `--` (siehe [SG-40](#sg-40-zusammengesetzte-zustaende))                                            |
| Transition mit Bedingung        | `-->` / `-->` mit Label           | Beschriftung am Pfeil; Guard in eckigen Klammern nach UML-Konvention                                                                      |
| Zwischenkommentar               | `note left of` / `note right of`  | Erbt globales `note`-Styling                                                                                                              |

### Typografie

| Eigenschaft                           | Soll-Wert                                    | Geltung                                                |
| ------------------------------------- | -------------------------------------------- | ------------------------------------------------------ |
| **FontSize** (Zustands-Label)         | **12 pt**                                    | Standard-Fliesstext (globales `element`)               |
| **FontSize** (Zustands-Beschreibung)  | **11 pt**                                    | Interne Aktivitaeten / Attribute (`AttributeFontSize`) |
| **FontColor** (Zustands-Label)        | Element-Labels `#000000` / `#D7E9F4`         | Beschriftung auf Blau-Tint-Fuellung                    |
| **FontColor** (Zustands-Beschreibung) | `#000000` / `#D7E9F4` (`AttributeFontColor`) | Beschreibungstext im Zustandskoerper                   |
| **ArrowFontSize**                     | **11 pt**                                    | Beschriftungen an Transitionen                         |

<!-- markdownlint-enable MD060 -->

## Konfiguration

### [SG-38] Pseudo-Zustaende typgerecht

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** State

**Regel:** Initial-, Final-, Choice-, Fork-, Join- und History-Pseudo-Zustaende **SOLLTEN** mit den kanonischen PlantUML-Stereotypen modelliert werden — nicht als normale `state`-Rechtecke.

    [*] --> Idle
    state choice1 <<choice>>
    state fork1 <<fork>>
    state join1 <<join>>
    state hist1 <<history>>
    Idle --> [*]

### [SG-39] Layout-Richtung

**Ebene:** Page  
**Geltung:** State

**Regel:** State-Diagramme **SOLLEN** die globale Leserichtung **top to bottom** beibehalten — der Zustandsfluss laeuft von oben nach unten. `left to right direction` **SOLLTE NICHT** gesetzt werden, es sei denn, das Diagramm ist bewusst kompakt und horizontal lesbar.

Globaler Default ist **top to bottom** — siehe [Globale Defaults — Richtung](../global-defaults.md#richtung-layout-logik).

### [SG-40] Zusammengesetzte Zustaende

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** State

**Regel:** Logisch zusammengehoerende Unterzustaende **SOLLTEN** in einem zusammengesetzten `state`-Block gruppiert werden. Nebenlaeufige Regionen innerhalb eines composite state **DUERFEN** mit `--` getrennt werden.

    state "Bestellung" as Bestellung {
      [*] --> Entwurf
      Entwurf --> Freigegeben
      --
      [*] --> VersandOffen
      VersandOffen --> Versendet
    }

### [SG-45] Leere Beschreibungen ausblenden

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** State

**Regel:** State-Diagramme **SOLLTEN** `hide empty description` setzen. Zustaende ohne Beschreibungstext werden als kompakte Box dargestellt; Zustaende mit expliziter Beschreibung (`State : Text` oder mehrzeilige Beschreibung) behalten den Beschreibungsbereich.

    hide empty description
