# Acacia PDF Viewer

Fork of the VS Code PDF custom editor configured for Project Acacia. The viewer defaults to page-by-page scrolling and exposes `acaciaPdf.scrollMode` so the behaviour stays consistent across machines.

## Installation

1. `cd /mnt/merged_ssd/Public-VS-Private/konashevich-pdf-viewer`
2. `npm install`
3. `npm run package` (rebuilds the bundled assets)
4. `npx vsce package` (produces `konashevich-pdf-viewer-1.0.0.vsix`)
5. Install the VSIX either via `code --install-extension konashevich-pdf-viewer-1.0.0.vsix` or the VS Code command palette (`Extensions: Install from VSIX...`).
6. Reload VS Code; PDFs will open with `konashevich.pdf.view` and respect the configured scroll mode.

## Configuration

`acaciaPdf.scrollMode` supports `page`, `vertical`, `horizontal`, and `wrapped`. The default remains `page` to ensure discrete scrolling.
