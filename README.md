# SwiftDrome Source

An AltStore/SideStore-compatible app source for SwiftDrome, a native iOS Subsonic/OpenSubsonic client.

## Adding this source

Add the following URL to your sideloading client (AltStore, SideStore, LiveContainer, etc.):

```
https://raw.githubusercontent.com/acealone/swiftdrome-app/main/source.json
```

## About the builds

Builds are unsigned `.ipa`s built from the private SwiftDrome source repo and published here as GitHub Release assets on each tagged version -- no Apple Developer account or signing involved. Suitable for sideloading tools that don't require a valid Apple signature.

See [CHANGELOG.md](CHANGELOG.md) for release history.

## FAQ — design decisions

Things the app does on purpose, and why.

### Why doesn't dragging the progress bar always land where I dropped it?

Because seeking inside a running stream is served by the server, not by the app. A server transcoding on the fly answers without a length and without byte ranges, so there is nothing to ask for the bytes at 2:30 — the player can only move inside the part of the stream it has already pulled down. Drag beyond that and the seek either settles back where playback was or never reports landing at all.

A copy on the device has none of that: it's a complete file, every position in it is reachable exactly, and the app switches to it for the seek whenever one is already there. Which is a large part of why it keeps a small window of tracks around the playhead in the first place.

### Why does the app download only one track at a time?

Two downloads from a server that transcodes on the fly are two transcodes racing each other for the same CPU — and near a crossfade it becomes four, because both tracks are in play. Whichever request loses, stalls; a stalled stream gets re-requested; and a transcoding server answers a re-request with the song from the beginning (see above). One download at a time, in priority order, is slower on paper and audibly better in practice.

### Why do gapless joins only happen with the original file or Opus?

A record mastered as one continuous piece is only seamless if the decoder knows exactly where the audio starts and ends inside each file. The server's original file and Opus carry that information; other on-the-fly transcodes strip it, and a "gapless" join built on guesswork is heard as a click or a stutter at the boundary. Transitions that can't be joined cleanly get the crossfade instead.

### Why does Wi-Fi ask for the original file instead of a smaller transcode?

Three reasons: the original seeks reliably (a file with a known length can be range-requested; an on-the-fly transcode cannot), it's the format gapless joins need, and a lossless copy downloaded at home is still good enough for any connection later — so it never has to be fetched twice. Cellular defaults to Opus, where the bytes matter more than the joins.

### Why are some tracks downloaded that I never asked to download?

The app keeps a small window around the playhead on the device: the next two tracks in the queue, the last few you played, and — on Wi-Fi — the track currently playing. That window is what makes skips land instantly, joins and blends have a file to work from, seeks exact, and a dropped signal survivable. It's a cache, not a library: it evicts itself and respects the storage limit in Settings.
