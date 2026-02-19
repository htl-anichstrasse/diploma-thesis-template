## Latex Template für Diplomarbeiten an der HTL Anichstraße

### Überblick über die Dateien und Verzeichnisse
```
├── content
│   ├── abstract.tex            Hier kommen das deutsche und englische Abstract rein
│   ├── einleitung.tex          Grundsätzliches zur gesamten Arbeit, auch indiv. Aufteilung der Arbeiten
│   └── latex_beispiele.tex     Grundsätzliche Latex-Funktionalität wird hier gezeigt 
├── figures
│   ├── bsp.png
│   ├── htl-logo2.png
│   └── htl-logo.png
├── main.tex                    Hier läuft alles zusammen. Dort ist auch Thema, Betreuer, Abteilung, Jahr usw. einzutragen
├── references.bib              Alle Zitate befinden sich hier. In latex_beispiele wird gezeigt wie man diese einbindet
├── sourcecode
│   └── First.java
├── template
│   ├── affirmation.tex         Eidesstattliche Erklärung
│   ├── listing_format.tex      Wie soll der Quellcode formatiert werden? Anwendung dazu in content/latex_beispiele
│   ├── lock_flag.tex           Falls ein Sperrvermerk gemacht werden soll, dieses file einblenden bzw. ausblenden (in main.tex)
│   ├── main_settings.tex       Grundsätzliches zum Basislayout. Hier sollte man wenig ändern müssen
│   ├── mycommands.tex          Bestimmte Befehle werden hier überschrieben für einheitliches Layout. Hier sollte man wenig ändern müssen
│   ├── pdf_settings.tex        Parameter für die PDF-Generierung. Hier sollte man wenig ändern müssen
│   ├── preamble.tex            Hier kommen die ganzen imports hin
│   ├── title_thesis_htlinn.tex Das Titelblatt, hier werden die Infos von main.tex eingebaut
│   └── typographic_settings.texHier sollte man wenig ändern müssen
```
## Anpassungen

### Einseitige Ansicht

In der Datei template/preamble.tex ist für die *documentclass* ganz oben ein Parameter *twoside = true* zu finden. Setzt man diesen auf *false* wechselt die Einrückung nicht bei jeder Seite sondern bleibt gleich  

### Ändern der Zitierweise

Möchte man z.B. auf IEEE-Zitierung umstellen (d.h. eine Literaturstelle wird mit [1], [2], [3] referenziert) muss man in *main.tex* folgende Zeilen auskommentieren und die 2 unteren hinzufügen

```latex
%\usepackage{natbib} %
%\bibliographystyle{agsm}
\usepackage{cite}
\bibliographystyle{IEEEtran}
```

Man muss allerdings vorher alle bereits von Latex erzeugten Dateien löschen.

### Im Header soll nur der Autor stehen der das Kapitel geschrieben hat

Vor dem Kapitel muss man dann


```latex
\renewcommand{\myauthor}{AUTOR1} 
```
eintragen
