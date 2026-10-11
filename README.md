# Power BI Theme Studio

A single-page tool that builds a Power BI theme (.json), a text-free background (.png) and an optional landing page background (.png), at the canvas size you pick (16:9, 4:3, Letter, Full HD, Tooltip or custom px). It is plain HTML, CSS and JavaScript, so it runs on GitHub Pages with no build step.

Files: `index.html` (the app), `config.js` (your settings), `.nojekyll` (tells GitHub Pages to serve the files as they are).

## 1. Put it on GitHub Pages (free)

1. On github.com click **New repository**. Name it, for example, `powerbi-theme-studio`. Keep it **Public** (Pages on private repos needs a paid plan).
2. Click **uploading an existing file**, drag in `index.html`, `config.js`, `.nojekyll` and `README.md`, then **Commit changes**.
   Or from a terminal:
   ```
   git init
   git add .
   git commit -m "Power BI Theme Studio"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/powerbi-theme-studio.git
   git push -u origin main
   ```
3. In the repo go to **Settings > Pages**. Under **Build and deployment** choose **Deploy from a branch**, branch `main`, folder `/ (root)`, then **Save**.
4. After a minute your site is live at `https://YOUR-USERNAME.github.io/powerbi-theme-studio/`.

Never share a GitHub password or access token with anyone, including chat assistants.

## 2. Free downloads, then login (currently OFF)

Login is switched off right now (`gate: false` in `config.js`), so every download is free and no login appears. To turn it on later, set `gate: true` and fill in the Firebase details below.

`config.js` controls this:

- `gate: true` turns the limit on. `false` makes everything free and skips login.
- `freeDesigns: 3` is how many different designs a visitor can download before they must log in. Downloading the theme, background and landing files of the same design counts as one.

Login uses Firebase Authentication (free Spark plan):

1. Go to console.firebase.google.com and **Add project**.
2. **Build > Authentication > Get started**. Under **Sign-in method** enable **Google** and **Email/Password**.
3. **Authentication > Settings > Authorized domains > Add domain**: `YOUR-USERNAME.github.io`.
4. **Project settings > Your apps > Web (</>)**. Register an app and copy `apiKey`, `authDomain`, `projectId` and `appId` into `config.js`. These values are meant to be public.
5. Commit the change. After login, downloads are unlimited.

Until Firebase is filled in, visitors who hit the limit see "Login is not set up on this site yet".

## Important limits

- The free-download counter is stored in the visitor's browser. Clearing site data or using a private window resets it, and anyone who edits the JavaScript can skip it. Treat it as a friendly gate, not security.
- Because the files are created in the browser, real enforcement needs a small server (for example a Firebase Cloud Function or Cloudflare Worker) that checks the login and builds the files.
- The login code has not been tested against your Firebase project. Test sign-in on the live site before sharing the link.

## Credits

KPI icons are from Feather (MIT licence). Fonts in the preview use your device's installed fonts.
