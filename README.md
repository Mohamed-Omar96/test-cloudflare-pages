# test-cloudflare-pages

Minimal static-site demo for Cloudflare Pages. Plain HTML, CSS, and a few lines of JS. No framework, no build step.

## What's here

| File | Purpose |
|---|---|
| `index.html` | Landing page |
| `style.css` | Styling |
| `_redirects` | URL redirect rules (declarative, parsed by Cloudflare) |
| `_headers` | HTTP header rules (declarative, parsed by Cloudflare) |

## Run locally

Just open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Note: `_redirects` and `_headers` are applied by Cloudflare at deploy time. They do nothing when you open the files locally.

## Deploy to Cloudflare Pages

1. Push this folder to a GitHub repo.
2. In the Cloudflare dashboard, go to **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Pick the repo. For build settings:
   - **Build command:** _(none)_
   - **Output directory:** `/` (or the subfolder path if this lives inside a larger repo)
4. Click **Save and Deploy**.

Every push to the default branch triggers a production deploy. Every pull request gets its own preview URL.

## Key things this demo is showing

- **Zero-config static hosting.** No `package.json`, no bundler, no framework. HTML goes up as-is.
- **Declarative redirects** via `_redirects` — see the file for syntax.
- **Declarative security headers** via `_headers` — see the file for syntax.
- **Pages Functions exist** (for light backend logic) but run on the Workers runtime. For anything non-trivial, use Workers directly — see the sibling `test-cloudflare-workers` folder.

## Docs

- Pages overview: https://developers.cloudflare.com/pages/
- `_redirects` reference: https://developers.cloudflare.com/pages/configuration/redirects/
- `_headers` reference: https://developers.cloudflare.com/pages/configuration/headers/
- Limits: https://developers.cloudflare.com/pages/platform/limits/
