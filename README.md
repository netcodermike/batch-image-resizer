# Batch Image Resizer

Write resized PNG copies of selected Mac images into an explicit output folder.

[![Build and verify](https://github.com/netcodermike/batch-image-resizer/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/batch-image-resizer/actions/workflows/verify.yml)

**Language:** Swift · **Platform:** macOS desktop · **App type:** Mac image resize and format conversion app

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- Multiple image selection
- Maximum-edge scaling
- Orientation-aware thumbnail generation
- Existing outputs rejected

## Requirements

macOS 13+ and Xcode command-line tools supporting Swift 5.9+. No external packages.

## Quick start

```sh
git clone https://github.com/netcodermike/batch-image-resizer.git
cd batch-image-resizer
swift build
swift run LocalApp
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Choose maximum edge 800, select landscape/portrait images, and choose a new output folder. Inspect orientation and output dimensions; run again to confirm existing output names are rejected.

## Architecture, configuration, and data

App.swift uses an AppKit file/folder picker and ImageIO thumbnail transformation, followed by PNG encoding. Inputs are untouched. Output names append -resized.png and existing names are rejected. The batch is capped at 100 selected files. Core dimension tests check aspect ratio and small-image behavior; target GUI and actual export acceptance remain manual.

## Verification

Build with the quick-start command where needed, then run:

```sh
swift run LocalApp --self-test
```

Manual acceptance: Choose maximum edge 800, select landscape/portrait images, and choose a new output folder. Inspect orientation and output dimensions; run again to confirm existing output names are rejected. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

No overwrite mode, metadata preservation guarantee, arbitrary format output, recursive scan, progress cancellation, or color-management controls. Operations are synchronous; large files can block the UI. ImageIO controls thumbnail resampling. Two inputs with the same stem can collide.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `Package.swift`
- `Sources/LocalApp/App.swift`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
