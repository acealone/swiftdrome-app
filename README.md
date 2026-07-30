# SwiftDrome

SwiftDrome is an iOS client for Subsonic-API-compatible music servers (primarily
[Navidrome](https://www.navidrome.org/)), built with SwiftUI and Apple's Liquid
Glass design language.

This repository is the **public release channel** for SwiftDrome. It does not
contain the app's source code — it hosts:

- unsigned `.ipa` builds, published automatically as GitHub Releases whenever
  a change lands on the main development branch
- [`CHANGELOG.md`](CHANGELOG.md), updated alongside each release
- [`source.json`](source.json), an [AltStore](https://faq.altstore.io/)-compatible
  source so SwiftDrome can be installed and updated through AltStore/SideStore

## Installing

1. Copy this source URL:

   ```
   https://raw.githubusercontent.com/acealone/swiftdrome-app/main/source.json
   ```

2. In AltStore or SideStore, go to **Sources → Add Source** and paste the URL.
3. Find SwiftDrome in the source and install it.

Because the `.ipa` is unsigned, it must be sideloaded (AltStore, SideStore,
LiveContainer, or similar) — it is not available on the App Store.

## Releases

Every release is also available directly under this repo's
[Releases](../../releases) page if you'd rather download the `.ipa` by hand
instead of going through AltStore.

## Updates

Releases here are generated automatically by CI in the private development
repository — nothing in this repo is edited by hand day-to-day. If something
looks stale or broken, please open an issue.
