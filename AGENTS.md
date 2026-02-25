# AGENTS.md

## Cursor Cloud specific instructions

This repository is a **GitHub profile README** containing a single `README.md` file. There is no application code, build system, or runtime dependencies.

### Available dev tools (globally installed)

| Tool | Command | Purpose |
|------|---------|---------|
| `markdownlint` | `markdownlint README.md` | Lint Markdown syntax and style |
| `markdown-link-check` | `markdown-link-check README.md` | Validate all HTTP links in the README |
| `marked` | Used via Node.js script | Render Markdown to HTML for preview |

### Lint

```sh
markdownlint README.md
```

Known lint warnings (line-length, table-column-style) are expected for this profile README and do not need to be fixed.

### Link validation

```sh
markdown-link-check README.md
```

The `mailto:` link will always report as "dead" (status 400) — this is a false positive since mailto URIs cannot be HTTP-verified.

### Preview

To render and preview the README locally:

```sh
cd /tmp && node -e "
const { marked } = require('marked');
const fs = require('fs');
const md = fs.readFileSync('/workspace/README.md', 'utf8');
fs.writeFileSync('/tmp/readme_preview.html', '<html><body>' + marked.parse(md) + '</body></html>');
"
```

Then open `/tmp/readme_preview.html` in the browser.
