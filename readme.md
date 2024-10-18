# Cheatsheet: Barrierefreies Webdesign

## 1. Struktur und Semantik

### 1.1 Grundlegende HTML-Struktur
- Verwenden Sie semantische HTML5-Elemente

| Element | Zweck | Tipps |
|---------|-------|-------|
| `<header>` | Kopfbereich der Seite oder eines Abschnitts | Kann mehrfach auf einer Seite verwendet werden |
| `<nav>` | Hauptnavigation | Verwenden Sie `aria-label`, wenn mehrere `<nav>` vorhanden sind |
| `<main>` | Hauptinhalt der Seite | Sollte nur einmal pro Seite verwendet werden |
| `<article>` | In sich abgeschlossener Inhalt | Ideal für Blog-Posts, Nachrichtenartikel etc. |
| `<aside>` | Nebeninhalte | Für Sidebars, Werbung, verwandte Links |
| `<footer>` | Fußbereich | Kann Kontaktinformationen, Copyright etc. enthalten |

```html
<header>
  <nav>
    <!-- Navigationsinhalt -->
  </nav>
</header>
<main>
  <article>
    <h1>Hauptüberschrift</h1>
    <!-- Hauptinhalt -->
  </article>
</main>
<footer>
  <!-- Fußzeileninhalt -->
</footer>
```

### 1.2 Überschriftenhierarchie
- Verwenden Sie `<h1>` bis `<h6>` in korrekter Reihenfolge

| Überschrift | Verwendung | Tipp |
|-------------|------------|------|
| `<h1>` | Hauptüberschrift der Seite | Nur einmal pro Seite verwenden |
| `<h2>` | Hauptabschnitte | Für wichtige Themenbereiche |
| `<h3>` - `<h6>` | Unterabschnitte | Logisch strukturieren, keine Ebenen überspringen |

```html
<h1>Haupttitel</h1>
<h2>Untertitel</h2>
<h3>Abschnittsüberschrift</h3>
```

### 1.3 Landmarks
- Nutzen Sie ARIA-Landmarks für wichtige Seitenabschnitte

| Landmark Role | Verwendung | HTML5 Äquivalent |
|---------------|------------|-------------------|
| `banner` | Globale Kopfzeile | `<header>` |
| `navigation` | Hauptnavigation | `<nav>` |
| `main` | Hauptinhalt | `<main>` |
| `contentinfo` | Fußzeileninformationen | `<footer>` |
| `search` | Suchfunktionalität | Kein direktes HTML5-Äquivalent |
| `form` | Wichtige Formulare | `<form>` |
| `complementary` | Ergänzende Inhalte | `<aside>` |

```html
<header role="banner">
<nav role="navigation">
<main role="main">
<footer role="contentinfo">
```

Tipp: Bei semantischen HTML5-Elementen ist die explizite Angabe der Landmark-Rolle oft redundant. Verwenden Sie sie nur, wenn nötig oder zur Verdeutlichung.

## 2. Inhalte

### 2.1 Bilder
- Fügen Sie alternative Texte hinzu

| Attribut | Verwendung | Tipp |
|----------|------------|------|
| `alt` | Beschreibung des Bildinhalts | Kurz und prägnant, aber informativ |
| `title` | Zusätzliche Informationen | Wird als Tooltip angezeigt, nicht für kritische Infos verwenden |
| `aria-labelledby` | Verweis auf separate Beschreibung | Für komplexere Beschreibungen |

```html
<img src="bild.jpg" alt="Beschreibung des Bildinhalts">
```
- Für dekorative Bilder:
```html
<img src="hintergrund.jpg" alt="">
```

Tipp: Verwenden Sie leere `alt`-Attribute nur für rein dekorative Bilder, die keine relevanten Informationen vermitteln.

### 2.2 Links
- Verwenden Sie beschreibende Linktexte

