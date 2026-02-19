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

### Die Ränder der Seite sind zu groß (bzw. der Textbereich ist zu klein)

In der Datei *template/preamble.tex* ist der Parameter *DIV* für die *Documentclass*, diesen verändern, z.B.:


```latex
\documentclass[%
enabledeprecatedfontcommands,
fontsize=\myfontsize,%% size of the main text
paper=\mypapersize,  %% paper format
parskip=\myparskip,  %% vertical space between paragraphs (instead of indenting first par-line)
DIV=11,            %% calculates a good DIV value for type area; 66 characters/line is great
headinclude=true,    %% is header part of margin space or part of page content?
footinclude=false,   %% is footer part of margin space or part of page content?
open=right,          %% "right" or "left": start new chapter on right or left page
appendixprefix=true, %% adds appendix prefix; only for book-classes with \backmatter
bibliography=totoc,  %% adds the bibliography to table of contents (without number)
draft=\mydraft,      %% if true: included graphics are omitted and black boxes
                     %%          mark overfull boxes in margin space
BCOR=\myBCOR,        %% binding correction (depends on how you bind
                     %% the resulting printout.
%\mylaterality        %% oneside: document is not printed on left and right sides, only right side
                     %% twoside: document is printed on left and right sides
twoside = true
]{scrbook}  %% article class of KOMA: "scrartcl", "scrreprt", or "scrbook".
            %% CAUTION: If documentclass will be changed, *many* other things
```   
