This is a site built using Hugo.

# How do I start an hugo site?

hugo new site <name-site>

# How do I run the server?

`hugo server`

# How do I build the site

`hugo`

# Set up this repo on a new machine

Install Hugo (extended edition) and Dart Sass before building or serving the site. On macOS with Homebrew:

```sh
brew install hugo
brew install sass/sass/sass
```

On Linux or Windows, install Hugo by following the [official Hugo instructions](https://gohugo.io/installation/) and install Dart Sass using [Hugo's Dart Sass instructions](https://gohugo.io/functions/css/sass/#dart-sass). Make sure both `hugo` and `sass` are available on your `PATH`.

From the repository directory, start the local server:

```sh
hugo server
```

To generate the production site instead, run `hugo`; the generated files are written to `public/`.

# How do I update the dependencies?

This site has no package manager or dependency lockfile. It uses the Hugo CLI and Dart Sass to build the site, and loads KaTeX from jsDelivr on pages that contain math.

## Update Hugo

Install the latest Hugo extended release. On macOS with Homebrew, run:

```sh
brew update
brew upgrade hugo
hugo version
```

On other platforms, follow the [official Hugo installation instructions](https://gohugo.io/installation/).

## Update Dart Sass

Hugo uses Dart Sass to compile `assets/scss/style.scss`. On macOS with Homebrew, update it with:

```sh
brew upgrade sass/sass/sass
hugo env
```

For other platforms and CI environments, see [Hugo's Dart Sass instructions](https://gohugo.io/functions/css/sass/#dart-sass). Keep Dart Sass installed in each environment that builds the site.

## Update KaTeX

Check the [latest KaTeX version on npm](https://www.npmjs.com/package/katex). In `layouts/partials/katex.html`, change the version in all three jsDelivr URLs (CSS, core JavaScript, and auto-render JavaScript), then replace each `integrity` value with the SHA-384 SRI hash for that exact file and version. Keep the versions and hashes pinned; jsDelivr documents [how to generate SRI hashes](https://www.jsdelivr.com/using-sri-with-dynamic-files).

After updating, run `hugo` to build the site and check any pages that use math rendering.
