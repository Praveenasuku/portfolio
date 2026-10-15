# Praveena S Portfolio

A one-page portfolio in plain HTML, CSS and JavaScript. There is no build step, so Vercel serves the files exactly as they are.

## What's in this folder

| File | What it is |
| --- | --- |
| `index.html` | The whole site: content, styles and scripts |
| `Praveena_S_Resume.pdf` | The resume the "Resume" buttons download |
| `og-image.png` | The preview image shown when the link is shared on LinkedIn, WhatsApp or Slack |
| `favicon.svg` | The browser tab icon |
| `robots.txt` | Lets search engines index the site |

## Preview on your Mac

Open Terminal and run:

```bash
cd ~/Downloads/praveena-portfolio-site
python3 -m http.server 8000
```

Then open http://localhost:8000 in your browser. Press `Ctrl + C` in Terminal to stop it.

## Deploy to Vercel

### Option A: through GitHub (recommended)

Recruiters can also see the repo, and every change you push redeploys the site automatically.

1. On GitHub, create a new repository, for example `portfolio`.
2. In the repo, choose **Add file → Upload files**, drag in every file from this folder, and commit.
3. Go to vercel.com and sign in with GitHub.
4. Choose **Add New → Project** and import the `portfolio` repo.
5. Set **Framework Preset** to **Other**, and leave the build command and output directory empty.
6. Click **Deploy**. Vercel gives you a live link when it finishes.

### Option B: from Terminal

This needs Node.js (`brew install node` if you don't have it).

```bash
npm install -g vercel
cd ~/Downloads/praveena-portfolio-site
vercel          # first run: log in and accept the defaults; gives a preview link
vercel --prod   # publishes the production link
```

## After the first deploy

1. Copy your production link, for example `https://praveena-portfolio-two.vercel.app`.
2. If your link is different, open `index.html` and use Find and Replace to change every `https://praveena-portfolio-two.vercel.app` to your link. Then redeploy (push to GitHub, or run `vercel --prod` again).
3. Check the share preview by pasting your link into LinkedIn Post Inspector (linkedin.com/post-inspector).
4. Add the link to your resume header, your LinkedIn profile's website field and your GitHub profile.

## Updating content

All the text lives in `index.html`. Search for these to find each section:

| Section | Search for |
| --- | --- |
| Hero (name, intro, buttons) | `class="hero"` |
| Projects | `class="proj"` |
| How I build AI systems | `id="approach"` |
| Skills rack | `class="rack"` |
| Experience | `class="jobs"` |
| Education and certifications | `id="education"` |
| Contact | `id="contact"` |

- **The "Ask my resume" console** answers from the `CHUNKS` list in the script near the bottom of `index.html`. When your resume changes, update the matching chunk text too, or the console will answer with old facts.
- **New resume PDF:** replace `Praveena_S_Resume.pdf` with a new file of the same name.
- **Adding a job:** copy one `<article class="job">` block, paste it at the top of the list and edit it. Then add a matching entry to `CHUNKS` so the console knows about it.
