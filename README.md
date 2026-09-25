# Lost Our Box Recruiting — Website

Static site (plain HTML/CSS, no build step) for lostourboxrecruiting.com, hosted on **GitHub
Pages** (free) at `Lost-Our-Box-Business/RecruitingWebsite`.

## Structure

- `index.html` — the whole one-page site (hero, what we do, how it works, contact form)
- `thank-you.html` — shown after a successful contact-form submission
- `style.css` — all styling
- `CNAME` — tells GitHub Pages which custom domain to serve this repo at (lostourboxrecruiting.com)

## Contact form and address

- **Contact form backend**: GitHub Pages only serves static files, so it can't process a form
  submission itself. The form posts to [FormSubmit](https://formsubmit.co) (free, no account), which
  emails every submission to contact@lostourboxrecruiting.com. **One-time activation:** the very
  first submission makes FormSubmit email an activation link to that address; click it once and
  submissions flow from then on. Spam is handled by a hidden honeypot field (`_honey`).
- **Business address**: the footer shows the same mailing address the Recruiting Agent app prints in
  every outreach email's CAN-SPAM footer (820 West Spring Creek Pkwy, #400z, Plano, TX 75023). If it
  ever changes, update it here and in the app's Settings > Email sending.

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
