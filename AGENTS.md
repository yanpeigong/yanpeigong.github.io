# Repository Guidelines

## Project Structure & Module Organization

This repository is a Jekyll 4 academic homepage. Site-wide settings and author metadata live in `_config.yml`; the homepage content is in `_pages/about.md`. Page composition belongs in `_layouts/` and reusable Liquid/HTML fragments in `_includes/`. Navigation data is stored in `_data/navigation.yml`. Styles are split between the `assets/css/main.scss` entry point and component partials under `_sass/`; JavaScript, fonts, and other static files live in `assets/`. Profile images and favicons are in `images/`. The `google_scholar_crawler/` Python utility publishes citation JSON through its GitHub Actions workflow. Treat `_site/` and `.jekyll-cache/` as generated output.

## Build, Test, and Development Commands

- `bundle install` installs the Ruby and Jekyll dependencies from `Gemfile`.
- `bundle exec jekyll serve` starts the local site at `http://127.0.0.1:4000`; `bash run_server.sh` is the provided shortcut.
- `bundle exec jekyll build` renders the production site into `_site/` and is the primary validation command.
- `pip install -r google_scholar_crawler/requirements.txt` installs crawler dependencies.
- From `google_scholar_crawler/`, run `python main.py` with `GOOGLE_SCHOLAR_ID` set to regenerate citation data.

Restart Jekyll after changing `_config.yml`; configuration changes are not reloaded automatically.

## Coding Style & Naming Conventions

Preserve existing formatting: two-space indentation for YAML, Liquid, HTML, and SCSS; four spaces for Python. Use lowercase Jekyll filenames and leading underscores for theme partials (for example, `_sass/_navigation.scss`). Keep content section anchors aligned with `_data/navigation.yml`. Do not hand-edit `assets/js/main.min.js`, bundled fonts, cache files, or generated `_site/` output.

## Testing Guidelines

There is no automated test suite or coverage target. Before submitting changes, run `bundle exec jekyll build` and inspect the local site at desktop and mobile widths. Verify internal hash links, images, author metadata, and citation placeholders. For crawler changes, run the script with a valid test Scholar ID and confirm both JSON files are produced under `google_scholar_crawler/results/`.

## Commit & Pull Request Guidelines

Recent commits use brief, imperative summaries such as `Fix GitHub Pages deployment with Jekyll 4`. Prefer that style and describe one logical change per commit; avoid vague messages such as `update`. Pull requests should include a concise summary, validation commands, and linked issues when applicable. Add before/after screenshots for visible layout or content changes, and call out workflow or configuration changes explicitly.

## Security & Configuration

Never commit API keys, analytics secrets, or Scholar credentials. Store `GOOGLE_SCHOLAR_ID` in GitHub Actions secrets. Keep `_config.yml`'s `repository` value accurate because citation URLs depend on it.
