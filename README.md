# Helldiver

Helldiver is a lightweight command-line program written in Python that converts your Markdown blog posts into blog-aware HTML. It's designed for blogs with the most minimal of features (think: a date when the post was written, *maybe* an author, and nothing more).

## Features

Helldiver allows you to:

- Specify a date and an author that will be included in the generated HTML (if you want to)
- Add classes to generated HTML tags that will get picked up by your CSS

## Getting Started

### Installation

Install Helldiver in 3 steps:

1. Install the package from PyPI
2. Add the program to your PATH
3. Grant executable rights

#### Installing the package from PyPI

Helldiver is built and packaged using [Poetry](https://python-poetry.org/). It requires Python 3.7 and can be installed simply using `pip`:

`pip install helldiver`

#### Adding Helldiver to your PATH

You can then add it to your PATH for ease-of-use. Add the following to your `~/.bashrc` or `~/.zshrc`:

`export PATH="/usr/local/lib/python3.7/site-packages/helldiver:$PATH"`

Don't forget to source with `source ~/.bashrc` or `source ~/.zshrc`. If you get an error from that, it could be because `pip` installed `helldiver` in a different location than what's written in the command above. `pip` generally installs packages to a folder called `site-packages`, but you can confirm `helldiver`'s location with:

`pip show helldiver | grep Location | sed 's/Location: //'`

Example output of above command: `/usr/local/lib/python3.7/site-packages`

#### Grant executable rights

Run `chmod +x /usr/local/lib/python3.7/site-packages/helldiver/helldiver.py` to allow the program to be run.

### Usage

There are two components to using Helldiver:

1. Adding a header line to your Markdown files that contain date/author information
2. Running the program with the required flags

#### Working with your Markdown

Helldiver uses the `%` character as a sentinel value, in between which you would place the desired date and author information. For example, at the top of your Markdown file, if you add the following line:

```
02/29/2020%Tim Smith%

# My title for my post

... content ...
```

The date and author retrieved will be `02/29/2020` and `Tim Smith` respectively.

Don't want to put a date, an author or either of them? That's completely okay, just leave the corresponding area in the header blank:

No date, no author: `%%`

Date, but no author: `2/29/2020%%`

Author, but no date: `%Tim Smith%`

#### Running the program

`helldiver.py` takes 3 required flags:

- `-f` or `--filename`: The file name of the Markdown file you want to convert
- `-m` or `--markdown`: The file path to the directory containing the above Markdown file
- `-ht` or `--html`: The file path to the directory you would like generated HTML to be placed in

For example, given the following directory structure:
  
```
.
|--- ...
|--- writing
|    |--- markdown
|         |--- sample-post.md
|     
|         
|--- ...
```

When I run: `helldiver.py -f sample-post -m writing/markdown/ -ht writing/`, I would expect a `sample-post.html` to be added to the `writing` directory:

```
.
|--- ...
|--- writing
|    |--- markdown
|    |    |--- sample-post.md
|    |---sample-post.html 
|         
|--- ...
```

Please keep in mind that both directories that store Markdown and HTML files must exist to begin with.

## Features in development

- Dictate the formatting of the date
- Specify class names you would like to add to generated HTML tags

## Why another "static site generator"?

It's true, there are existing (and amazing) projects like [jekyll](https://jekyllrb.com/) and [pelican](https://blog.getpelican.com/) that act as full-suite static site generators. As lightweight as they are though, even they were too "feature-complete" for my use case when I was building [my own personal website](https://github.com/rbnsl/personal-website). I needed something simple to make my Markdown blog-ready and wanted to have some fun in the process; thus, Helldiver was born.