# Executive Summary

## Was ist der Style Guide?

Ein verbindliches Regelwerk dafür, wie PlantUML-Diagramme im doubleSlash Corporate Design aussehen. Es basiert auf dem [doubleSlash Living Styleguide](https://doubleslash.style/).

## Warum gibt es ihn?

| Problem                                       | Lösung durch Style Guide                           |
| --------------------------------------------- | -------------------------------------------------- |
| Jedes Team stylt Diagramme anders             | Einheitliche CI-Farben und Layouts                 |
| Definitionen pro Diagramm sind schwer wartbar | Atomic Design: Tokens → Bausteine → Diagrammregeln |

## Architektur auf einen Blick

```txt
Design Tokens (Farben, Schrift, Abstände)
        ↓
Wiederverwendbare Bausteine (Stereotypen, Sub-Blöcke)
        ↓
Regeln pro Diagrammtyp (Sequence, Class, C4, …)
        ↓
Include-Snippets für Autoren
        ↓
Referenzdiagramme (Golden Samples)
```
