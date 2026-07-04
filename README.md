# plenty-web

Single-page "coming soon" site for **Plenty** — used as the public URL for
Play Console / BillDesk merchant verification while the app is in internal testing.

Static HTML/CSS/JS, no build step. Everything lives in `index.html`.

## Publish on GitHub Pages

```bash
cd plenty-web
git init -b main
git add .
git commit -m "Plenty coming-soon landing page"
gh repo create plenty-web --public --source=. --push   # or create the repo on github.com and push
```

Then on GitHub: **Settings → Pages → Build and deployment → Source: "Deploy from a branch"**,
branch `main`, folder `/ (root)`. Save.

Live in ~1 minute at: **https://sandy1206.github.io/plenty-web/**

> The repo must be **public** for free GitHub Pages. `.nojekyll` skips the Jekyll build.

## Waitlist form (FormSubmit)

The email form POSTs to `https://formsubmit.co/ajax/arsudesandip4@gmail.com` — a free,
no-signup form backend that emails each submission to that address.

**One-time activation required:** the first submission triggers a confirmation email to
`arsudesandip4@gmail.com`. Click the link in it, otherwise submissions are not delivered.

Optional hardening after activation: FormSubmit's activation email gives you a random
alias (e.g. `formsubmit.co/ajax/a1b2c3...`) — swap it into `WAITLIST_EMAIL` in
`index.html` so your raw address isn't in the page source for the form (it still
appears in the visible mailto links, which is intentional for merchant verification).

## Later

- Custom domain: add a `CNAME` file + DNS record, no other changes needed.
- Privacy policy (required for Play listing): add `privacy.html` here and link it
  from the footer → `https://sandy1206.github.io/plenty-web/privacy.html`.
