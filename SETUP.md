# 🚀 Setup Guide — The Ultimate GitHub Profile

Your new profile has **5 dynamic features** powered by GitHub Actions. Here's how to set each one up.

## 📁 File Structure

Copy everything into your `EmperorAkashi20/EmperorAkashi20` repo:

```
EmperorAkashi20/
├── .github/
│   └── workflows/
│       ├── snake.yml                    ← 🐍 Snake animation
│       ├── 3d-contrib.yml               ← 🏙️ 3D contribution skyline
│       ├── wakatime.yml                 ← ⏱️ WakaTime coding stats
│       └── profile-summary-cards.yml    ← 📊 Stats cards (backup)
├── assets/
│   └── header.svg                       ← 🎨 Custom animated banner
└── README.md                            ← The profile itself
```

---

## ⚠️ IMPORTANT: Enable Workflow Permissions First!

Before running ANY workflow:

1. Go to your repo → **Settings** → **Actions** → **General**
2. Scroll to **Workflow permissions**
3. Select **"Read and write permissions"**
4. Save

---

## 🐍 1. Snake Animation (2 min)

This turns your contribution graph into an animated snake game.

1. Push the `snake.yml` workflow file
2. Go to **Actions** → **Generate Snake Animation** → **Run workflow**
3. Wait ~30 seconds — it creates an `output` branch with the SVG
4. Done! The README already points to the correct URL

**Auto-updates:** Every 12 hours

---

## 🏙️ 2. 3D Contribution Skyline (2 min)

An isometric 3D bar chart of your contributions — looks like a city skyline.

1. Push the `3d-contrib.yml` workflow file
2. Go to **Actions** → **GitHub Profile 3D Contrib** → **Run workflow**
3. Wait ~30 seconds — it commits a `profile-3d-contrib/` folder with SVGs
4. Done! The README already references these files

**Auto-updates:** Once daily

**Want private repo contributions?** Create a [Personal Access Token](https://github.com/settings/tokens) with `repo` scope, add it as a secret named `MY_PERSONAL_ACCESS_TOKEN`, and replace `GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}` with `GITHUB_TOKEN: ${{ secrets.MY_PERSONAL_ACCESS_TOKEN }}` in the workflow.

---

## ⏱️ 3. WakaTime Coding Stats (5 min)

Shows your real coding hours by language, editor, and OS. This is the killer feature that sets your profile apart.

### One-time setup:

1. Create a [WakaTime account](https://wakatime.com)
2. Install the [WakaTime plugin](https://wakatime.com/plugins) in your editor (VS Code, IntelliJ, etc.)
3. Get your API key from [wakatime.com/api-key](https://wakatime.com/api-key)
4. In your repo → **Settings** → **Secrets and variables** → **Actions** → **New repository secret**:
   - Name: `WAKATIME_API_KEY`
   - Value: your WakaTime API key
5. Create another secret:
   - Name: `GH_TOKEN`
   - Value: A [Personal Access Token](https://github.com/settings/tokens) with `repo` scope
6. Push the `wakatime.yml` workflow file
7. Go to **Actions** → **WakaTime Readme** → **Run workflow**

**Note:** WakaTime needs a few days of data before it shows meaningful stats. The section between `<!--START_SECTION:waka-->` and `<!--END_SECTION:waka-->` in your README auto-updates daily.

**Auto-updates:** Once daily at midnight UTC

---

## 📊 4. Profile Summary Cards (optional backup)

This generates stats, language charts, and productive time cards.
The README currently uses the live API (`github-profile-summary-cards.vercel.app`).
If it ever goes down, switch to the GitHub Action version.

1. Push the `profile-summary-cards.yml` workflow file
2. Go to **Actions** → **GitHub Profile Summary Cards** → **Run workflow**
3. Replace the API URLs in README with the generated SVG paths:

```markdown
![Stats](https://raw.githubusercontent.com/EmperorAkashi20/EmperorAkashi20/main/profile-summary-card-output/github_dark/3-stats.svg)
```

---

## 🎨 5. Custom SVG Banner

Already included in `assets/header.svg`. No setup needed — it renders directly from the repo.

Features:

- Animated code rain background
- Floating particles
- Terminal-style subtitle with blinking cursor
- Pulsing status indicators (BUILDING • SHIPPING • SCALING)

To customize, edit `assets/header.svg`:

- Change name on line with `RISHABH SETHIA`
- Change subtitle text on the `~/dev $` line
- Change colors by replacing `#58a6ff` (blue) with your preferred hex color

---

## 🔄 Recommended Run Order

Run workflows in this order after pushing all files:

1. **Generate Snake Animation** (creates `output` branch)
2. **GitHub Profile 3D Contrib** (commits `profile-3d-contrib/` folder)
3. **WakaTime Readme** (updates README in-place)
4. **GitHub Profile Summary Cards** (optional, commits `profile-summary-card-output/`)

After the first manual run, everything auto-updates on schedule.

---

## 💡 Tips

- **Private contributions:** Enable "Include private contributions on my profile" in GitHub Settings → Public profile → Contributions & Activity
- **WakaTime takes time:** Give it 3-7 days of coding before the stats look meaningful
- **If stats cards break:** Switch from the API URLs to the GitHub Action-generated SVGs (see step 4 above)
- **Timezone:** The productive-time card uses `utcOffset=5.5` (IST). Change this if you're elsewhere
