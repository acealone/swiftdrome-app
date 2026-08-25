# SwiftDrome Source

An AltStore/SideStore-compatible app source for SwiftDrome, a native iOS Subsonic/OpenSubsonic client.

## Adding this source

Add the following URL to your sideloading client (AltStore, SideStore, LiveContainer, etc.):

```
https://raw.githubusercontent.com/acealone/swiftdrome-app/main/source.json
```

## Requirements

- **iOS 26 or later.**
- **Your own music server.** Navidrome is what the app is built and tested against; other Subsonic-compatible servers work too, as far as they support the same features.

## About the builds

Builds are unsigned `.ipa`s built from the private SwiftDrome source repo and published here as GitHub Release assets on each tagged version -- no Apple Developer account or signing involved. Suitable for sideloading tools that don't require a valid Apple signature.

The source can also carry a second entry, **SwiftDrome Nightly**: a build of the newest, still-in-progress version, replaced every time rather than kept as separate versions. Installing it replaces the normal app and keeps your settings and downloads.

See [CHANGELOG.md](CHANGELOG.md) for release history.

## What the app does

### Your library

- Artists, albums, songs, genres and playlists. Albums and artists are grouped by first letter, with a strip down the side to jump around.
- Search, with tabs for artists, albums and songs.
- Favourites for artists, albums, songs and shows, each with their own place in the Library tab and on Home.
- Home shelves for recently played, recently added, most played, random albums, favourites and top artists — tap a headline to see the whole list.
- Your library is copied onto the phone, so browsing is instant and works with no connection. The app checks for new music when it starts, and you can ask for a full refresh any time.
- If your server has more than one library, you can pick which ones you want to see.
- Cover art you've seen is kept on the phone, so browsing looks right offline too.
- **Podcasts.** Any album tagged with a genre like "Podcast" shows up as a show, even if your server split it into several albums. Episodes are listed newest first, and playing one gives you skip-back-15, skip-forward-15 and previous/next episode instead of shuffle and repeat.

### Playing music

- One queue, in the order you'll hear it: the rest of the record you put on plus anything you added yourself. Drag to reorder, swipe to remove. It's still there when you reopen the app.
- The queue keeps itself topped up with music like what's playing, so one song can carry on all evening. **Start Radio** on any song does the same thing on purpose.
- Shuffle and repeat, and an option to leave very short tracks (intros, skits) out of what the queue picks for itself.
- **Crossfade** of up to 12 seconds, and **gapless** playback for albums meant to run without breaks.
- **Two ways of playing.** "System" is the normal one. "Render (alpha)" is a newer one that's better at joining songs and jumping around inside them — see the FAQ below.
- **Volume levelling** (ReplayGain), so a loud remaster doesn't arrive twice as loud as the track before it.
- **Dragging the progress bar lands where you dropped it**, which isn't a given on iOS — see the FAQ.
- **Separate quality for Wi-Fi and mobile data.** At home you get the original file; on data you get a smaller version by default. If a connection can't keep up, the app fetches a smaller copy so the music keeps playing, and gets the good one next time.
- Lyrics, following along line by line if your server has them with timings.
- Sleep timer, AirPlay, lock screen controls, and music that comes back by itself after a phone call or an alarm.
- **Pick up where another device left off.** If something is playing elsewhere and reports to your server, Home offers to continue it here.
- Play counts and scrobbling, which you can turn off.

### Downloads and storage

- The app quietly keeps the songs around what you're listening to — the next couple, the current one, the last few — so skipping is instant and a lost signal doesn't stop the music. This clears itself out and stays inside a size limit you set (512 MB to 10 GB).
- **Downloads are separate and permanent.** Keep a song, an album or a playlist and it stays until you remove it, in whatever quality you choose, over Wi-Fi only unless you allow mobile data. No size limit.
- A Downloaded screen showing kept albums, everything else on the phone, and what's still waiting to arrive — you can cancel one or all of them.
- Every song shows where it stands: queued, downloading, kept, or just cached.

### Look and feel

