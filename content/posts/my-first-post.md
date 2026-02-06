---
title: Setting Up My First Tech Blog with Hugo and GitHub Pages
date: 2026-02-06T15:01:06Z
tags:
    - hugo
    - github-pages
    - blog
    - tutorial
categories:
    - Setup
---

Hugo + GitHub Pages

## Prerequisites
- Git installed
- A GitHub account
- Hugo installed

## Step 1: Install Hugo
**On Windows:** Download from winget, see [link](https://gohugo.io/installation/windows/) for more details
```
winget install Hugo.Hugo.Extended
```

## Step 2: Create a New Hugo Site

```bash
hugo new site myblog
cd myblog
```

This creates the basic Hugo directory structure:

```
myblog/
├── archetypes/
├── content/      # Your posts go here
├── data/
├── layouts/
├── static/       # Images, CSS, etc.
├── themes/       # Themes folder
└── hugo.toml     # Configuration file
```

## Step 3: Choose and Install a Theme

I chose the [Hugo Stack theme](https://github.com/CaiJimmy/hugo-theme-stack) for its clean design and good documentation support.

Install the theme as a git submodule:

```bash
git submodule add https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack
```

## Step 4: Configure Your Site

Edit `hugo.toml`:

```toml
baseURL = 'https://your-username.github.io/'
languageCode = 'en-us'
title = 'Your Blog Title'
theme = 'hugo-theme-stack'
publishDir = 'docs'  # Important for GitHub Pages!
```

**Important:** Setting `publishDir = 'docs'` is crucial because GitHub Pages only supports deploying from root or `/docs` folder.

## Step 5: Test Locally

```bash
hugo server -D
```

Open `http://localhost:1313` in your browser. You should see your site!

## Step 6: Create GitHub Repository

1. Go to GitHub and create a new repository
2. Name it `your-username.github.io` (replace with your actual username)

## Step 7: Connect Local to GitHub

Initialize git and connect to remote:

```bash
git init
git branch -M main
git add .
git commit -m "Initial blog setup"
```

Add remote repository:

```bash
git remote add origin https://github.com/your-username/your-username.github.io.git
```

## Step 8: Generate and Deploy

Generate the static site:

```bash
hugo
```

This creates your website in the `docs/` folder.

Push to GitHub:

```bash
git add .
git commit -m "Add generated site"
git push -u origin main
```

## Step 9: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**:
   - Branch: `main`
   - Folder: `/docs`
4. Click **Save**

Wait 1-2 minutes for deployment. Your site will be live at `https://your-username.github.io/`!

## Common Issues I Encountered

### Issue 1: 404 Page Not Found

**Problem:** Site showed 404 after deployment.

**Solution:**

- Ensure `publishDir = 'docs'` is set in `hugo.toml`
- Run `hugo` to generate the site
- Check GitHub Pages settings point to `/docs` folder
- Make sure `docs/index.html` exists


## Writing Your First Post

Create a new post:

```bash
hugo new content/posts/my-first-post.md
```

Edit the file and set `draft: false`:

```markdown
---
title: "My First Post"
date: 2026-02-06
draft: false
tags: ["hello"]
---

Your content here...
```

## Publishing Workflow

My typical workflow for new posts:

1. **Create post:** `hugo new content/posts/post-name.md`
2. **Write content** in your favorite editor
3. **Preview locally:** `hugo server -D`
4. **Generate site:** `hugo`
5. **Deploy:**

```bash
git add .
git commit -m "Add new post: post title"
git push
```

Wait 1-2 minutes, and the post is live!
Happy blogging! 

