# Gulf Community Performance — Website

Static one-page site. No build step, no framework, no dependencies beyond a Google Fonts CDN link.

```
index.html
assets/
  logo.png
  hero.jpg
  event.jpg
```

## Deploying via GitHub + Cloudflare Pages

1. Create a new GitHub repo and push this folder's contents to it (`index.html` and `assets/` at the repo root).
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Connect to Git**, pick the repo.
3. Build settings: **Framework preset: None**, **Build command: (leave blank)**, **Build output directory: `/`**.
4. Deploy. Cloudflare gives you a `*.pages.dev` URL immediately; add a custom domain under the project's **Custom domains** tab when ready.

Every push to the connected branch auto-redeploys.

## Notes / placeholders to fill in before launch

- Footer currently has `[SOCIAL LINKS]` and `[CONTACT EMAIL]` placeholders — swap in real links once the owner provides them.
- "Join" buttons link out to `https://runsignup.com/MemberOrg/GCP` for the actual registration/payment step.
- The floating chat bubble in the bottom-right corner is a visual placeholder for the n8n-powered chatbot; it isn't wired to anything yet.