- Apple's Liquid Glass on the tab bar, mini player and search field, with plain content behind it. The mini player grows into the full player rather than opening a new screen.
- Light, dark or automatic, four accent colours, English and German. Both can be changed inside the app, which matters if you're running it in something like LiveContainer.
- Left-handed mode, which mirrors the buttons on album, artist and playlist screens.
- A small pixel-art companion on the mini player. On by default, and switchable off in Settings → Pets.
- Custom login headers, if your server sits behind something that needs one.
- A log viewer in the app, with crash and hang reports, so a problem can be reported with something attached to it.
- A dot on the server card that says whether your server is answering, and a way to check on demand.

## FAQ — design decisions

Things the app does on purpose, and why.

### Why does dragging the progress bar sometimes wait?

It depends on whether the song is already on your phone.

**If it is, the jump is instant and exact.** iOS on its own is bad at this for some formats — it guesses the spot and can be half a minute out — so the app doesn't let it guess. It finds the right spot itself.

**If the song is still downloading, anything already here is instant too.** Jump back, or forward into the part that's arrived, and it plays right away — no waiting, no re-downloading, and it works with no connection at all.

**If you jump past what's arrived, the app waits for it.** The music keeps playing, the playhead stays where you put it with "waiting for the download" next to it, and playback moves there as soon as the download catches up.

The one case that can still refuse is a song being converted by your server as it sends. There's no way to ask a server for the middle of something it's making up as it goes, so the bar can settle back where the music already was.

### Why does the app download only one song at a time?

If your server converts music as it sends it, two downloads at once means two conversion jobs fighting over the same server — four during a crossfade, since two songs are in play. Whichever one loses stalls, gets asked for again, and a converting server can only answer that by starting the song over. One at a time is slower on paper and better in practice.

The song you're actually listening to comes first, which is why nothing else is fetched while it's still arriving.

### Why is gapless playback only sometimes gapless?

Joining two songs with no gap only works if the app knows exactly where the music starts and ends in each file. Your server's original files carry that, and so does Opus. Other conversions throw it away, and a join based on a guess is heard as a click. Where a clean join isn't possible, you get the crossfade instead.

### Why does Wi-Fi fetch the original file instead of a smaller one?

Three reasons: it's what gapless joins need, jumping around inside it works properly, and a full-quality copy fetched at home is good enough everywhere else — so it never has to be fetched twice. On mobile data the app asks for Opus instead, where the data matters more than the joins.

### Why are songs downloaded that I never asked for?

The app keeps a handful of songs around what you're listening to: the next two, the one playing, and the last few. That's what makes skipping instant, keeps the music going when the signal drops, and lets you jump around inside a song.

It's temporary — it clears itself out and stays inside the storage limit in Settings. **Keep** is the other thing: a song, album or playlist you keep on purpose isn't part of that, isn't deleted on its own, and only goes when you remove it.

### What is "Render (alpha)", and should I turn it on?

It's a second way of playing music. The normal one hands the file to iOS and lets it get on with it. This one plays the audio itself, which means it can put one song straight after another with genuinely nothing in between, and land exactly where you drop the progress bar.

It's marked alpha because bits are still missing rather than because it breaks — a few joins fall back to a small gap. The normal player stays the default. If gapless albums matter to you, it's worth trying; the switch is in Playback settings and you can go back at any time.

### Why did the quality drop in the middle of a song?

Because the alternative is music that stutters, or never starts. If a connection can't carry the quality you asked for, the app fetches a smaller copy so the song plays at all, and asks for the next one at a size that connection can actually manage. The full-quality version replaces it the next time you play that song somewhere better.

You can turn this off in Playback settings. Then you always get exactly the quality you chose — which on a bad connection can mean a long wait, or nothing.

### Why can I see AAC in the format list but not choose it?

Because it doesn't work properly here: every song comes out with a fraction of a second of silence at the start, and no join across that can be clean. The row is left visible but greyed out so the answer to "where did AAC go?" is on screen instead of missing.

### Why does my library have to download before I can browse it?

So browsing doesn't wait on your server every time you open a screen — and works with no connection at all. It's built once, kept on the phone, and topped up when the app starts. The first build takes a while on a big collection, but you can browse while it runs.

### Why do podcasts behave differently from music?

Episodes are streamed and not kept: nothing is downloaded ahead, and nothing stays on the phone afterwards. Downloading an hour-long episode before starting it would mean a long wait for nothing, so episodes stream even on a connection too slow for music. Jumping around inside one asks your server and lands straight away.
