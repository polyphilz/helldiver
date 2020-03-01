# Helldiver

Helldiver is a lightweight command-line program written in Python that converts your Markdown blog posts into blog-aware HTML. It's designed for blogs with the most minimal of features (think: a date when the post was written, *maybe* an author, and nothing more).

## Features

Helldiver allows you to:

- Specify a date and an author that will be included in the generated HTML (if you want to)
- Add classes to generated HTML tags that will get picked up by your CSS

## Getting Started

In progress.

## Features in development

- Dictate the formatting of the date
- Specify class names you would like to add to generated HTML tags

## Why another "static site generator"?

It's true, there are existing (and awesome) projects like [jekyll](https://jekyllrb.com/) and [pelican](https://blog.getpelican.com/) that act as full-suite static site generators. As lightweight as they are though, even they were too "feature-complete" for my use case when I was building [my own personal website](https://github.com/rbnsl/personal-website). I didn't need themes or generation of my entire site, and I just wanted something so simple it barely required more than a cursory glance at the documentation. I just needed my Markdown to become blog-ready, and thus, Helldiver was born.
