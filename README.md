# 🚲 Madrid Bike Tours

> **My first vibe-coded website — built entirely with AI (GitHub Copilot)**

**Live site → [https://madrid-bike-tours.github.io/](https://madrid-bike-tours.github.io/)**

---

## About This Project

This is my first website created through **vibe coding** — a workflow where you describe what you want in plain language and AI writes all the code. Not a single line of HTML, CSS, Jekyll, or Python in this project was typed manually by me. Every layout, stylesheet, blog post, GitHub Actions workflow, and deployment script was generated through a conversation with GitHub Copilot.

The site is a fully functional **Jekyll static website** for a fictional Madrid bike tours business, published on GitHub Pages. It has a homepage, four tour pages, a blog with three articles, an about page, a FAQ, and a contact form — all styled with a custom responsive design.

---

## What Is Vibe Coding?

Vibe coding is a style of software development where you collaborate with an AI assistant to build software by describing intent rather than writing syntax. You say *"create a Jekyll site for Madrid bike tours with a blog"* and the AI generates the project structure, writes the code, fixes the errors, and deploys it. You guide, the AI executes.

This project was built 100% this way — from the initial scaffold to the GitHub Actions CI/CD pipeline and the Python deployment script.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Static site generator | [Jekyll 4.3](https://jekyllrb.com/) |
| Hosting | [GitHub Pages](https://pages.github.com/) |
| CI/CD | GitHub Actions |
| Fonts | Google Fonts (Montserrat + Lora) |
| Icons | Font Awesome 6 |
| Images | Unsplash CDN |
| Deployment script | Python 3.11 |
| Contact form | Formspree (ready to wire up) |

---

## Features

- **Responsive design** — works on mobile, tablet, and desktop
- **Hero sections** with full-width background images on every page
- **Tour collection** — Jekyll collection with custom `tour` layout, booking sidebar, difficulty badges, and pricing
- **Blog** — full post layout with hero image, reading time, share buttons, prev/next navigation, and tags
- **Homepage** — hero, features grid, tour cards, testimonials, blog preview, and CTA section
- **Tours index** — filterable by difficulty (Easy / Moderate / Challenging)
- **Contact & booking form** — multi-field form with tour selector and date picker
- **FAQ page**
- **SEO** — `jekyll-seo-tag`, `jekyll-feed`, `jekyll-sitemap` plugins
- **Auto-deploy** — push to `main` → GitHub Actions builds Jekyll → site goes live
- **Python deploy script** — one command to commit and push using a specific SSH key (for multi-account GitHub setups)

---

## Project Structure

```
github_pages_1/
│
├── .github/
│   └── workflows/
│       └── jekyll.yml          # GitHub Actions — builds & deploys on push to main
│
├── jekyll/                     # Jekyll site root
│   ├── _config.yml             # Site config (title, URL, nav, social, plugins)
│   ├── Gemfile                 # Ruby gems (Jekyll 4.3 + plugins)
│   │
│   ├── index.html              # Homepage
│   ├── about.md                # About page
│   ├── contact.md              # Contact & booking form
│   ├── faq.md                  # FAQ
│   ├── tours.html              # Tours index with difficulty filter
│   │
│   ├── blog/
│   │   └── index.html          # Blog index
│   │
│   ├── _layouts/
│   │   ├── default.html        # Base HTML shell (head, header, footer)
│   │   ├── page.html           # Generic content page
│   │   ├── post.html           # Blog post (hero, meta, share, prev/next)
│   │   └── tour.html           # Tour detail (hero, booking sidebar)
│   │
│   ├── _includes/
│   │   ├── header.html         # Sticky nav with mobile hamburger menu
│   │   ├── footer.html         # Footer with links, social, contact
│   │   └── post-navigation.html
│   │
│   ├── _tours/                 # Tour collection — one .md file per tour
│   │   ├── classic-city-tour.md
│   │   ├── retiro-park-morning-ride.md
│   │   ├── madrid-rio-greenway.md
│   │   └── tapas-bikes-night-tour.md
│   │
│   ├── _posts/                 # Blog posts (YYYY-MM-DD-slug.md)
│   │   ├── 2025-06-10-best-cycling-routes-madrid.md
│   │   ├── 2025-05-15-cycling-through-retiro-park.md
│   │   └── 2025-04-20-best-food-after-bike-tour-madrid.md
│   │
│   └── assets/
│       └── css/
│           └── main.css        # ~700 lines of custom CSS (no framework)
│
├── deploy.py                   # Python deploy script (SSH key auth)
├── deploy.cfg                  # Deploy config (key path, remote, branch)
├── .gitignore
└── README.md
```

---

## How Deployment Works

```
You run: python deploy.py
         │
         ├── git add -A
         ├── git commit -m "deploy: YYYY-MM-DD HH:MM"
         └── git push (via SSH key from deploy.cfg)
                  │
                  └── GitHub Actions triggers
                           │
                           ├── ruby/setup-ruby  (installs gems)
                           ├── jekyll build     (generates _site/)
                           └── actions/deploy-pages  → live at GitHub Pages
```

The Python script uses `GIT_SSH_COMMAND` to inject a specific SSH key, which lets you deploy from a machine that has multiple GitHub accounts configured.

---

## Running Locally

**Prerequisites:** Ruby 3.x, Bundler

```bash
cd jekyll
bundle install
bundle exec jekyll serve --livereload
```

Open **http://localhost:4000** in your browser. The site hot-reloads when you save files.

---

## Adding a Blog Post

Create `jekyll/_posts/YYYY-MM-DD-your-title.md`:

```markdown
---
layout: post
title: "Your Post Title"
date: 2025-08-01 10:00:00 +0200
author: Your Name
categories: [Routes]
tags: [cycling, madrid]
excerpt: "Short summary shown on blog cards."
image: https://images.unsplash.com/photo-XXXXXXXXXX?w=1400&q=80
---

Your post content here in Markdown...
```

Then deploy:

```bash
python deploy.py -m "new post: your title"
```

---

## Adding a Tour

Create `jekyll/_tours/your-tour-name.md`:

```markdown
---
layout: tour
title: "Your Tour Name"
tagline: "One-line description"
image: https://images.unsplash.com/photo-XXXXXXXXXX?w=1400&q=80
duration: "2 hours"
distance: "10 km"
difficulty: Easy        # Easy | Moderate | Challenging
price: 30
group_size: "Max 12"
language: "English, Spanish"
includes:
  - Bike & helmet
  - Expert guide
  - Water
---

Tour description in Markdown...
```

---

## Deploy Script Options

```bash
python deploy.py                            # auto commit message + push
python deploy.py -m "add new tour"         # custom commit message
python deploy.py -k ~/.ssh/other_key       # override SSH key
python deploy.py -b staging                # push to different branch
```

---

## Lessons Learned (Vibe Coding)

- AI-generated scaffolds are production-quality starting points, not throwaway prototypes
- Describing the *what* clearly ("Madrid bike tours site with blog, tours collection, booking form") gives better results than describing *how*
- Errors become prompts — paste the terminal output and the AI fixes it
- Security matters even in vibe coding: the AI caught and removed an accidentally committed SSH private key before the first push
- Multi-account SSH deployment (`GIT_SSH_COMMAND`) is a real-world problem the AI solved without being asked specifically

---

*Built with ❤️ and AI in Madrid*
