# Loud Pragmatic

A personal blogging theme with music release support.

## Getting started

You need the following files in your web-site sources (`./static/*`) to make the theme work properly.

### Your main logo

- `./static/images/logo.svg`

### Icons

- `./static/favicon.ico` # 48 x 48
- `./static/favicon.svg`
- `./static/safari-pinned-tab.svg`
- `./static/apple-touch-icon.png`

### How is it used?

Here is the list of some HTML tags generated for these files:

```html
<link rel="icon" href="/favicon.ico" sizes="48x48">
<link rel="icon" href="/favicon.svg" sizes="any" type="image/svg+xml">
<link rel="apple-touch-icon" href="/apple-touch-icon.png">
<link rel="mask-icon" href="/safari-pinned-tab.svg" color="{{ .Site.Params.Theme.Colors.Main | default "#5a2673" }}">
```

### Configuration

This is a configuration file example that can be used with the theme:

```yaml
baseURL: https://the.internet/
languageCode: en-US
title: Best website ever
theme: loud-pragmatic
enableRobotsTXT: true # if you don't bring your own
copyright: John Doe

# styling recommended for default colors
markup:
  highlight:
    tabWidth: 2
    style: vulcan
  tableOfContents:
    endLevel: 3
    startLevel: 1

# theme parameters
params:
  # used in the meta tag
  licenseURL: http://creativecommons.org/licenses/by-nc-sa/4.0/
  # default author on the website
  # can be overwritten in the front matter with the same YAML
  author:
    pictureURL: /images/myface.jpg
    name: John Doe
    email: mail@server.internet
  # separate contact email rendered in the footer
  contact:
    email: mail@server.internet
  # to extend `head` and `footer` content with your custom markup
  customHTML:
    head: '<meta name="fediverse:creator" content="@<username>@mastodon.social">'
    footer: 'Unless indicated otherwise, the content is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/" rel="nofollow noreferrer" target="_blank">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License (CC BY-NC-SA 4.0)</a>.'
  # theme customization
  theme:
    # default colors
    colors:
      # header, footer, meta and link tags in `head`
      main: "#5a2673"
      background: "#141116"
      # on hover
      highlight: "#8952A2"
      # tables, table of content, preview cards, etc
      border: "#D7DADC"
      # preview card on the list
      card:
        background: "#252426"
        # this must have an alpha value, it tints the cover image in the preview with an overlay
        overlay: "rgba(20,17,22,0.6)"
      text:
        # content text
        main: "#D7DADC"
        secondary: "#C0C0C0"
        # smaller text with additional details, e.g. preview cards
        # on hover or unhovered links in the content
        highlight: "#FFF"


# if menu identifiers are set, this will render SVG icons in
# `/images/menus/<identifier>.svg` if found.
# Put this in `./static/images/menu/*.svg`.
menu:
  main:
    # section menus should be configured in their corresponding "_index.md" files via the front matter, for example:
    # title: "Blog posts"
    # description: "Full list of all articles."
    # date: 2021-12-27T00:00:00+01:00
    # menus:
    #   main:
    #     name: Posts
    #     weight: 1
    - identifier: linkedin # this will render `/images/menus/linkedin.svg`
      name: LinkedIn
      title: My LinkedIn profile
      url: https://www.linkedin.com/in/<username>
      weight: 21
    - identifier: github
      name: Github
      title: My Github profile
      url: https://github.com/<username>
      weight: 22
    - identifier: mastodon
      name: Mastodon
      title: My Mastodon profile
      url: https://mastodon.social/<username>
      weight: 23
      params:
        rel: me # for link verification
```

### File structure

In order to generate your static web-site with Hugo you need to maintain the following file structure of your blog sources:

```
./content
  _index.md # home page
  posts/
    post1/
      cover.jpg
      index.md
    post2/
      cover.jpg
      index.md
    _index.md # section page
  music/
    music1/
      cover.jpg
      index.md
    music2/
      cover.jpg
      index.md
    _index.md # section page
./themes/
  loud-pragmatic # this theme: e.g. git a submodule reference
./static
  images/
    logo.svg # rendered in the footer
    menu/ # if exists will match by menu item identifier
      linkedin.svg
      github.svg
      mastodon.svg
  apple-touch-icon.png
  favicon.svg
  favicon.ico
  safari-pinned-tab.svg
```

## Creating content

### Blog post

To create a post run:

```sh
hugo new content posts/this-is-a-test/index.md
```
(change `this-is-a-test` to the title of your post)

If there is a file `cover.*` (e.g. `cover.png`) in the `posts/this-is-a-test` directory, it will be picked up as a cover in the post preview and on the post page.

### Music release

To create a music release run:

```sh
hugo new content music/this-is-a-test/index.md
```
(change `this-is-a-test` to the title of your music release)

If there is a file `cover.*` (e.g. `cover.png`) in the `music/this-is-a-test` directory, it will be picked up as a cover of the music release.

Audio player entries will be automatically generated for all audio files with one of the following extensions: mp3, aac, ogg, flac, alac, ape, wav, aiff, wma, m4a, opus. Ordering is alphabetical.

These files can be stored on any level inside the music release directory (`music/this-is-a-test`).
