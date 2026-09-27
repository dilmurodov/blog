# blog

A Jekyll blog. There is no admin panel — that is deliberate. Posts are Markdown
files in `_posts/`, and **Asli edits them from Telegram**.

## How a post gets written

```
you, in Telegram  ──▶  Asli  ──▶  commit on a branch  ──▶  "Open PR" button
                                                              │
                                        you review the diff on GitHub, merge
                                                              │
                                        GitHub Pages rebuilds ─┘
```

Ask him in the group:

> напиши пост про то, как мы подняли codebase-memory в homelab

He edits in his sandbox, commits, and calls `propose_deploy` with this
repository's name. You get a card with the diff and an **Open PR** button.
Nothing is pushed until you tap it, and nothing reaches `master` until you
merge — Asli cannot merge.

For this to work the repository must be listed in
`homelab.services.asli.repos` in the homelab config, and Asli's GitHub token
must cover it.

## Writing a post by hand

`_posts/YYYY-MM-DD-slug.md`:

```markdown
---
layout: post
title: "Заголовок"
---

Текст.
```

The date in the filename is what orders the index.

## Publishing

GitHub Pages builds Jekyll natively — push to `master` and it rebuilds. No CI
to configure. Enable it in Settings → Pages → Source: *Deploy from a branch*.

Set `baseurl` in `_config.yml` to `/<repo-name>` if the site is served at
`<user>.github.io/<repo>`, or leave it empty for a custom domain.

## Local preview

```bash
bundle install
bundle exec jekyll serve
```

## Where the layout came from

`_layouts/` and `css/` are adapted from [mbrooker-blog](https://github.com/mbrooker/mbrooker-blog),
MIT, itself branched from [mojombo.github.com](https://github.com/mojombo/mojombo.github.com) —
Tom Preston-Werner's blog, by the author of Jekyll.

Only the MIT-licensed files were taken. His posts are CC-BY-3.0 and were not
copied, and the layout was stripped of his name, bio, contact details and
links. See [NOTICE](NOTICE).
