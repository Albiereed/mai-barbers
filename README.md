# Mai Barbers — booking website

A mobile-friendly booking website for Mai Barbers, live at
**https://mai-barbers.vercel.app**

Customers pick a real open day and time straight off the calendar on the homepage,
enter their name and phone number, and the booking is confirmed instantly — the
slot is locked the moment they book so nobody else can take it.

The admin signs in at **`/admin.html`** to set weekly opening hours, generate
bookable slots, add one-off times, and view or cancel bookings.

## How it's built

This is a plain static site (`index.html`, `admin.html`) — no build step, no
server code. All the booking logic runs in the browser against a
[Supabase](https://supabase.com) Postgres database:

- **`slots`** — individual bookable times (date, start, end, booked or not)
- **`bookings`** — who booked what
- **`availability_template`** — the weekly hours used to generate new slots
- Row Level Security keeps this safe: anyone can see and book an *open* slot,
  but only a signed-in admin can see bookings, edit hours, or manage slots.
  Booking itself goes through a `book_slot` database function that locks the
  row so two people can never grab the same time.

Because everything is static, it deploys anywhere for free — this project is
hosted on [Vercel](https://vercel.com), connected to this GitHub repo, so any
change pushed to `main` goes live within a minute or two.

## Day-to-day use

- **Set your hours / generate times / manage bookings** — sign in at
  `https://mai-barbers.vercel.app/admin.html`. No code changes needed for any
  of this.
- **Change wording, prices, colours, photos** — edit `index.html` on GitHub
  (or ask Claude to) and push. Vercel redeploys automatically.

## The Supabase project

Project: **mai-barbers**, region Oceania (Sydney). The site connects to it
with a public "publishable" key that's safe to expose in the page source —
Row Level Security is what actually keeps data safe, not the key. The admin
password is set via Supabase's own invite-email flow and is never stored in
this repo.

If you ever need to change database settings, sign in at
[supabase.com](https://supabase.com) → the **mai-barbers** project.

## Local development (optional)

There's nothing to install or build — these are plain HTML files. Open
`index.html` directly in a browser, or serve the folder with any static
file server:

```
npx serve .
```
