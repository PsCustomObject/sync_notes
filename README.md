# 🛠️ sync_notes.py – Markdown Auto-Sync for Just the Docs

![Syncs Markdown to Just the Docs](https://img.shields.io/badge/Markdown%20Sync-Just%20the%20Docs-blueviolet?style=flat-square&logo=markdown)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)
![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB?style=flat-square&logo=python)

This script automates the process of preparing Markdown notes for use with [Just the Docs](https://just-the-docs.github.io/just-the-docs/), the static site generator used by GitHub Pages.

It converts clean `.md` files from your working directories into fully formatted, YAML-front-matter–ready documents inside the `docs/` folder. It also builds a sidebar-compatible index and generates correct navigation metadata.

I wrote this small script out of personal need to support my site [Terraforming My Career](https://pscustomobject.github.io/terraforming-my-career).
It’s tailored for a specific workflow, so consider it more of an exercise than a general-purpose tool — but if you find any part of it useful, feel free to fork and adapt it to your needs!

---

## ✅ Features

- Automatically wraps each Markdown file with required [Jekyll front matter](https://jekyllrb.com/docs/front-matter/)
- Parses filenames like `chapter-01-terraform.md` into titles like `Chapter 1 – Terraform`
- Injects `title`, `parent`, and `nav_order` values for sidebar hierarchy
- Regenerates each `index.md` file with an up-to-date table of contents
- Skips unchanged files using a `.sync_hashes.json` cache
- Handles invisible BOM characters from editors like Zed or VS Code
- Supports `--dry-run` mode to preview changes
- Supports `--clean` mode to force a full rebuild

---

## 📁 Expected Folder Structure

```bash
    terraforming-my-career/
    ├── reading_notes/
    │   ├── chapter-01-intro.md
    │   ├── chapter-02-first-code.md
    │   └── ...
    ├── terraform/
    │   └── 01-getting-started.md
    ├── sync_notes.py
    ├── .sync_hashes.json
    └── docs/
        ├── reading_notes/
        │   ├── index.md
        │   └── chapter-01-intro.md
        └── ...
```

---

## 🚀 Usage

```bash
# Normal mode (sync only changed files)
python3 sync_notes.py

# Force full rebuild
python3 sync_notes.py --clean

# Preview changes without writing files
python3 sync_notes.py --dry-run

# Combine both
python3 sync_notes.py --clean --dry-run
