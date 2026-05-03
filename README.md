# Mount Pleasant — Cayo District, Belize

A single-page website for the Mount Pleasant industrial development. Static, self-contained, no build step required.

## What's in this folder

```
mount-pleasant-site/
├── index.html       — the entire site (HTML + CSS + JS, all inline)
├── images/          — 8 project images (renderings + existing photos)
└── README.md        — this file
```

The site is fully self-contained — no external dependencies except Google Fonts (loaded over CDN at runtime).

## Deploying to Vercel

You have three paths. The drag-and-drop path is fastest.

### Option 1 — Drag and drop (easiest, no CLI needed)

1. Go to https://vercel.com/new
2. Click **"Browse all templates"** at the bottom (or just look for the import/upload area)
3. Actually — Vercel's main flow is now Git-based. The simplest no-Git path is the CLI below. If you want pure drag-and-drop, use **Netlify** (https://app.netlify.com/drop) — drag this folder, get a live URL in 30 seconds.

### Option 2 — Vercel CLI (recommended, ~2 minutes)

1. Install Node.js if you don't have it: https://nodejs.org
2. Open a terminal in this folder (`mount-pleasant-site/`)
3. Run:
   ```bash
   npx vercel
   ```
4. Follow the prompts:
   - "Set up and deploy?" → **Y**
   - "Which scope?" → choose your Vercel account
   - "Link to existing project?" → **N**
   - "Project name?" → press enter (or type a name like `mount-pleasant`)
   - "Directory?" → press enter (uses the current folder)
   - "Override settings?" → **N**
5. Vercel deploys it and gives you a `*.vercel.app` URL. Share that with your team.

For a production deploy, run `npx vercel --prod` next.

### Option 3 — GitHub + Vercel (best for ongoing updates)

1. Create a new GitHub repo
2. Push this folder's contents to the repo:
   ```bash
   cd mount-pleasant-site
   git init
   git add .
   git commit -m "Initial site"
   git remote add origin https://github.com/YOUR-USERNAME/mount-pleasant-site.git
   git push -u origin main
   ```
3. Go to https://vercel.com/new
4. Click **Import** next to your repo
5. Click **Deploy** (no settings to change — Vercel auto-detects static HTML)
6. Live in under a minute

After this, every push to `main` auto-deploys. Pull request previews work too — great for sharing draft changes with the team.

## Sharing with the team

Once deployed, Vercel gives you:

- **Production URL** — `your-project.vercel.app` (or your custom domain)
- **Preview URLs** — every commit/PR gets its own preview link

Forward either to your team. They just open the link in any browser — no login needed. Vercel sites are public by default.

## Adding a custom domain

In Vercel project settings → **Domains** → add your domain (e.g. `mountpleasantbz.com`). Vercel walks you through DNS setup — usually a single CNAME record at your registrar.

## Things to update before going live

A few placeholders in the current build:

- **Construction Co. link** in the header — currently `#`, swap for the real URL when the construction company site is live (search `class="construction-link"` in `index.html`)
- **Contact email** in the footer — currently `enquiries@mountpleasantbz.com` — replace with your actual address (search `enquiries@mountpleasantbz.com` in `index.html`)
- **Inquiry form** — currently shows a "thank you" state on submit but doesn't actually send. To wire it to email:
  - Easiest: use **Formspree** (https://formspree.io) or **Tally** (https://tally.so) — paste their form action URL into the `<form>` tag and you're done
  - Or wire a Vercel Serverless Function in `/api/inquiry.js` and update the form to POST there

## Updating the site later

Edit `index.html` directly — all CSS and JS are inline so there's nothing to compile. Save the file and:
- **CLI path:** run `npx vercel --prod` again
- **GitHub path:** commit and push — Vercel auto-deploys

## Notes

- All 8 images are bundled locally in `/images/` — the site works completely offline once deployed
- Total folder size: ~36 MB (mostly the high-res renderings)
- Browser support: any modern browser (Chrome, Safari, Firefox, Edge — last 2 years)
- Mobile-responsive at all breakpoints
