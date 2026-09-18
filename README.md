# Sound Signal website

One-page site for soundsignal.co. Plain HTML, no build step, no dependencies.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole site. All CSS, JS and images are inline, so this file is the site. |
| `404.html` | Branded not-found page. GitHub Pages serves this automatically. |
| `CNAME` | Tells GitHub Pages the custom domain is soundsignal.co. Do not delete. |
| `Sound-Signal-5-Signs-Checklist.pdf` | The lead magnet. Linked from the checklist section. |
| `og-image.png` | Preview image shown when the link is shared on LinkedIn, Slack, iMessage. |
| `favicon.ico`, `favicon-512.png`, `apple-touch-icon.png` | Browser tab and home screen icons. |
| `robots.txt`, `sitemap.xml` | Search engine basics. |
| `.nojekyll` | Stops GitHub from running Jekyll on the folder. |

## Deploy to GitHub Pages

1. Create a repo, for example `sound-signal-site`. Public is fine and free.
2. Upload everything in this folder to the root of the repo.
3. Repo **Settings > Pages**. Source: "Deploy from a branch". Branch: `main`, folder: `/ (root)`. Save.
4. Still on the Pages screen, set the custom domain to `soundsignal.co` and check "Enforce HTTPS" once it becomes available.
5. At your domain registrar, add these DNS records:
   - Four `A` records for the apex domain `soundsignal.co`: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - One `CNAME` record for `www` pointing to `<your-github-username>.github.io`
6. DNS takes anywhere from a few minutes to a few hours. The HTTPS certificate is issued automatically after that.

To update the site later, replace `index.html` in the repo. Changes go live in about a minute.

## Connect the form

The assessment form validates and traps bots already, but it needs somewhere to send submissions.

1. Sign up at [formspree.io](https://formspree.io) with info@soundsignal.co. The free plan covers 50 submissions a month.
2. Create a form and copy its endpoint, which looks like `https://formspree.io/f/abcdwxyz`.
3. Open `index.html` and find this line near the bottom:
   ```js
   const FORM_ENDPOINT = "";
   ```
4. Paste the endpoint between the quotes and save:
   ```js
   const FORM_ENDPOINT = "https://formspree.io/f/abcdwxyz";
   ```
5. Submit the form once yourself to confirm the email arrives.

Until that endpoint is set, the form tells visitors it is not connected yet rather than failing silently.

### Spam protection

Three layers are already in place:

- A hidden honeypot field named `_gotcha`. Bots fill it, people never see it. Formspree also drops submissions that fill it.
- A three second minimum before a submission is accepted, which stops instant bot posts.
- Required name, work email and brand, so junk submissions take effort.

If spam still gets through, turn on reCAPTCHA in the Formspree dashboard. No code change needed.

## Notes

- The page is a single file on purpose. Open it in any browser to preview before you push.
- Photos are the biggest remaining gap. Replace the two LinkedIn headshots in the founders section when you have real ones.
- The Gibbon case study card is a placeholder until the copy is ready.
