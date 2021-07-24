---
sidebar_position: 4
---

# Building this site

Small variations from the [introductory](intro.md) site that comes out of the box with docusaurus.

## Getting Started

Get started by **creating a new site**.

Or **try Docusaurus immediately** with **[new.docusaurus.io](https://new.docusaurus.io)**.

## Generate a new site

Generate a new Docusaurus site using the **classic template**:

```shell
npx @docusaurus/init@latest init my-website classic
```

## Start your site

Run the development server:

```shell
cd my-website

npx docusaurus start
```

Your site starts at `http://localhost:3000`.

Open `docs/intro.md` and edit some lines: the site **reloads automatically** and display your changes.

## Register with Github

```shell
git init
git remote add origin https://github.com/mmockus/docs.git  
```

:::note

change this page to make the shell command dynamic for yarn vs npm

:::

## Deploy

Do a bunch of stuff to register your SSH

```shell
GIT_USER=mmockus USE_SSH=true yarn deploy
```
