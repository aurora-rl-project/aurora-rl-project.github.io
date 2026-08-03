# AuroraRL blog

A self-contained static site for the AuroraRL announcement post — *"RL over Commodity
Networks: Overcoming the Bandwidth Barrier with Lossless Sparse Deltas."*

No build step, no framework, no external fonts or JS libraries. All figures are
hand-authored inline SVG that recolors automatically in light/dark mode.

```
blog/
├── index.html        # the post (figures inline)
├── assets/style.css  # theme + figure color system
└── README.md         # this file
```

## Preview locally

```bash
# from the repo root
uv run python -m http.server 8000 --directory blog
# open http://localhost:8000
```

(Any static server works, e.g. `npx serve blog` or VS Code Live Server.)

## Publish to GitHub Pages (aurora-rl-project.github.io)

A GitHub **user/org Pages** site is served from the root of a repo named
`<org>.github.io`. To publish under the `aurora-rl-project` org:

```bash
# 1. create the org Pages repo (one time)
gh repo create aurora-rl-project/aurora-rl-project.github.io --public

# 2. push the contents of this blog/ folder to its default branch root
cd blog
git init -b main
git add .
git commit -m "feat: AuroraRL announcement post"
git remote add origin git@github.com:aurora-rl-project/aurora-rl-project.github.io.git
git push -u origin main
```

GitHub Pages builds automatically; the site goes live at
**https://aurora-rl-project.github.io/** within a minute or two.

> Project-page alternative: if you'd rather host it under the code repo
> (`aurora-rl-project/aurora-rl`), drop these files in a `docs/` folder and
> enable Pages → *Deploy from branch* → `main` / `/docs`. The URL becomes
> `https://aurora-rl-project.github.io/aurora-rl/`.

## Editing

- Prose and figures live in `index.html`.
- Colors, typography, and the figure palette live in `assets/style.css`
  (`--c-delta`, `--c-full`, `--c-ms`, `--c-ideal`, …) — change them once and every
  SVG follows.
- A custom domain: add a `CNAME` file containing the domain and configure DNS.