| Attribut | Verwendung | Tipp |
|----------|------------|------|
| `href` | Ziel-URL | Verwenden Sie relative URLs für interne Links |
| `rel` | Beziehung zum Ziel | `external` für externe Links, `noopener` für Sicherheit |
| `target` | Öffnungsverhalten | Vorsichtig verwenden, kann Nutzererfahrung beeinträchtigen |

```html
<a href="produkte.html">Unsere Produktpalette ansehen</a>
```
- Für externe Links:
```html
<a href="https://example.com" rel="external noopener">Partnerwebsite besuchen <span class="sr-only">(öffnet in neuem Tab)</span></a>
```

Tipp: Vermeiden Sie generische Linktexte wie "Klicken Sie hier" oder "Mehr". Der Linktext sollte das Ziel oder den Zweck des Links klar beschreiben.

### 2.3 Tabellen
- Strukturieren Sie Tabellen korrekt

| Element | Verwendung | Tipp |
|---------|------------|------|
| `<caption>` | Titel der Tabelle | Kurze Beschreibung des Tabelleninhalts |
| `<thead>` | Kopfzeile der Tabelle | Enthält die Spaltenüberschriften |
| `<tbody>` | Hauptinhalt der Tabelle | Enthält die Datenzeilen |
| `<th>` | Überschriftenzellen | Verwenden Sie `scope="col"` oder `scope="row"` |
| `<td>` | Datenzellen | Für den eigentlichen Tabelleninhalt |

```html
<table>
  <caption>Produktübersicht</caption>
  <thead>
    <tr>
      <th scope="col">Produkt</th>
      <th scope="col">Preis</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Produkt A</th>
      <td>10 €</td>
    </tr>
  </tbody>
</table>
```

Tipp: Verwenden Sie Tabellen nur für tabellarische Daten, nicht für Layout-Zwecke.

## 3. Formulare

### 3.1 Grundstruktur
- Verwenden Sie Labels und gruppieren Sie Formularelemente

| Element/Attribut | Verwendung | Tipp |
|------------------|------------|------|
| `<label>` | Beschriftung für Formularelemente | Immer mit `for`-Attribut verwenden |
| `<fieldset>` | Gruppierung verwandter Formularelemente | Besonders nützlich für Radiobuttons und Checkboxen |
| `<legend>` | Beschreibung für `<fieldset>` | Kurz und informativ halten |
| `required` | Kennzeichnung von Pflichtfeldern | Mit visueller Indikation kombinieren |
| `aria-describedby` | Verknüpfung mit zusätzlichen Beschreibungen | Für Hilfetexte oder Fehlermeldungen |

```html
<form>
  <fieldset>
    <legend>Persönliche Informationen</legend>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name" required>
    
    <label for="email">E-Mail:</label>
    <input type="email" id="email" name="email" required>
  </fieldset>
</form>
```

### 3.2 Fehlerbehandlung
- Verknüpfen Sie Fehlermeldungen mit den entsprechenden Feldern

| Attribut | Verwendung | Tipp |
|----------|------------|------|
| `aria-invalid` | Kennzeichnung ungültiger Eingaben | Auf `true` setzen bei Fehler |
| `aria-describedby` | Verknüpfung mit Fehlermeldung | ID der Fehlermeldung angeben |
| `role="alert"` | Kennzeichnung von Fehlermeldungen | Für wichtige, zeitkritische Meldungen |

```html
<label for="password">Passwort:</label>
<input type="password" id="password" name="password" aria-describedby="password-error" required>
<p id="password-error" role="alert">Das Passwort muss mindestens 8 Zeichen lang sein.</p>
```

Tipp: Geben Sie klare Anweisungen zur Fehlerbehebung und positionieren Sie Fehlermeldungen nahe den betroffenen Feldern.

## 4. Tastaturzugänglichkeit

### 4.1 Fokus-Management
- Stellen Sie eine logische Tab-Reihenfolge sicher
- Implementieren Sie einen sichtbaren Fokus-Indikator

