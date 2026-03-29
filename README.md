# Clark Bai — Portfolio

Personal portfolio website for Clark Bai, computer science graduate specialising in bioinformatics and machine learning.

Built with [Astro](https://astro.build), TypeScript, and plain CSS. Deployed to Netlify.

---

## Local development

**Requirements:** Node 22+

```sh
npm install
npm run dev
```

The dev server starts at <http://localhost:4321>.

| Command             | Action                                  |
| ------------------- | --------------------------------------- |
| `npm run dev`       | Start local dev server (port 4321)      |
| `npm run build`     | Build production site to `./dist/`      |
| `npm run preview`   | Preview the production build locally    |

---

## Docker

### Dev server (hot-reload)

```sh
docker build --target dev -t clark-portfolio:dev .
docker run -p 4321:4321 -v "$(pwd)/src:/app/src" clark-portfolio:dev
```

Open <http://localhost:4321>. Changes to `src/` are reflected live via the volume mount.

### Production build (nginx)

```sh
docker build --target production -t clark-portfolio:prod .
docker run -p 8080:80 clark-portfolio:prod
```

Open <http://localhost:8080>.

---

## Project structure

```text
clark-portfolio/
├── public/             # Static assets (cv.pdf, favicon, og-image)
├── src/
│   ├── components/     # Astro components (Nav, Footer, ProjectCard)
│   ├── content/
│   │   ├── blog/       # One .md file per blog post
│   │   └── projects/   # One .md file per project
│   ├── layouts/        # Base.astro, BlogPost.astro
│   ├── pages/          # Route files (index, about, projects, blog, contact)
│   └── styles/         # global.css, components.css
├── Dockerfile
├── astro.config.mjs
└── package.json
```

### Adding content

- **New project:** add a Markdown file to `src/content/projects/` — the project grid and tag filters update automatically.
- **New blog post:** add a Markdown file to `src/content/blog/` — no other changes needed.

---

## CI/CD

| Workflow | Trigger | Steps |
| -------- | ------- | ----- |
| `ci.yml` | Every push / PR | Lint → build → Lighthouse → link check |
| `cd.yml` | Merge to `main` | Build → deploy to Netlify |

Lighthouse performance budget: ≥ 95 desktop / ≥ 90 mobile. PRs that regress scores below these thresholds will fail CI.

---

## Deployment

Hosted on Vercel.
