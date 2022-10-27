<h1>

![Image](./images/favicon_32x32.png) GIA: Generally an Information Arsenal

</h1>

## ℹ️ What is this?

This is GIA (pronounced *Guy-uh* because why not) - a blog meant to reciprocate what I believe, what I know and what I find interesting.

This is a static blog that uses Jekyll and GitHub Pages. The base template is HPSTR made by [Michael Rose @mmistakes](https://github.com/mmistakes).

## ❓ Why?

Well everyone needs a medium to express themselves and their thoughts!

## What can I expect to see or read?

Like I said, whatever that I deem interesting enough finds its place here. However, the frequency of posts fluctuates a lot (with it being on the lower side of the spectrum for the most part) - you have been warned.

To summarize, ***expect the unexpected***. 

> Not sponsored by [Oscar Wilde](https://en.wikipedia.org/wiki/Expect_the_Unexpected).

---

## Contributing

I am the sole author of the blog and don't have any plans to have posts from external sources, but you're free to recommend posts, writings and whatnot. I'll make sure I add you as a source if I do end up using your material or ideas.

As for bugs and other issues, feel free to report them! Fixes are welcomed as well!

## Local Development and Installation

To build and serve locally, you need to make sure you have **Jekyll** installed (which requires **Ruby**). This project uses a `Gemfile` to track dependent gems, and using `bundler` to work with the `Gemfile` is convenient. See [Jekyll - Ruby 101](https://jekyllrb.com/docs/ruby-101/) and [Jekyll - Installation](https://jekyllrb.com/docs/installation/) for more information if you're unsure about the workings.

First install all the gems in the `Gemfile`:

```
bundle install
```

Use the following command to get the local server up and running (with live reloading capabailities set up):

```
bundle exec jekyll serve --trace --livereload -o
```