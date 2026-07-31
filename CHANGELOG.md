# Changelog

All notable changes to SwiftDrome are documented here.

## [Unreleased]

- Add sync-app-repo.yml: continuous README/CHANGELOG sync to the public repo
- Update CHANGELOG.md in the public app repo on release too

## [0.1.0] - 2026-07-30

- Replace custom pill tab bar with native iOS 26 search-role tab
- Publish releases to acealone/swiftdrome-app on version tags
- Add VS Code workspace config, resolved package pins, and app bootstrap plan
- Simplify pill tab bar bubble to Apple's built-in glass interaction
- Fix search circle and back button taps not registering
- Revert bottom bar to independent glass effects, drop the morph
- Bring MiniPlayerView into the same glass container as the tab bar
- Fix remaining pill bar glass-on-glass, flaky search taps, keyboard margin

## [latest-build] - 2026-07-27

- Bypass login for UI testing; give every CI run a direct .ipa link
- Attach glassEffectID directly to each component's glass effect, not its wrapper
- Fix Sendable conformance on swiftDromeGlassEffectID's id parameter
- Uniform pill-bar scaling and morphing search expand animation
- Make search expand/collapse the bottom bar instead of navigating to a tab
- Auto-focus search field on tab switch
- Make the pill bubble fully clear glass while dragging
- Add top-right profile button, trim tab bar to 3 tabs, fix bubble squeeze timing
- Drop signing entirely -- ship unsigned IPA for sideloading
- Call swift sdk install directly instead of xtool sdk install
- Discover the Darwin SDK bundle name instead of assuming darwin.xtoolsdk
- Install missing swift runtime deps before swiftly toolchain install
- Split anisette libs out of the XTOOL_CONFIG_B64 secret
- Add GitHub Action to build, sign, and release an IPA via xtool

## [xtool-sdk-v1] - 2026-07-15

- Add search circle, playlists tab, and localization to tab bar
- Add draggable pill tab bar, Home and Settings tabs
- Round out Liquid Glass adoption in the mini player and now-playing view
- feat: add track thumbnails to QueueView
- feat: add thumbnails to search results
- feat: add cover art header and track thumbnails to PlaylistDetailView
- feat: add cover art header to AlbumDetailView
- feat: add artist avatar to ArtistsListView
- feat: render Playlists as a cover-art grid
- feat: render Albums as a cover-art grid
- refactor: use CoverArtImage in MiniPlayerView and NowPlayingView
- feat: add CoverArtImage component
- feat: decode coverArt on Playlist
- docs: add implementation plan for cover art and grid layouts
- docs: add design spec for cover art and grid layouts
- fix: correct audio session timing, load-failure detection, and mini-player glass-on-glass per design spec
- feat: wire tab navigation, playback, and Liquid Glass chrome into the app
- feat: add MainTabView with Liquid Glass mini-player accessory
- feat: add library home with category picker
- feat: add search
- feat: add genre browsing
- feat: add playlist browsing with tap-to-play
- feat: add artist and album browsing with tap-to-play
- feat: add mini-player bar
- feat: add Now Playing sheet and Queue view
- fix: guard stale artwork race and drop unsupported macOS platform from App package
- feat: add lock-screen and Control Center integration to PlayerService
- feat: add scrobbling and favorite toggling to PlayerService
- feat: add PlayerService wrapping AVPlayer around QueueEngine
- feat: add Liquid Glass compatibility helpers
- feat: add genre filtering to getAlbumList2
- docs: add implementation plan for Liquid Glass navigation and playback
- docs: add design spec for Liquid Glass navigation and playback UI
- fix: set explicit Keychain accessibility (AfterFirstUnlockThisDeviceOnly) for stored credentials
- feat: wire login and artist-list flow into RootView
- fix: make SessionStore @MainActor, remove nonisolated(unsafe) workaround
- feat: add LoginView
- feat: add SessionStore for login/session state
- feat: add Keychain-backed ServerCredentials storage
- chore: scaffold App package (xtool project)
- docs: update SwiftDrome spec for xtool-based App package (no Mac/Xcode required)
- feat: add public initializers to Album, Artist, Playlist, Genre, SearchResults
- feat: add typed HTTP-status error to SubsonicClient
- fix: make QueueEngine back()/advance() symmetric via redo stack
- feat: add non-destructive context reset to QueueEngine
- feat: add Play-Next priority stack to QueueEngine
- feat: add QueueEngine context playback and history back-skip
- feat: add playlist mutation, favorites, scrobble, and media URL endpoints
- feat: add library browsing endpoints to SubsonicClient
- feat: add SubsonicClient core with auth request building and error handling
- feat: add Subsonic models and response envelope decoding
- docs: fix typo'd MD5 test vector in SwiftDromeKit plan
- feat: add Subsonic token auth hashing
- chore: scaffold SwiftDromeKit package
- docs: add SwiftDromeKit core implementation plan
- docs: add SwiftDrome V1 design spec

