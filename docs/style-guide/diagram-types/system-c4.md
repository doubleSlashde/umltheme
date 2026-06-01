# System- & C4-Diagramme

System- und C4-Diagramme modellieren die **strukturelle Sicht** eines Systems: Systemkontext, Container, Komponenten, Module und Code-Ebene (C4+M) sowie externe Akteure und Schnittstellen. Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte für C4-Stereotypen und externe Elemente.

**Organismus:** C4-Stereotypen (`<<context>>` … `<<code>>`), `agent` / `database` / `interface`, System-Bundle, orthogonales Layout.

Globale Typografie-, Farb- und Rendering-Defaults gelten zusätzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

<!-- prettier-ignore-start -->
!!! note "To-be-Design"
    Die Tabellen auf dieser Seite beschreiben den **Soll-Standard (to-be)**. Die Umsetzung in den Theme-Dateien (`doubleslash-gen2.puml`, `puml-theme-gen2-system.puml`) erfolgt separat.
<!-- prettier-ignore-end -->

**Golden Samples:**

- [`systemmodel.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/systemmodel.puml)
- [`systemmodel_with_levels.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/systemmodel_with_levels.puml)

## Systemmodell (Beispiel)

=== "light"

    ```puml
    @startuml systemmodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    left to right direction
    skinparam componentStyle rectangle
    hide stereotype
    title Systemmodell

    rectangle "Systemkontext" {

        rectangle "Container" <<container>> {
            [Komponente 1]
            [Komponente 2]
        }
        interface "Schnittstelle 1" as IF1
        note top of IF1
            Kurzbeschreibung der
            internen Schnittstelle
        end note
    }

    agent "Aufrufendes System" as Caller <<external>>
    agent "Legacy-System" as Legacy <<external>>
    database "Externe\nDatenbank" as eDB <<external>>
    interface "Partner-API" as IF2 <<external>>

    IF1 <|-- [Komponente 1] : implementiert
    IF2 <|-- Legacy : implementiert
    Caller ~~> IF1 : nutzt

    [Komponente 1] ~~> eDB : nutzt
    [Komponente 2] ~~> IF2 : nutzt
    @enduml
    ```

=== "dark"

    ```puml
    @startuml systemmodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    left to right direction
    skinparam componentStyle rectangle
    hide stereotype
    title Systemmodell

    rectangle "Systemkontext" {

        rectangle "Container" <<container>> {
            [Komponente 1]
            [Komponente 2]
        }
        interface "Schnittstelle 1" as IF1
        note top of IF1
            Kurzbeschreibung der
            internen Schnittstelle
        end note
    }

    agent "Aufrufendes System" as Caller <<external>>
    agent "Legacy-System" as Legacy <<external>>
    database "Externe\nDatenbank" as eDB <<external>>
    interface "Partner-API" as IF2 <<external>>

    IF1 <|-- [Komponente 1] : implementiert
    IF2 <|-- Legacy : implementiert
    Caller ~~> IF1 : nutzt

    [Komponente 1] ~~> eDB : nutzt
    [Komponente 2] ~~> IF2 : nutzt

    @enduml
    ```

## Geltende Werte

### C4-Stereotypen

