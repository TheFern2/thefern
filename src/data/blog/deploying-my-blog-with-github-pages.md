---
title: "Deploying My Blog with GitHub Pages and a Custom Domain"
description: "How I set up my portfolio and blog using Astro, GitHub Pages, and my own domain."
pubDatetime: 2026-02-27T00:00:00Z
tags:
  - web
  - astro
  - github
featured: true
---

I finally got around to setting up a proper portfolio and blog. Here's how I did it.

## The Stack

- **Astro** with the AstroPaper theme (free)
- **GitHub Pages** for hosting (free)
- **Custom domain** via Squarespace DNS ($20)
- **Domain email** via ProtonMail ($15) 

## Why Astro?

I considered React-based options like Next.js, but for a mostly static site with blog posts, Astro made more sense. It ships zero JavaScript by default and has great Markdown support out of the box. Who doesn't love markdown, *amirite?*

## Setting Up GitHub Pages

The deployment is handled by GitHub Actions. Every push to `main` triggers a build and deploy.

The workflow builds the site with `npm run build` and deploys the `dist` folder to GitHub Pages.

## Custom Domain

I already had a domain through Squarespace. Setting it up:

1. Adding a `CNAME` file to the repo with my domain
2. Configuring A records pointing to GitHub's IPs
3. Adding a CNAME record for `www`
4. Enabling the custom domain in GitHub repo settings

DNS propagation took a few minutes, then HTTPS was automatically provisioned.

## Domain email

I have been paying Proton Plus for a few years now. I didn't even know I could use it to add my domains. I was working on a project when I asked ai for options to use a professional email. It gave me several options. *Well since you're already using proton, why not add your domain there?* In past projects, I used aws workmail in the past which can run up 10-20 bucks. It makes perfect sense to use something I am already paying for, specially since some of this might be short lived projects.

- Go into settings
- Custom domains
- Add your domain, follow prompts
- Add records to your domain
- Add your own address once domain is verified

## What's Next

Now that the infrastructure is in place, I can focus on actually writing content and adding projects. The nice thing about this setup is that publishing is just a git push.