| CSS-Selektor | Verwendung | Tipp |
|--------------|------------|------|
| `:focus` | Stil für fokussierte Elemente | Deutlich sichtbar, aber nicht störend gestalten |
| `:focus-visible` | Nur bei Tastaturfokus | Für differenzierte Fokus-Stile |
| `outline` | Umrandung für fokussierte Elemente | Kontrastreiche Farbe wählen |
| `box-shadow` | Alternative zu `outline` | Kann für weichere Effekte verwendet werden |

```css
:focus {
  outline: 3px solid #4A90E2;
  outline-offset: 2px;
}
```

Tipp: Entfernen Sie niemals den Fokus-Indikator vollständig. Wenn Sie ihn anpassen, stellen Sie sicher, dass er gut sichtbar bleibt.

### 4.2 Skiplinks
- Bieten Sie Skiplinks für Screenreader-Nutzer an

| Attribut | Verwendung | Tipp |
|----------|------------|------|
| `class="skip-link"` | Styling des Skiplinks | Normalerweise visuell versteckt, bei Fokus sichtbar |
| `href="#main-content"` | Ziel des Skiplinks | ID des Hauptinhaltsbereichs |

```html
<a href="#main-content" class="skip-link">Zum Hauptinhalt springen</a>
```

Tipp: Positionieren Sie Skiplinks als erste fokussierbare Elemente auf der Seite.

## 5. ARIA (Accessible Rich Internet Applications)

### 5.1 Dynamischer Inhalt
- Verwenden Sie `aria-live` für dynamische Inhalte

| Attribut | Wert | Verwendung |
|----------|------|------------|
| `aria-live` | `off` | Standardwert, keine Ankündigung |
| | `polite` | Ankündigung, wenn der Benutzer pausiert |
| | `assertive` | Sofortige Ankündigung, wichtige Updates |
| `aria-atomic` | `true`/`false` | Gesamten Inhalt oder nur Änderungen ankündigen |
| `aria-relevant` | `additions`/`removals`/`text`/`all` | Art der relevanten Änderungen |

```html
<div aria-live="polite" aria-atomic="true">
  <!-- Dynamisch aktualisierter Inhalt -->
</div>
```

Tipp: Verwenden Sie `aria-live="assertive"` sparsam, da es die aktuelle Benutzeraktion unterbricht.

### 5.2 Erweiterte Widgets
- Nutzen Sie ARIA-Attribute für komplexe Komponenten

| Attribut | Verwendung | Tipp |
|----------|------------|------|
| `aria-expanded` | Zustand von ausklappbaren Elementen | `true` wenn geöffnet, sonst `false` |
| `aria-controls` | ID des kontrollierten Elements | Verknüpft Steuerung mit Inhalt |
| `aria-haspopup` | Zeigt an, dass ein Popup geöffnet werden kann | Wert kann `true`, `menu`, `listbox`, etc. sein |
| `role` | Definiert die Rolle eines Elements | Nur verwenden, wenn HTML-Semantik nicht ausreicht |

```html
<button aria-expanded="false" aria-controls="dropdown-menu">
  Menü öffnen
</button>
<ul id="dropdown-menu" role="menu" hidden>
  <li role="menuitem"><a href="#">Option 1</a></li>
  <li role="menuitem"><a href="#">Option 2</a></li>
</ul>
```

Tipp: Testen Sie komplexe Widgets gründlich mit verschiedenen Screenreadern, da die Unterstützung variieren kann.

## 6. Visuelles Design

### 6.1 Farben und Kontrast
- Stellen Sie ausreichenden Farbkontrast sicher

| Kontrastwert | Verwendung | Tipp |
|--------------|------------|------|
| 4.5:1 | Mindestkontrast für normalen Text | Gilt für Text unter 18pt oder 14pt fett |
| 3:1 | Mindestkontrast für großen Text | Gilt für Text über 18pt oder 14pt fett |
| 3:1 | Mindestkontrast für UI-Komponenten | Gilt für Ränder von Eingabefeldern, Icons, etc. |

