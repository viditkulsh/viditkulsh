# 🪄 Profile README — How it works

The animated profile README is **live at `github.com/viditkulsh/viditkulsh`** (public profile repo).
It renders on the GitHub profile page. The CV LaTeX source stays in the private `Vidit_Kulsh_CV` repo.

> Everything below runs with **zero secrets** — the workflows use the built-in `GITHUB_TOKEN`.

---

## Workflows (in `.github/workflows/`)

| Workflow | Produces | README points at | Trigger |
|---|---|---|---|
| `🐍 snake.yml` | `snake.svg`, `snake-dark.svg`, `snake.gif` on the `output` branch | `raw.githubusercontent.com/.../output/snake.svg` | push + every 12h |
| `🧊 3d-contrib.yml` | `profile-3d-contrib/*.svg` on `main` | `./profile-3d-contrib/profile-night-rainbow.svg` | push + daily |
| `📊 metrics.yml` | `metrics/github-metrics.svg` on `main` (lowlighter/metrics, built-in token) | `./metrics/github-metrics.svg` | push + daily |

Run them once manually from the **Actions** tab (**Run workflow**) if you ever want an immediate refresh;
otherwise they self-update on their schedules. Images lag one run after a fresh push (they 404 for ~1–2 min, then self-heal).

### 3D calendar variants
The 3D action emits several SVGs. The README uses `profile-night-rainbow.svg`; swap to
`profile-green-animate.svg` · `profile-season-animate.svg` · `profile-gitblock.svg` · `profile-night-view.svg`.

---

## Live elements that need no workflow (external SVG services)

- Animated **waving header** + footer (theme-adaptive light/dark via `<picture>`)
- **Typing** subtitle · **dev-quote** banner
- **Streak** stats card · **animated activity graph**
- **Profile-views** counter · collapsible **`<details>`** experience

> ⚠️ The `github-readme-stats` "stats" card and the `github-profile-trophy` card were **removed** —
> those shared-instance services were rate-limited ("Something went wrong") / over quota (HTTP 402).
> The self-generated **metrics card** (committed SVG, immune to runtime rate limits) covers that ground reliably.

---

## Notes

- **Stats undercounting?** Enable *GitHub → Settings → Profile → "Include private contributions on my profile."*
- **Restyle every external card at once** → change `theme=tokyonight` / `theme=tokyo-night` in the URLs.
- **Metrics card too tall / want different sections?** Edit `base:` and the `plugin_*` options in `metrics.yml`.
- **Confidentiality:** the README is deliberately free of employer name, platform domain, internal
  architecture, and product-specific standards. Keep it that way when editing.
