# JF Go AR drop demo (8 Oct 2026)

Jamie, walking in Greenvale: "push me a notification saying something's nearby, walk to it, AR camera, light beam, dumbbell, tap, collect animation."

- Live: https://jamie185.github.io/jf-go-ar-20261008/ (repo jamie185/jf-go-ar-20261008, public, noindex). Standalone page, not JF Coach.
- `?d=lat,lng&n=Park` = suggested drop. On the first GPS fix the page keeps it if 60-450 m away, otherwise picks a JF Go park-path candidate 150-320 m away, ahead of the walking direction (`parks.js` = candidates within ~3 km of Greenvale only; rebuild from `jf-go-lab-1006/site/app/data/go-candidates.json` for elsewhere).
- Flow: intro (permissions on tap) > Leaflet/OSM map + compass arrow + metres/steps > camera (getUserMedia back camera, webkitCompassHeading/deviceorientationabsolute, beta for horizon) with a canvas beam, edge arrows, dumbbell from 45 m, tap from 25 m > flash, burst, fly-in, reward card, "Drop another".
- Push: JFcall Web Push to jamie@ (`/tmp/jfgo-push.js` run in jfcall-server: kind "sms" with no phone so the SW opens `data.url`; if a JFcall window is alive the SW focuses JFcall instead). Backup link posted to Jamie's Mia DM via `/opt/jf/ava-discord-mirror/to_jamie.py` post(). JF Coach native pushes can't open external origins (pushTapRoute.mjs).
- Location came from Find My on Glass (cu-glass), no API.
- Test: `node tools/sim.cjs` (system Chrome headless, simulated GPS/compass).
