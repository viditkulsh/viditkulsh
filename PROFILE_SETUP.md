# 🪄 README — Setup & Suggestions

This repo's `README.md` is an animated, gimmick-rich landing page that mirrors `cv.pdf`.
It lives **here in the `viditkulsh/Vidit_Kulsh_CV` repo** (your chosen placement), so all
generated-image URLs and Actions are scoped to this repo.

> 💡 Want it on your **profile page** (`github.com/viditkulsh`) too? Create a public repo
> named exactly `viditkulsh`, copy `README.md` + `.github/` into it, and find/replace the
> repo name `Vidit_Kulsh_CV` → `viditkulsh` in the snake/metrics image URLs. Both can coexist.

---

## 1. Secrets to add (one time)

Repo → **Settings → Secrets and variables → Actions → New repository secret**:

| Secret | Used by | How to get it |
|---|---|---|
| `METRICS_TOKEN` | `metrics.yml` | [Classic PAT](https://github.com/settings/tokens) with scopes `repo`, `read:user`, `read:org` |
| `WAKATIME_API_KEY` | `waka.yml` | [wakatime.com/settings/account](https://wakatime.com/settings/account) — then install the WakaTime editor plugin so time is tracked |
| `GH_TOKEN` | `waka.yml` | Reuse the **same PAT value** as `METRICS_TOKEN` (needs `repo` scope to commit the README) |

The snake and 3D workflows need **no secrets** — they use the built-in `GITHUB_TOKEN`.

---

## 2. Run the Actions once

Push, then go to the **Actions** tab, enable workflows, and hit **"Run workflow"** on each:

| Workflow | Produces | README points at |
|---|---|---|
| `🐍 snake.yml` | `output` branch → `snake.svg`, `snake-dark.svg`, `snake.gif` | `raw.githubusercontent.com/.../output/snake.svg` |
| `🧊 3d-contrib.yml` | `profile-3d-contrib/*.svg` on `main` | `./profile-3d-contrib/profile-night-rainbow.svg` |
| `📊 metrics.yml` | `metrics/github-metrics.svg` + `…-iso.svg` | `./metrics/github-metrics.svg` |
| `⏱️ waka.yml` | edits README between `START_SECTION:waka` markers | inline section |

> Images **404 until their workflow runs once** — that's expected on a fresh push.

### 3D calendar variants
The 3D action emits several SVGs. The README uses `profile-night-rainbow.svg`; swap to
`profile-green-animate.svg` · `profile-season-animate.svg` · `profile-gitblock.svg` · `profile-night-view.svg`.

---

## 3. Already live (zero setup, render on push)

- ✅ Animated **waving header** + footer (theme-adaptive light/dark via `<picture>`)
- ✅ **Typing** subtitle · **dev-quote** banner
- ✅ **GitHub stats / top-langs / streak / trophies** cards
- ✅ **Animated activity graph** (contribution line chart)
- ✅ **Mermaid** architecture diagram (native render)
- ✅ **Profile-views** counter · collapsible **`<details>`** experience

---

## 4. Still-optional gimmicks (say the word)

| Gimmick | Shows | Needs |
|---|---|---|
| **Spotify now-playing** | Live "currently listening" card | Spotify OAuth (novatorem on Vercel) |
| **Blog auto-post** | Latest posts from an RSS/dev.to/Medium feed | `blog-post-workflow` Action + feed URL |
| **Holopin badges** | Collectible open-source achievement badges | Holopin account |

---

## 5. Maintenance notes

- **Stats look empty?** `include_all_commits` + `count_private` are on; also enable
  *Settings → Profile → "Include private contributions on my profile."*
- **Restyle every card at once** → change `theme=tokyonight` in the URLs
  (`radical`, `dracula`, `catppuccin_mocha`, …).
- **Metrics card too tall?** Trim `base:` / drop a plugin in `metrics.yml`.
- Snake/3D/metrics **lag one run** — they refresh on cron (snake 12h, others daily)
  or whenever you click "Run workflow".
- This README replaced nothing destructive — `cv.tex` and `src/` are untouched.
