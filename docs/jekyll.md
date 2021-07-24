---
sidebar_position: 7
---

# Jekyll

## Getting Started

<https://jekyllrb.com/docs/installation/>

## Install Ruby

```shell
sudo apt install ruby
```

## Install Jekyll

<https://jekyllrb.com/docs/installation/ubuntu/>

```shell
jekyll new .
```

## open the gemfile

```shell
code Gemfile
```

## Modify Gemfile

Disable the jekyll version it will be pulled from the `github-pages`

```gemfile
# gem "jekyll", "~> 4.2.0"
```

Enable github-pages and pin it to a version
you can find the current versions of <https://pages.github.com/versions/>

```gemfile
gem "github-pages", "~> 215", group: :jekyll_plugins
```

## Install theme

Used the [minimal-mistakes theme](https://github.com/mmistakes/minimal-mistakes)
Configuration instructions: [Configure minimal-mistakes](https://mmistakes.github.io/minimal-mistakes/)

```shell
gem "minimal-mistakes-jekyll"
# allow remote themes for Jekyll
gem 'jekyll-remote-theme' # , '~> 2.0'
# needed for minimal-mistakes
gem "jekyll-include-cache", group: :jekyll_plugins
```

## Useful commands

```shell
bundle install
bundle update
bundle exec jekyll serve
```