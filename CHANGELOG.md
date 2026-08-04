# Changelog

## [Unreleased]

## [0.4.0] - 2026-08-04

- Settings rows are now drawn on the same glass the mini player sits on, and pressing one is answered by the highlight moving under your finger rather than by nothing happening until the next screen appears. The Library list and the login form use the same cards, so they follow.
- The paragraph under the storage meter is gone; the meter says what's used out of what.

- Fixed Now Playing sliding off to one side when a track's artwork finished loading, leaving the controls sitting off-centre for the rest of the song.

- Album tracks are now only joined gaplessly when the next one actually follows on. Track 1 into track 3 of the same album is crossfaded like any other transition, since the recording doesn't run on and joining them would close a gap the album intended. Tracks the server sends no number for are crossfaded too, rather than joined on a guess.

- Fixed Quality on Wi-Fi going blank the moment that connection was switched from the original file to a transcode. It now falls back to the highest bitrate on offer.
- The Keep Albums Intact toggle is gone. Consecutive album tracks are joined rather than crossfaded, which is all the old toggle ever chose between.
- The Playback screen says what it is actually doing in one line — "Detected environment: Wi-Fi / Lossless" — instead of a paragraph.

- The queue is now one list in the order you'll hear it, instead of three sections named after where the app happened to be holding each track. The track playing is marked with a level meter over its artwork and the screen opens scrolled to it, with the last five you played above.
- Tapping anything in the queue plays it straight away. Tracks between it and what's playing are dropped rather than skipped through, and the queue tops itself back up afterwards.
- Queue entries can be removed by swiping, and Edit gives the tracks you queued yourself a handle for dragging them into order. Holding any track opens a menu to play it now, move it up next, favourite it, or remove it.

- Everything about streaming and how one track gives way to the next now lives on its own Playback screen in Settings, instead of taking up three sections of the main list.
- Streaming quality is now set per connection. Each of Wi-Fi and cellular picks what to ask the server for — the original file, or Opus, AAC or MP3 — and, when transcoding, a bitrate from 96 up to 320 kbps. The transcode toggles are gone: "Off (Original)" in the format picker is what they did. Existing settings carry over, so nothing changes until you change it.

- Album tracks now also join gaplessly when streaming Opus, not only when streaming the original files.
- The stream format picker offers Opus, AAC and MP3. Ogg Vorbis is gone because iOS can't play it, and FLAC because transcoding to it saves nothing; anyone who had either selected is moved to Opus.

- Albums now play gaplessly: consecutive tracks run into each other with no silence between them, so records mastered as one continuous piece finally play as one. It sits alongside crossfading rather than replacing it: album tracks are joined, everything else still blends.
- Gapless needs the original file: a server transcoding on the way out strips the information a seamless join depends on, and for some formats there's no way to carry it. It applies wherever transcoding is off, which by default is Wi-Fi.
- Skipping forward onto a track that's already been lined up for a gapless join is now instant, since it's loaded and ready rather than being fetched from scratch.

- Playback no longer runs out. The queue is kept stocked with ten tracks similar to what you're listening to, gathered from the server and topped up as they're played, so a single song can carry on indefinitely.
- Playing a track from an album still queues the rest of that album — the similar tracks are gathered on top of it, and start once the album has played out. Playing anything else starts the whole thing over from the new track.
- When the server has no similar tracks to suggest — libraries without that data would otherwise just stop — the queue falls back to other songs by the artists you're listening to, drawn from a random album of theirs rather than the same few tracks every time.
- Tracks you add with Play Next always come before the automatically gathered ones, and are taken into account when gathering: what comes next is based on everything you've lined up, not just the song playing. Nothing you've already heard or queued is suggested again.

- Settings now opens with the server you're connected to: which one, the account it's using, and whether it's answering, plus how many custom headers are set.
- Settings has a Theme setting — Light, Dark or Auto — which applies across the whole app. Theme, Accent Color and Language are now grouped under Appearance.
- Storage now has a maximum size — 512 MB up to 10 GB — with a meter showing how much of it is in use. The recently played tracks the app keeps for offline replay and instant seeking aren't governed by it and are always kept; Clear Cache still removes them along with everything else.
- The app version and Subsonic API revision moved to a line at the bottom of Settings instead of taking up a row of their own.
- Crossfading is now configurable in Settings: turn it off, or set the overlap anywhere from 0 to 12 seconds. Consecutive album tracks are left out of it, so albums still play in the order they were sequenced.

