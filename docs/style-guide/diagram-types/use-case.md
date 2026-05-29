# Use-Case-Diagramme

Use-Case-Diagramme modellieren die **funktionale Sicht** eines Systems: welche Akteure mit welchen Anwendungsfällen interagieren und wie Use Cases untereinander in Beziehung stehen (`<<include>>`, `<<extends>>`). Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer Use-Case-Elemente.

**Organismus:** `actor` (Menschen oder externe Rollen), `usecase` (Anwendungsfaelle als Ovale), `rectangle` (Systemgrenzen).

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

**Golden Sample:** [`usecase.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/usecase.puml)

=== "light"

    ```puml
    @startuml usecasemodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    left to right direction
    hide stereotype
    title Use-Case-Diagramm

    actor "Kunde" as kunde
    actor "Support" as support

    rectangle "Online Shop" {
      usecase "Bestellung aufgeben" as UC1
    }

    rectangle "Backoffice" {
      usecase "Bestellung bearbeiten" as UC2
      usecase "Storno verarbeiten" as UC3
    }

    kunde --> UC1
    support --> UC2
    support --> UC3

    usecase "Legacy-Zahlung" <<External>> as UC4
    UC1 ..> UC4 : <<include>>
    UC3 ..> UC2 : <<extends>>
    @enduml
    ```

=== "dark"

    ```puml
    @startuml usecasemodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    left to right direction
    hide stereotype
    title Use-Case-Diagramm

    actor "Kunde" as kunde
    actor "Support" as support

    rectangle "Online Shop" {
      usecase "Bestellung aufgeben" as UC1
    }

    rectangle "Backoffice" {
      usecase "Bestellung bearbeiten" as UC2
      usecase "Storno verarbeiten" as UC3
    }

    kunde --> UC1
    support --> UC2
    support --> UC3

    usecase "Legacy-Zahlung" <<External>> as UC4
    UC1 ..> UC4 : <<include>>
    UC3 ..> UC2 : <<extends>>
    @enduml
    ```

## Geltende Werte

### Geltende Atome & Molekuele

<!-- markdownlint-disable MD060 -->

| Mechanismus                     | Soll-Wert (Light)                                                                                 | Soll-Wert (Dark)                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Use Case (`usecase`)            | Hintergrund Blau-Tint `#D7E9F4`; BorderThickness 0; Label Default Text `#000000`                  | Hintergrund Dark Blau-Grau `#22303C`; BorderThickness 0; Label Darkmode Text `#D7E9F4`            |
| Actor (`actor`)                 | Hintergrund/Rahmen Light Grey `#C6C6C6`; BorderThickness 3; Label Tertiary Tint `#6D6D6D`         | Hintergrund/Rahmen Medium Light Grey `#B6B6B6`; BorderThickness 3; Label Secondary Tint `#AFC1C7` |
| Systemgrenze (`rectangle`)      | Hintergrund Alice Blue `#F0F8FF` (`$ALICEBLUE`); BorderThickness 0; Label `#000000`               | Hintergrund Dark Surface Alt `#3A3A3A`; BorderThickness 0; Label `#D7E9F4`                        |
| Stereotyp `<<External>>`        | Hintergrund Super Light Grey `#F8F8F8`, BorderThickness 0                                         | Hintergrund Dark Surface `#2D2D2D`, BorderThickness 0                                             |
| Assoziationen / Abhaengigkeiten | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **11 pt** (globales `arrow`) | Pfeilfarbe Medium Grey `#7A7A7A`; Pfeilstaerke **1.5**; Beschriftung **11 pt**                    |

Hinweis: Use-Case-Ovale erben die globale Form-Fuellung (Blau-Tint / Dark Blau-Grau) und den dezenten Rahmen (BorderThickness 0). Systemgrenzen nutzen den Container-Token Alice Blue — nicht die Use-Case-Fuellung.

### Element-Typen (Syntax)

| Zweck                         | Empfohlenes Element | Hinweis                                                                                     |
| ----------------------------- | ------------------- | ------------------------------------------------------------------------------------------- |
| Mensch / externe Rolle        | `actor`             | Stick-Figure; nicht als `participant` oder `class` modellieren                              |
| Anwendungsfall im System      | `usecase`           | Oval; Kurzbeschriftung in Klammern: `usecase "Name" as UC1` oder `UseCase (Name) as UC1`    |
| Systemgrenze / Subsystem      | `rectangle`         | Gruppiert Use Cases eines Systems; Label = Systemname                                       |
| Fremdsystem / Legacy-Use-Case | `<<External>>`      | Auf `usecase` (oder `actor` bei Fremdrolle); kanonisch Kleinschreibung `external` in Themes |
| Include / Extend              | `..>` / `<..`       | Mit Stereotyp-Label `<<include>>` bzw. `<<extends>>` an der Kante                           |

### Typografie

| Eigenschaft                       | Soll-Wert                                          | Geltung                                                 |
| --------------------------------- | -------------------------------------------------- | ------------------------------------------------------- |
| **FontSize** (Use-Case-Label)     | **12 pt**                                          | Standard-Fliesstext (globales `element`)                |
| **FontSize** (Systemgrenze-Label) | **14 pt**                                          | Beschriftung von `rectangle` (Systemname)               |
| **FontColor** (Use-Case-Label)    | Default Text `#000000` / Darkmode Text `#D7E9F4`   | Beschriftung auf Blau-Tint-Fuellung                     |
| **FontColor** (Actor-Label)       | Tertiary Tint `#6D6D6D` / Secondary Tint `#AFC1C7` | Zurueckhaltender als Element-Labels auf Formen          |
| **FontColor** (Rectangle-Label)   | Element-Labels `#000000` / `#D7E9F4`               | Systemgrenzen-Beschriftung                              |
| **ArrowFontSize**                 | **11 pt**                                          | Beschriftungen an Kanten (`<<include>>`, `<<extends>>`) |

<!-- markdownlint-enable MD060 -->

## Konfiguration

### [SG-28] Layout-Richtung

**Ebene:** Page  
**Geltung:** Use Case

**Regel:** Use-Case-Diagramme **SOLLTEN** `left to right direction` setzen. Nur bei wenigen, vertikal gestapelten Akteuren und Systemen **DARF** `top to bottom direction` gewaehlt werden.

```plantuml
left to right direction
```

Globaler Default fuer die Leserichtung ist **top to bottom** — siehe [Globale Defaults — Richtung](../global-defaults.md#richtung-layout-logik). Fuer Use Case ist **left to right** der diagrammtyp-spezifische Soll-Standard.

### [SG-29] Systemgrenze mit `rectangle`

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Use Case

**Regel:** Das System im Fokus **SOLL** durch ein `rectangle` mit sprechendem Label abgegrenzt werden. Use Cases des Systems **SOLLTEN** innerhalb der Systemgrenze liegen.

=== "✅ Empfohlen"

```text
--8<-- "_snippets/style-guide/usecase-system-boundary.puml"
```

### [SG-30] Akteure mit `actor`

**Ebene:** Syntax  
**Geltung:** Use Case

**Regel:** Menschliche oder externe Rollen **SOLLTEN** mit dem Schluesselwort `actor` deklariert werden — nicht als generische Knoten oder Klassen.

```plantuml
actor Kunde
actor "Payment Provider" as payment
```

### [SG-31] Externe Use Cases und Akteure

**Ebene:** Stereotyp/Domain  
**Geltung:** Use Case

**Regel:** Fremdsysteme, Legacy-Anwendungsfaelle oder externe Rollen ausserhalb der Systemgrenze **SOLLTEN** den Stereotyp `<<External>>` tragen (Theme-Styling: Füllung Super Light Grey / Dark Surface, Border 0). In Theme-Dateien ist die kanonische Schreibweise `<<external>>` (Kleinschreibung).

```plantuml
usecase "Legacy-Zahlung" <<External>> as UC_Legacy
actor "Externer Partner" <<External>> as partner
```

### [SG-32] Stereotyp-Labels ausblenden

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Use Case

**Regel:** Use-Case-Diagramme **SOLLTEN** `hide stereotype` setzen. **Styling** ueber `<<External>>` bleibt aktiv; nur der sichtbare Stereotyp-Text (`<<External>>` als Label) wird ausgeblendet.

```plantuml
hide stereotype
```

**Empfohlene Reihenfolge** (direkt nach `!theme` / `!include`):

```plantuml
left to right direction
hide stereotype

title [Projekt] — Use Case: [Subject]
```
