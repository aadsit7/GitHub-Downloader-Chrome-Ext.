GitHub Folder Downloader
========================

A single self-contained web page (index.html) that lets you download one
top-level folder from a public GitHub repository as a ZIP — keeping the
folder's internal structure — entirely in your browser. No login, token,
or outside service required.


WHAT IT DOES
------------
1. On load, it reads the source repository's default branch from the
   GitHub API.
2. It lists every top-level folder in that repo and shows each one as a
   selectable option.
3. When you pick a folder and click "Download ZIP", it gathers that
   folder's files, packs them into a ZIP (folder structure preserved),
   and downloads it as "<folder-name>.zip".

File downloads happen through raw.githubusercontent.com, which does not
count against GitHub's anonymous API rate limit, so normal use stays well
within limits.


SOURCE REPOSITORY
-----------------
The page reads its folder list from a SEPARATE public repo. By default:

    aadsit7/Chrome-EXT-format

To point the page at a different public repo, open index.html and edit the
two constants near the top of the <script> block:

    const SOURCE_OWNER = "aadsit7";
    const SOURCE_REPO  = "Chrome-EXT-format";


HOW TO OPEN IT LOCALLY
----------------------
Just double-click index.html, or open it in any modern web browser. That's
it — everything runs client-side.


HOW TO PUBLISH WITH GITHUB PAGES
--------------------------------
index.html lives at the root of this repository, so GitHub Pages serves it
as the main page automatically.

1. Push this repository to GitHub.
2. In the repo, go to: Settings > Pages.
3. Under "Build and deployment", set Source to "Deploy from a branch".
4. Choose the branch you pushed to and the "/ (root)" folder, then Save.
5. After a minute, your page will be live at:
       https://<your-username>.github.io/<this-repo-name>/


HOW TO USE
----------
1. Open the published page (or the local file).
2. Wait for the folder list to load.
3. Select a folder.
4. Click "Download ZIP".
5. Your browser downloads "<folder-name>.zip".


NOTES
-----
- Anonymous GitHub API use is limited to about 60 requests per hour. If you
  hit that limit, the page will tell you in plain language; just wait a bit
  and try again.
- Binary files (PNG/JPG/ICO icons, etc.) are downloaded as binary, so they
  arrive intact.
- Everything is in the single index.html file; the only external piece is
  the JSZip library, loaded from a CDN.
