<h1>

![Image](./images/favicon_32x32.png) GAIA: Generally An Information Arsenal

</h1>

## ℹ️ What is this?

This is GAIA (pronounced *Guy-uh* because why not) - a blog meant to reciprocate what I believe, what I know and what I find interesting.

This is a static blog built with Jekyll and hosted on GitHub Pages. The base template is HPSTR by [Michael Rose @mmistakes](https://github.com/mmistakes).

## ❓ Why?

Everyone needs a medium to express themselves and their thoughts!

## What can I expect to see or read?

Whatever I deem interesting enough finds its place here. The frequency of posts fluctuates a lot (often on the lower side) - you have been warned.

To summarize, ***expect the unexpected***.

> Not sponsored by [Oscar Wilde](https://en.wikipedia.org/wiki/Expect_the_Unexpected).

---

## Contributing

I am the sole author of the blog and don't have plans for external posts, but you're free to recommend ideas. I'll add you as a source if I use your material.

As for bugs and other issues, feel free to report them! Let 'em come my way!

---

## Local Development

### Requirements
- Ruby
- Jekyll
- Bundler

### Setup

```bash
bundle install
```

### Running locally

```bash
bundle exec jekyll serve --trace --livereload -o
```

Or if you have the convenience scripts set up:

```bash
pnpm serve       # Published posts only
pnpm serveall    # Includes drafts
```

### Creating content

```bash
pnpm draft "My Post Title"           # Create draft
pnpm publish _drafts/my-post.md      # Publish draft
pnpm post "Quick Post"               # Create post directly
```

---

## Comment System

Comments are handled by a custom Netlify Function linked to a private repo that:
1. Receives comment form submissions
2. Checks spam via Akismet
3. Commits comments as YAML files to `_data/comments/`
4. GitHub Pages rebuilds and displays them

No database and no third-party accounts required for commenters.

---

## License

Content © Sid. Original theme based on HPSTR by Michael Rose (although I guess it's barely recognizable as that now).