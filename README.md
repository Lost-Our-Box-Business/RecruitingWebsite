# Lost Our Box Recruiting — Website

Static site (plain HTML/CSS, no build step) for lostourboxrecruiting.com, hosted on **GitHub
Pages** (free) at `Lost-Our-Box-Business/RecruitingWebsite`.

## Structure

- `index.html` — the whole one-page site (hero, what we do, how it works, contact form)
- `thank-you.html` — shown after a successful contact-form submission
- `style.css` — all styling
- `CNAME` — tells GitHub Pages which custom domain to serve this repo at (lostourboxrecruiting.com)

## Before this goes fully live

- **Contact form backend**: GitHub Pages only serves static files — no server code, so it can't
  process a form submission itself the way Netlify Forms could. This site uses
  [Formspree](https://formspree.io) instead (free tier, 50 submissions/month):
  1. Sign up free at formspree.io with contact@lostourboxrecruiting.com (or forward to it).
  2. Create a new form; Formspree gives you a form ID (`https://formspree.io/f/xxxxxxxx`).
  3. In `index.html`, replace `REPLACE_WITH_FORMSPREE_ID` in the `<form action="...">` with that ID.
  4. Formspree emails you every submission automatically — no extra dashboard step needed.
- **Business address**: `index.html`'s footer has a `TODO` placeholder where the real mailing
  address needs to go (legally required once this address is reused in any commercial email
  footer — see the Recruiting Agent app's `OutreachTemplateBuilder`).

## DNS (GoDaddy)

GitHub Pages needs these records at GoDaddy for `lostourboxrecruiting.com` (apex domain) plus
`www`. In GoDaddy: **My Products → DNS → Manage** for the domain, then add/edit:

| Type  | Name | Value                  |
|-------|------|------------------------|
| A     | @    | 185.199.108.153        |
| A     | @    | 185.199.109.153        |
| A     | @    | 185.199.110.153        |
| A     | @    | 185.199.111.153        |
| CNAME | www  | lost-our-box-business.github.io |

Delete any existing GoDaddy "parked domain" A record or forwarding rule for `@` first — GoDaddy
often defaults new domains to a parking page that conflicts with these. DNS propagation can take
up to a few hours.

Once DNS resolves, go to the repo's **Settings → Pages** and confirm the custom domain shows a
green check, then enable **Enforce HTTPS** (GitHub auto-issues a certificate once DNS is verified,
usually within an hour).

## Local preview

Just open `index.html` directly in a browser — no build step or server needed for basic viewing.
