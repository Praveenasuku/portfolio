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
| Hero (particle name, intro, buttons) | `class="hero"` |
| Projects and the system map | `id="systems"` |
| How I build AI systems | `id="approach"` |
| Ask my resume console | `id="ask"` |
| Experience timeline | `class="role` |
| Skills | `class="tier` |
| Education and certifications | `id="education"` |
| Contact | `id="contact"` |

- **The "Ask my resume" console** answers from the `CHUNKS` list in the script near the bottom of `index.html`. When your resume changes, update the matching chunk text too, or the console will answer with old facts.
- **New resume PDF:** replace `Praveena_S_Resume.pdf` with a new file of the same name.
- **Adding a job:** copy one `<li class="role">` block, paste it at the top of the list and edit it. Then add a matching entry to `CHUNKS` so the console knows about it.

## Changing the colours

The whole colour scheme is the `:root` block at the top of the `<style>` tag. The current theme is warm black with orange, amber and red.

| Token | Used for |
| --- | --- |
| `--bg-c`, `--s1-c` | Page background and panels |
| `--text-c` | Main text and the particle name |
| `--accent-c` | AI steps, highlights and links on hover (orange) |
| `--service-c` | Services, company names and the name's amber tint |
| `--guard-c` | Guardrails, human checks and the status dot (red) |
| `--glow-c` | The soft glow behind the hero, map and contact section |

Values ending in `-c` are three numbers (red green blue, for example `255 122 26`), not hex codes, so every tint on the page and the hero particles follow them automatically. If you change the background, also update `theme-color` in the `<head>` and `favicon.svg`.

## Motion

- **3D embedding galaxy:** a WebGL cloud of glowing points, grouped into topic clusters like vectors in a vector database, sits behind the whole page (`Galaxy` in the script, `<canvas id="galaxy">`). The mouse tilts it and lights up nearby points like a search query, a click sends a ripple, and a random cluster flashes every few seconds. Scrolling morphs it: galaxy (hero), knowledge sphere (systems), index lattice (ask my resume), double helix (experience), ring (contact). Phones get fewer points and a dimmer cloud behind text; browsers without WebGL simply skip it.
- **On load:** the name assembles from particles, then the header drops in and the intro and buttons rise.
- **On scroll:** section headings swipe up word by word, and content slides in (`REVEALS` list in the script sets what moves and how). A two-row stack marquee runs under the hero.
- **On hover (mouse and trackpad):** an orange glow follows the cursor, buttons pull toward the pointer, and skill tags lift.
- **On phones:** the system map nudges sideways once to show it can be swiped.
- Visitors who turn on "reduce motion" in their device settings get the same page with no animation.
