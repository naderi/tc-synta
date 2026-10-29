# Synta

**English** | [Deutsch](README.de.md)

A source code viewer with syntax highlighting (Lister plugin) for [Total Commander](https://www.ghisler.com), 32 and 64 bit.
Press F3 on a source file and read it right there – with syntax highlighting, line numbers and an optional minimap. A switch shows minified or messy code formatted – the file itself is never changed. Languages and color schemes are plain text files that anyone can extend. Native, no runtime, nothing to install besides the plugin.

![Synta showing an HTML file formatted, with line numbers and the minimap](docs/screenshot.png)

## Supported languages

C, C++, C#, Java, JavaScript, TypeScript, Python, PowerShell, Batch, Shell, SQL, Go, Rust, PHP, HTML (with embedded CSS and JavaScript), Astro, XML, CSS, SCSS/Less, JSON, YAML, TOML, INI, Registry files, Markdown, Diff, Lua, Pascal/Delphi, Visual Basic, Ruby, Kotlin, Swift, AutoHotkey, AutoIt, Makefile, Dockerfile, CMake, EDIFACT, CSV/TSV (every column in its own color) and Synta's own definition files.

Files without an extension are recognized by their name (`Makefile`, `Dockerfile`) or by a `#!` line.

## Features

- **Show formatted** (Ctrl+B, switch at the top right): JSON, XML, HTML, CSS, SQL and C-like languages pretty-printed; only white space changes
- Word wrap, minimap, line numbers, indent guides, highlighted current line
- Language picker at the top left, in case a file was recognized wrongly
- Select with the mouse (double-click: word, click on a line number: line), copy with Ctrl+C, select all with Ctrl+A
- Search with Total Commander's Find (F7 / F3), go to line (Ctrl+G)
- Zoom with Ctrl+mouse wheel; selectable font and tab width
- Light and dark design (automatic like Windows, or fixed) in the Windows 11 look; color schemes Ayu Light, Ayu Dark and Ayu Mirage
- Text encodings: UTF-8, UTF-16 (with or without BOM) and legacy code pages (Windows 125x, CP866, CP850, KOI8, Shift-JIS, GBK, Big5, ...), detected automatically and switchable in the context menu (Encoding); files up to 512 MB
- Status bar with language, encoding, line endings, number of lines and the cursor position
- English and German user interface (follows the Windows language)

## Own languages and color schemes

- `Languages\*.lang`: one file per language (keywords, comments, strings, …). `Languages\_template.lang` explains every key.
- `Themes\*.theme`: one file per color scheme; colors as `#RRGGBB` or `#RRGGBBAA`, optionally bold / italic.
- Context menu → *Open "Languages" folder* / *Open "Themes" folder*. New or changed files are used for the next file the Lister opens; errors are shown in the status bar and under *Errors in definition files…*.
- To change a built-in language, copy its file and set `Priority=1` in the copy – an update replaces the built-in files, not your copy.

## Download and installation

1. Download **`Synta.zip`** from the [latest release](https://github.com/naderi/tc-synta/releases/latest).
2. Open the ZIP in Total Commander (Enter on the file) and confirm the question whether to install the plugin.

Settings are stored in `Synta.ini` next to the plugin (all keys are described in the [Settings](#settings) section). Requires Windows 10 or 11.

JSON and XML are also shown by [TreeView](https://totalcmd.net/plugins/treeview) (as tree and grid). If both plugins are installed, the one listed first in *Configuration → Plugins → Lister plugins* opens these files.

## Keys

| Key | Action |
|---|---|
| Ctrl+B | *Show formatted* on / off |
| Ctrl+G | *Go to line…* |
| Ctrl+A, Ctrl+C | Select all, copy |
| F7 / F3 | Find (Total Commander's search) |
| Ctrl+mouse wheel | Zoom |
| Arrow keys, Page Up / Down, Home, End | Scroll |
| F1 | About |

More options – *Word wrap*, *Minimap*, *Line numbers*, *Text cursor*, *Top bar*, *Tab width*, *Theme*, *Color scheme*, *Font…* – are in the context menu (right click).

## Settings

`Synta.ini` (section `[Synta]`) is created next to the plugin on first use; if that folder is read-only, next to Total Commander's `lsplugin.ini`. Most values can also be changed in the Lister; they are written back to the file.

| Key | Values | Meaning |
|---|---|---|
| `Theme` | `0` automatic (default), `1` light, `2` dark, `3` like Total Commander | `0` is dark if Total Commander or Windows is dark; `3` follows only Total Commander's dark mode |
| `LightScheme` | scheme name (default `Ayu Light`) | Color scheme in light mode |
| `DarkScheme` | scheme name (default `Ayu Dark`) | Color scheme in dark mode (also `Ayu Mirage`) |
| `Font` | font name (default `Cascadia Mono`) | Code font, fixed-pitch fonts only |
| `FontSize` | `6`–`40` (default `10`, decimals allowed) | Size in points |
| `TabWidth` | `1`–`16` (default `4`) | Width of a tab in characters |
| `Wrap` | `1` / `0` (default `0`) | Word wrap |
| `LineNumbers` | `1` / `0` (default `1`) | Line numbers |
| `Formatted` | `1` / `0` (default `0`) | Show formatted |
| `Minimap` | `1` / `0` (default `0`) | Minimap |
| `TopBar` | `1` / `0` (default `1`) | Top bar with language, word wrap, minimap and *Show formatted*. `0` hides it; everything stays available in the context menu. |
| `Cursor` | `1` / `0` (default `1`) | Text cursor: arrow keys move it (Shift selects, Ctrl+arrows jump by word, Ctrl+Home / End), instead of scrolling |

## License

Freeware – free to use, but **not for sale**. See [LICENSE](LICENSE). Color palette Ayu by dempfi (MIT license).

## Support

If Synta saves you time, you can support its development on Ko‑fi. ☕

<a href='https://ko-fi.com/N7N123QIX0' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://storage.ko-fi.com/cdn/kofi2.png?v=6' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

---

© 2026 [Ali Naderi](https://github.com/naderi) · [digitalent.dev](https://digitalent.dev/en/)
