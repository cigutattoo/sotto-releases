# Sotto Releases

Android APK binaries for Sotto. **Source code is not public yet** (pending audit /
reproducible build / real-world usage); only release binaries are published here.

## Signing (verify before installing)

All APKs in this repo are signed with the same certificate. Before installing,
verify the certificate fingerprint matches the one below. The fingerprint never
changes for any legitimate Sotto release on any channel — if it doesn't match,
it's not from us.

**Release signing certificate SHA-256 (capsule)**

```
DD:72:BC:31:36:83:62:86:04:DF:68:A9:68:6C:29:F1:9B:E7:E3:0C:F1:BC:49:60:5A:6E:22:47:7F:FC:70:8D
```

How to verify on your own machine (requires the Android SDK `apksigner`):

```
apksigner verify --print-certs app-arm64-v8a-release.apk
```

Look for "Signer #1 certificate DN: CN=Sotto" and the fingerprint above.

## Checksums

Every release has a `SHA256SUMS` file attached. After downloading, run the
corresponding command for your platform:

```
# Linux / macOS
sha256sum -c SHA256SUMS

# macOS (alternative)
shasum -a 256 -c SHA256SUMS

# Windows PowerShell
Get-FileHash app-arm64-v8a-release.apk -Algorithm SHA256
# Compare the output against SHA256SUMS
```

## Assets per release

| File | Description | Size (v1.0.0) |
| --- | --- | --- |
| `app-arm64-v8a-release.apk` | 64-bit ARM (almost all Android phones 2018+) | ~40 MB |
| `app-armeabi-v7a-release.apk` | 32-bit ARM (older phones) | ~31 MB |
| `app-x86_64-release.apk` | x86_64 (emulators / very rare Intel Android devices) | ~46 MB |
| `app-release.aab` | Google Play format (not for sideloading) | ~82 MB |
| `SHA256SUMS` | Checksum file for all four artifacts | — |

## Version history

| Version | Notes |
| --- | --- |
| v1.0.0 | Initial public release |

## What this repo is

This repo holds release binaries only. Source code, issue tracker, and
documentation live in `cigutattoo/sotto` (private, until open-source conditions
are met). The release binaries here are **exactly** the ones built from the
commit tagged `v1.0.0` in the private source repo — that tag's commit hash is
recorded in each release note.
