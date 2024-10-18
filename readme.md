# Visuelles Cheatsheet: Barrierefreies Webdesign

```
+--------------------------------------------------------------------------------------------------+
|                                 BARRIEREFREIES WEBDESIGN                                         |
+--------------------------------------------------------------------------------------------------+

+------------------+  +------------------+  +------------------+  +------------------+
|    STRUKTUR      |  |     INHALTE      |  |    FORMULARE     |  |  INTERAKTIVITÄT  |
+------------------+  +------------------+  +------------------+  +------------------+
| • Semantisches HTML| | • Alternative     | | • Labels         | | • Fokus-Mgmt.    |
| • Landmarks        | |   Texte           | | • Gruppierung    | | • Tastaturzugang |
| • Überschriften    | | • Beschreibende   | | • Fehlerhandling | | • ARIA für       |
|                    | |   Links           | |                  | |   dyn. Inhalte   |
+--------------------+ +--------------------+ +------------------+ +------------------+
| <header>           | | <img alt="...">    | | <label for="..."> | | :focus {        |
| <main>             | | <a href="...">     | | <fieldset>        | |   outline: ...  |
| <nav>              | |   Beschreibung     | | <legend>          | | }               |
| <footer>           | | </a>               | |                   | |                 |
+--------------------+ +--------------------+ +------------------+ +------------------+

+------------------+  +------------------+  +------------------+  +------------------+
|  VISUELLES DESIGN|  |    MULTIMEDIA    |  |     TESTING      |  |  DOKUMENTATION   |
+------------------+  +------------------+  +------------------+  +------------------+
| • Farbkontrast   | | • Untertitel      | | • Autom. Tests    | | • Accessib. Stmt. |
| • Schriftgrößen  | | • Audiodeskription| | • Man. Prüfung    | | • Styleguide      |
| • Responsivität  | | • Transkripte     | | • Nutzer-Feedback | | • Best Practices  |
+--------------------+ +--------------------+ +------------------+ +------------------+
| color: #333;      | | <track kind=      | | WAVE, axe         | | Dokumentieren Sie|
| font-size: 1rem;  | |   "captions"...>  | | Screenreader-Test | | Ihre Maßnahmen   |
| @media (min-width:| | <audio>           | |                   | | zur              |
|   768px) { ... }  | |   <source ...>    | |                   | | Barrierefreiheit |
+--------------------+ +--------------------+ +------------------+ +------------------+

+--------------------------------------------------------------------------------------------------+
|                                   BEST PRACTICES                                                 |
+--------------------------------------------------------------------------------------------------+
| • Verwenden Sie semantisches HTML wo immer möglich                                               |
| • Stellen Sie sicher, dass alle Funktionen per Tastatur zugänglich sind                          |
| • Testen Sie regelmäßig mit verschiedenen Hilfsmitteln (Screenreader, etc.)                      |
| • Halten Sie sich an WCAG 2.1 Richtlinien (mindestens Level AA)                                  |
| • Schulen Sie Ihr Team in Barrierefreiheit und machen Sie es zu einem integralen Teil des        |
|   Entwicklungsprozesses                                                                          |
+--------------------------------------------------------------------------------------------------+
```
