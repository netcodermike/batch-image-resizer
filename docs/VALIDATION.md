# Validation

Authoring date: November 6, 2026. Host: Windows. Target: macOS desktop.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `macos-latest`:

```sh
swift build -c release
swift run -c release LocalApp --self-test
```

## Manual acceptance

Choose maximum edge 800, select landscape/portrait images, and choose a new output folder. Inspect orientation and output dimensions; run again to confirm existing output names are rejected. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.

## Observed CI result

Passed: [target-platform build/check](https://github.com/netcodermike/batch-image-resizer/actions/runs/42205433281). Source commit: `6b3fb0c3070c8eeaadaa6cba3447163225a9e135`. Later documentation-only changes do not alter the tested implementation. The reproducible commands above identify test scope; native GUI/audio/permissions are not implied by compilation.
