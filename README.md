# SWP-SEA · Mykonos 2026

One file: `index.html`. No build step, no dependencies, nothing to install.
Open it locally, or drop it on Netlify Drop / Vercel / GitHub Pages and send the link.

## Everything editable lives in one place

Open `index.html`, scroll to `const CONFIG = {` near the top of the `<script>`.
Countdown, crew, teams, rooms, packing list, villa facts and the whole itinerary
are in there. Nothing below `END OF CONFIG` needs touching.

## Crew photos

Put images next to `index.html` (e.g. an `img/` folder) and swap:

    { name: "Cameron", photo: null }        ->   { name: "Cameron", photo: "img/cam.jpg" }

Square crops, roughly 300x300, work best.

## Villa photos and video

The nine photos are embedded in the file as WebP, so it stays a single file you
can send anywhere. To swap one, search `<figure class=` in the villa section and
replace the `src`. To cut the file size, point them at real files instead:

    <figure class="g3"><img src="img/villa-03.jpg" alt="..." loading="lazy"></figure>

Gallery sizes are `g2` (square), `g3` (3:2) and `g4` (5:4). Mix them for the
scrapbook look.

The tour video loads only when someone taps play, so the page stays light.
Change `videoId` in `CONFIG.villa` to swap it.

## Teams

`order` controls where each team appears on screen (1, 2, 3 reads Thursday,
Friday, Saturday). `day` and `drink` are what gets printed. The itinerary
references teams by `id`, not by position, so reordering is safe.

## Itinerary

Each day has a `date` (real calendar date, used for weather and the DONE stamp)
and a `label` (what is printed on the card).

`cocktailAt` and `specialAt` decide which row the cocktail tag and the special
event box sit under: `"morning"`, `"afternoon"`, `"evening"`, `"dinner"` or
`"late"`. Remove the field and the block disappears.

Note: the supplied itinerary says Wednesday 17th, but 17 September 2026 is a
Thursday, and the airport meet is Wednesday 16th. Labels were left as supplied.

## Weather

Open-Meteo, no API key, refreshes every 30 minutes. Forecasts only exist about
16 days ahead, so cards show "Forecast coming soon" until then.
