# NDUSTRIO.US

Industrial-strength design & development studio site. A single-page static site built with raw HTML, Tailwind CSS, and vanilla JavaScript — deployed on Netlify.

**Live:** [ndustrio.us](https://ndustrio.us)

## Stack

| Layer       | Tech                                                       |
|-------------|------------------------------------------------------------|
| Markup      | Single `index.html` — no framework, no build step          |
| Styling     | [Tailwind CSS](https://tailwindcss.com) via CDN            |
| Typography  | [Azeret Mono](https://www.fontshare.com/fonts/azeret-mono) via Fontshare |
| Icons       | [Iconify](https://iconify.design) (Lucide set)             |
| Effects     | CSS glitch text, scanline overlay, chromatic aberration, noise texture |
| Forms       | [Netlify Forms](https://docs.netlify.com/forms/setup/) with honeypot spam protection |
| Hosting     | [Netlify](https://netlify.com) with automatic SSL          |

## Project Structure

```
.
├── index.html          # The entire site — markup, styles, and scripts
├── favicon.svg         # SVG favicon (cyan "N" on black)
├── og-image.png        # 1200x630 Open Graph social share image
├── site.webmanifest    # PWA manifest
├── netlify.toml        # Netlify config — publish dir, security headers, caching
└── .gitignore
```

## Local Development

No install, no build. Just open the file:

```sh
open index.html
```

Or serve it locally for Netlify Forms testing:

```sh
npx netlify-cli dev
```

## Deployment

Pushes to `main` auto-deploy via Netlify. There is no build command — Netlify serves the static files directly from the repo root.

### Netlify Config

Defined in `netlify.toml`:

- **Publish directory:** `.` (repo root)
- **Security headers:** `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy`, `Content-Security-Policy`
- **Caching:** SVG assets cached for 1 year (`immutable`)

### Custom Domain

DNS for `ndustrio.us` points to Netlify. SSL is provisioned automatically via Let's Encrypt.

## Contact Form

The contact form uses Netlify Forms — no backend code required. Submissions appear in the Netlify dashboard under **Forms > contact**. Spam protection is handled by a hidden honeypot field.

## Analytics

An analytics placeholder exists in the `<head>` of `index.html`. Drop in your preferred provider:

```html
<!-- Analytics: drop your snippet here (Plausible, Umami, etc.) -->
<script defer data-domain="ndustrio.us" src="https://plausible.io/js/script.js"></script>
```

Or enable [Netlify Analytics](https://docs.netlify.com/monitor-sites/analytics/) from the dashboard (no code change needed).

## OG Image

The `og-image.png` is a generated 1200x630 card used for social sharing previews (Twitter, Slack, iMessage, etc.). To regenerate it with ImageMagick:

```sh
magick -size 1200x630 xc:black \
  -font "Courier-Bold" -pointsize 110 -fill white -gravity center -annotate +0-60 "NDUSTRIO.US" \
  -font "Courier-Bold" -pointsize 24 -fill "#00ffff" -gravity center -annotate +0+60 "DESIGN  &  DEVELOPMENT" \
  -stroke "#ff00ff" -strokewidth 2 -draw "line 350,345 850,345" \
  og-image.png
```

## License

All rights reserved. This is a proprietary site for NDUSTRIO.US / Ndustrious Design Group.
