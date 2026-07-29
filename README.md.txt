# Ahlaat.Pk

A simple storefront (product grid + cart + checkout) with a backend that emails
you on Gmail every time someone places an order, and sends the customer a
confirmation email too.

## 1. Get a Gmail App Password

Gmail won't accept your normal password for this — you need an "App Password":

1. Turn on 2-Step Verification on your Google account (required first): https://myaccount.google.com/security
2. Go to https://myaccount.google.com/apppasswords
3. Create a new app password (name it anything, e.g. "Ahlaat.Pk")
4. Copy the 16-character password it gives you

## 2. Configure the project

```bash
cp .env.example .env
```

Open `.env` and fill in:
```
GMAIL_USER=youraddress@gmail.com
GMAIL_APP_PASSWORD=the16charpassword
```

## 3. Install and run

```bash
npm install
npm start
```

Then open http://localhost:3000 in your browser. Add items to the cart,
check out, and you should get an order email in your Gmail inbox within a
few seconds (plus a confirmation email sent to whatever address the
customer typed in).

## Editing your products

Open `public/index.html` and edit the `PRODUCTS` array near the top of the
`<script>` tag — change names, prices, descriptions, and emoji icons (or
swap the emoji for real `<img>` tags if you have product photos).

## Putting this online (so real customers can order)

Right now this only runs on your own computer. To make it a real live
store, deploy it to a host that runs Node.js servers, for example:

- **Render** (render.com) — free tier, connects to a GitHub repo
- **Railway** (railway.app)
- **Fly.io**

In any of these, you'd push this folder to GitHub, connect the repo, and
set `GMAIL_USER` / `GMAIL_APP_PASSWORD` as environment variables in their
dashboard (never commit your `.env` file).

## Notes and limits

- This is a minimal starter, not a full Shopify replacement: there's no
  payment processing (Stripe/PayPal), no inventory tracking, and no order
  database — every order just triggers an email. That's usually enough for
  a small shop taking orders manually (e.g. "pay via Venmo, I'll ship it"),
  but add a payment gateway before handling real transactions at any volume.
- The cart lives in the browser tab's memory — refreshing the page clears it.
-