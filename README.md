# Blog

My personal blog, built with Jekyll and the free [Lagrange](https://github.com/LeNPaul/Lagrange)
theme by Paul Le (MIT licence, see `LICENSE.md`).

Address: https://jeremiaoc.github.io/

## Write a new post

1. Create `_posts/YYYY-MM-DD-short-title.md` (start from `_drafts/post-template.md`).
2. Front matter:

   ```yaml
   ---
   title: "My post"
   category: research      # optional: research | science | philosophy | random (shown in the archive)
   tags: [nmr, thoughts]   # optional: posts sharing a tag appear under "You may also enjoy"
   image: my-picture.jpg   # optional: header image, file in assets/img/
   ---
   ```
3. Write in Markdown. LaTeX works with `$...$`.
4. Commit and push to `main`. The site rebuilds in about a minute.

Drafts in `_drafts/` are never published.

## Change the site

| What | Where |
|---|---|
| Site title, subtitle, your name | `_config.yml` |
| Menu items, social icons, comments, analytics | `_data/settings.yml` |
| About page | `about.md` |
| Colours and fonts | `_sass/` |

## Publishing

Push to `main`. The workflow `.github/workflows/pages.yml` builds the site and deploys it to
GitHub Pages (**Settings → Pages → Build and deployment → Source: GitHub Actions**).
The site lives at https://jeremiaoc.github.io/.

## Preview locally (optional)

```bash
bundle install
bundle exec jekyll serve --drafts
# open http://localhost:4000/
```
