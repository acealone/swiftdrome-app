# Changelog

## [Unreleased]

## [0.7.4] - 2026-08-10

- The app can be installed and updated from the AltStore source again. Every build so far reported itself as version 1.0.0 no matter which release it was — the version was never written into the app, so the build tool filled in its own placeholder — and AltStore refuses to install an app whose version disagrees with the one the source advertises. Builds now carry their real version number, and the source lists the iOS version the app actually needs (26) rather than the 17 it was seeded with.

## [0.7.2] - 2026-08-10

- Closing Now Playing lands the pill exactly where the mini player sits. On a full screen the shrink used to stop a notch-height short and the pill snapped down the last stretch — the landing spot was measured against the wrong edge of the screen, in a way that happened to cancel out in windowed setups like LiveContainer's multitasking mode.

## [0.7.1] - 2026-08-10

- Switching tabs no longer freezes the app while something is playing. The mini player's new home in the tab bar could send the bar's layout in circles — the player's height depended on what the bar offered, and the bar's size depended on the player's height — and on any tab you entered after launch the app locked up solid. The player now states its own height, and the layout settles.
- Pulling the queue down follows your finger again. Since the player became one surface with the mini player, the queue's pull-to-close still worked — but the screen no longer moved with the drag, so the player just vanished on release with nothing warning it was about to. The pull now carries the whole surface down as it always did in the player layout.
- If the app ever hangs again, it writes that down: a new hang.log records when the interface stopped responding and for how long, and comes along when exporting logs from Settings — so a freeze can be reported with evidence, the way a crash always left a crash.log.

## [0.7.0] - 2026-08-10

