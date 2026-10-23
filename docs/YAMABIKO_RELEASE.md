# YamabikoChat iOS distribution fork

This fork publishes the full iOS flavor only. The Node.js base and complete
materialized source tree remain pinned by `upstream-base.txt` and
`expected-tree.txt`. The upstream mobile patch series is rebased onto Node.js
24.22.1 (October 2026 security release). Upstream README changes are retained;
upstream CI file removals were refreshed. Runtime patches applied cleanly.

Review and merge the upgrade PR, then dispatch **Yamabiko iOS release** on
`recipe`. The workflow cold-builds both arm64 slices, combines the framework,
runs the existing curated iOS Simulator JS suite, the upstream Brotli/TLS
security regression tests, and native-addon test, then
publishes an iOS-only prerelease with SHA256SUMS, the composite LICENSE and
source provenance. Tags point to the recipe commit. No shared compiler or
binary cache is used for release builds. Do not upload or replace release
binaries manually; fix the source and run a new versioned release instead.

The inherited all-platform release pipeline is removed in this fork because
its Android and BrowserStack credentials and gates are outside this iOS-only
scope. This release does not claim upstream's Android or physical-device gates.
The original release process remains documented in RELEASING.md for reference.
