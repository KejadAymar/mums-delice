# Mum's Delice site: deploy on Coolify

Static site (HTML + images) served by nginx. No build step.

## Deploy
1. Push this folder to a Git repo (GitHub/GitLab).
2. Coolify: New Resource > Public/Private Repository > pick the repo and branch.
3. Build Pack: **Dockerfile**. Port: **80**.
4. Domains: set your domain (https://yourdomain.ca). Coolify issues the HTTPS certificate.
5. Deploy. Check https://yourdomain.ca/healthz returns "ok".

## Afterwards
- The QR code on the label currently points to the claude.ai address. Once the domain is live, send it to Claude to regenerate the print file with the new QR.
- GSAP and Lenis load from public CDNs (cdnjs, jsDelivr) and the fonts from Google Fonts. To self-host them, download the files into public/vendor and update the three script tags and the font link in public/index.html.

## GitHub Pages (free hosting)
1. Create a GitHub repo and push this folder (including the hidden `.github` folder).
2. Repo > Settings > Pages > Source: **GitHub Actions**.
3. Push to `main` (or run the "Deploy to GitHub Pages" workflow). The site goes live at https://USERNAME.github.io/REPO/ after about a minute.
4. Custom domain: Settings > Pages > Custom domain, then add the DNS records GitHub shows.
Note: on a project page (USERNAME.github.io/REPO/) the site is served under /REPO/, so the root-relative paths /img/... in the sharing tags will not resolve. Use a custom domain or a repo named USERNAME.github.io for a clean root.
