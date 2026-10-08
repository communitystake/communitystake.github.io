# Community Stake Foundation website

Static website for Community Stake Foundation, Sint Maarten. Plain HTML and CSS with no build step and no frameworks, hosted on GitHub Pages.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Home |
| `about.html` | About / Our purpose |
| `how-we-work.html` | How we work |
| `vendors.html` | Local vendor registration form |
| `proposals.html` | Project proposal form |
| `contact.html` | Contact details and privacy note (`contact.html#privacy`) |
| `thank-you.html` | Confirmation page after a form is sent |
| `404.html` | Page-not-found page (GitHub Pages serves it automatically) |
| `styles.css` | Shared stylesheet |
| `favicon.svg` | Site icon |
| `robots.txt` | Currently blocks all crawlers (noindex period) |

All links are relative, so the site works unchanged at a `github.io` address or a custom domain.

## Before going live

1. **Form endpoints.** In `vendors.html` and `proposals.html`, replace `VENDOR_FORM_ID` and `PROPOSAL_FORM_ID` in the form `action` URLs with the real Formspree form IDs.
2. **Email placeholder.** Replace every `[CSF email]` with the public contact address (footer on every page, plus `contact.html`).
3. **Redirect after submit.** The forms submit via JavaScript (AJAX) and then open `thank-you.html`, which works on the Formspree free plan. The hidden `_next` field is only used on paid Formspree plans and must then hold the full URL, for example `https://example.org/thank-you.html?form=vendor`.
4. **Formspree settings.** Restrict each form to the site's domain, and keep the `_gotcha` honeypot field.

## Publishing on GitHub Pages

Repository Settings → Pages → Deploy from a branch → `main` / root. For a custom domain, add it under Settings → Pages (GitHub creates a `CNAME` file) and point the domain's DNS at GitHub Pages.

## Search indexing (temporary)

Pages currently include `<meta name="robots" content="noindex, nofollow">` and `robots.txt` disallows all crawlers so the free `github.io` address stays out of search results. **Remove noindex when the custom domain goes live** (strip the meta tag from every HTML page / from `tools/build.py`, and change `robots.txt` back to `Allow: /`).
