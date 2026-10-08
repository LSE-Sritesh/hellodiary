# PRD. hello diary (hourly group vlog app)

Version 0.1, 8 October 2026. Owner Sritesh. Status, draft for prototype.

Our version is called hello diary. This document uses "the app" throughout and "Setlog" only when describing the reference product.

## 1. What we are building

A private, small group video diary. Roughly once an hour everyone in a room gets the same push notification at the same random moment. Each person films a two second clip right then, no retakes, no uploads from the gallery, no filters. At the end of the day the clips from everyone in the room stitch themselves into one chronological vlog that anyone in the room can watch and export.

The whole product is one loop.

1. The push lands.
2. You open the camera and film two seconds.
3. You glance at what your friends filmed this hour.
4. At midnight the day becomes a short film of your group.

Everything else in the app exists to make that loop reliable, fast and fun.

## 2. Why this and why now

Setlog went from an iOS launch in December 2025 to roughly ten million users by October 2026, with Japan, Korea, Singapore and Taiwan leading. The research findings behind this PRD are summarised in the memory file for this project and the key points are these.

* People are tired of curated feeds. A forced two second clip reads as proof of life, not performance.
* A synchronised prompt creates a shared moment. Everyone in the room is filming at the same minute.
* Posting costs almost nothing. Two seconds, one tap, done.
* The end of day vlog is the payoff and it is shareable, which is free marketing on TikTok and Instagram.
* Rooms are small and private, so there is no audience anxiety.

Setlog's growth was seeded by K pop idols. Japan proves the format spreads without celebrities, through friend invites. Our seeding plan is an open question (section 13).

## 3. Goals and non goals

**Goals for the prototype (this phase)**

* A working click through of every core screen, faithful to the reference UI.
* The real loop on one device. Prompt, two second capture, slot timeline, daily vlog playback, export.
* Enough simulated friends and clips that the logs screen feels alive on first open.

**Goals for v1 (next phase)**

* Real multi user rooms with invite codes, push notifications and server side stitching.
* iOS first, Android close behind.

**Non goals, for now**

* Monetisation. Setlog has none. We decide later.
* Public profiles, discovery, feeds, follower counts, likes from strangers.
* Editing tools of any kind. The absence of editing is the product.
* End to end encryption in the prototype. It is on the v1 list.

## 4. Who it is for

Primary, friends aged 18 to 30 who already share daily life in a group chat. They want a lighter way to stay in each other's day without typing.

Secondary, couples, housemates, small teams on a trip, families split across countries (hence the country flag and local time option).

Age gate 13 and over, matching the reference app.

## 5. Core rules of the format

These rules are the product. Breaking any of them turns the app into another video feed.

| Rule | Detail |
|---|---|
| One prompt per hour | Every member of a room gets the same push at the same random minute within the hour. |
| Two second clips | Hard cap. The recording stops itself at two seconds. |
| Film now | The camera opens live. No gallery, no imports, no filming ahead of the prompt. |
| No retakes | Once a clip is captured for an hour slot, that slot is done. |
| No filters, no edits | Flash, zoom (0.5x and 1x) and camera flip only. |
| Optional caption | One short line of text after capture. Can be left blank. |
| Daily auto compile | At the day boundary all clips in a room stitch into one vertical vlog, in time order. |
| Day boundary | The day runs from 04:00 to 03:59 so late nights stay with the right day. |
| Small rooms | Solo vlog, 2, 3, 4, 5 or 6 to 20 members. Stack rooms allow up to 40 and have no hourly slots. |

Note from research. A July 2026 Setlog update reportedly relaxed the strict hourly timing. The prototype keeps the hour slot as the unit but allows filming inside the slot after the prompt lands, rather than only within a short window. Revisit after testing.

## 6. Feature list and priority

P0 ships in the prototype. P1 is v1. P2 is later.