- Settings now opens from a gear in the top-right corner of nearly every screen — Home, Library, Playlists, Search, and the album, playlist and artist pages — and the screen grows out of the gear you tapped rather than sliding up as a detached sheet, closing back into it the same way. The person icon that used to sit on three of the tabs is gone.
- Album pages have been rebuilt to match the design: the artwork starts large and settles smaller as you scroll, the artist's name under the title now opens their page, and a dim line beneath it gives the genre, year, file format, song count and length. Play and shuffle sit in a new action row along with a heart that stars the album itself and a menu for queueing the whole album. Track rows show their number and length, and can be swiped — right for Play Next, left for Play Last.
- The Play and Shuffle buttons on album, playlist and artist pages now clear what you had queued and play the record clean. Queued songs used to survive the button and wedge themselves between the record's tracks — right where the gapless joins and album volume-levelling live. If you'd rather keep the queue, Settings › Playback has a new "Keep queue on Play" switch that restores the old behaviour, Apple Music's: queued songs survive and play after the first track. Either way, tapping a single song keeps your queue, and Play Next / Play Last from the menu remain the way to queue a record around what you're hearing.
- Play Next and Play Last are now two different things everywhere: Play Next puts a song in front of what you've already queued, Play Last behind it. Swiping album tracks and the action-row menus offer both, and so does holding down any song — in albums, playlists, search results, favourites, the artist pages, the Songs list and Downloaded.
- Artist pages are no longer a bare grid of covers. They open with a full-width image fading into the page, the artist's name and library stats on it, then the same action row the album page has (the heart stars the artist), their top songs with a See All list, the albums as a shelf with years, an About section with their biography, and similar artists to jump to — the last three whenever the server can provide them.
- Playlist pages get the same action row in place of the old wide Play/Shuffle buttons, and the header now shows the length of the playlist and its owner. There is no heart on playlists — the server has nothing to star them with.
- Search results can now be filtered with a Top / Artists / Albums / Songs bar under the search field. Top shows the three kinds in sections of their own, and each section's See All jumps to its filter.
- The Library list now matches the design's order and adds the two entries it was missing: Songs, every song in the library arriving in batches as you scroll, and Downloaded, the tracks already on the device, newest first.
- Home's section headlines now carry a chevron and open the section as a full grid — not just the ten covers the shelf shows, but the whole server list, arriving in batches as you scroll. Recently Played, Recently Added, Most Played and Favorites run as deep as the library does; Random Albums keeps drawing fresh ones for as long as you keep going.
- The queue shows the current track's year and genre with a heart to star it, right under the track — the same row Now Playing has.
- The queue is no longer a screen of its own: tapping the list button morphs Now Playing in place — the artwork shrinks into a compact row for the current track, the seek bar gives way to the year-and-genre line with its heart, and what's coming next fills the screen below, headed by an Up Next count of the songs you queued. Tapping the list button again morphs it back. The list also no longer opens with the songs you've already heard above the current track — it starts with the track playing and looks forward only; the back button remains the way to return to something heard.
- New in Settings: Left-Handed Controls (Accessibility) mirrors the album, playlist and artist action rows so play and shuffle sit under the left thumb; Scrobble to Server (Misc) can turn off play reporting entirely, including the "now playing" notes clients normally send.
- Tracks that are on the device now say so, with a small arrow beside them in the queue, on albums and playlists, in your favourites and in search results. What is downloaded changes as you listen — the next two tracks are fetched ahead and the ones you have just played are kept — and until now the only way to find out what would still play without a signal was to lose the signal.
- The app now downloads the next two tracks in the queue instead of one, and keeps the last five you played. A skip lands on a track that is already on the device rather than one being fetched from scratch, the join or blend into the track after next has a file to work from, and stepping back through what you have just heard plays from the device rather than the network. On Wi-Fi the track playing is fetched alongside its own stream too, so it is on disk before you reach the end of it.
- Downloaded tracks now remember the quality they were fetched at, and a copy that is better than the connection would ask for is played rather than fetched again — a lossless copy pulled at home is what plays after you leave the house, instead of being downloaded a second time as a smaller file. Now Playing reports the format and bitrate of the copy actually playing, rather than the one your current connection is configured for.
- Dragging the progress bar is now instant wherever the track is on the device, which after the change above is most of the time on Wi-Fi. The "Buffering to seek…" wait is gone with it: the app no longer stops the music to download a whole track before honouring a scrub. The trade, stated plainly — on cellular, dragging forward past the part already buffered may not move at all, and the track simply carries on from where it was.
- Songs you've lined up with Play Next now survive starting something else. Tapping a track in an album, a playlist, a search result or your favourites used to throw the whole hand-built queue away without a word — the queue screen was simply empty afterwards and the songs you'd queued never played. The tapped track now plays straight away, your queued songs follow it, and the album or playlist you tapped into carries on after them. Tapping a song that was already in the queue plays it now and takes it out of the queue rather than playing it twice in a row.
- Now Playing only closes when you pull it down. Swiping in from the left edge — the reflex for going back — used to pick the whole screen up and carry it off sideways, so the player slid around under any drag in any direction. A pull down now carries the whole player with it and uncovers the library behind, a short pull springs it back, and a sideways swipe does nothing at all. Opening it from the mini player still zooms out of the artwork the way it did.
- Library → Albums is now divided into sections by first letter, with the letter of the section you are in shown at the top of the screen as you scroll, and an index down the right-hand edge you can tap or slide a finger along to jump to a letter. Names starting with a number or a symbol are collected under "#" at the end, and accented names file under the plain letter, so "Ólafur" sits with the Os rather than off on its own.
- Library → Albums now shows every album you have, and a genre screen every album in that genre. Both stopped at 50 without saying so — an alphabetical list that ended somewhere around "B" while the rest of the library was only reachable through search or the artist pages. The albums arrive in batches now, so the first of them are on screen while the rest are still coming in.
- The previous button now starts the current track over when you're more than a few seconds into it, and only steps back to the track before when you press it near the beginning — so two quick presses still reach the previous track. It used to leave the track you were listening to every time, which on a long set or a live album meant losing your place and having to skip forward to get back to the start of it. The lock screen, headphone controls and CarPlay all behave the same way, since they go through the same button.
- Songs you've starred now show a filled heart as soon as the app opens, wherever a heart is drawn — Now Playing, albums, playlists and the queue. The app used to start each session knowing nothing about your favourites and only learned them from the taps you made since, so a song starred yesterday or from another client looked unstarred, and unstarring it took two taps because the first one starred it again. Signing out clears them, so the next person to sign in gets their own.
- Switching the theme to Auto now recolours the Settings screen straight away, the way switching between Light and Dark already did. Auto was being passed on as "no preference", which left the screen on whichever of Light or Dark had been chosen before it instead of handing it back to the system.
- Music comes back on its own after a phone call, Siri or an alarm, where before the call simply ended the listening session: the app stayed silent while Now Playing, the mini player and the lock screen all still showed it playing, the lock screen's progress bar ran on through the whole call, and getting the music back took two presses of play. The app now pauses with the interruption, at the position the call arrived, and starts again by itself once the system says it may. Taking headphones out or putting AirPods away pauses too, and stays paused — one press of play picks it back up.
- The menu you get from holding a song in the queue — Play Now, Play Next, the favourite entry and Remove from Queue — is now in your language like the rest of the app. It was the one menu left in English on a German phone, even though the translations for it were already there.
- Now Playing follows the Light theme instead of staying black. The screen was built dark on purpose — black behind the artwork, white text over it — so choosing Light left one screen out of the app. It now takes its ground and its text colour from the theme, and the blurred artwork behind everything is lightened rather than darkened under Light, so the titles, times and transport controls read against it the way they always did under Dark. Dark looks exactly as it did.
- Opening the mini player no longer lays a new screen over the app: the pill itself grows into Now Playing, the artwork travelling from thumbnail to full size as one piece, and pulling the player down shrinks it back into the pill the same way. The flicker of the screen behind while closing the player is gone with the old transition — nothing behind the player is scaled back anymore, because nothing is presented over it. The pill still lives with the tab bar and tucks itself into it when the bar shrinks away on scroll, exactly as before.

