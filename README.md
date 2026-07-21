# Your site

A small four-page site (About, Photography, CV, Road to Tokyo) built with
[Eleventy](https://www.11ty.dev/), a static site generator. You write pages
in Markdown, run one command, and it produces plain HTML/CSS you can host
anywhere for free.

## 1. First-time setup

You need [Node.js](https://nodejs.org/) installed (any recent LTS version).
Then, in this folder:

```
npm install
```

## 2. Working on it locally

```
npm start
```

This opens a local preview at `http://localhost:8080` that live-reloads as
you edit files. Stop it with `Ctrl+C`.

## 3. Editing content

Everything you'll touch day-to-day lives under `src/`:

| Page             | File                                    |
|-------------------|------------------------------------------|
| About             | `src/index.md`                          |
| Photography       | `src/photography.md`                    |
| CV                | `src/cv.md`                             |
| Road to Tokyo list| `src/road-to-tokyo/index.md` (auto-generated, don't edit) |
| Road to Tokyo posts | `src/road-to-tokyo/posts/*.md`        |

**About / CV** — plain HTML-in-Markdown, just edit the text directly.

**Photography** — edit the `photos:` list at the top of `src/photography.md`
(the "front matter" between the `---` lines). Each entry needs an image
`src` path and an optional `caption`. Drop your actual photos into
`src/images/photography/` (replacing the placeholder ones), matching the
filenames you reference.

**Road to Tokyo** — this is the one built for your Obsidian workflow. To add
a new entry:

1. Copy `src/road-to-tokyo/posts/first-post.md` to a new file in the same
   folder (e.g. `week-two.md`).
2. Edit the front matter at the top: `title`, `date`, and `permalink`
   (the URL — keep it lowercase with hyphens, e.g. `/road-to-tokyo/week-two/`).
3. Write below it in normal Markdown, same as you're used to in Obsidian.
   Reference images like `![alt text](/images/road-to-tokyo/your-photo.jpg)`
   and put the actual image files in `src/images/road-to-tokyo/`.

New posts appear automatically on the Road to Tokyo index, newest first —
no need to edit that page yourself.

If you already have a Road to Tokyo `.md` file from Obsidian, the easiest
path is to split it into one file per entry in `src/road-to-tokyo/posts/`,
add the three front-matter lines to each, and drop any linked images into
`src/images/road-to-tokyo/`.

## 4. Building

```
npm run build
```

This produces the finished site as plain files in `_site/`. You don't need
to run this by hand if you deploy via Cloudflare Pages (below) — it does
this step for you automatically on every update.

## 5. Deploying to Cloudflare Pages (free)

Since your domain is already on Cloudflare, this is the simplest path.

**Recommended: connect a GitHub repo**
1. Push this folder to a new GitHub repository.
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages →
   Connect to Git**, pick the repo.
3. Build settings: Build command `npx @11ty/eleventy`, Build output
   directory `_site`.
4. Deploy. From then on, every time you push a change to GitHub, Cloudflare
   rebuilds and redeploys automatically.
5. Under the project's **Custom domains**, add your domain — Cloudflare
   will wire up the DNS for you since it's already on your account.

**Alternative: deploy straight from your computer, no GitHub**
```
npm run build
npx wrangler pages deploy _site
```
Follow the prompts to log in and create the project. You'd then re-run
these two commands whenever you want to publish changes.

Either way, cost is $0/month — you're just paying for the domain you
already have.
