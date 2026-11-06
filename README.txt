CITY DRAGONS — FIRE PERFORMANCE UPDATE

This version keeps your uploaded game and reduces lag when dragon fire is used.

Performance changes:
- Reuses one low-poly fireball geometry instead of building new geometry per shot.
- Removes the extra dynamic point light from every fireball.
- Limits the screen to 4 active fireballs at a time.
- Adds a short firing cooldown to prevent rapid-fire overload.
- Uses cheaper fireball collision-distance checks.
- Slightly lowers Retina rendering resolution and shadow-map size to reduce GPU load.

HOW TO PLAY ON MAC
1. Extract this ZIP file.
2. Open the extracted folder.
3. Double-click index.html, or right-click and choose Open With > Google Chrome.
4. Press 1, 2, or 3 to control an unlocked dragon.
5. Press F or left-click to shoot fire.

The game still needs an internet connection to load its Three.js library if it is not cached.

UPGRADE UPDATE (visual + feel layer, nothing removed)
- Gradient sky dome with a glowing sun
- Fire trails, embers and impact/kill bursts (one pooled draw call, so no new lag)
- Screen shake on hits, red damage flash, combo counter, HP bar
- Glassier HUD panels
- All missions, saves, accounts, shop and story code left untouched

REALISM UPDATE (dragon + gorilla)
- Dragon: overlapping glossy scale texture, long snout with teeth and glowing throat, slit-pupil eyes, curved horns,
  spine ridge, tapered spiked tail, clawed legs, bat-style wings with bones and a scalloped membrane.
- Gorilla: fur texture, ~800 fur tufts (one draw call), silverback saddle, bare chest, brow and crest,
  glossy eyes, nostrils, ears, knuckle-walking hands, toes, subtle breathing.
- Wing flapping, controls, shooting, saves and the Cinder/Frost dragon unlocks are unchanged.

SMOOTH / REALISTIC TEXTURE UPDATE
- Removed the square "pixel" speckles: ground and dirt now use 1024px soft grass-blade textures with mipmaps.
- Rendering now uses up to 2x resolution (sharper on Retina). If it ever lags, change the "2" back to 1.5 in setPixelRatio.
- Human trainer rebuilt: skin texture, face (eyes, nose, lips, ears, brows), textured hair, cloth-weave jacket and pants,
  hands, boots. Outfit shop colors still work.
- Enemy monsters and black dragons: block shapes replaced with smooth rounded forms; dragons get scale bump texture.
- Eggs and fireballs use much smoother geometry.

LIVING WORLD UPDATE (the surprise)
- Full day/night cycle (5 minutes per day): sunrise, golden hour, sunset, stars, moon, shooting stars.
- Dynamic weather: storms roll in on their own, with rain, thunder and lightning, darker sky and fog.
- Swaying grass that follows you, rippling river, flocks of birds by day, fireflies by night.
- Flight feel: field-of-view kick and speed lines at high speed, dragon roar + whoosh when you shoot fire.
- Flight HUD: compass heading, altitude, speed and the in-game clock.
- Cinematic film grain and vignette.
- New keys: B = call/clear a storm, N = skip ahead 3 hours, P = photo mode (hides the HUD).

FIX: the first Living World build showed a blank screen (a Three.js color call that doesn't exist crashed the first frame).
Fixed, and the new effects are now wrapped so a problem in them can never blank the game again (check the browser console for warnings).

CINEMATIC GRAPHICS UPDATE
- Full post-processing pipeline: HDR bloom/glow, god-ray sun shafts, filmic grade (warm highlights, cool shadows),
  chromatic edge softness, vignette and fine film grain.
- Live sky reflections (image-based lighting) on every material: glossy dragon scales, eyes, water, wet ground.
- 4096px sun shadows for much crisper shadows.
- Adaptive resolution: if the game runs slowly it automatically lowers render resolution a step.
- Safety: if anything in the new renderer fails it silently falls back to the normal renderer (see the browser console).

TRAINER JUMP + LIVE PLAYER COUNT
- As the trainer on foot, Space is now a normal jump (with gravity). Dragons and the Sky Bike still fly with Space / Shift.
- Dev menu (K) -> "Live Player Count": players online now, players in the last 30 days, and every username with
  online/last-seen status. It refreshes every 5 seconds while open.

IMPORTANT: this game has no server, and accounts live only in each player's own browser, so by default the
Live Player Count can only see accounts on the device you are using. To count players on ALL devices:
  1. Go to https://console.firebase.google.com and create a free project.
  2. Build -> Realtime Database -> Create database. Copy its URL
     (looks like https://your-project-default-rtdb.firebaseio.com).
  3. In the database "Rules" tab paste:
       { "rules": { "players": { ".read": true, "$u": { ".write": true } } } }
     (Anyone who knows the URL can read the player list. Fine for a prototype, not for private data.)
  4. Open index.html, find   const PLAYER_STATS_DB_URL='';   and put your URL between the quotes.
  5. Publish the game and every player's login/heartbeat will show up in the dev menu.
