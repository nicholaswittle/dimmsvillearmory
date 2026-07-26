# Dimmsville Armory

Website for Dimmsville Armory — a licensed Type 07 firearms manufacturer and NFA/Class III
dealer in Thompsontown, Pennsylvania.

Built by [WiSense LLC](https://wisensellc.com).

## What it is

A single self-contained page. No dependencies, no build step, no framework — `index.html`
carries its own styles and scripts, and the only other files are two deploy configs.

- **FFL transfer request form** — customers buying from out-of-state dealers submit the firearm
  and selling-dealer details, and the shop is emailed directly
- **Special order inquiry form** — for firearms, optics, ammo, and accessories not in stock
- Services, transfer walkthrough, FAQ, hours with live open/closed status, and map

### Intake only

Nothing is sold or paid for on this site. Both forms collect information so the shop can start a
conversation — every sale, ATF Form 4473, background check, and payment happens in person at the
licensed premises. Neither form asks for a Social Security number, driver's license number, date
of birth, or home address.

## Deploying

Canonical host is Cloudflare Workers (static assets, no server code):

```bash
pnpm dlx wrangler deploy
```

Vercel serves a 307 redirect to the Worker so the `.vercel.app` URL stays valid:

```bash
npx vercel --prod
```

## Local development

Open `index.html` in a browser. That's the whole workflow.

## Configuration

| What | Where |
|---|---|
| Store hours | `SCHED` object in the inline script — also update `openingHoursSpecification` in the `<head>` |
| Form delivery | `action` on both `<form>` elements |
| Phone number | Search `7179536359` |
| Colors | The four `:root` token blocks at the top of the `<style>` |
| Hero photo | Commented `<img>` slot inside `.hero-media` |