```css
body {
  color: #333; /* Dunkler Text */
  background-color: #fff; /* Heller Hintergrund */
}
```

Tipp: Verwenden Sie Tools wie den WebAIM Contrast Checker, um Ihre Farbkombinationen zu testen.

### 6.2 Responsive Design
- Implementieren Sie ein flexibles Layout

| CSS-Eigenschaft | Verwendung | Tipp |
|-----------------|------------|------|
| `display: flex` | Flexibles Box-Layout | Gut für eindimensionale Layouts |
| `display: grid` | Rasterbasiertes Layout | Ideal für zweidimensionale Layouts |
| `@media` | Medienabfragen für responsive Designs | Definieren Sie Breakpoints für verschiedene Geräte |

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
.column {
  flex: 1 1 300px;
}
```

Tipp: Testen Sie Ihr Design auf verschiedenen Geräten und Bildschirmgrößen.

## 6. Visuelles Design (Fortsetzung)

### 6.3 Schriftgrößen
- Verwenden Sie relative Einheiten für Schriftgrößen

| Einheit | Beschreibung | Tipp |
|---------|--------------|------|
| `rem` | Relativ zur Wurzel-Schriftgröße | Ideal für konsistente Skalierung |
| `em` | Relativ zur Eltern-Schriftgröße | Nützlich für komponenten-basiertes Styling |
| `%` | Prozentual zur Eltern-Schriftgröße | Ähnlich wie `em`, aber oft intuitiver |
| `vw` | Relativ zur Viewportbreite | Vorsichtig verwenden, kann zu extremen Größen führen |

```css
body {
  font-size: 16px; /* Basis-Schriftgröße */
}
h1 {
  font-size: 2rem; /* Relativ zur Basis-Schriftgröße */
}
```

Tipp: Eine Basis-Schriftgröße von 16px ist ein guter Ausgangspunkt. Stellen Sie sicher, dass Text auch bei 200% Zoom noch lesbar ist.

### 6.4 Zeilenabstand und Textausrichtung

| Eigenschaft | Empfehlung | Tipp |
|-------------|------------|------|
| `line-height` | Mindestens 1.5 | Verbessert die Lesbarkeit, besonders bei längeren Texten |
| `text-align` | Linksbündig für längere Texte | Zentrierter Text kann für Nutzer mit Leseschwäche schwierig sein |
| `max-width` | Ca. 60-80 Zeichen pro Zeile | Verbessert die Lesbarkeit und verhindert zu lange Zeilen |

```css
body {
  line-height: 1.5;
  text-align: left;
}
p {
  max-width: 60ch; /* ch-Einheit entspricht der Breite der "0" im aktuellen Font */
}
```

Tipp: Vermeiden Sie vollständig gerechtfertigten Text (`text-align: justify`), da ungleichmäßige Wortabstände die Lesbarkeit beeinträchtigen können.

## 7. Multimedia

### 7.1 Video-Untertitel
- Fügen Sie Untertitel zu Videos hinzu

| Attribut/Element | Verwendung | Tipp |
|------------------|------------|------|
| `<track>` | Definiert Text-Tracks für `<video>` | Kann für Untertitel, Beschreibungen etc. verwendet werden |
| `kind` | Art des Text-Tracks | `"captions"` für Untertitel, `"descriptions"` für Audiobeschreibungen |
| `srclang` | Sprache des Tracks | Verwenden Sie standardisierte Sprachcodes (z.B. "de" für Deutsch) |
| `label` | Beschriftung für die Auswahl des Tracks | Sollte die Sprache oder Art des Tracks klar benennen |

```html
<video controls>
  <source src="video.mp4" type="video/mp4">
  <track kind="captions" src="captions.vtt" srclang="de" label="Deutsch">
