# Agent Guidelines for al-folio

A simple, clean, and responsive Jekyll theme for academics.

## Quick Links by Role

- **Are you a coding agent?** → Read [`.github/copilot-instructions.md`](.github/copilot-instructions.md) first (tech stack, build, CI/CD, common pitfalls & solutions)
- **Customizing the site?** → See [`.github/agents/customize.agent.md`](.github/agents/customize.agent.md)
- **Writing documentation?** → See [`.github/agents/docs.agent.md`](.github/agents/docs.agent.md)
- **Need setup/deployment help?** → [INSTALL.md](INSTALL.md)
- **Troubleshooting & FAQ?** → [TROUBLESHOOTING.md](TROUBLESHOOTING.md)
- **Customization & theming?** → [CUSTOMIZE.md](CUSTOMIZE.md)
- **Quick 5-min start?** → [QUICKSTART.md](QUICKSTART.md)

## Essential Commands

### Local Development (Docker)

The recommended approach is using Docker.

```bash
# Initial setup & start dev server
docker compose pull && docker compose up
# Site runs at http://localhost:8080

# Rebuild after changing dependencies or Dockerfile
docker compose up --build

# Stop containers and free port 8080
docker compose down
```

### Pre-Commit Checklist

Before every commit, you **must** run these steps:

1.  **Format Code:**
    ```bash
    # (First time only)
    npm install --save-dev prettier @shopify/prettier-plugin-liquid
    # Format all files
    npx prettier . --write
    ```
2.  **Build Locally & Verify:**

    ```bash
    # Rebuild the site
    docker compose up --build

    # Verify by visiting http://localhost:8080.
    # Check navigation, pages, images, and dark mode.
    ```

## Critical Configuration

When modifying `_config.yml`, these **must be updated together**:

- **Personal site:** `url: https://username.github.io` + `baseurl:` (empty)
- **Project site:** `url: https://username.github.io` + `baseurl: /repo-name/`
- **YAML errors:** Quote strings with special characters: `title: "My: Cool Site"`

## Development Workflow

- **Git & Commits:** For commit message format and Git practices, see [.github/GIT_WORKFLOW.md](.github/GIT_WORKFLOW.md).
- **Code-Specific Instructions:** Consult the relevant instruction file for your code type.

| File Type                                     | Instruction File                                                                                |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Markdown content (`_posts/`, `_pages/`, etc.) | [markdown-content.instructions.md](.github/instructions/markdown-content.instructions.md)       |
| YAML config (`_config.yml`, `_data/`)         | [yaml-configuration.instructions.md](.github/instructions/yaml-configuration.instructions.md)   |
| BibTeX (`_bibliography/`)                     | [bibtex-bibliography.instructions.md](.github/instructions/bibtex-bibliography.instructions.md) |
| Liquid templates (`_includes/`, `_layouts/`)  | [liquid-templates.instructions.md](.github/instructions/liquid-templates.instructions.md)       |
| JavaScript (`_scripts/`)                      | [javascript-scripts.instructions.md](.github/instructions/javascript-scripts.instructions.md)   |

## Common Issues

For troubleshooting, see:

