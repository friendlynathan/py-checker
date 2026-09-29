# PyGenuine — Python Package Authenticator & Library Directory

**Protecting Vibe Coders from AI Package Hallucinations & Slopsquatting.**

A single-page web app that verifies whether a Python package name actually exists on PyPI before you `pip install` it — catching the fabricated package names that AI coding assistants confidently hallucinate, and the typosquatted "slopsquatting" packages that attackers register to exploit them.

## Features

- **PyPI REST verification** — `checkPyPIPackage()` queries the live PyPI JSON API for every package name and reports real existence, latest version, and release date.
- **Stdlib detection** — flags packages that ship with Python itself (e.g. `os`, `json`, `requests`-lookalikes) so you don't search PyPI for them.
- **Import-to-PyPI mapping** — `parsePythonImportsAndReqs()` parses pasted Python code or `requirements.txt` content and maps import names to their correct distribution names (e.g. `Pillow` ↔ `PIL`).
- **Clipboard + file input** — drag-and-drop or paste code/requirements directly into the scanner; results stream in as each package is checked.
- **Risk scoring & slopsquatting guide** — `calculateRiskScore()` grades each result, with a risk-level guide for common failure patterns.
- **Clean requirements export** — one-click copy/download of verified-good `requirements.txt` output.
- **80+ library directory** — curated, filterable directory of popular Python packages with categories and search.
- **Compatibility matrix** — filterable table of library/platform support.
- **Dark mode** — Tailwind-based dark UI, no build step required.

## Run locally

No build step — it's a static page:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000>.

(Opening `index.html` directly in a browser also works.)

## Deploy to GitHub Pages

1. Push this repository to GitHub (see below).
2. In your repo on GitHub: **Settings → Pages → Build and deployment**.
3. Under **Source**, select **Deploy from a branch**, pick branch `main`, folder `/ (root)`, and **Save**.
4. Your live demo will be available at:

   ```
   https://<your-username>.github.io/<repo-name>/
   ```

## Project structure

```
.
├── index.html    # Entire app: markup, Tailwind config, styles, and JS
├── README.md
└── .gitignore
```

## Tech stack

- Vanilla HTML/CSS/JS (no framework, no bundler)
- Tailwind CSS (CDN) with custom brand palette
- PyPI JSON API (`https://pypi.org/pypi/{name}/json`)
- FontAwesome + Google Fonts (Inter, JetBrains Mono)
