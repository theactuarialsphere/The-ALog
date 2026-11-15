# Flipbook library: free hosting on GitHub Pages

A small static site that turns your PDFs into page-flip books. It has no ads, no watermark and no limit on the number of editions.
Everything sits in one folder, so you can upload all of it in one go on GitHub.

## What's in here

| File                              | What it does                                              |
|-----------------------------------|-----------------------------------------------------------|
| `index.html`                      | The library page. Covers are drawn automatically from page 1 of each PDF. |
| `viewer.html`                     | The flipbook viewer.                                      |
| `editions.json`                   | **The only file you edit** to add or remove editions.     |
| `styles.css`                      | Colours and fonts. Change the `:root` values to rebrand.  |
| `pdf.min.js`, `pdf.worker.min.js`, `page-flip.browser.js` | Libraries. Don't change these.    |
| `sample.pdf`                      | Placeholder edition. Delete it once your real one is in.  |

## One-time setup (about 10 minutes, all in the browser)

1. Sign in to github.com and click **New repository**. Give it a name (for example `alog`) and set it to **Public**. Then click **Create repository**.
2. Click **uploading an existing file**, select *all* the files from this folder and drag them in. Click **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment*, set Source to **Deploy from a branch** and Branch to **main** / **(root)**, then click **Save**.
4. Wait 1–2 minutes. Your site will be live at
   `https://<your-username>.github.io/<repo-name>/`

## Adding a new edition

1. In the repository, click **Add file → Upload files** and upload the PDF. Use a simple file name with no spaces, such as `edition-2.pdf`.
2. Open `editions.json`, click the pencil icon, and add an entry:

```json
{
  "id": "edition-2",
  "title": "The ALog — Edition 2",
  "subtitle": "Bilingual edition",
  "date": "October 2026",
  "file": "edition-2.pdf"
}
```

Separate entries with commas. Entries show up in the order you list them, so put the newest first if you want it at the top. Delete the `sample` entry and `sample.pdf` once your first real edition is in.

3. Commit. The site updates within a minute or two.

## Sharing links

- A specific edition: `.../viewer.html?ed=edition-2`
- A specific page: `.../viewer.html?ed=edition-2#p=12`

## Good to know

- **File size:** GitHub's web upload accepts files up to **25 MB**. Magazines exported "for web" or "smallest file size" are usually well under that, and smaller PDFs open faster for readers.
- **Load time:** the viewer prepares every page before showing the book. For a 40–60 page magazine this takes a few seconds, and a progress bar shows meanwhile.
- **Custom domain (optional):** Settings → Pages → Custom domain lets you use something like `alog.yourdomain.mu` for free, if you own the domain.
- **Embedding on another site:**
  `<iframe src="https://<user>.github.io/<repo>/viewer.html?ed=edition-2" width="100%" height="700" style="border:0" allowfullscreen></iframe>`

Libraries: StPageFlip (MIT) and PDF.js (Apache 2.0). Their licences are included.
