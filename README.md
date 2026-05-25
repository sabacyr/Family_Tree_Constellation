# Family Tree in Constellation Style by Saba Cyr
 
My grandmother used to tell me that the stars in the sky are our loved ones and families who have passed, looking down at us to protect us. I never forgot that. This project is my way of keeping that idea alive. Every person in my family gets a star. The older they are, the brighter and bigger it burns. You can hover over them, watch the constellation lines reach out to their family, and click to open their story.
 
It is a single HTML file. Just open it in a browser and your family is there in the sky.
 
---
 
## What you see when you open it
 
A deep purple night sky. Hundreds of tiny stars twinkling across the screen. Soft nebula clouds drifting slowly in shades of violet, cobalt, teal, and rose. A moon in the top corner shaped by the actual phase of the moon tonight. Every now and then a shooting star crosses the sky.
 
Scattered among the decorative stars are your family members. Each one is a glowing five-pointed star, sized and colored by generation. Great-grandparents burn large and gold. Grandparents glow purple. Parents shimmer blue. Your generation shines green. Children pulse pink.
 
Hover over a star and dashed constellation lines reach out to their spouse, parents, and children. Their name floats above them. Click, and a frosted glass panel slides in from the right showing the full family tree, every generation arranged oldest at the top and youngest at the bottom, styled like a retro pixel screen.
 
---
 
## Features
 
**The sky**
- Real moon phase calculated from today's date, all 8 phases rendered correctly
- Six nebula clouds slowly rotating in distinct colors
- 1200 background stars filling the full screen, each twinkling at its own rate
- Shooting stars appearing from random directions, fading cleanly
- Live clock and date in the bottom left corner
**The stars**
- Every person is a star, size and color set by generation
- Large stars breathe with a slow pulse, important ancestors pulse faster
- Hover shows constellation lines to immediate family and a name label
- Click triggers a sparkle burst and opens the family panel
**Navigation**
- Scroll to zoom in toward your cursor
- Click and drag to pan when zoomed in
- Zoom never goes past the opening view, no empty black space ever
- Dragging is disabled at minimum zoom
**The family panel**
- Full ancestry chart as a pure SVG diagram
- Generations labeled from great-grandparents down to grandchildren
- Blue header bar for male, rose for female
- Pink heart marriage line between couples, red broken line with X for divorced
- The person you clicked is highlighted with a glowing border
- Panel opens with the clicked person's generation centered on screen
- Frosted glass background, the starfield shows through
- CRT scanline effect, pixel font, typing animation on the name
- Cards load in staggered from top to bottom when the panel opens
- Scroll inside the panel independently from the sky zoom
---
 
## How to add your family
 
Open the file in any text editor or directly on GitHub. Find this near the top of the script:
 
```js
const people = {
```
 
Each person is one line:
 
```js
p1: { name:"Grandmother", born:1921, died:2003, spouse:"p2",
      size:19, color:"#ffd97a", gender:"f" },
```
 
**Fields you need:**
 
| Field | Example | What it means |
|-------|---------|---------------|
| `name` | `"Sarah Jones"` | Full name |
| `born` | `1950` | Birth year |
| `died` | `1990` or `null` | Death year, or null if still alive |
| `size` | `9` | How big the star appears |
| `color` | `"#90d8ff"` | Star color as a hex code |
| `gender` | `"m"` or `"f"` | Card color in the panel |
 
**Fields you can add optionally:**
 
| Field | Example | What it means |
|-------|---------|---------------|
| `spouse` | `"p2"` | ID of their partner |
| `parents` | `["p1","p2"]` | IDs of father and mother |
| `divorced` | `true` | Shows a broken line instead of a heart |
 
**Star sizes by generation:**
 
| Size | Who |
|------|-----|
| `19` | Great-grandparents |
| `15` | Grandparents |
| `12` | Parents |
| `9` | Your generation |
| `7.5` | Children |
 
**Color ideas:**
 
| Color | Hex |
|-------|-----|
| Warm gold | `#ffd97a` |
| Soft purple | `#c8b8ff` |
| Sky blue | `#90d8ff` |
| Mint green | `#b8f0c8` |
| Pink | `#ffc8e8` |
| Amber | `#ffb870` |
 
Every entry except the last one inside `people { }` needs a comma at the end.
 
---
 
## Putting it online with GitHub Pages
 
1. Create a new repository on github.com
2. Upload `family_tree_constellation_template.html` and this README to the repo
3. Update the template with your family's information and rename it to `index.html`
4. Go to Settings, then Pages, then set Source to main branch and save
5. Your site goes live at `https://yourusername.github.io/repo-name/star_family_tree_commented.html`
To update: click the file on GitHub, click the pencil icon, edit the `people` section, click Commit changes. The live site updates in about 30 seconds.
 
---
 
## Customization
 
**Nebula colors** -- find `const nebulae = [` and change the `color` and `a` values. Higher `a` means more vivid.
 
**Star density** -- find `Array.from({ length: 1200 }` and change 1200 to whatever feels right.
 
**Shooting star frequency** -- find `nextShoot = 5000 + Math.random() * 9000`. Lower numbers mean more frequent.
 
**Shooting star speed** -- find `const speed = 4 + Math.random() * 3` and increase the 4.
 
**Panel width** -- find `width: 760px` in the `#panel` CSS rule.
 
---
 
## Technical notes
 
One HTML file. The pixel font Press Start 2P loads from Google Fonts, if offline it falls back to Courier New. The family chart uses pure SVG rectangles and text elements, so it renders correctly in all browsers. The sky runs on an HTML5 canvas at 60fps. The moon phase is calculated from a known reference date and the 29.53-day lunar cycle. Stars are placed in a world coordinate space equal to the screen size so there is never empty black space at minimum zoom.
 
---
