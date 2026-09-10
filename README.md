# Mai Barbers — website + booking form

This repo is a complete, ready-to-deploy website:

- `index.html` — the full site, including a working booking **request form** (name, phone, service, preferred date/time, notes)
- `thank-you.html` — the confirmation page a visitor lands on if their browser has JavaScript turned off

There's no old booking system linked anywhere — requests are collected straight off this site and land in your own inbox.

## The two free pieces

1. **Vercel** hosts the site itself and gives you the live link (and later your own domain).
2. **FormSubmit.co** catches the booking form and emails you each request — Vercel only hosts files, it doesn't process forms on its own, and FormSubmit is a free, no-signup way to fill that gap without writing any backend code.

## 1. Point the form at your email (2 minutes)

Open `index.html` in this repo, find this line near the booking form (search for `formsubmit`):

```html
<form method="POST" action="https://formsubmit.co/you@example.com" id="bookingForm">
```

Replace `you@example.com` with the email you want bookings sent to, and commit the change.

**Important — activate it:** the very first submission FormSubmit receives for a new email address triggers a one-time confirmation email to that address. Open it and click **Confirm** or bookings won't come through. Easiest way to trigger that: deploy the site (step 2), then submit the booking form yourself once with test details.

## 2. Connect this repo to Vercel

1. Go to **vercel.com** and sign in (you can sign in with your GitHub account).
2. Click **Add New → Project → Import Git Repository**, and choose this `mai-barbers` repo.
3. Leave the build settings as default — it's plain HTML, no build step needed — and click **Deploy**.
4. You'll get a live link immediately, like `https://mai-barbers.vercel.app` — that already works from any phone or computer, anywhere.

From then on, any change pushed to this repo (including edits made right in GitHub's web editor) redeploys automatically — no re-uploading files.

## 3. Connect your own domain

Buying a domain isn't free (usually ~NZ$20–45/year — e.g. a `.co.nz` or `.com` from a registrar like Namecheap, GoDaddy, or a `.nz`-approved NZ registrar), but attaching it to Vercel is:

1. In your Vercel project: **Settings → Domains → Add**.
2. Type your domain and follow the on-screen instructions — either point your domain's nameservers at Vercel, or add the A/CNAME records it gives you at your registrar.
3. Vercel issues a free SSL certificate automatically once the DNS change is detected (can take anywhere from a few minutes to a few hours).

## 4. Making changes later

- Small edits (prices, hours, phone number, text): edit `index.html` right in GitHub (click the file, then the pencil/edit icon), commit the change, and Vercel redeploys automatically within a minute or two. I can also make these edits for you any time — just send me what should change.
- Prices and hours on the current site are placeholders — search `index.html` for the `$` prices and the hours table to swap in your real numbers.

## Notes

- The booking form only works once the site is deployed and your FormSubmit email is confirmed (see step 1) — opening `index.html` directly on your computer won't send anything anywhere.
- Real info already on the site: business name, address (499 Princes Street, Dunedin), and your Instagram/TikTok/Facebook links.
- Still placeholders to update: service prices, opening hours, and there's no phone number on the site yet — send it over and I'll add it.