- [Common Pitfalls & Workarounds](.github/copilot-instructions.md#common-pitfalls--workarounds) in copilot-instructions.md
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) for detailed solutions
- [GitHub Issues](https://github.com/alshedivat/al-folio/issues) to search for your specific problem.

## Current Personal-Site Rules

These rules summarize the currently approved customization direction for this repository. Future edits should preserve them unless the user explicitly asks to change them.

### Site Identity

- Language is **English only** for visible site content.
- The site owner is:
  - `name`: `Youqian Gao`
  - `github`: `youqiangao`
  - `email`: `youqiangao@szu.edu.cn`
  - `affiliation`: `Shenzhen University, Shenzhen Audencia Financial Technology Institute`
  - `position`: `Assistant Professor`
- Research interests should stay centered on:
  - statistical learning theory
  - transfer learning
  - representation learning

### Content Scope

- Keep the site minimal and academic.
- `blog` and `projects` are disabled and should stay hidden unless explicitly re-enabled.
- The main visible sections are:
  - `about`
  - `news`
  - `publications`
- The home page should emphasize:
  - short academic bio
  - social/contact icons
  - selected news
  - selected publications

### About Page Layout

- Use a simple two-column intro area: text on the left, profile photo on the right.
- The profile photo should be slightly smaller than the stock al-folio layout.
- The social icons must appear directly below the main bio paragraph, not at the bottom of the page.
- The sentence `Email is the best way to reach me.` should not be shown.
- Do not show the extra profile metadata block under the photo if it duplicates the bio.
- The homepage owner name should remain bold, but the navbar brand name should use normal weight.

### Visual Style

- Keep the overall layout narrower than the default al-folio width.
- Maintain a clean white academic look rather than adding heavy visual decoration.
- Section headings such as `news` and `selected publications` should remain black rather than theme-colored links.
- The preferred accent color is `#9c27d8`.
- Use that accent color selectively for:
  - important inline links that should stand out
  - publication badges such as `JASA`
  - publication title accents when requested
- Do not recolor the entire site indiscriminately; preserve black text for major headings and core body content unless explicitly requested.

### Navigation and Features

- Hide the navbar search button.
- Disable publication-page filtering/search UI.
- Keep unnecessary default pages hidden from navigation, including:
  - `blog`
  - `projects`
  - `cv`
  - `teaching`
  - `repositories`
  - `profiles`
  - `dropdown`

### Publications Rules

- Publications are managed in `_bibliography/papers.bib`.
- The current featured paper is the JASA paper:
  - `Gao, Y. and Dai, B. (2025). Word-level maximum mean discrepancy regularization for word embedding.`
- Prefer showing `HTML` and `CODE` buttons when links exist.
- Do not show the `Bib` button unless explicitly requested.
- Publication titles and venue badges may use the accent color when requested.
- If a venue badge color does not follow the global publication style, check `_data/venues.yml` because venue-specific colors can override default SCSS.

### News Rules

- News items are managed in `_news/`.
- Keep the current two core news items unless the user changes them:
  - `2025-08-04`: JASA paper accepted
  - `2026-04-14`: HKSS-John Aitchison Prize in Statistics
- If a specific paper title is linked inside a news item and the user wants emphasis, it can be styled with the accent color while leaving surrounding text unchanged.

### Local Development

- This repository is currently intended to be previewed locally with Ruby/Jekyll rather than Docker.
- The user may keep the working copy in OneDrive for editing, but local preview/build behavior can be less reliable there depending on permissions and file-watching behavior.
- If local commands are referenced, prefer the user’s shell helpers:
  - `alf` or `alfolio` to start the site
  - `alfstop` to stop the local server

### Git and Push Workflow

- The canonical GitHub repository for deployment is:
  - `origin = https://github.com/youqiangao/youqiangao.github.io.git`
- The original al-folio template repository should not be used as the push target for this personal site.
- Prefer pushing from a plain Terminal session rather than the VS Code Git UI.
- In this repository, VS Code background Git activity can interfere with first-time pushes or remote setup.
- If a push fails from VS Code with errors such as:
  - `RPC failed`
  - `curl 16 Error in the HTTP2 framing layer`
  - `fatal: the remote end hung up unexpectedly`
  then retry from Terminal before assuming the repository is broken.
- The preferred push workflow is:
  1. `git add .`
  2. `git commit -m "message"`
  3. `git push`
- If GitHub push transport is unstable, configure Git to use HTTP/1.1:

```bash
git config --global http.version HTTP/1.1
```

- If needed, additional fallback settings that are known to help are:

```bash
git config --global http.postBuffer 524288000
git config --global core.compression 0
```

- When troubleshooting first push behavior, close VS Code and retry the push from Terminal before taking more invasive recovery steps.

### Deployment Rules

- This site is deployed as a GitHub Pages personal site for:
  - `https://youqiangao.github.io`
- `_config.yml` must stay aligned with personal-site deployment:
  - `url: https://youqiangao.github.io`
  - `baseurl:` must remain empty
- The repository name for deployment is expected to be:
  - `youqiangao.github.io`
- Deployment is triggered automatically by pushing to `main` or `master`.
- The repository uses the existing workflow in [deploy.yml](.github/workflows/deploy.yml) to build the site and publish the generated `_site` output to the `gh-pages` branch.
- GitHub Pages should be configured to serve from:
  - `Deploy from a branch`
  - branch `gh-pages`
  - folder `/ (root)`
- For deployment health, the important workflow signals are:
  - `Deploy site`
  - `pages build and deployment`
- Other workflows such as Prettier, CV rendering, Lighthouse, or auxiliary checks may fail without blocking the main academic homepage from being published.
- After a successful push, allow a short delay for GitHub Pages propagation and then verify:
  - `https://youqiangao.github.io`
