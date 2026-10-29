# Synta

[English](README.md) | **Deutsch**

Ein Quelltext-Betrachter mit Syntaxhervorhebung (Lister-Plugin) für den [Total Commander](https://www.ghisler.com), 32 und 64 Bit.
F3 auf einer Quelltext-Datei, und sie lässt sich direkt lesen – mit Syntaxhervorhebung, Zeilennummern und auf Wunsch einer Minimap. Ein Schalter zeigt minimierten oder unordentlichen Code formatiert an – die Datei selbst wird nie verändert. Sprachen und Farbschemen sind Textdateien, die jeder erweitern kann. Nativ, ohne Laufzeitumgebung, außer dem Plugin muss nichts installiert werden.

![Synta zeigt eine HTML-Datei formatiert, mit Zeilennummern und Minimap](docs/screenshot.png)

## Unterstützte Sprachen

C, C++, C#, Java, JavaScript, TypeScript, Python, PowerShell, Batch, Shell, SQL, Go, Rust, PHP, HTML (mit eingebettetem CSS und JavaScript), Astro, XML, CSS, SCSS/Less, JSON, YAML, TOML, INI, Registry-Dateien, Markdown, Diff, Lua, Pascal/Delphi, Visual Basic, Ruby, Kotlin, Swift, AutoHotkey, AutoIt, Makefile, Dockerfile, CMake, EDIFACT, CSV/TSV (jede Spalte in einer eigenen Farbe) und Syntas eigene Definitionsdateien.

Dateien ohne Endung werden an ihrem Namen (`Makefile`, `Dockerfile`) oder an einer `#!`-Zeile erkannt.

## Funktionen

- **Formatiert anzeigen** (Strg+B, Schalter oben rechts): JSON, XML, HTML, CSS, SQL und C-ähnliche Sprachen werden schön eingerückt; nur Leerraum ändert sich
- Zeilenumbruch, Minimap, Zeilennummern, Einrückungslinien, hervorgehobene aktuelle Zeile
- Sprachauswahl oben links, falls eine Datei falsch erkannt wurde
- Mit der Maus markieren (Doppelklick: Wort, Klick auf eine Zeilennummer: Zeile), mit Strg+C kopieren, mit Strg+A alles markieren
- Suche mit dem Suchen-Dialog des Total Commanders (F7 / F3), Gehe zu Zeile (Strg+G)
- Zoom mit Strg+Mausrad; Schriftart und Tabulatorbreite wählbar
- Helles und dunkles Design (automatisch wie Windows, wie Total Commander oder fest) im Windows-11-Stil; Farbschemen Ayu (Light, Dark, Mirage, Mirage Light), GitHub, Solarized, One, Catppuccin, Gruvbox, Tokyo Night, Rosé Pine und Visual Studio (jeweils hell und dunkel)
- Textkodierungen: UTF-8, UTF-16 (mit oder ohne BOM) und ältere Codepages (Windows 125x, CP866, CP850, KOI8, Shift-JIS, GBK, Big5, ...), automatisch erkannt und im Kontextmenü umschaltbar (Kodierung); Dateien bis 512 MB
- Statusleiste mit Sprache, Kodierung, Zeilenenden, Zeilenzahl und Cursorposition
- Deutsche und englische Oberfläche (folgt der Windows-Sprache)

## Eigene Sprachen und Farbschemen

- `Languages\*.lang`: eine Datei pro Sprache (Schlüsselwörter, Kommentare, Zeichenketten, …). `Languages\_template.lang` erklärt jeden Schlüssel.
- `Themes\*.theme`: eine Datei pro Farbschema; Farben als `#RRGGBB` oder `#RRGGBBAA`, optional fett / kursiv.
- Kontextmenü → *Ordner „Languages“ öffnen* / *Ordner „Themes“ öffnen*. Neue oder geänderte Dateien gelten für die nächste Datei, die der Lister öffnet; Fehler stehen in der Statusleiste und unter *Fehler in Definitionsdateien…*.
- Um eine eingebaute Sprache zu ändern, kopiere ihre Datei und setze in der Kopie `Priority=1` – ein Update ersetzt die eingebauten Dateien, nicht deine Kopie.

## Erkennungszeichenfolge

Der Total Commander bietet Synta nur die Dateien an, auf die seine *Erkennungszeichenfolge* (Detect string) passt. Synta baut sie bei der Installation aus den Endungen aller `Languages\*.lang`-Dateien; im Synta öffnen sich also nur bekannte Quelltext-Typen (dazu Dateien ohne Endung, die Synta selbst prüft). `.ts` und `.mts` brauchen den Term `MULTIMEDIA`, weil der Total Commander sie als Video behandelt.

Für die Erkennungszeichenfolge erlaubt der Total Commander 2 KB. Wird die Liste der Endungen länger (viele eigene Sprachen), weicht Synta auf „alles außer üblichen Binärtypen“ aus (`!(EXT="EXE"|EXT="DLL"|…)`); Dateien ohne Sprache lehnt Synta dann beim Laden ab.

Um Synta auf die gewünschten Typen zu beschränken, ändere die Zeichenfolge unter *Konfigurieren → Optionen → Plugins → Lister-Plugins → Synta → Konfigurieren* oder `detect=` im Abschnitt `[ListerPlugins]` der `wincmd.ini` (nur bei geschlossenem Total Commander):

```
EXT=""|EXT="C"|EXT="H"|EXT="CPP"|EXT="PY"|EXT="JS"|EXT="JSON"|EXT="LANG"|EXT="THEME"|(MULTIMEDIA & (EXT="TS"|EXT="MTS"))
```

## Download und Installation

1. **`Synta.zip`** von der [neuesten Version](https://github.com/naderi/tc-synta/releases/latest) herunterladen.
2. Die ZIP-Datei im Total Commander öffnen (Enter auf der Datei) und die Frage nach der Installation des Plugins bestätigen.

Die Einstellungen stehen in `Synta.ini` neben dem Plugin (alle Schlüssel sind im Abschnitt [Einstellungen](#einstellungen) beschrieben). Voraussetzung: Windows 10 oder 11.

JSON und XML zeigt auch [TreeView](https://totalcmd.net/plugins/treeview) (als Baum und Raster). Sind beide Plugins installiert, öffnet das in *Konfigurieren → Plugins → Lister-Plugins* zuerst aufgeführte diese Dateien.

## Tasten

| Taste | Aktion |
|---|---|
| Strg+B | *Formatiert anzeigen* an / aus |
| Strg+G | *Gehe zu Zeile…* |
| Strg+A, Strg+C | Alles markieren, kopieren |
| F7 / F3 | Suchen (Suche des Total Commanders) |
| Strg+Mausrad | Zoom |
| Pfeiltasten, Bild auf / ab, Pos1, Ende | Scrollen |
| F1 | Über Synta |

Weitere Optionen – *Zeilenumbruch*, *Minimap*, *Zeilennummern*, *Textcursor*, *Knöpfe* (oben, Statusleiste oder ausgeblendet), *Tabulatorbreite*, *Zeilenabstand*, *Design*, *Farbschema*, *Schriftart…* – stehen im Kontextmenü (Rechtsklick).

## Einstellungen

`Synta.ini` (Abschnitt `[Synta]`) wird bei der ersten Nutzung neben dem Plugin angelegt; ist dieser Ordner schreibgeschützt, neben der `lsplugin.ini` des Total Commanders. Die meisten Werte lassen sich auch im Lister ändern; sie werden in die Datei zurückgeschrieben.

| Schlüssel | Werte | Bedeutung |
|---|---|---|
| `Theme` | `0` automatisch (Standard), `1` hell, `2` dunkel, `3` wie Total Commander | `0` ist dunkel, wenn der Total Commander oder Windows dunkel ist; `3` folgt nur dem Dunkelmodus des Total Commanders |
| `LightScheme` | Schemaname (Standard `Ayu Light`) | Farbschema im hellen Design |
| `DarkScheme` | Schemaname (Standard `Ayu Dark`) | Farbschema im dunklen Design (auch `Ayu Mirage`) |
| `Font` | Schriftname (Standard `Cascadia Mono`) | Code-Schriftart, nur Festbreitenschriften |
| `FontSize` | `6`–`40` (Standard `10`, Dezimalstellen erlaubt) | Größe in Punkt |
| `TabWidth` | `1`–`16` (Standard `4`) | Breite eines Tabulators in Zeichen |
| `Wrap` | `1` / `0` (Standard `0`) | Zeilenumbruch |
| `LineNumbers` | `1` / `0` (Standard `1`) | Zeilennummern |
| `Formatted` | `1` / `0` (Standard `0`) | Formatiert anzeigen |
| `Minimap` | `1` / `0` (Standard `0`) | Minimap |
| `Buttons` | `1` / `2` / `0` (Standard `1`) | Wo die Knöpfe für Sprache, Zeilenumbruch, Minimap und *Formatiert anzeigen* sitzen: `1` obere Leiste, `2` Statusleiste, `0` ausgeblendet; alles bleibt im Kontextmenü erreichbar. Ein älteres `TopBar=0` wird zu `2`. |
| `LineSpacing` | `0`–`40` (Standard `4`) | Zusätzlicher Zeilenabstand in Pixeln |
| `Cursor` | `1` / `0` (Standard `1`) | Textcursor: Die Pfeiltasten bewegen ihn (Umschalt markiert, Strg+Pfeile springen wortweise, Strg+Pos1 / Ende) statt zu scrollen |

## Lizenz

Freeware – frei nutzbar, aber **nicht zum Verkauf**. Siehe [LICENSE](LICENSE). Farbpalette Ayu von dempfi (MIT-Lizenz).

## Unterstützung

Wenn Synta dir Zeit spart, kannst du die Entwicklung auf Ko‑fi unterstützen. ☕

<a href='https://ko-fi.com/N7N123QIX0' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=6' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

---

© 2026 [Ali Naderi](https://github.com/naderi) · [digitalent.dev](https://digitalent.dev/de/)
