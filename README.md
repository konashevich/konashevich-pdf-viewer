# PDF Viewer (Page Scroll)

A PDF viewer for VS Code and Cursor, based on [PDF.js](https://mozilla.github.io/pdf.js/). It opens every `.pdf` file in an editor tab and shows one page at a time by default.

- [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=oleksiiko.konashevich-pdf-viewer)
- [Open VSX](https://open-vsx.org/extension/oleksiiko/konashevich-pdf-viewer)

## Features

- **Page-by-page scrolling.** The mouse wheel moves to the next or previous page when you reach the edge of the current one.
- **Page Fit by default.** A new document opens with the whole page visible.
- **Dual Page Mode.** The Tools menu (`>>`) has a *Dual Page Mode* action that shows two pages side by side, fitted to the window.
- **Printing.** The Print button, `Ctrl+P` and the menu entry open the system print dialog. See [Printing](#printing).
- **Live reload.** The view refreshes when the PDF file changes on disk and keeps the current page.
- **Links to other PDFs.** Relative links between PDF files open in a new tab.

## Printing

Printing inside an editor webview does not work: the browser print call returns at once and PDF.js closes its "Preparing document for printing" dialog. This extension therefore starts an installed Chromium-based browser in a temporary window that shows the PDF and opens the operating system print dialog.

The extension looks for Chrome, Edge, Brave or Chromium in their standard install locations on Windows, macOS and Linux. Edge is included with Windows 11. If none is found, the extension shows a warning. The temporary profile and files are deleted when the browser window closes.

## Settings

| Setting | Default | Description |
| --- | --- | --- |
| `acaciaPdf.scrollMode` | `page` | Default scroll mode: `page`, `vertical`, `horizontal` or `wrapped`. |

The setting key keeps its original name so that existing configurations continue to work.

## Installation

Install **PDF Viewer (Page Scroll)** from the Visual Studio Marketplace or Open VSX (Cursor uses Open VSX). To install a VSIX file instead, run `Extensions: Install from VSIX...` from the Command Palette.

To make this viewer the default for PDF files, use `Open With...` on a PDF and choose **PDF Viewer (Page Scroll)**.

## Development

The repository holds the compiled extension (`dist/extension.js`), the viewer script (`assets/main.mjs`) and the PDF.js distribution (`assets/pdf.js`). There is no TypeScript source in this repository, and `dist/extension.js` is edited directly.

- `pdfjs_version.txt` pins the PDF.js release and its SHA-1 hash.
- `patches/pdf.js.patch` holds the changes applied to the PDF.js viewer.
- `tools/prepare_pdfjs.sh` downloads the pinned PDF.js release into `assets/pdf.js` and reapplies the patch.

Package and publish:

```bash
npm run package        # builds konashevich-pdf-viewer-<version>.vsix
npm run publish:vsce   # needs VSCE_PAT
npm run publish:ovsx   # needs OVSX_PAT
```

## License and credits

Licensed under the [Apache License 2.0](LICENSE.txt).

This extension is a fork of [mathematic-inc/vscode-pdf](https://github.com/mathematic-inc/vscode-pdf) (Copyright 2021 Mathematic, Inc.) and bundles [PDF.js](https://github.com/mozilla/pdf.js) by Mozilla, which is also licensed under Apache 2.0. See [CHANGELOG.md](CHANGELOG.md) for the history of changes.