| # | Feature | Priority | Notes |
|---|---|---|---|
| F1 | Onboarding, name and permissions | P0 | Terminal style screens, see 7.1 |
| F2 | Create room, choose size | P0 | vlog, 2, 3, 4, 5, 6 to 20, stack |
| F3 | Join room with code | P0 | Six character code |
| F4 | Hourly prompt scheduler | P0 | Random minute per hour, one per room day |
| F5 | Camera with two second capture | P0 | Smiley shutter, hour label, zoom, flash, flip |
| F6 | Caption after capture | P0 | Optional |
| F7 | Logs home, room cards | P0 | Latest clip thumbnail, room name, members, time |
| F8 | Room timeline by hour | P0 | Who has logged this hour, who has not |
| F9 | Daily vlog playback | P0 | Chronological, hour and name overlays |
| F10 | Export daily vlog | P0 | One vertical video file |
| F11 | Account settings | P0 | Photo, name, colour, reminders, flag and local time, backup |
| F12 | Notifications panel | P0 | Prompt history and reactions |
| F13 | Reactions and replies on a clip | P1 | Emoji reactions, short text replies |
| F14 | Zip, one to one photo swap, view once | P1 | Stub only in prototype |
| F15 | Stack rooms | P1 | Up to 40 people, archive, full day export, no hourly slot |
| F16 | Real push notifications | P1 | APNs and FCM |
| F17 | Server side stitching | P1 | FFmpeg job on upload, or on demand at day end |
| F18 | End to end encryption of media | P1 | Match the reference app's privacy claim |
| F19 | Share sheet to Instagram and TikTok | P1 | Export then hand off |
| F20 | Country flag and local time per member | P1 | Opt in, approximate |
| F21 | Backup and restore | P2 | |
| F22 | Screenshot alerts | P2 | Setlog has none. Decide after testing |

## 7. Screens and flows

Each screen below maps to a reference screenshot in the folder "Setlog's UIUX". Visual rules are in section 8.

### 7.1 Onboarding (screens 01 to 03)

Black screen, monospace type, a small popcorn mascot top left, a "need help?" link top right. Copy reads like a terminal.

1. "→ welcome to setlog" then "to get started we need your first and last name…". Two inputs, First then Last. Links for next and cancel, underlined, no buttons.
2. "→ permissions" then "first, we need a few permissions…". Camera is explained with the line that photos and videos are end to end encrypted and only you and friends you share with can see them. Microphone is explained as recording audio while capturing videos. Each row turns into a green tick when granted. A continue link at the bottom.
3. Notifications permission uses the same pattern.
4. Lands on the logs home with no rooms and a nudge to create one.

### 7.2 Logs home (screen 05)

Wordmark top left in teal, profile icon top right. A vertical list of room cards. Each card is a 16 by 9 thumbnail of the latest clip with the room name on the left, the latest logger's name in the middle, the capture time on the right, a share icon bottom right. Tapping a card opens the room timeline.

Bottom bar on every main screen, three controls. A bell on the left for notifications, a two segment toggle in the middle (camera, logs), a plus on the right.

### 7.3 Plus menu (screen 06)

A dark sheet rising from the plus button with three rows. Create a room, join with code, a divider, then start a zip.

### 7.4 New room (screen 04)

Sheet with a close cross, a star mascot, the title "new room" and a pink tick to confirm. One optional text field for room name. A row of pills for room size, vlog, 2, 3, 4, 5, 6 to 20, stack. Selected pill fills pink. A helper line below reads "you + 2 friends". A secondary outlined button "join with code". Below the sheet, a large outlined pink button "CREATE A ROOM".

On create, the app generates a six character invite code and shows it with a copy action.

### 7.5 Camera (screen 07)

Full bleed viewfinder with rounded corners inside the phone. The current hour slot ("18:00") sits vertically in the centre in a chunky white font. Zoom labels ".5" and "1" above the shutter, the active one in yellow. The shutter is a large blue smiley face with a dark blue ring. A flash bolt sits left of the shutter. The bottom bar swaps the bell and plus for a timer icon on the left and a camera flip on the right, the toggle in the middle still reads camera and logs.

Tap the smiley. A ring fills around it over two seconds and the recording stops itself. The clip plays back once with an optional caption field and a single post action. There is no retake. If the hour slot is already logged the shutter shows a tick and a line that says when the next prompt is due.

### 7.6 Room timeline

Room name and member colour dots at the top. A list of hour slots for today from 04:00. Each slot shows a small tile per member, filled with the clip thumbnail if logged, dimmed if not. Tap a tile to play it. A primary action "watch today's log" plays the full compile. Secondary actions for invite code and export.

### 7.7 Daily vlog playback

Full screen vertical player. Clips play in order with the hour label and the logger's name overlaid, a segmented progress bar across the top, tap to pause, swipe down to close. Export produces one vertical video file.

### 7.8 Account (screen 08)

Title "account", QR icon top right for sharing your profile. Sections for profile photo, name, colour (six swatches, cyan, orange, purple, green, blue, pink), hourly log reminders (1hr, 3hr, off), a toggle for country flag and local time with a one line explanation, then backup. Your chosen colour becomes the glow around the edge of the screen, which is why the reference screenshots show a green border before onboarding and a pink one after.

### 7.9 Notifications panel

A list of prompts that fired today with their time, plus reactions and joins. The prototype adds a single "fire a prompt now" action here so the loop can be tested without waiting an hour. This is a prototype only control.

