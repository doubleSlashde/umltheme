# Class- & Datenmodelle

Klassendiagramme modellieren die **statische Struktur** (Klassen, Interfaces, Attribute, Methoden, Beziehungen). Datenmodelle (ER) nutzen dieselbe PlantUML-Syntax mit dem Schlüsselwort `entity` fuer persistente Objekte und Kardinalitaeten an Kanten.

Diese Seite dokumentiert die **diagrammtyp-spezifischen** Sollwerte fuer Class-, Interface-, Entity- und Package-Elemente sowie fuer ER-/Datenmodell-Konventionen.

Globale Typografie-, Farb- und Rendering-Defaults gelten zusaetzlich: [Globale Defaults](../global-defaults.md) · Farb-Token: [Design Tokens](../design-tokens.md).

## Klassenmodell (Beispiel)

=== "light"

    ```puml
    @startuml classmodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    hide circle
    hide empty members
    hide stereotype
    title Klassenmodell
    left to right direction

    interface Schnittstelle

    class Klasse implements Schnittstelle {
      - Attribut : AndereKlasse
      + Methode1()
    }
    class AndereKlasse {
      - Attribut : Typ
      + Methode2()
    }
    class Unterklasse extends Klasse {}

    class AufrufendeKlasse <<external>> {
      + useInterface()
    }

    AufrufendeKlasse --> Schnittstelle : verwendet
    Klasse *-- AndereKlasse : aggregiert
    note top of Klasse: Diese Notiz liefert eine nähere\n Beschreibung der Klasse
    @enduml
    ```

=== "dark"

    ```puml
    @startuml classmodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    hide circle
    hide empty members
    hide stereotype
    title Klassenmodell
    left to right direction

    interface Schnittstelle

    class Klasse implements Schnittstelle {
      - Attribut : AndereKlasse
      + Methode1()
    }
    class AndereKlasse {
      - Attribut : Typ
      + Methode2()
    }
    class Unterklasse extends Klasse {}

    class AufrufendeKlasse <<external>> {
      + useInterface()
    }

    AufrufendeKlasse --> Schnittstelle : verwendet
    Klasse *-- AndereKlasse : aggregiert
    note top of Klasse: Diese Notiz liefert eine nähere\n Beschreibung der Klasse
    @enduml
    ```

## Datenmodell (Beispiel)

=== "light"

    ```puml
    @startuml datamodel
    !theme light from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    hide circle
    hide empty members
    hide stereotype
    left to right direction
    title Datenmodell

    entity Entität1 {
      + name : text
      e1Id : SERIAL (PK)
      e2Id : INTEGER (FK)
    }

    entity Entität2 {
      Name : Text
      e2Id : SERIAL (PK)
    }

    entity OtherEntity <<external>> {
      otherId : SERIAL (PK)
      name : Text
    }

    Entität2 }o---|| Entität1
    Entität2 }o---|{ OtherEntity
    @enduml
    ```

=== "dark"

    ```puml
    @startuml datamodel
    !theme dark from https://raw.githubusercontent.com/doubleSlashde/umltheme/refs/heads/main/doubleslash/v3/

    hide circle
    hide empty members
    hide stereotype
    left to right direction
    title Datenmodell

    entity Entität1 {
      + name : text
      e1Id : SERIAL (PK)
      e2Id : INTEGER (FK)
    }

    entity Entität2 {
      Name : Text
      e2Id : SERIAL (PK)
    }

    entity OtherEntity <<external>> {
      otherId : SERIAL (PK)
      name : Text
    }

    Entität2 }o---|| Entität1
    Entität2 }o---|{ OtherEntity
    @enduml
    ```

## Geltende Werte

### Standard-Settings

Diese vier Direktiven sind **kein Theme-Styling**, sondern verbindliche **Autor-Settings** fuer Class- und Datenmodell-Diagramme. Sie gehoeren **nach** dem Theme-Include und **vor** den Element-Deklarationen (wie in den Golden Samples).

| Setting                   | Soll       | Wirkung                                                                                                                                      | Ausnahme                                                                       |
| ------------------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| `hide circle`             | **setzen** | Entfernt den **Buchstaben-Kreis** vor dem Klassennamen (C/I/E/A — PlantUML-Klassifikations-Spot). Das Diagramm wirkt ruhiger und CI-konform. | Nur weglassen, wenn der Spot bewusst zur Legende noetig ist.                   |
| `hide empty members`      | **setzen** | Blendet **leere** Attribut- und Methoden-Bereiche aus (z. B. `class X {}` oder Klassen ohne Member). Reduziert Leerraum in grossen Modellen. | `show members` nur bei bewusst leeren Platzhalter-Klassen.                     |
| `hide stereotype`         | **setzen** | Blendet **Stereotyp-Labels** aus (`<<interface>>`, `<<external>>` als Text). **Styling** ueber `<<external>>` / `interface` bleibt aktiv.    | `show stereotype`, wenn der Stereotyp-Name im Bild sichtbar sein soll.         |
| `left to right direction` | **setzen** | Layout **horizontal** (links nach rechts). Besser lesbar bei vielen Entitaeten und Assoziationen (ER, Service-Landschaften).                 | `top to bottom direction` bei wenigen, tief verschachtelten Generalisierungen. |

