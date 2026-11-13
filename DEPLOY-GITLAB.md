# Putting the TFP Vantage page on GitLab

Project: **https://gitlab.com/gitlab.tfp/sbone**

The page publishes itself with **GitLab Pages**: `.gitlab-ci.yml` copies the site into `public/` on every push to
the default branch, and GitLab serves it. Nothing to install.

## 1. Get the files into the project

Choose **A** (simplest, keeps the history) or **B** (no git needed).

### A. Push from the PC that has the files

The project must be **empty** (create it with "Initialize repository with a README" **unticked**). If it already has
a README, see "If the push is rejected" below.

```
cd ~/tfp-vantage-site
git remote add gitlab https://gitlab.com/gitlab.tfp/sbone.git
git push -u gitlab main
```

When git asks to sign in:
- **Username:** your GitLab username
- **Password:** a **personal access token**, not your GitLab password. Make one at GitLab → your avatar →
  **Edit profile → Access tokens → Add new token**, tick **write_repository**, set an expiry date, and copy it.

**If the push is rejected** because the project already has a README: run
`git pull gitlab main --allow-unrelated-histories --no-edit`, then `git push -u gitlab main`.

### B. Upload in the browser

1. Open the project → **Edit → Web IDE**.
2. Drag in **all** of these from the `tfp-vantage-site` folder, keeping the folders as they are:
   `index.html`, `.gitlab-ci.yml`, `README.md`, `DEPLOY-GITLAB.md`, and the whole `assets` folder.
   (`.gitlab-ci.yml` starts with a dot: if you can't see it, turn on "show hidden files" in your file browser.)
3. Click **Commit**, write a short message, and commit to the **main** branch.

## 2. Check that it published

1. **Build → Pipelines**: the `pages` job should turn green within a minute or two.
   - If it waits with "no runners": GitLab.com asks new accounts to verify themselves (phone or card) before running
     jobs. Follow the link it shows. The job uses a few seconds of the free monthly minutes.
2. **Deploy → Pages**: the page's address is shown there. Open it.

## 3. Settings to check

- **Address:** the group name `gitlab.tfp` contains a dot, which breaks HTTPS on the plain Pages address
  (`gitlab.tfp.gitlab.io`). Keep **"Use unique domain"** ticked in **Deploy → Pages** (it is on by default): the
  address is then like `https://sbone-<letters>.gitlab.io`, with working HTTPS.
- **Who can see it:** if the project is **private**, go to **Settings → General → Visibility, project features,
  permissions → Pages** and choose **Everyone**, so customers can open the page while the code stays private.
- **Your own domain (optional, later):** **Deploy → Pages → New domain**, e.g. `vantage.tfp.com.my`; GitLab shows
  the DNS record to add and gets the HTTPS certificate itself.

## 4. After it is live

Send the new address to whoever maintains TFP Vantage, so that:
- the TFP Vantage demo's back link and the "who may show the demo" setting point at the new page;
- the address at the end of the video (it says `ezzzy01.github.io/tfp-vantage`) is updated and the video re-made;
- the old copy on GitHub (`ezzzy01.github.io/tfp-vantage`) can be removed, or kept, as you prefer.
