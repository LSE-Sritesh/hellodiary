# hello diary prototype

One file, no build step. `setlog-prototype.html` is the whole app. The file keeps its original name so the published link stays the same.

Look and feel follow the LSE style (dark by default, press T or use account, appearance, for bright). Century Gothic is embedded in the file. The script wordmark uses Mr Dafoe from Google Fonts, so it needs a connection the first time.

## Run it

Easiest, double click the file. It opens in your browser and asks for camera and microphone. Allow both.

For your phone, serve the folder and open it over https, or use the published artifact link from the chat. The published link cannot use the camera (the page sandbox refuses device access), so it shows a stand in viewfinder. Everything else works there.

To serve on your laptop, run this from the project folder and open http://localhost:8765/setlog-prototype.html

```bash
python -m http.server 8765 --directory prototype
```

## What works

* Onboarding, name and permissions, in the terminal style.
* Logs home with room cards. A demo room called besties with two pretend friends is seeded on first run so the screen is not empty.
* Plus menu, create a room (all seven size pills), join with code, zip stub.
* Camera with the hour label, 0.5x and 1x zoom, flash, flip, and the smiley shutter. One tap records two seconds. No retakes for that hour.
* Caption and post. The clip goes to every room you are in.
* Room timeline by hour slot, showing who logged and who missed.
* Daily log player, chronological, with hour, name, time and caption overlays.
* Export, which stitches the day into one vertical video in the browser.
* Account, photo, name, colour (the screen glow follows it), reminders, flag toggle, backup.
* Notifications panel with a "fire a prompt now" button for testing. The real scheduler picks a random minute each hour.

## What is simulated

* Friends. Mina and Jun are placeholders with generated clips. There is no server.
* Push notifications. The prompt shows as an in app banner, and as a browser notification if you allowed it and the tab is in the background.
* Zip and reactions. Stubs only.

## Where data lives

Everything is stored in the browser (localStorage for metadata, IndexedDB for the video blobs). "log out and wipe this device" in account clears it all.