**Empfohlene Reihenfolge** (direkt nach `!theme` / `!include`):

```plantuml
hide circle
hide empty members
hide stereotype
left to right direction

title [Projekt] — Klassenmodell: [Subject]
```

`title` darf vor oder nach `left to right direction` stehen; die `hide`-Zeilen **SOLLTEN** vor dem Diagramminhalt zusammenstehen.

Globaler Default fuer die Leserichtung ist **top to bottom** — siehe [Globale Defaults — Richtung](../global-defaults.md#richtung-layout-logik). Fuer Class & Data ist **left to right** der diagrammtyp-spezifische Soll-Standard.

### Element-Typen (Syntax)

| Zweck                       | Empfohlenes Element | Hinweis                                                                    |
| --------------------------- | ------------------- | -------------------------------------------------------------------------- |
| Domänen-/Service-Klasse     | `class`             | Standard-Fuellung und Header-Typografie                                    |
| Vertrag / API               | `interface`         | Cyan-Fuellung, verstaerkter Rahmen — nicht als normale `class` modellieren |
| Persistenz / ER-Datenmodell | `entity`            | Gleiche Flächenfarben wie `class`; Kardinalitaeten an Kanten               |
| Fremdsystem / Legacy        | `<<external>>`      | Auf `class` oder `entity`; kanonisch Kleinschreibung `external`            |
| Logische Gruppierung        | `package`           | Alice-Blue-Container; verschachtelbar                                      |
| Objektinstanz (Laufzeit)    | `object`            | Siehe [Object-Diagramme](data-and-misc.md#sg-56-object-diagramme)          |

Weitere deklarative Typen (`enum`, `abstract`, `annotation`, …) erben die Klassen-Defaults; Stereotyp-Buchstaben (C/A/I/E/N) folgen [Globale Defaults — Stereotyp-Badges](../global-defaults.md#stereotyp-badges-buchstaben-c-a-i-e-n).

### Sichtbarkeit (Member)

| Eigenschaft                 | Soll-Wert                                                                                             |
| --------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Sichtbarkeitszeichen**    | `-` private, `#` protected, `~` package, `+` public (PlantUML-Standard)                               |
| **Visibility-Icons**        | PlantUML-Standard-Icons **oder** `skinparam classAttributeIconSize 0` fuer rein textuelle Darstellung |
| **Empfehlung Datenmodelle** | Icons aus (`classAttributeIconSize 0`), wenn viele Attribute/PK/FK gezeigt werden                     |

## Konfiguration

### [SG-22] Standard-Settings

**Ebene:** Syntax / Diagrammstruktur  
**Geltung:** Class & Data

**Regel:** Klassen- und Datenmodell-Diagramme **SOLLTEN** die drei `hide`-Direktiven setzen.

```code
hide circle
hide empty members
hide stereotype
```

### [SG-23] Externe Klassen und Entitaeten

**Ebene:** Stereotyp/Domain  
**Geltung:** Class & Data

**Regel:** Fremdsysteme, Legacy-Datenbanken oder externe Domänen **SOLLTEN** den Stereotyp `<<external>>` tragen.

=== "✅ Empfohlen"

```text
--8<-- "_snippets/style-guide/class-external.puml"
```

### [SG-24] Interfaces typgerecht

**Ebene:** Syntax  
**Geltung:** Class

**Regel:** Verträge und APIs **SOLLTEN** mit dem Schluesselwort `interface` (oder explizitem Interface-Stereotyp) modelliert werden.

```plantuml
interface PaymentPort
class OrderService implements PaymentPort
```

### [SG-25] Datenmodell mit `entity`

**Ebene:** Syntax / Domain  
**Geltung:** Data (ER)

**Regel:** Persistente Tabellen/Entitaeten in ER-Diagrammen **SOLLTEN** `entity` statt `class` verwenden. Primaer- und Fremdschluessel **SOLLTEN** in Attributnamen kenntlich gemacht werden (z. B. `(PK)`, `(FK)`).

```plantuml
entity Order {
  orderId : SERIAL (PK)
  customerId : INTEGER (FK)
}
```

### [SG-26] Packages und Namespaces

**Ebene:** Struktur  
**Geltung:** Class & Data

**Regel:** Logische Module **DUERFEN** mit `package` oder Namespaces (`set separator ::`) gruppiert werden.

### [SG-27] Layout-Richtung

**Ebene:** Page  
**Geltung:** Class & Data

**Regel:** Class- und Datenmodell-Diagramme **SOLLTEN** `left to right direction` setzen. Nur bei wenigen, vertikal gegliederten Generalisierungen **DARF** `top to bottom direction` gewaehlt werden.

```plantuml
left to right direction
```