- The Now Playing screen has been rebuilt. Crossfades are now visible while they happen: the cover art of the track coming in dissolves across the one going out, the background colour turns over with it, and a line under the progress bar names the incoming track. The tail of the progress bar is marked so you can see where the next track will start blending in.
- Now Playing shows what you're actually hearing: genre and year above the progress bar, and a line beneath it giving whether the track is streaming or playing from the device, its format, bitrate and ReplayGain.
- Now Playing has a sleep timer — 15, 30, 45 or 60 minutes, after which playback pauses where it got to, so pressing play carries on.
- Now Playing's layout follows Apple Music more closely: the volume slider is gone, play/pause has lost its surrounding circle, and the row along the bottom is AirPlay, download state, lyrics, queue and the sleep timer. Favourite and a menu button sit above the progress bar.
- Settings now shows how much space downloaded tracks are taking, with a Clear Cache button to free it.
- Reopening the app brings back what you were listening to: the miniplayer shows the track paused where you left off, and pressing play carries on from there.

- Tracks now crossfade into each other: the next track starts 6 seconds before the current one ends, with the outgoing track fading out as the incoming one fades in. The player switches to the new track once the fade is over, already 6 seconds in.
- The progress bar on the lock screen and in Control Center now works: it follows playback, and dragging it moves the track instead of snapping back.
- Fixed the elapsed time freezing and crossfades stopping after seeking. A seek that the server never confirmed left the player ignoring its own clock indefinitely.
- Fixed crossfading cutting tracks off before their real end, which got worse the longer you listened and after seeking. The fade is now paced by how much of the current track is actually left, so it can only finish when the track does.
- Fixed a song jumping back to its own beginning partway through, after which the timer ran ahead of what you were hearing, the crossfade came in somewhere in the middle, and every following track did the same. The app was streaming a song and downloading that same song at the same time, leaving the server transcoding it twice at once; upcoming tracks are now fetched ahead of time, one at a time, and never while they're being played.
- Fixed the next track being brought in mid-song on servers that transcode on the fly. The stream's own reported length can start out far short of the real track and grow as it arrives, and that estimate was being used to decide when the track ended.
- The same song twice in a row no longer crossfades into itself, which sounded like the track restarting over the top of itself.
- Reaching the end of the queue now stops both players and clears the lock screen instead of leaving audio behind.
- Settings gained a Playback section: a Transcode Audio toggle that switches between the server's original file and a transcoded stream, plus a format picker (Opus, MP3, AAC, Ogg Vorbis, FLAC). Opus is the default.
- The five most recently played tracks are now kept on the device, so replaying a song or skipping back to it plays from local storage instead of downloading it again.
- Fixed the progress bar in Now Playing and the one on the lock screen drifting apart. Scrubbing in the app now moves the lock screen too, scrubbing on the lock screen now actually moves playback instead of snapping back, and the two stay in step after a stall or a buffer.
- Dragging the progress bar in Now Playing no longer fights you: the handle stays where you put it while you drag, and playback jumps once you let go.
- The login screen is shown again on launch. A debug bypass had been left in place, so the app opened straight into the library without ever asking for your server and credentials.
- Seeking now works on Opus. A stream the server is still transcoding cannot be jumped around in, so dragging the progress bar either did nothing or slid straight back. The app now notices when a seek isn't served, downloads the track, and resumes from the requested spot -- Now Playing shows "Buffering to seek..." for the moment that takes, and every later seek in the same track is instant because it's then on the device.
- The Transcode Audio toggle in Settings is now two: Transcode on Wi-Fi and Transcode on Cellular, each with its own default -- off on Wi-Fi, where the server's original file costs nothing you'd notice and can be seeked in straight away, and on for cellular, where a small Opus stream is the point. The format picker applies to both, and a line at the bottom of the section says what all of it adds up to on the connection you're on right now.
- Seeking is now immediate on Wi-Fi with transcoding turned on: the track is quietly downloaded while it plays, so dragging the progress bar has the whole song to work with rather than waiting for it to be fetched first. On cellular, and anywhere Low Data Mode is on, nothing is downloaded speculatively -- seeking there still fetches the track at the moment you ask for it, with the same "Buffering to seek..." wait as before.
- Picking Opus in Settings no longer warns that iOS can't play it. It plays -- it's the default and always has been -- so the caveat only appears for Ogg Vorbis now, which genuinely doesn't play.

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
