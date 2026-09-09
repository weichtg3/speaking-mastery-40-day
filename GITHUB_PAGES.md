# GitHub Pages Deployment

This repository includes a zero-build static site and GitHub Actions deployment.

## One-time setup

1. Create a GitHub repository and push this project to the `main` branch.
2. In GitHub, open **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to **GitHub Actions**.
4. Push to `main`, or use **Actions → Deploy Speaking Mastery to GitHub Pages → Run workflow**.
5. After the workflow finishes, the public URL appears in the deployment summary and in **Settings → Pages**.

Typical URL:

```text
https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/
```

## Local preview

The site fetches Markdown content, so preview it through a local web server:

```bash
python3 -m http.server 8000 --directory site
```

Then open:

```text
http://localhost:8000
```

## Repository layout

```text
.
├── .github/
│   └── workflows/
│       └── deploy-pages.yml
├── site/
│   ├── index.html
│   ├── .nojekyll
│   └── content/
│       ├── PROGRAM.md
│       ├── RESOURCES.md
│       ├── SHARING.md
│       └── TRACKER.md
├── PROGRAM.md
├── RESOURCES.md
├── SHARING.md
├── TRACKER.md
├── GITHUB_PAGES.md
└── README.md
```

## Why this implementation

The deployment is intentionally dependency-free: no Node, npm, Jekyll, Docusaurus, or build step is required. GitHub Actions publishes the `site/` directory directly. The browser uses `marked` to render the course Markdown into the styled site.