## [0.6.0] - 2026-08-07

- Home can now be pulled down to refresh, which reloads the carousels without leaving the screen. Random Albums is deliberately left out of that refresh — it is picked once when the app starts and otherwise stays put, so the covers you were about to tap don't move under you. A refresh button at the right-hand end of its headline picks a new set whenever you want one: it taps back under your finger as you press it, turns while the new covers are on their way, and comes out of the turn as a checkmark — so you can tell a shuffle that landed on similar-looking covers from a button that didn't do anything.
- A track ending normally now moves straight on to the next one. The scrobble for the finished track is still sent, but the app no longer waits for the server to acknowledge it first, so a slow or unreachable server can't leave a gap of silence at the boundary.
- The album, artist, playlist and search labels outside Home read as ordinary text again instead of picking up the accent colour: Albums, Playlists, an artist's albums, Library's Recently Added, Favorites and the search results all follow the same treatment Home already got.
- Pressing play on the track the app brought back from your last session now keeps playing when you put the phone away. It used to stop the moment the app left the screen, leaving the lock screen showing something that wasn't playing and a play button that started the wrong song — the app claims the audio the system reserves for playing in the background at the moment you press play, rather than only when you choose a new track.
- That resumed track also starts where you left it rather than at the beginning. The position was only restored for tracks already downloaded to the device; a track being streamed silently began again from 0:00 while the progress bar claimed otherwise, which on cellular was every time. Where the stream can't be moved to the saved position, the app now fetches the track and picks up from there, the same way dragging the progress bar already does.
- Search now waits for a short pause in typing before asking the server, rather than sending a request for every letter. A ten-letter query costs one search instead of ten, which on a server that is also streaming to you is work it no longer has to do. Clearing the field still empties the results at once.

## [0.5.0] - 2026-08-06

- The Library now lists what you've starred, in three entries of its own: Favorite Artists, Favorite Albums and Favorite Songs. Tapping a favourite song starts playing from there through the rest of them, and the heart beside it is filled, so a song can be unstarred from the list; artists and albums open as they do anywhere else.
- Now Playing reports the streaming quality when an encoding is selected: the file's own rate when the original is being sent, and the rate the stream was requested at when it's being transcoded.
- The buffering notice now shares the genre/year line above the progress bar instead of adding a row of its own, so nothing shifts up or down as it comes and goes.
- That same line on Now Playing reads year first and genre second, rather than the other way round.
- Home's carousels have bigger covers, and the album, artist and top-artist labels under them are no longer tinted with the accent colour — they read as ordinary text again.
- Switching between Light and Dark in Settings now recolours the Settings screen straight away, instead of leaving it on the old appearance until it is closed and reopened. The mini player above the tab bar follows the change too, rather than waiting for the next launch.
- ReplayGain is now applied during playback, so a loud remaster no longer arrives at twice the volume of the album track before it. A new section on the Playback screen in Settings turns it on or off and, when it's on, offers: the mode (Auto — album levels while a record plays through, track levels elsewhere — or Album or Track), a pre-amp, a default gain for tracks the server sends no ReplayGain information for, and clipping protection for lossy files whose peaks overshoot. Only tracks louder than the reference are turned down — nothing is boosted, though a negative pre-amp buys the headroom to make quieter tracks come up too. Any of these is heard on the track already playing rather than at the next one.
- Downloading a track to the device no longer holds the whole file in memory while it arrives — it is written straight to disk instead. A lossless track used to cost tens of megabytes of memory for the length of the download, twice over at the peak, which on a busy phone is the kind of thing that gets an app in the background closed.
- Emptying the downloaded tracks while something is playing no longer makes the Now Playing line flicker between the crossfade indicator and the track's details, showing both at once. Files the app had noted as downloaded are now checked to still be there before it plays or joins one, and a blend that fails is not retried for the rest of the track.

## [0.4.0] - 2026-08-05

### One track into the next

- Tracks now crossfade: the next one starts before the current one ends, with the outgoing track fading out as the incoming one fades in. The overlap is 6 seconds by default and can be set anywhere from 0 to 12, or turned off, on the new Playback screen in Settings.
- Consecutive album tracks are joined gaplessly instead of blended, so records mastered as one continuous piece finally play as one. Only a genuine continuation is joined — track 1 into track 3 was never meant to butt together, so it gets the crossfade like any other transition, as does a track the server sends no number for.
- A gapless join needs the server's original file or an Opus stream: any other transcode on the way out strips the information a seamless join depends on. Wi-Fi asks for the original file by default, so that's where it applies unless you change it.
- Playback no longer runs out. The queue keeps itself stocked with ten tracks similar to what you're listening to, topped up as they play, so a single song can carry on indefinitely. Where a server has no similar tracks to offer, it falls back to other songs by the artists you're playing, drawn from a random album of theirs rather than the same few tracks every time. Starting from an album still queues the rest of that album first.