## 8. Visual and interaction rules

The layout follows the reference app. The look follows the Lemon Sky LSE style, dark theme by default with a bright theme available.

* Near black canvas (#141416) with white text. Secondary text in the LSE muted grey. The bright theme flips to white with dark ink.
* Two type families. Century Gothic for everything you read and tap. A monoline script (Mr Dafoe, close to the "Simplicity" lettering reference) for the wordmark and the onboarding headlines only, never for body copy.
* Yellow (#FFCB05) is the one accent. It marks the primary action, the selected pill, the prompt banner and the shutter ring. Blue (#00AEEF) labels and categorises, so it carries eyebrow labels, the invite code and the on state of switches. No other hues.
* Eyebrow labels are small, uppercase, letter spaced blue with a triangle bullet, as on LSE slides.
* Everything is lowercase except the CREATE A ROOM button.
* Corners are small (6 to 14px) rather than fully round. Circles are kept for icon buttons, colour swatches and the shutter.
* The screen edge glows in the user's chosen colour. Default is yellow.
* Motion is minimal. Sheets slide up. The shutter ring fills over two seconds. Nothing else animates.
* The T key, or the appearance control in account, flips between dark and bright.

## 9. Data model (prototype)

**Profile**
first, last, colour, reminderInterval (1hr, 3hr, off), showFlagAndTime, onboarded.

**Room**
id, name, type (vlog, group, stack), size, inviteCode, members, createdAt.

**Member**
id, name, colour, isMe, isDemo.

**Clip**
id, roomIds, memberId, dayKey, slotHour, capturedAt, caption, video (blob), thumbnail.

**Prompt**
dayKey, slotHour, minute, firedAt.

**Notification**
id, type (prompt, reaction, join), text, createdAt, read.

Day key uses the 04:00 boundary. A clip captured at 01:30 on the 9th belongs to the 8th.

## 10. Prompt scheduling

1. At the start of each hour the app picks a random minute between 0 and 50.
2. When the clock reaches that minute the prompt fires. One notification per room per hour.
3. The camera opens straight into the slot for that hour.
4. The slot stays open until the end of the hour. After that it is marked missed.
5. Reminders (1hr or 3hr) are separate, softer nudges and never replace the prompt.

Stack rooms skip all of the above and accept clips at any time.

## 11. Technical approach

**Prototype (now)**
One self contained HTML file. Real camera through the browser on a phone or laptop, with a simulated viewfinder when the camera is refused so every screen still works. Clips recorded in the browser at two seconds. Storage in the browser so the day survives a reload. Daily vlog stitched in the browser by replaying clips onto a canvas and recording that as one file.

**v1 (next)**
React Native or Flutter, single codebase. Backend on a managed stack (Supabase or Firebase for auth, rooms and realtime, object storage for clips). Push through APNs and FCM. A worker stitches the day with FFmpeg at the day boundary and on demand. Encryption at rest first, end to end once the key exchange design is settled.

**The one thing to get right**
Reliable stitching and export. Users of the reference app complain about endless loading and black exports. A boring, always working export is a visible differentiator.

## 12. Success metrics for the prototype

| Metric | Target |
|---|---|
| A new person completes onboarding and creates a room | Under 60 seconds |
| Time from prompt to posted clip | Under 15 seconds |
| Daily vlog plays back with correct order and overlays | 100 percent of test days |
| Export produces a playable file | 100 percent of attempts |

For v1 the numbers that matter are rooms with 3 or more active members, clips per member per day (Setlog's dating rooms require 7), day 7 retention, and exports shared out per room per week.

## 13. Open questions

1. Mascot. The name is hello diary. Setlog uses a popcorn character and a star. We still need our own characters.
2. Seeding. Campuses, a creator cohort, or a niche community. Research says the format spreads without celebrities but still needs a first dense cluster.
3. Prompt strictness. Short window after the push, or the whole hour. Test both.
4. Does a clip go to every room you are in, or do you pick a room each time. The reference app shows no room picker on the camera, so the prototype posts to every room.
5. Privacy edge cases. Partner surveillance and location overexposure were real criticisms. Decide early whether members can hide a slot or leave a room silently.

## 14. Risks

* Notification fatigue. Up to 20 pushes a day. The 1hr and 3hr reminder settings help, and we should test fewer prompt hours (for example 09:00 to 23:00).
* Retention cliff. BeReal fell off after the novelty. The daily vlog payoff and the shareable export are our answer. Measure exports per room.
* Export failures. See 11. Treat as a P0 bug class.
* Platform rules. Camera only capture, age gating and encryption claims all need to hold up in App Store review.