Verschachtelte `rectangle`-Blöcke tragen den passenden C4-Stereotyp. Hintergrund-Token sind modusabhängig — siehe [Design Tokens — C4](../design-tokens.md#ubersicht).

<!-- markdownlint-disable MD060 -->

| Stereotyp       | Hintergrund (Token) | Rahmen                                  | Schrift                            |
| --------------- | ------------------- | --------------------------------------- | ---------------------------------- |
| `<<context>>`   | `$CONTEXT_BG`       | `$DS_BLUE`, Thickness **1**, solid      | `$BLACK`, **bold** (Headline)      |
| `<<container>>` | `$CONTAINER_BG`     | `$DS_LIGHTGREY`, Thickness **1**, solid | `$BLACK`                           |
| `<<component>>` | `$COMPONENT_BG`     | kein Rahmen                             | `$BLACK`, **12 pt** (Body-Default) |
| `<<module>>`    | `$MODULE_BG`        | kein Rahmen                             | `$BLACK`, **12 pt** (Body-Default) |
| `<<code>>`      | `$CODE_BG`          | kein Rahmen                             | `$WHITE`, **12 pt** (Body-Default) |

Hinweis: Context und Container erhalten sichtbare Rahmen zur Abgrenzung der äußeren Ebenen — Context mit Markenblau (`$DS_BLUE`), Container dezent mit `$DS_LIGHTGREY`. Innere Ebenen (Component, Module, Code) verlassen sich auf die Hintergrund-Tints ohne zusätzlichen Rahmen.

### Externe Elemente

Externe Systeme **MÜSSEN** den Stereotyp `<<external>>` tragen (siehe [SG-43](#sg-43-externe-systeme)). Kanonische Schreibweise in Theme-Dateien: Kleinschreibung `<<external>>`.

| Element                  | Hintergrund (Token) | Rahmen                                                                               |
| ------------------------ | ------------------- | ------------------------------------------------------------------------------------ |
| `interface` (intern)     | `$DS_CYAN`          | `$DS_CYAN`, Thickness **2** — siehe [Globale Defaults](../global-defaults.md#linien) |
| `interface <<external>>` | `$DS_GREY`          | `$DS_GREY`, Thickness **2** (gefüllt, dunkelgrau)                                    |
| `database <<external>>`  | `$SUPERLIGHTGREY`   | `$DS_GREY`, Thickness **1** (dunkelgrauer Rahmen)                                    |
| `agent <<external>>`     | `$SUPERLIGHTGREY`   | kein Rahmen (Thickness **0**)                                                        |

<!-- markdownlint-enable MD060 -->

### Element-Typen (Syntax)

| Zweck                            | Empfohlenes Element           | Hinweis                                                                                            |
| -------------------------------- | ----------------------------- | -------------------------------------------------------------------------------------------------- |
| Systemkontext / äußerste Ebene   | `rectangle` + `<<context>>`   | Umschließt alle internen Container; Headline **bold**                                              |
| Anwendung, Service, Datenbank    | `rectangle` + `<<container>>` | Verschachtelt Components; dezenter grauer Rahmen                                                   |
| Logische Bausteine               | `rectangle` + `<<component>>` | Verschachtelt Module; kein Rahmen                                                                  |
| Modul / Deployment-Einheit       | `rectangle` + `<<module>>`    | Verschachtelt Code-Elemente; kein Rahmen                                                           |
| Quellcode / Klasse               | `rectangle` + `<<code>>`      | Innerste Ebene; Text `$WHITE` auf `$CODE_BG`                                                       |
| Fremdsystem / externer Akteur    | `agent <<external>>`          | Außerhalb der Systemgrenze                                                                         |
| Externe Datenhaltung             | `database <<external>>`       | Füllung Super Light Grey; Rahmen `$DS_GREY`                                                        |
| Externe Schnittstelle            | `interface <<external>>`      | Gefüllt mit `$DS_GREY` — nicht als internes Cyan-Interface modellieren                             |
| Interne Schnittstelle            | `interface`                   | Primary Cyan (`$DS_CYAN`) — globaler Interface-Standard                                            |
| Technische Komponente (PlantUML) | `[Component Name]`            | Rechteck **ohne** UML-Komponenten-Icon — siehe [Komponenten-Darstellung](#komponenten-darstellung) |

### Typografie

Diagrammtyp-spezifische Schriftgrößen und -stile. Globale Body-Defaults: [Design Tokens — Typografie](../design-tokens.md#typografie).

| Eigenschaft                       | Soll-Wert                               | Geltung                                     |
| --------------------------------- | --------------------------------------- | ------------------------------------------- |
| **FontSize** (Context-Headline)   | **12 pt**, **bold**                     | Beschriftung von `rectangle <<context>>`    |
| **FontSize** (Container-Label)    | **12 pt**, normal                       | Beschriftung von `rectangle <<container>>`  |
| **FontSize** (Component-Label)    | **12 pt**, normal                       | Body-Default — nicht vergrößert             |
| **FontSize** (Module-Label)       | **12 pt**, normal                       | Body-Default                                |
| **FontSize** (Code-Label)         | **12 pt**, normal                       | Body-Default; Farbe `$WHITE` auf `$CODE_BG` |
| **FontColor** (Context–Component) | Element-Labels `$BLACK` / Darkmode Text | Beschriftungen auf C4-Hintergründen         |
| **FontColor** (Code-Label)        | `$WHITE` / `$TEXT_WHITE`                | Kontrast auf dunkler Code-Ebene             |
| **ArrowFontSize**                 | **11 pt**                               | Beschriftungen an Kanten (globales `arrow`) |

## Konfiguration

System-Diagramme nutzen das dedizierte Theme-Bundle `puml-theme-gen2-system.puml` (setzt u. a. `!pragma layout smetana`, `skinparam Linetype ortho`, `hide stereotype`). Details: [Globale Defaults — Richtung & Layout](../global-defaults.md#richtung-layout-logik).

**Empfohlene Reihenfolge** (direkt nach `!include`):

```plantuml
!include .../puml-theme-gen2-system.puml
left to right direction
skinparam componentStyle rectangle

title [Projekt] — System: [Subject]
```

### Komponenten-Darstellung

PlantUML-Komponenten (`[Name]`) kennen mehrere Darstellungsmodi (`rectangle`, `uml1`, `uml2`). Der Corporate-Standard ist der **rechteckige Modus ohne Icon** — keine UML-Komponenten-Ecke wie bei `uml1` / `uml2` (PlantUML-Default).

| Eigenschaft      | Soll-Wert   |
| ---------------- | ----------- |
| `componentStyle` | `rectangle` |

```plantuml
skinparam componentStyle rectangle
```

Autoren **SOLLTEN** diese Direktive in System- und C4-Diagrammen setzen, sobald `[…]`-Komponenten verwendet werden. C4-`rectangle`-Blöcke mit `<<component>>` sind davon unberührt.

### [SG-42] C4-Verschachtelung

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** System & C4

**Regel:** C4-Ebenen **SOLLTEN** als verschachtelte `rectangle`-Blöcke mit passendem Stereotyp modelliert werden — von außen nach innen: `<<context>>` → `<<container>>` → `<<component>>` → `<<module>>` → `<<code>>`.

=== "✅ Empfohlen"

    ```text
    --8<-- "_snippets/style-guide/c4-levels.puml"
    ```

### [SG-43] Externe Systeme

**Ebene:** Stereotyp/Domain  
**Geltung:** System & C4

**Regel:** Externe Systeme **MÜSSEN** mit `agent`, `database` oder `interface` und dem Stereotyp `<<external>>` kennzeichnet werden — nicht als normale interne Container oder Components.

```plantuml
agent "Payment Provider" as PaymentProvider <<external>>
database "Legacy DB" as LegacyDB <<external>>
interface "Partner API" as PartnerAPI <<external>>
```
