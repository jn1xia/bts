# bts

Unofficial 3D seat-view simulator for **BTS WORLD TOUR 'ARIRANG' in Jakarta** at Gelora Bung
Karno (GBK) Main Stadium: Sat 26, Sun 27 and Tue 29 December 2026 (the 29th was added on 17 June).

Open `index.html` in a browser (it loads three.js r128 from cdnjs). The whole site is that one file.

## What it does

- **My seat**: a first-person view from any seat at eye height, seated or standing. Drag to look
  around; scroll, pinch or use the Eyes / 2× / 4× buttons to zoom.
- **Stadium**: orbit the whole bowl. Sections are tinted by ticket category; click one to sit there.
- **Seat panel**: pick a seat from the map (drawn to scale, laid out like the official seat map),
  the section list, or the row and seat sliders. It shows the distance to the nearest stage edge,
  the pavilion and the nearest corner stage, your eye height, how much of the best screen a
  sightline raycast can see and how big it looks, how tall a member looks at arm's length, and
  whether GBK's ring roof covers your seat.
- **Stage**: the 360° stage described in reviews of the tour, with a pavilion modelled on
  Gyeonghoeru (hipped-and-gabled roof with upturned eaves and a dancheong band) over a turntable
  with a taegeuk LED floor. Four runways narrow in steps to lifting corner stages, and their LED
  strips are solid or broken like the trigram in that corner of the Korean flag. Four LED screens
  hang under the roof, one facing each side.
- **Crowd**: every seat is sold. Fans near you are jointed figures at two levels of detail, in
  tour tees and everyday colours, some in bucket hats. Most hold an ARMY Bomb Ver. 4 (clear globe
  on a slim handle). About 8% hold up printed slogan banners ("BORAHAE", "SELAMAT DATANG",
  "WELCOME HOME" and more), and about 18% also film on their phones. Every other seat shows its
  ARMY Bomb as a point of light, and one pose shader moves every fan and glow together.
- **Moments** (Auto cycles through them): Purple ocean, ARIRANG red (a white sweep round the bowl),
  Taegeuk (the stadium splits red and blue), Rainbow (with the turntable spinning), Fireworks (from
  the roof ring, with flame cannons), Phone lights, and Slogans up. The ARMY Bombs are centrally
  synced, as on the real tour.
- **Performers**: seven stand-in figures (generic, not likenesses) dance on the turntable, walk the
  runways to the corner stages, ride the lifts up and come back on an 80-second loop, each under a
  follow spot from the decks at the back of the upper tribune.
- **Show / House lights**, **Clear / Rain** (late December is the rainy season in Jakarta; rain
  stays off the stands under the roof, and fans in the open put on ponchos), Jakarta's skyline
  around the stadium, and a D-day countdown to the next show.

## Data

Ticket categories and prices follow iMe Indonesia's seat map. Prices exclude tax and admin fees.
Every category has numbered seats, and all three shows are sold out.

| Category | Where | Price |
| --- | --- | --- |
| VIP Package | Floor blocks A–D between the runways; includes the soundcheck | Rp4.500.000 |
| Platinum Floor / Tribune (lower) | Floor blocks A–D behind the VIP blocks, and the front rows of the lower tribune | Rp3.650.000 |
| CAT 1 (lower tribune) | Back rows of the lower tribune | Rp2.800.000 |
| CAT 2 (upper tribune) | Front rows of the upper tribune | Rp2.300.000 |
| CAT 3 (upper tribune) | Back rows of the upper tribune | Rp1.800.000 |

The layout follows the official map: FOH and production at the B end, a tunnel with production
either side of it at the D end, camera decks mid A and C sides, follow-spot decks round the back of
the upper tribune, and wheelchair bays along the front of the B half of the lower tribune.

The bowl is scaled from the official map (about 0.4 m per pixel). The front of the lower tribune
is a four-centred oval and every row is parallel to it. With 38 lower and 26 upper rows, the model
has 77,136 tribune seats, close to GBK's published capacity of 77,193. Exact block edges, sector
numbers, row counts, stage and screen sizes, and where the roof ends are **estimates**, so confirm
your seat against the official map.

Not affiliated with BIGHIT MUSIC, HYBE, iMe Indonesia, Live Nation or GBK.

## Visitor counter

The published site shows "N visitors so far" under the title. It counts each browser once: the
first visit adds one and leaves a flag in the browser, and later visits only read the total. It uses
[Abacus](https://github.com/JasonLovesDoggo/abacus), a free counter service that needs no account.
It runs only on `jn1xia.github.io`, so local copies and previews never change the count. If the
service is slow or down, the line simply stays hidden.

- **See the total any time:** https://abacus.jasoncameron.dev/get/jn1xia.github.io/bts-arirang-visitors
- **Protect the count (optional, only possible before the counter goes live):** open
  https://abacus.jasoncameron.dev/create/jn1xia.github.io/bts-arirang-visitors in a browser and save
  the `admin_key` it shows somewhere private (never in this repo). With that key you can later
  correct the number with Abacus's `/set` call. Once the live site has counted a single visit,
  `/create` is refused for good.
- **Limits:** this counts browsers, not people. The same person counts again on another device,
  after clearing browser data, and in each app's built-in browser (Instagram, TikTok and WhatsApp
  keep separate storage). Browsers that block storage only see the total and are not counted.

For visitors per day, countries and devices, sign up free at [GoatCounter](https://www.goatcounter.com)
and put your site code in `GOATCOUNTER_CODE` near the end of `index.html`.

## Deploy

Hostinger no longer has a free plan (its free brand, 000webhost, closed in 2024), so this uses
GitHub Pages, which is free for public repositories.

- **Right now, from this branch:** go to Settings → Pages → Build and deployment, set Source to
  "Deploy from a branch", then pick branch `ccr-c2cf7112-cju41j` and folder `/ (root)`. The site goes
  live at https://jn1xia.github.io/bts/ in about a minute.
- **From `main` later:** set Source to "GitHub Actions". `.github/workflows/pages.yml` then
  publishes every push to `main`, and you can also run it by hand from the Actions tab.

Any other static host works too: upload `index.html` as the site's only file. (The visitor counter
only counts on `jn1xia.github.io`; add another host name to `LIVE_HOSTS` in `index.html` to count
there.)

To preview locally, serve the folder, for example `python3 -m http.server`, and open
http://localhost:8000. Add `?debug` to the address to expose a small `window.__bts` test hook.
