# Publish this site on GitHub (step by step)

This folder is the whole website. There is nothing to build or install. When you finish, it will be live at:

`https://<your-github-username>.github.io/<repository-name>/`

Suggested repository name: `wlsa-innovation-universe`

---

## Before you publish: 5-minute checklist

The site will be **public** (anyone with the link can open it, and search engines may find it).

- [ ] **Staff names.** The site shows names and roles (Slava Matvejevs, Taylor, Jose Dominguez, Jing Wu, Jackey & Jimmy, Johnson, Sofian). Confirm everyone is happy to be listed publicly.
- [ ] **School logo.** `wlsa-logo.png` is the school crest. Confirm the school allows it on a public GitHub page.
- [ ] **Placeholder text.** Many planets still say "Details to be confirmed" or "Part of …". Public visitors will see that. Fill them in first, or accept it for now. All wording is in `universe-data.js`.
- [ ] **No private data.** The site contains no student data, passwords, keys or internal links. (Checked: it loads nothing from the internet and uses no logins.)
- [ ] **Which GitHub account.** A school account is easier to hand over later than a personal one. [confirm with your school's policy]

**Reaching it from mainland China.** `github.io` addresses can be slow or unreachable from some networks in mainland China. Test the live link from the school network and from a phone on mobile data before sharing it widely. [confirm] If it does not load reliably, the same folder can be hosted on any ordinary web server (it is just static files).

---

## Route A: upload in the browser (no software needed)

1. Sign in at https://github.com (create a free account if you need one).
2. Click **+** (top right) → **New repository**.
3. **Repository name:** `wlsa-innovation-universe`. Choose **Public**. Leave "Add a README" **unticked**. Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Open this folder in File Explorer, press **Ctrl+A** to select everything inside it, and drag it all into the GitHub page. (Drag the *contents*, not the folder itself, so `index.html` ends up at the top level.)
6. Wait for the upload to finish. Scroll down, type a message such as `Publish site`, and click **Commit changes**.
7. Check that `index.html` is listed at the top level of the repository (not inside a sub-folder).
8. Go to **Settings → Pages** (left menu).
9. Under **Build and deployment → Source**, choose **Deploy from a branch**.
10. Under **Branch**, choose **main** and **/ (root)**, then click **Save**.
11. Wait 1–3 minutes and refresh the Pages settings page. A box appears saying **Your site is live at …**. Click the link.

If the page is blank or shows a 404, see "Troubleshooting" below.

---

## Route B: use git (best if you will update the site often)

You need git installed (it is already installed on this computer). Do this once.

1. On github.com create a **new empty repository** (as in Route A steps 2–3).
2. **Copy this folder out of OneDrive first**, for example to `C:\Sites\wlsa-innovation-universe`. (OneDrive and git's hidden `.git` folder can conflict.)
3. Open **PowerShell** in the copied folder and run these commands. Replace the name, email and `<your-github-username>`:

```powershell
git init -b main
git config user.name "Your Name"
git config user.email "you@example.com"
git add .
git commit -m "Publish WLSA Innovation & Technology Universe"
git remote add origin https://github.com/<your-github-username>/wlsa-innovation-universe.git
git push -u origin main
```

4. GitHub will ask you to sign in the first time. If it asks for a password, use a **personal access token** (GitHub → Settings → Developer settings → Personal access tokens) or sign in through the browser window that opens. [confirm current GitHub sign-in steps]
5. Turn on Pages: **Settings → Pages → Source: Deploy from a branch → Branch: main, / (root) → Save**.
6. After 1–3 minutes your site is live at the address shown on that page.

---

## Updating the site later

The preview-then-approve routine still applies: change a copy, look at it, then publish.

1. Edit the files. Almost all content lives in **`universe-data.js`** (planets, people, descriptions, connections between worlds).
2. Check it locally: open `index.html` in Chrome or Edge.
3. Publish the change:
   - **Route A:** open the file on GitHub, click the pencil icon, edit, **Commit changes**. Or upload the changed file again (**Add file → Upload files**).
   - **Route B:** `git add .` then `git commit -m "Describe the change"` then `git push`.
4. GitHub rebuilds in 1–3 minutes. Press **Ctrl+F5** to bypass your browser's cached copy.

---

## Optional: a custom address

To use something like `universe.yourschool.edu`:

1. **Settings → Pages → Custom domain**, enter the address, **Save**.
2. Ask whoever manages the school's domain to add a **CNAME** record pointing to `<your-github-username>.github.io`.
3. Tick **Enforce HTTPS** once it becomes available.

[confirm DNS details with your IT team]

---

## Troubleshooting

| Problem | Likely cause and fix |
|---|---|
| 404 "There isn't a GitHub Pages site here" | Pages is not switched on yet, or the repository is private. Check **Settings → Pages** and that the repository is **Public**. [confirm: private-repository Pages depends on your GitHub plan] |
| Blank page | `index.html` is inside a sub-folder. It must be at the top level of the repository. Re-upload the folder's *contents*. |
| "Something went really wrong, and we can't process that file" while uploading | GitHub's browser uploader rejects **empty (0-byte) files** and sometimes hidden files. The name of the failing file is shown just above the message. Remove that file from the upload list (the "×" next to it) and carry on. Every file in this folder now has content, and `.nojekyll` is optional (this site works without it). If it still fails, upload the files in two or three smaller batches, or use Route B (git). |
| Page loads but looks unstyled or broken | A file did not upload (often `universe-data.js` or `styles-4.css`). Compare the file list on GitHub with this folder. All 14 files must be present. |
| You still see an old version | Browser cache. Press **Ctrl+F5**, or wait a few minutes. |
| The site works but a deep link like `#/innovation/proto` goes to the start | Make sure the `#` part is kept when copying the address. The part after `#` is the page. |
| Does not open from mainland China | See the note above. Test from the school network. [confirm] |

---

## What is in this folder

| File | Purpose |
|---|---|
| `index.html` | The page |
| `universe-data.js` | **All the content.** Edit this to change planets, people, text and connections |
| `graph.js` | Builds the map from the data automatically |
| `app-1.js`, `app-2.js` | The original iWLSA universe |
| `app-3.js` | Navigation and universe screens |
| `app-4.js` | The draggable, collapsible, resizable map |
| `app-5.js` | Search across all universes |
| `styles-1.css` … `styles-4.css` | Appearance |
| `wlsa-logo.png` | School crest |
| `404.html` | Page shown for a wrong address |
| `.nojekyll` | Tells GitHub to publish the files exactly as they are |
| `README.md`, `PUBLISH-TO-GITHUB.md`, `.gitignore` | Documentation and housekeeping (not needed by the site) |
