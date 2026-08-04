# Changelog

## [Unreleased]

- Fixed the Now Playing background dropping to black for a moment when a track changed. Cover art is now kept in memory, so it also appears instantly on screens you've already visited.
- Now Playing reports the codec you're actually hearing rather than the format of the file on the server, which differ whenever the server is transcoding. The bit rate is shown only where it describes the stream.
- The buffering notice sits above the progress bar instead of below the times, where it pushed the controls down as it came and went.
- A crossfade now shows in the metadata line as a moving indicator that tracks the blend, replacing the caption that named the incoming track and counted seconds.
- The queue needs no Edit button. Tracks you queued yourself carry a grip on the right and can be dragged into order at any time, and every row swipes away to remove it. A labelled rule marks where your queue ends and the tracks that follow on their own begin — those can be removed but not reordered.

## [0.4.0] - 2026-08-04

### One track into the next

- Tracks now crossfade: the next one starts before the current one ends, with the outgoing track fading out as the incoming one fades in. The overlap is 6 seconds by default and can be set anywhere from 0 to 12, or turned off, on the new Playback screen in Settings.
- Consecutive album tracks are joined gaplessly instead of blended, so records mastered as one continuous piece finally play as one. Only a genuine continuation is joined — track 1 into track 3 was never meant to butt together, so it gets the crossfade like any other transition, as does a track the server sends no number for.
- A gapless join needs the server's original file or an Opus stream: any other transcode on the way out strips the information a seamless join depends on. Wi-Fi asks for the original file by default, so that's where it applies unless you change it.
- Playback no longer runs out. The queue keeps itself stocked with ten tracks similar to what you're listening to, topped up as they play, so a single song can carry on indefinitely. Where a server has no similar tracks to offer, it falls back to other songs by the artists you're playing, drawn from a random album of theirs rather than the same few tracks every time. Starting from an album still queues the rest of that album first.

### Now Playing

- The screen has been rebuilt around the crossfade, which you can now see happening: the cover art of the track coming in dissolves across the one going out, the background colour turns over with it, and a line under the progress bar names the incoming track. The tail of the bar is marked, so you can see where the next track will start blending in.
- It says what you're actually hearing — genre and year above the progress bar, and beneath it whether the track is streaming or playing from the device, its format, bitrate and ReplayGain.
- Added a sleep timer: 15, 30, 45 or 60 minutes, after which playback pauses where it got to, so pressing play carries on.
- The layout follows Apple Music more closely. The volume slider is gone, play/pause has lost its surrounding circle, and the row along the bottom is AirPlay, download state, lyrics, queue and the sleep timer, with favourite and a menu button above the progress bar.
- Dragging the progress bar no longer fights you: the handle stays where you put it while you drag, and playback jumps once you let go. The lock screen and Control Center bar follows playback and can be dragged too, and the two stay in step after a stall or a buffer.
- Reopening the app brings back what you were listening to: the miniplayer shows the track paused where you left off, and pressing play carries on from there.

### Queue

- The queue is one list in the order you'll hear it, rather than three sections named after where the app happened to be holding each track. What's playing is marked with a level meter over its artwork and the screen opens scrolled to it, with the last five you played above.
- Tapping anything in the queue plays it straight away. The tracks between it and what's playing are dropped rather than skipped through, and the queue tops itself back up afterwards.
- Entries can be removed by swiping, and Edit gives the tracks you queued yourself a handle for dragging them into order. Holding any track opens a menu to play it now, move it up next, favourite it, or remove it. Anything you add with Play Next stays ahead of the automatically gathered tracks.

### Streaming and storage

- Streaming quality is now set per connection. Wi-Fi and cellular each choose what to ask the server for — the original file, or Opus, AAC or MP3 — and a bitrate from 96 up to 320 kbps when transcoding. A line on the same screen says what all of it adds up to on the connection you're on right now.
- Seeking is immediate on Wi-Fi: the track is quietly downloaded while it plays, so dragging the progress bar has the whole song to work with. On cellular, and anywhere Low Data Mode is on, nothing is downloaded speculatively — seeking there fetches the track at the moment you ask for it, showing "Buffering to seek…" for the moment that takes, after which every later seek in that track is instant.
- The most recently played tracks are kept on the device, so replaying a song or skipping back to it plays from local storage instead of downloading it again.
- Storage has a maximum size — 512 MB up to 10 GB — with a meter showing how much of it is in use. Those recently played tracks aren't governed by it and are always kept; Clear Cache removes them along with everything else.

### Settings

- Everything about streaming and how one track gives way to the next now lives on its own Playback screen, instead of taking up three sections of the main list.
- Settings opens with the server you're connected to: which one, the account it's using, whether it's answering, and how many custom headers are set.
- Added a Theme setting — Light, Dark or Auto — which applies across the whole app. Theme, Accent Color and Language are grouped under Appearance.
- The cards are drawn on the same glass the mini player sits on, and pressing a row is answered by the system's highlight moving under your finger. The Library list and the login form use the same cards, so they follow.
- The app version and Subsonic API revision moved to a line at the bottom instead of taking up a row of their own.

## [0.3.0] - 2026-07-31

- Redesigned Login, Home, Library, Playlist, Now Playing, Search, and Settings with a new flat, card-based look.
- Added support for custom HTTP headers when logging in (useful for reverse proxies that require an API key).
- Home now shows Recently Played, Most Played, Random, and Favorite albums, plus a Top Artists row.
- Library now opens directly into Playlists, Artists, Albums, and Genres, plus a Recently Added grid.
- Now Playing gained a volume slider and an AirPlay button.
- Playlists now show a collage cover along with Play and Shuffle buttons.

## [0.2.2] - 2026-07-31

- Fixed the Search tab's cancel button sometimes not appearing, which could leave you unable to switch away from Search.
- Hid the miniplayer's skip button when the tab bar is minimized, so it doesn't feel cramped in the compact layout.

## [0.2.1] - 2026-07-31

- Fixed a crash that could occur when starting a stream while artwork was loading.
- Fixed playback stopping when the app moved to the background.
- Tightened up the miniplayer's thumbnail sizing and spacing.

## [0.2.0] - 2026-07-31

- Added an accent color option (Settings > Accent Color) that now tints buttons and highlights throughout the app.
- Added subtle haptic feedback when switching tabs.
- Added an Export Logs option in Settings to share app logs (useful for troubleshooting).
- The search field now focuses automatically when you open the Search tab.
