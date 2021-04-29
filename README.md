# How to Build and Publish

## Building from source

`jupyter-book build <source-dir>`

## Push your book to a branch hosted by GitHub Pages

The easiest way to use GitHub-pages with your built HTML is to use the [`ghp-import`](https://github.com/davisp/ghp-import) package. `ghp-import` is a lightweight Python package that makes it easy to push HTML content to a GitHub repository.

`ghp-import` works by copying *all* of the contents of your built book (i.e., the `_build/html` folder) to a branch of your repository called `gh-pages`, and pushes it to GitHub. The `gh-pages` branch will be created and populated automatically for you by `ghp-import`. To use `ghp-import` to host your book online with GitHub Pages follow the steps below:

```{note}
Before performing the below steps, ensure that HTML has been built for each page of your book. There should be a collection of HTML
files in your book's `_build/html` folder.
```

1. Install `ghp-import`

   ```bash
   pip install ghp-import
   ```

2. From the `master` branch of your book's root directory (which should contain the `_build/html` folder) call `ghp-import` and point it to your HTML files, like so:

   ```bash
   ghp-import -n -p -f _build/html
   ```

```{warning}
Make sure that you included the `-n` - this tells GitHub *not* to build your book with
[Jekyll](https://jekyllrb.com/), which we don't want because our HTML is already built!
```

Typically after a few minutes your site should be viewable online at a url such as: `https://<user>.github.io/<myonlinebook>/`. If not, check your repository settings under **Options** -> **GitHub Pages** to ensure that the `gh-pages` branch is configured as the build source for GitHub Pages and/or to find the url address GitHub is building for you.

To update your online book, you would simply make changes to your book's content on the `master` branch of your repository, re-build your book with `jupyter-book build mybookname/`, and then use `ghp-import -n -p -f mylocalbook/_build/html` as before to push the newly built HTML to the `gh-pages` branch.

```{warning}
Note this warning from the [`ghp-import` GitHub repository](https://github.com/davisp/ghp-import):

"...*`ghp-import` will DESTROY your gh-pages branch...and assumes that the `gh-pages` branch is 100% derivative. You should never edit files in your `gh-pages` branch by hand if you're using this script...*"
```

For [additional details](https://jupyterbook.org/publish/gh-pages.html)
