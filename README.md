# Personal Website — Xuancheng Ye

A simple static personal/academic website. No build step, no framework — just HTML, CSS, and vanilla JS.

## Structure

```
index.html              Main page (all sections)
css/style.css           Styling, light/dark theme
js/script.js            Theme toggle, mobile nav, footer year
assets/
  CV_Xuancheng_Ye.pdf     CV (not currently linked anywhere on the page)
  profile.jpg             Circular avatar photo (overlaps the banner)
  dive-banner.jpg         Hero banner photo (scuba diving), cropped to a wide strip
  gallery/
    climbing/             Rock climbing photos
    diving/                Scuba diving photos
```

## Adding photos to the Rock Climbing / Scuba Diving galleries

There's no upload button (this is a static site with no backend), but adding a photo takes two steps:

1. Drop the image file into `assets/gallery/climbing/` or `assets/gallery/diving/`.
2. In `index.html`, find the `<!-- SKILLS -->` section and add one block inside the matching `.photo-grid` div:
   ```html
   <a href="assets/gallery/climbing/your-photo.jpg" target="_blank" rel="noopener">
     <img src="assets/gallery/climbing/your-photo.jpg" alt="Rock climbing" loading="lazy" />
   </a>
   ```
   (For Rock Climbing, also delete the `<p class="gallery-empty">Photos coming soon.</p>` line once you add the first photo.)

Each photo becomes a square thumbnail that opens full-size in a new tab when clicked. No size limit is enforced, but keep individual photos under a few MB so the page loads quickly — resizing to ~1200px on the long edge before adding is plenty for web display.

## Before you publish

- [ ] Double check the CV filename in `assets/` matches the link in `index.html` whenever you update your CV (currently the CV file isn't linked from the page).
- [ ] If you ever want to swap the banner or avatar photo, just replace `assets/dive-banner.jpg` / `assets/profile.jpg` with a new image of the same filename (or update the `src` in `index.html`).

## Deploying to GitHub Pages

1. Create a new GitHub repository (e.g. `personal-website`, or `<your-username>.github.io` if you want it as your main user site).
2. From this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial personal website"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. On GitHub: go to the repo → **Settings → Pages** → under "Build and deployment", set **Source** to "Deploy from a branch", branch `main`, folder `/ (root)` → Save.
4. Your site will be live at:
   - `https://<your-username>.github.io/<repo-name>/` (project repo), or
   - `https://<your-username>.github.io/` (if the repo is named `<your-username>.github.io`)

It can take a minute or two for GitHub Pages to build after the first push.
