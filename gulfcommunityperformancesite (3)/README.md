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

## Chatbot (n8n) — live

The chat widget (bottom-right bubble) is wired up and live. It's built and running directly as the "GCP Website Chatbot" workflow on your n8n instance (nebulawebonline.app.n8n.cloud) — there's no file to import; the workflow itself is the source of truth, so this folder doesn't ship a copy of it.

- Webhook: `https://nebulawebonline.app.n8n.cloud/webhook/gcp-chat` — already set as `N8N_WEBHOOK_URL` in `index.html`.
- Model: Claude (Anthropic), using the Anthropic credential already in your n8n account.
- Leads: interested visitors who share a name + email get logged automatically to a Google Sheet named **"GCP Chatbot Leads"** (tab "Leads") in your Google Drive — a header row appears after the first captured lead.
- Both the FAQ path and the lead-capture path were test-executed directly against the live workflow before shipping this — confirmed working end to end.

What the bot does: answers questions about GCP's mission, programs, service area, the $50/year membership, and the three partner race discounts (Trail Hog Half Marathon, Santa Run 5K, Kraken); always points visitors to the real RunSignup link to actually join; and gently asks for a name + email from interested visitors who haven't signed up yet, logging that as a lead in the sheet above.

To make changes later (edit the system prompt, swap the leads destination, adjust the model), open the workflow directly at nebulawebonline.app.n8n.cloud — no need to re-import anything.

## Other notes / placeholders to fill in before launch

- Footer currently has `[SOCIAL LINKS]` and `[CONTACT EMAIL]` placeholders — swap in real links once the owner provides them.
- "Join" buttons link out to `https://runsignup.com/MemberOrg/GCP` for the actual registration/payment step.
