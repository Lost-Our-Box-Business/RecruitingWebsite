# Lost Our Box Recruiting — Website

Static site (plain HTML/CSS, no build step) for lostourboxrecruiting.com.

## Structure

- `index.html` — the whole one-page site (hero, what we do, how it works, contact form)
- `thank-you.html` — shown after a successful contact-form submission
- `style.css` — all styling
- `netlify.toml` — tells Netlify to publish the repo root as-is

## Before this goes fully live

- **Business address**: `index.html`'s footer has a `TODO` placeholder where the real mailing
  address needs to go (legally required once this is linked from any commercial email footer —
  see the Recruiting Agent app's `OutreachTemplateBuilder`).
- **Contact form**: uses [Netlify Forms](https://docs.netlify.com/manage/forms/setup/) — no backend
  code needed. Submissions land in the Netlify dashboard and can be forwarded to
  contact@lostourboxrecruiting.com via Site settings → Forms → Form notifications → Email
  notification. This has to be configured once, by hand, after the first deploy (Netlify only
  detects the form after it sees the deployed HTML).

## Deploying

1. Push this repo to GitHub (private is fine).
2. In Netlify: **Add new site → Import an existing project**, connect the GitHub repo, leave build
   command blank and publish directory as `.` (already set via `netlify.toml`).
3. Once deployed, go to **Site settings → Domain management → Add a domain** and add
   `lostourboxrecruiting.com`. Netlify will show the DNS records to add (either point nameservers
   at Netlify, or add the specific A/CNAME records it gives you) at your domain registrar.
4. Go to **Site settings → Forms → Form notifications** and add an email notification to
   contact@lostourboxrecruiting.com so submissions actually reach someone.
