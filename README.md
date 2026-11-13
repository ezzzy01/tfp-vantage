# TFP Vantage: product page

The public website for **TFP Vantage**, the AI assistant for SAP Business One by **TFP Digital Sdn. Bhd.**
One static page: no build step, no server code, no database. Any static host can serve it (GitLab Pages, GitHub Pages,
a web server).

To publish it on GitLab, see [DEPLOY-GITLAB.md](DEPLOY-GITLAB.md).

## What is on the page

| Section | What it shows |
|---|---|
| Top | Headline, "Try it now" (live demo) and "Watch the video" |
| Video | 92-second video of TFP Vantage on SAP's sample company |
| Features | Sales, money, stock, look-ups, charts and Excel, the team |
| See it | Real screens: answers, dashboard, customer page, lists, dark mode, phone |
| How it works | Connect read-only, ask in plain words, get the answer |
| Security | Read-only, on your own server, sign-in and roles, companies kept apart |
| Pricing | On your server, Hosted by us, Enterprise |
| FAQ | Common questions |
| Contact | Email, and "a product of TFP Digital Sdn. Bhd." |

## Files

```
index.html                    the whole page (text, layout, colours, scripts)
assets/favicon.svg            the TFP Vantage "V" icon in the browser tab
assets/brand/                 TFP Digital logo (tfp-digital-96.png, tfp-digital-192.png)
assets/img/                   screenshots (01-...webp); "-960" = smaller copy for phones
assets/video/                 the video (tfp-vantage-720.mp4) and its still frame (poster.jpg)
.gitlab-ci.yml                publishes the page with GitLab Pages
.nojekyll                     only for GitHub Pages; harmless elsewhere
```

## Changing things

All changes are in `index.html`. Open it in any text editor, search for the text below, change it, save, and upload
it again (or commit and push). GitLab republishes the page by itself within a minute or two.

| To change | Search `index.html` for |
|---|---|
| The live demo address ("Try it now") | `<meta name="demo-url" content="...">` near the top. Empty = the buttons become "Ask for a demo" by email |
| Contact email | `idham.hakim@tfp.com.my` (it appears in several places: change them all) |
| Prices | `RM 90`, `RM 1,000`, `RM 3,000` (pricing section and the FAQ answer "How much does it cost?") |
| Plan details | `<div class="plan` (one block per plan) |
| Questions and answers | `<details>` (one block per question) |
| Screenshots | Replace the files in `assets/img/` with new ones of the same name and size (1440 x 900) |

## Good to know

- Screens and the video show **SAP's public sample company (OEC Computers)**, never real customer data.
- The page loads nothing from other websites: no trackers, no fonts or scripts from elsewhere.
- Light and dark mode follow the visitor's device. It works on phones from 360 px wide.
- SAP and SAP Business One are trademarks of SAP SE (as the page footer says).