</video>
```

Tipp: Bieten Sie, wenn möglich, Untertitel in mehreren Sprachen an. Stellen Sie sicher, dass die Untertitel synchron zum Gesprochenen sind.

### 7.2 Audiobeschreibungen
- Bieten Sie Transkripte für Audioinhalte an

| Element/Attribut | Verwendung | Tipp |
|------------------|------------|------|
| `<audio>` | Einbettung von Audiodateien | Immer mit Bedienelementen (`controls`) versehen |
| `<source>` | Quelldatei für Audio | Bieten Sie mehrere Formate für bessere Kompatibilität |
| `type` | MIME-Typ der Audiodatei | Hilft Browsern, das richtige Format zu wählen |

```html
<audio controls>
  <source src="podcast.mp3" type="audio/mpeg">
  <source src="podcast.ogg" type="audio/ogg">
  Ihr Browser unterstützt das Audio-Element nicht.
</audio>
<a href="transcript.html">Transkript lesen</a>
```

Tipp: Stellen Sie Transkripte in einem zugänglichen Textformat bereit, idealerweise auf derselben Seite wie der Audioinhalt.

## 8. Testing

### 8.1 Automatisierte Tests
- Nutzen Sie Tools wie axe oder WAVE für erste Überprüfungen

| Tool | Verwendung | Tipp |
|------|------------|------|
| axe DevTools | Browser-Erweiterung für Entwickler | Integriert sich gut in den Entwicklungsprozess |
| WAVE | Online-Tool und Browser-Erweiterung | Bietet visuelle Feedback direkt auf der Webseite |
| Lighthouse | Integriert in Chrome DevTools | Prüft Barrierefreiheit zusammen mit Performance und SEO |

Tipp: Automatisierte Tests sind ein guter Ausgangspunkt, ersetzen aber keine manuellen Tests und Nutzertests.

### 8.2 Manuelle Tests
- Führen Sie Tastatur-Navigation-Tests durch
- Testen Sie mit Screenreadern (z.B. NVDA, JAWS)

| Testmethode | Was zu prüfen ist | Tipp |
|-------------|-------------------|------|
| Tastatur-Navigation | Fokusreihenfolge, Erreichbarkeit aller Funktionen | Testen Sie ohne Maus, nur mit Tastatur |
| Screenreader-Test | Verständlichkeit der Inhalte, korrekte Ankündigungen | Lernen Sie die Grundlagen eines Screenreaders |
| Zoom-Test | Lesbarkeit und Layout bei 200% Zoom | Prüfen Sie auf horizontales Scrollen und überlappendes Layout |
| Farbkontrast-Check | Lesbarkeit von Text und Erkennbarkeit von UI-Elementen | Nutzen Sie Tools wie den WebAIM Contrast Checker |

Tipp: Erstellen Sie eine Checkliste für manuelle Tests und führen Sie diese regelmäßig durch, besonders nach größeren Änderungen.

### 8.3 Nutzertests
- Beziehen Sie Menschen mit Behinderungen in Ihre Testprozesse ein

| Testgruppe | Fokus | Tipp |
|------------|-------|------|
| Screenreader-Nutzer | Navigation, Verständlichkeit von Inhalten | Testen Sie mit verschiedenen Screenreader-Kombinationen |
| Tastatur-Nutzer | Bedienbarkeit ohne Maus | Achten Sie auf Fallstricke wie versteckte Inhalte |
| Nutzer mit eingeschränktem Sehvermögen | Lesbarkeit, Kontraste, Zoom-Funktionalität | Testen Sie verschiedene Kontrasteinstellungen und Zoomstufen |
| Nutzer mit kognitiven Einschränkungen | Klarheit der Sprache, Struktur der Inhalte | Achten Sie auf klare, einfache Anleitungen und konsistentes Design |

Tipp: Planen Sie Nutzertests frühzeitig ein und führen Sie sie regelmäßig durch. Das Feedback von echten Nutzern ist unersetzlich für die Verbesserung der Barrierefreiheit.
