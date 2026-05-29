# Anti-Patterns & technische Schulden

Bekannte Limitierungen der Ist-Architektur mit Workaround und Soll-Vorschlag.

## AP-01 Stereotyp-Casing { #ap-01-stereotyp-casing }

**Status:** ⚠️ Teilweise  
**Ebene:** Molekül / Stereotyp

**Problem:** Inkonsistente Schreibweise:

| Kontext                      | Ist            | Soll (kanonisch) |
| ---------------------------- | -------------- | ---------------- |
| Sequence Participant         | `<<External>>` | `<<external>>`   |
| Use Case                     | `<<External>>` | `<<external>>`   |
| Class, agent, database, card | `<<external>>` | `<<external>>` ✓ |

**Workaround (Autor):** `<<external>>` verwenden; in Sequence ggf. beide Varianten testen.

**Soll (Maintainer):** Alle skinparam-Stereotyp-Keys auf `<<external>>` vereinheitlichen (Minor-Release).

**Implementierung:** `doubleslash-gen2.puml` Z. 399–402, 460–462, 535–537, 555–557, 580, 645–646

## AP-02 Hardcoded style blocks { #ap-02-hardcoded-style-bloecke }

**Status:** ⚠️ Teilweise  
**Ebene:** Organismus  
**Geltung:** Mindmap, WBS (teilweise Gantt `closed`)

**Problem:** `<style>` kann keine `$`-Variablen referenzieren → Light-only-Hex-Werte:

- `#D7E9F4`, `#515151`, `#00A5E1`, `white`, `black`, `#8A9DB3`

**Workaround (Autor):** Für Dark-Mode eigenes `<style>`-Override nach Include; oder Light-Mode erzwingen.

**Soll (Maintainer):** Separate `mindmap-dark.puml` / conditional style files; oder PlantUML-Feature abwarten.

**Implementierung:** `doubleslash-gen2.puml` Z. 718–795, 854–857

## AP-03 colors.puml nicht eingebunden { #ap-03-colorspuml-nicht-eingebunden }

**Status:** 📋 geplant  
**Ebene:** Atom

**Problem:** [`doubleslash/colors.puml`](https://github.com/doubleSlashde/umltheme/blob/main/doubleslash/colors.puml) definiert erweiterte CI-Farben (`$DS_CYAN`, `$DS_GREEN`, …), wird aber nicht von Gen2 included.

**Workaround:** Nur Tokens aus `doubleslash-gen2.puml` verwenden.

**Soll (Maintainer):** `colors.puml` in Gen2 einbinden oder Duplikate entfernen.

## AP-04 Globale Layout-Pragmas { #ap-04-globale-layout-pragmas }

**Status:** ⚠️ Teilweise  
**Ebene:** Organismus (querwirkend)

**Problem:** `!pragma layout smetana` und `skinparam Linetype ortho` gelten global, nicht nur für System-Diagramme.

**Workaround (Autor):** `skinparam Linetype polyline` lokal setzen wenn nötig.

**Soll (Maintainer):** Pragmas in `puml-theme-gen2-system.puml` verschieben (Minor, ggf. visuelle Regression).

**Implementierung:** `doubleslash-gen2.puml` Z. 706–707

## AP-05 Rectangle-Override-Konflikt { #ap-05-rectangle-override-konflikt }

**Status:** ⚠️ Teilweise  
**Ebene:** Bundle-Override vs. Use Case

**Problem:** Use-Case-Systemgrenzen (`!startsub rectangle`: BorderThickness 0) kollidieren mit System-Bundle (blaue Borders, Thickness 1).

**Workaround:** Use-Case-Diagramme **ohne** System-Bundle; nur `doubleslash-gen2.puml`.

**Soll (Maintainer):** System-Bundle scoped auf C4-Stereotypen, nicht globales Rectangle.

## AP-06: Legacy Root-Themes

**Status:** ✅ dokumentiert (Deprecation)  
**Ebene:** Template

**Problem:** `puml-theme-doubleslash-*.puml` im Repo-Root leiten auf Gen2 um, sind aber deprecated.

**Workaround:** Migration zu Gen2-URLs — siehe [Theme usage](../theme-usage.md#legacy-themes-deprecated).

**Soll:** Major-Release entfernt Redirects; SemVer in [Versionierung](versioning.md).

## AP-07: Sequence TitleFontColor

**Status:** ⚠️ Workaround aktiv  
**Ebene:** Organismus

**Problem:** Sequence-Titel übernimmt globale TitleFontColor nicht zuverlässig.

**Workaround:** Explizites `TitleFontColor $FGCOLOR` in `!startsub sequence`.

**Implementierung:** `doubleslash-gen2.puml` Z. 365–366

## AP-08: Inline-Farben in Golden Samples

**Status:** 📋 Beispiel-Schuld  
**Ebene:** Page

**Problem:** [`piprocess.puml`](https://github.com/doubleSlashde/umltheme/blob/main/examples/gen2/remote_testing/piprocess.puml) nutzt `<color:red>` in Bedingungen.

**Workaround:** Nicht als Style-Vorbild kopieren.

**Soll:** Golden Sample bereinigen in separatem PR.
