# halftoneatheer.com

Single page site. No build step, no dependencies. Open `index.html` in a browser
and it runs.

## Files

```
index.html                    the whole site
favicon.svg                   the mark
CNAME                         custom domain for GitHub Pages
assets/
  HalftoneDisplay.woff        the typeface, used by the page
  HalftoneDisplay.ttf         same typeface, for design tools
  halftone.webp               the portrait
  share.png                   link preview image
.nojekyll                     stops GitHub reprocessing the files
```

## Publishing on GitHub Pages

1. Create a repository and upload everything in this folder to the root.
2. Settings, then Pages.
3. Under Source choose **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. Save. The first build takes about a minute.

The site appears at `https://YOURNAME.github.io/REPO/`.

## Custom domain

`CNAME` already contains `halftoneatheer.com`, so Pages will ask for that domain
as soon as you publish. To make it resolve, add these records at your registrar:

| Type  | Name | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | YOURNAME.github.io     |

Then tick **Enforce HTTPS** in Settings, Pages. DNS can take a few hours.

If you want to test on the github.io address first, delete `CNAME`.

## Things you will want to change

**Booking link.** Bottom of `index.html`:

```js
const CAL_LINK = "atheer-half-tone-iv7zpe/30min";
```

Drives the popup, the preload and the fallback link together.

**Social links.** Instagram and Behance in the footer still point at `#contact`.
Replace those two `href` values with real URLs.

**Email.** `ahlan@halftoneatheer.com`, in two places, the footer link and the
`mailto:` behind it.

**The drawing.** The composition is defined once, near the top of the script, as
`STROKES`, six paths for one half which are mirrored on the fly. The relief at the
foot of the page is `LOWER`, six filled shapes, same idea. Editing a number there
changes the hero, the About background and the footer together.

**The mark.** Six `<g class="pk">` rectangles in the header. Move a coordinate and
the physics follows it, nothing else to update.

## Notes

Reduced motion is respected throughout: the drawing stops breathing, the relief
holds still, the pucks stay home.