### Now Playing

- The screen has been rebuilt around the crossfade, which you can now see happening: the cover art of the track coming in dissolves across the one going out, the background colour turns over with it, and a moving indicator in the metadata line tracks the blend. The tail of the progress bar is marked, so you can see where the next track will start blending in.
- It says what you're actually hearing — genre and year above the progress bar, and beneath it whether the track is streaming or playing from the device, its format, bitrate and ReplayGain. The codec named is the one reaching you rather than the format of the file on the server, which differ whenever the server is transcoding, and the bit rate is shown only where it describes the stream.
- The background no longer drops to black for a moment when a track changes. Cover art is kept in memory, so it also appears instantly on screens you've already visited.
- The buffering notice sits above the progress bar instead of below the times, where it pushed the controls down as it came and went.
- Added a sleep timer: 15, 30, 45 or 60 minutes, after which playback pauses where it got to, so pressing play carries on.
- The layout follows Apple Music more closely. The volume slider is gone, play/pause has lost its surrounding circle, and the row along the bottom is AirPlay, download state, lyrics, queue and the sleep timer, with favourite and a menu button above the progress bar.
- Dragging the progress bar no longer fights you: the handle stays where you put it while you drag, and playback jumps once you let go. The lock screen and Control Center bar follows playback and can be dragged too, and the two stay in step after a stall or a buffer.
- Reopening the app brings back what you were listening to: the miniplayer shows the track paused where you left off, and pressing play carries on from there.

### Queue

- The queue is one list in the order you'll hear it, rather than three sections named after where the app happened to be holding each track. What's playing is marked with a level meter over its artwork and the screen opens scrolled to it, with the last five you played above.
- Tapping anything in the queue plays it straight away. The tracks between it and what's playing are dropped rather than skipped through, and the queue tops itself back up afterwards.
- Reordering needs no Edit button. Tracks you queued yourself carry a grip on the right: press it and the row lifts with a tap you can feel, follows your finger straight up and down without wandering sideways, and ticks as it passes each track it displaces. Pressing anywhere else on a row opens a menu to play it now, move it up next, favourite it, or remove it, and the list still scrolls normally. Anything you add with Play Next stays ahead of the automatically gathered tracks.
- A labelled rule marks where your queue ends and the tracks that follow on their own begin — those can be removed but not reordered.
- Swiping a track away removes it, on the tracks still to come rather than on ones already played, and the row goes with it. A track you remove from the continuous queue is not offered again the next time the queue tops itself up.
- Your queue survives closing the app. Reopening restores what was playing along with everything queued behind it, what had already been played, and the tracks gathered to follow on.

### Streaming and storage

- Streaming quality is now set per connection. Wi-Fi and cellular each choose what to ask the server for — the original file, or Opus, AAC or MP3 — and a bitrate from 96 up to 320 kbps when transcoding. A line on the same screen says what all of it adds up to on the connection you're on right now.
- Seeking is immediate on Wi-Fi: the track is quietly downloaded while it plays, so dragging the progress bar has the whole song to work with. On cellular, and anywhere Low Data Mode is on, nothing is downloaded speculatively — seeking there fetches the track at the moment you ask for it, showing "Buffering to seek…" for the moment that takes, after which every later seek in that track is instant.
- The most recently played tracks are kept on the device, so replaying a song or skipping back to it plays from local storage instead of downloading it again.
- Storage has a maximum size — 512 MB up to 10 GB — with a meter showing how much of it is in use. Those recently played tracks aren't governed by it and are always kept; Clear Cache removes them along with everything else.

### Settings

- Everything about streaming and how one track gives way to the next now lives on its own Playback screen, instead of taking up three sections of the main list.
- Settings opens with the server you're connected to: which one, the account it's using, whether it's answering, and how many custom headers are set.
- Added a Theme setting — Light, Dark or Auto — which applies across the whole app. Theme, Accent Color and Language are grouped under Appearance. The Theme label takes its own line where a language's word for it is too long to sit beside the choices.
- The cards are drawn on the same glass the mini player sits on, and pressing a row is answered by the system's highlight moving under your finger. The Library list and the login form use the same cards, so they follow.
- The app version and Subsonic API revision moved to a line at the bottom instead of taking up a row of their own.

### Language

- The app is now translated throughout rather than only in the tab bar. Login, Home, Library, Search, Settings, Playback, Now Playing, the queue and every error message read in your language, as does the accent colour picker in the iOS Settings app. German is complete; counts like "3 songs" follow each language's own singular and plural rules.

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
