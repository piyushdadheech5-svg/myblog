# Complete Guide: Building & Deploying a Personal Blog
## From Zero to Live Website at piyushdadheech.com

**Created:** December 27, 2025
**Author:** Piyush Dadheech
**Website:** https://piyushdadheech.com

---

# Table of Contents

1. [What We Built](#what-we-built)
2. [Understanding the Tools - The WHY](#understanding-the-tools)
3. [The Architecture - How It All Works Together](#the-architecture)
4. [Our Journey - Step-by-Step What We Did](#our-journey)
5. [Beginner's Tutorial - Create Your Own Blog](#beginners-tutorial)
6. [How to Update Your Blog](#how-to-update)
7. [Troubleshooting Guide](#troubleshooting)

---

# What We Built

We created a **professional personal blog** that is:
- ✅ Live at **https://piyushdadheech.com** (custom domain)
- ✅ Secure with HTTPS (green padlock in browser)
- ✅ Fast and modern (static site)
- ✅ Automatically deployed (push code → site updates)
- ✅ Free to host (no monthly fees)
- ✅ Professional looking (clean design with PaperMod theme)

**Features:**
- Personal bio and introduction
- Blog posts
- Social media links (LinkedIn, X/Twitter)
- Mobile responsive
- Search functionality
- Dark/light mode toggle

---

# Understanding the Tools

## What is Hugo and WHY did we use it?

**What is Hugo?**
- Hugo is a **static site generator**
- It takes simple text files (written in Markdown) and converts them into a complete website
- Think of it as a tool that builds websites automatically from templates and content

**Why Hugo?**
- ✅ **Fast:** Builds websites in milliseconds
- ✅ **Simple:** Write blog posts in plain text (Markdown)
- ✅ **Free:** Completely open source
- ✅ **Secure:** No database = no security vulnerabilities
- ✅ **Popular:** Large community, many themes available

**The Alternative:**
- We could use WordPress, but it requires a database, hosting costs money, slower, and more complex to maintain
- Hugo sites are just HTML/CSS/JS files = simpler, faster, free to host

---

## What is Git and GitHub and WHY did we need it?

**What is Git?**
- **Version control system** - like "track changes" for your entire website
- Keeps history of every change you make
- Allows you to undo mistakes, see what changed when

**What is GitHub?**
- A website that **stores your code online** (like Google Drive for code)
- Owned by Microsoft
- Free for public projects

**Why did we need GitHub?**
- ✅ **Backup:** Your code is safely stored in the cloud
- ✅ **Deployment:** Netlify watches your GitHub repository and auto-deploys when you push changes
- ✅ **Version History:** See every change you've ever made
- ✅ **Collaboration:** Others can contribute if needed
- ✅ **Industry Standard:** This is how professional developers work

**The Flow:**
1. You make changes to your blog locally (on your computer)
2. You "commit" (save) those changes with git
3. You "push" (upload) to GitHub
4. Netlify automatically detects the changes and rebuilds your site
5. Your website updates automatically (30-60 seconds later)

---

## What is Netlify and WHY did we use it?

**What is Netlify?**
- A **hosting platform** for static websites
- Provides free hosting, automatic deployments, SSL certificates, and more
- Industry-leading platform used by millions of websites

**Why Netlify?**
- ✅ **Free:** No cost for personal blogs
- ✅ **Automatic Deployment:** Connects to GitHub, auto-deploys on every push
- ✅ **Free SSL:** Automatic HTTPS certificates (the green padlock)
- ✅ **Fast CDN:** Your site loads quickly worldwide
- ✅ **Custom Domains:** Use your own domain (piyushdadheech.com)
- ✅ **Easy:** Simple interface, great documentation

**Alternatives:**
- **Vercel:** Similar to Netlify (also excellent)
- **GitHub Pages:** Free but more limited features
- **Traditional Hosting (Bluehost, etc.):** Costs money, requires server management

**Why Netlify won:**
- Best combination of ease-of-use and features
- Excellent free tier
- Automatic SSL certificate provisioning
- Great Hugo support

---

## What is DNS and Domain Names?

**What is a Domain Name?**
- Your website address: `piyushdadheech.com`
- Like a street address for your website
- Costs ~$10-15/year to own

**What is DNS (Domain Name System)?**
- **DNS = Phone book of the internet**
- Converts human-readable names (`piyushdadheech.com`) into computer addresses (IP: `75.2.60.5`)
- When someone types your domain, DNS tells their browser where to find your website

**How DNS Works:**
1. User types `piyushdadheech.com` in browser
2. Browser asks DNS: "Where is this website?"
3. DNS responds: "It's at IP address 75.2.60.5"
4. Browser connects to that IP (Netlify's servers)
5. Netlify serves your website

**What are DNS Records?**
- **A Record:** Points domain to an IP address (like `piyushdadheech.com` → `75.2.60.5`)
- **CNAME Record:** Points one domain to another (like `www.piyushdadheech.com` → `comforting-rolypoly-87d4a4.netlify.app`)
- **NS Records (Nameservers):** Tell the world which DNS provider manages your domain

**Why did we configure DNS?**
- To connect your custom domain (`piyushdadheech.com`) to Netlify's servers
- Without DNS configuration, typing your domain wouldn't know where to find your website

---

## What is Cloudflare?

**What is Cloudflare?**
- **Domain registrar:** Where you bought `piyushdadheech.com`
- **CDN provider:** Can speed up websites (we didn't use this feature)
- **DNS provider:** Manages your DNS records

**Why Cloudflare?**
- You bought the domain there
- It's a reputable registrar
- Provides DNS management interface

---

## What is SSL/HTTPS?

**What is SSL/HTTPS?**
- **HTTPS = Secure version of HTTP** (the protocol browsers use to load websites)
- **SSL Certificate = Digital ID card** that proves your website is authentic
- Encrypts data between visitor and website

**Why is it important?**
- ✅ **Security:** Protects visitor data from hackers
- ✅ **Trust:** Browsers show green padlock, users trust your site
- ✅ **SEO:** Google ranks HTTPS sites higher
- ✅ **Required:** Many browsers warn users about non-HTTPS sites

**How we got it:**
- Netlify provides free SSL certificates from **Let's Encrypt**
- Automatically renews every 3 months
- Zero cost, zero maintenance

---

# The Architecture

## How All the Pieces Work Together

```
┌─────────────────────────────────────────────────────────────┐
│                    YOUR LOCAL COMPUTER                       │
│                                                              │
│  ┌────────────────────────────────────────────┐             │
│  │         Hugo Blog Files                     │             │
│  │  - content/ (blog posts)                   │             │
│  │  - hugo.toml (configuration)               │             │
│  │  - themes/PaperMod (design)                │             │
│  │  - layouts/ (custom templates)             │             │
│  └────────────────────────────────────────────┘             │
│                        │                                     │
│                        │ git add, commit                     │
│                        ▼                                     │
│  ┌────────────────────────────────────────────┐             │
│  │          Local Git Repository              │             │
│  │    (tracks all your changes)               │             │
│  └────────────────────────────────────────────┘             │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              │ git push
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                         GITHUB                               │
│              (Code Storage in the Cloud)                     │
│                                                              │
│  Repository: piyushdadheech5-svg/myblog                     │
│  - Stores all your code                                     │
│  - Keeps version history                                    │
│  - Backs up everything                                      │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              │ Webhook (auto-trigger)
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                        NETLIFY                               │
│                  (Build & Hosting Platform)                  │
│                                                              │
│  1. Detects new push to GitHub                              │
│  2. Downloads your code                                     │
│  3. Runs: hugo --gc --minify                                │
│  4. Generates static HTML/CSS/JS                            │
│  5. Deploys to CDN (global servers)                         │
│  6. Issues SSL certificate                                  │
│                                                              │
│  Your site is now live!                                     │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              │ Serves website
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    CLOUDFLARE DNS                            │
│                                                              │
│  DNS Records:                                               │
│  piyushdadheech.com → 75.2.60.5 (Netlify)                  │
│  www.piyushdadheech.com → netlify.app (Netlify)            │
└─────────────────────────────┬───────────────────────────────┘
                              │
                              │ DNS lookup
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                      VISITOR'S BROWSER                       │
│                                                              │
│  1. User types: piyushdadheech.com                          │
│  2. DNS resolves to Netlify servers                         │
│  3. Browser loads your website (HTTPS)                      │
│  4. Green padlock shows = secure!                           │
└─────────────────────────────────────────────────────────────┘
```

## The Workflow

**One-time Setup (What we did):**
1. Install Hugo locally
2. Create blog with PaperMod theme
3. Configure settings (title, bio, social links)
4. Create GitHub repository
5. Push code to GitHub
6. Create Netlify account
7. Connect Netlify to GitHub repo
8. Configure build settings
9. Buy domain (piyushdadheech.com)
10. Configure DNS in Cloudflare
11. Provision SSL certificate

**Ongoing Updates (How you'll work):**
1. Write new blog post (Markdown file)
2. Test locally: `hugo server`
3. Commit: `git add . && git commit -m "New post"`
4. Push: `git push`
5. Netlify auto-deploys (~30 seconds)
6. Your website updates automatically!

---

# Our Journey

## Step-by-Step What We Did (With Explanations)

### Phase 1: Local Development

#### Step 1: Started Hugo Server
**Command:** `hugo server --bind 0.0.0.0 --port 1313`

**What this did:**
- Started a local web server on your computer
- Made the blog accessible at `http://localhost:1313`
- Enabled live reload (changes appear instantly)

**Why:**
- Test your blog locally before publishing
- See changes in real-time
- No need to deploy to see updates

---

#### Step 2: Removed GitHub Icon
**File:** `hugo.toml`
**Changed:** Removed the GitHub social icon configuration

**Why:**
- You didn't want to link to a GitHub profile on your blog
- Social icons should only show platforms you actively use

---

#### Step 3: Changed Twitter to X Icon
**File:** `hugo.toml`
**Changed:** `name = "twitter"` → `name = "x"`
**URL:** Updated to `https://x.com/Piyush92m`

**Why:**
- Twitter rebranded to X
- PaperMod theme supports X icon
- Keeps branding current

---

#### Step 4: Updated Site Title
**File:** `hugo.toml`
**Changed:** `title = "Piyush's Blog"` → `title = "Piyush Dadheech"`

**Why:**
- Your name is your brand
- More professional than generic "blog" title
- Shows in browser tab and site header

---

#### Step 5: Added Waving Hand Emoji
**File:** `hugo.toml`
**Changed:** `Title = "Hi!"` → `Title = "Hi 👋"`

**Why:**
- Friendly, welcoming touch
- Adds personality
- Modern web design trend

---

#### Step 6: Updated Bio
**File:** `hugo.toml`
**Changed:** Generic bio → "I'm Piyush, endlessly curious, a tad confused, wannabe writer. Welcome to my corner of the internet."

**Why:**
- Personal, authentic voice
- Sets expectations for visitors
- Shows personality and honesty

---

#### Step 7: Customized Footer
**File:** Created `layouts/partials/footer.html`

**What we tried:**
- First attempted to add "Stay curious." to footer
- Created custom footer partial
- Eventually removed it for cleaner design

**Why we created custom layouts:**
- Override theme defaults
- Full control over design
- Customization without modifying theme files

**Why we removed it:**
- Cleaner, simpler design won
- Less is more in web design

---

#### Step 8: Updated Social Links
**File:** `hugo.toml`
**Changed:**
- LinkedIn: `https://www.linkedin.com/in/dadheechpiyush`
- X: `https://x.com/Piyush92m`

**Why:**
- Connect visitors to your professional profiles
- Build your online presence
- Enable networking

---

#### Step 9: Replaced Welcome Post
**File:** `content/posts/my-first-post.md`
**Changed:** Detailed welcome post → Minimal "Watch this space."

**Why:**
- Placeholder until you write real content
- Sets expectation that content is coming
- Cleaner than lorem ipsum or dummy text

---

### Phase 2: Version Control (Git & GitHub)

#### Step 10: Created .gitignore
**File:** `.gitignore`

**What it does:**
- Tells git which files to ignore
- Excludes build files (`public/`), OS files, temporary files

**Why:**
- Don't backup generated files (public folder is rebuilt every time)
- Keep repository clean
- Reduce repository size
- Avoid committing sensitive files

**Key exclusions:**
- `public/` - Generated by Hugo, don't need in version control
- `.hugo_build.lock` - Temporary file
- `*.deb` - Hugo installer (not needed in repo)

---

#### Step 11: Configured Git
**Commands:**
```bash
git config user.name "Piyush Dadheech"
git config user.email "piyushdadheech5@example.com"
```

**Why:**
- Git needs to know who is making changes
- Shows author in commit history
- Professional practice

---

#### Step 12: First Git Commit
**Command:** `git add . && git commit -m "Initial commit..."`

**What this did:**
- Saved a snapshot of all your blog files
- Created version history starting point
- Prepared files for pushing to GitHub

**Why:**
- Version control best practice
- Can revert to this point if needed
- Required before pushing to GitHub

---

#### Step 13: Created GitHub Repository
**Name:** `myblog`
**Visibility:** Public

**Why public?**
- Required for free GitHub Pages (if needed)
- Required for free Netlify hosting
- Open source is fine for a blog (no sensitive data)
- Others can see your code and learn

---

#### Step 14: Pushed to GitHub
**Command:** `git push`

**What this did:**
- Uploaded all your code to GitHub
- Created online backup
- Enabled Netlify to access your code

**Why:**
- Code is now safely backed up in cloud
- Netlify can pull your code to build the site
- Industry standard workflow
- Enables collaboration if needed

---

### Phase 3: Deployment (Netlify)

#### Step 15: Created Netlify Account
**How:** Signed up with GitHub authentication

**Why GitHub authentication?**
- Single sign-on (no new password to remember)
- Automatically connects Netlify to your GitHub account
- Streamlines repository access

---

#### Step 16: Imported Repository to Netlify
**What we did:**
- "Add new site" → "Import from GitHub"
- Selected `myblog` repository
- Branch: `main`

**What this created:**
- Connection between GitHub and Netlify
- Webhook (GitHub notifies Netlify of new pushes)
- Build pipeline

---

#### Step 17: Fixed Build Error (netlify.toml)
**Problem:** Build failed with "hugo: command not found"

**Why it failed:**
- Netlify didn't know Hugo was needed
- No Hugo binary in build environment

**Solution:** Created `netlify.toml`
```toml
[build]
  command = "hugo --gc --minify"
  publish = "public"

[context.production.environment]
  HUGO_VERSION = "0.146.0"
```

**What this file does:**
- Tells Netlify: "Install Hugo version 0.146.0"
- Build command: `hugo --gc --minify` (build optimized site)
- Publish directory: `public` (where Hugo outputs the site)

**Why this approach:**
- Configuration as code (settings in repo, not just UI)
- Reproducible builds
- Anyone can see build configuration

---

#### Step 18: Successful Deployment
**Result:** Site live at `comforting-rolypoly-87d4a4.netlify.app`

**Why random name?**
- Netlify auto-generates subdomain from random words
- Ensures uniqueness
- You can change it or use custom domain

**What happened:**
1. Netlify pulled code from GitHub
2. Installed Hugo 0.146.0
3. Ran `hugo --gc --minify`
4. Generated HTML/CSS/JS in `public/`
5. Deployed to Netlify CDN
6. Site now accessible worldwide

---

### Phase 4: Custom Domain

#### Step 19: Bought Domain
**Domain:** `piyushdadheech.com`
**Registrar:** Cloudflare
**Cost:** ~$10-15/year

**Why buy a domain?**
- Professional brand (your name)
- Easy to remember
- Better than `comforting-rolypoly-87d4a4.netlify.app`
- Investment in personal brand

**Why .com?**
- Most recognized extension
- Professional standard
- Widely trusted

---

#### Step 20: Added Domain to Netlify
**Steps:**
1. Domain management → Add domain
2. Entered `piyushdadheech.com`
3. Netlify verified domain ownership

**What Netlify created:**
- Primary domain: `piyushdadheech.com`
- Automatic redirect: `www.piyushdadheech.com` → `piyushdadheech.com`

**Why Netlify needs domain added:**
- Configure SSL certificate for your domain
- Set up redirects
- Monitor domain health

---

#### Step 21: Configured DNS in Cloudflare
**Records created:**
1. **A Record:** `@` → `75.2.60.5` (Netlify's load balancer)
2. **A Record:** `@` → `99.83.190.102` (Netlify backup)
3. **CNAME Record:** `www` → `comforting-rolypoly-87d4a4.netlify.app`

**Why these records?**
- A records point domain to Netlify's servers (by IP address)
- Two A records for redundancy (if one fails, the other works)
- CNAME for www subdomain
- Proxy status OFF = Netlify handles everything

**Why we couldn't use CNAME for root domain:**
- DNS specification doesn't allow CNAME at root (@)
- Must use A records for apex domain
- Technical limitation of DNS protocol

---

#### Step 22: DNS Propagation Wait
**Time:** ~10-30 minutes

**What happened:**
- DNS changes spread across global DNS servers
- Checked propagation with dnschecker.org
- Saw green checkmarks = fully propagated

**Why it takes time:**
- DNS is distributed worldwide (thousands of servers)
- Each server caches records for a period (TTL)
- Changes propagate gradually
- Can take up to 48 hours (usually much faster)

---

#### Step 23: SSL Certificate Provisioning
**Initial problem:** Certificate provisioning failed

**Why it failed:**
- DNS wasn't fully propagated yet
- Netlify couldn't verify domain ownership

**Solution:**
- Waited for DNS to propagate
- Clicked "Verify DNS configuration"
- Clicked "Provision certificate"

**What Netlify did:**
1. Verified domain points to Netlify (DNS check)
2. Requested certificate from Let's Encrypt
3. Let's Encrypt verified domain ownership (challenge-response)
4. Issued certificate
5. Installed certificate on Netlify CDN
6. Enabled HTTPS

**Why Let's Encrypt?**
- Free SSL certificates
- Automated renewal (every 90 days)
- Trusted by all browsers
- Non-profit that makes web more secure

---

### Final Result

✅ **Website Live:** https://piyushdadheech.com
✅ **HTTPS Enabled:** Green padlock in browser
✅ **Auto-Deploy:** Push to GitHub → Site updates
✅ **Free Hosting:** No monthly costs
✅ **Professional:** Custom domain, secure, fast

---

# Beginner's Tutorial

## Create Your Own Blog (Non-Coder's Guide)

This is a complete, step-by-step guide for someone with **no coding experience** to create their own blog like piyushdadheech.com.

**What you'll need:**
- A computer (Windows, Mac, or Linux)
- Internet connection
- Credit card for domain ($10-15, one-time yearly fee)
- 2-3 hours of time

**What you'll get:**
- Professional blog with your own domain
- Free hosting (no monthly fees)
- HTTPS security
- Ability to write and publish posts anytime

---

### Part 1: Install Required Software

#### 1.1 Install Git

**What is Git?** Version control software (think "track changes" for your website)

**Windows:**
1. Go to: https://git-scm.com/download/win
2. Download the installer
3. Run the installer
4. Click "Next" through all options (defaults are fine)
5. Click "Install"

**Mac:**
1. Open Terminal (Applications → Utilities → Terminal)
2. Type: `git --version` and press Enter
3. If not installed, it will prompt you to install (follow prompts)

**Linux:**
```bash
sudo apt-get update
sudo apt-get install git
```

**Verify installation:**
Open terminal/command prompt and type:
```bash
git --version
```
You should see something like `git version 2.x.x`

---

#### 1.2 Install Hugo

**What is Hugo?** The tool that builds your blog from text files

**Windows:**
1. Go to: https://github.com/gohugoio/hugo/releases
2. Find the latest release
3. Download: `hugo_extended_X.XXX.X_windows-amd64.zip` (replace X with version number)
4. Extract the ZIP file
5. Move `hugo.exe` to `C:\Hugo\bin`
6. Add to PATH:
   - Search Windows for "Environment Variables"
   - Click "Environment Variables"
   - Under "System variables", find "Path"
   - Click "Edit"
   - Click "New"
   - Add: `C:\Hugo\bin`
   - Click OK on all dialogs

**Mac (using Homebrew):**
```bash
brew install hugo
```

Don't have Homebrew? Install it first:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**Linux:**
```bash
sudo snap install hugo
```

**Verify installation:**
```bash
hugo version
```
You should see the version number.

---

### Part 2: Create Your Blog

#### 2.1 Create New Hugo Site

Open terminal/command prompt and run:

```bash
# Go to your home directory
cd ~

# Create new Hugo site
hugo new site my-blog

# Go into the blog directory
cd my-blog
```

**What this did:**
- Created a new folder called `my-blog`
- Set up the basic Hugo structure

---

#### 2.2 Install PaperMod Theme

**What is a theme?** The design/look of your website

```bash
# Initialize git repository
git init

# Add PaperMod theme as submodule
git submodule add https://github.com/adityatelange/hugo-PaperMod themes/PaperMod

# Add theme to git
git add .
```

---

#### 2.3 Configure Your Blog

**Open the file:** `hugo.toml` (in your my-blog folder)

**Replace everything with:**

```toml
baseURL = 'https://example.org/'
languageCode = 'en-us'
title = "Your Name"
theme = 'PaperMod'

[params]
  defaultTheme = "auto"
  ShowReadingTime = true
  ShowShareButtons = false
  ShowPostNavLinks = true
  ShowBreadCrumbs = true
  ShowCodeCopyButtons = true
  ShowWordCount = true

[params.homeInfoParams]
  Title = "Hi 👋"
  Content = "Write your bio here. Who are you? What do you write about?"

[[params.socialIcons]]
  name = "linkedin"
  url = "https://linkedin.com/in/yourprofile"

[[params.socialIcons]]
  name = "x"
  url = "https://x.com/yourhandle"

[menu]
  [[menu.main]]
    identifier = "posts"
    name = "Posts"
    url = "/posts/"
    weight = 10

  [[menu.main]]
    identifier = "archives"
    name = "Archives"
    url = "/archives/"
    weight = 20

  [[menu.main]]
    identifier = "search"
    name = "Search"
    url = "/search/"
    weight = 30

[outputs]
  home = ["HTML", "RSS", "JSON"]
```

**Customize:**
- Change `"Your Name"` to your actual name
- Update the bio in `Content`
- Update social media links (or remove sections you don't need)

---

#### 2.4 Create Your First Post

```bash
hugo new content/posts/my-first-post.md
```

**Open the file:** `content/posts/my-first-post.md`

**Edit to:**

```markdown
+++
date = '2025-12-27T00:00:00Z'
draft = false
title = 'My First Blog Post'
description = 'Welcome to my blog'
tags = ['introduction']
+++

## Hello World!

This is my first blog post.

Write your content here using Markdown.

### What is Markdown?

Markdown is a simple way to format text:

- **Bold text:** `**bold**`
- *Italic text:* `*italic*`
- [Links](https://example.com): `[text](url)`
- Lists: Use `-` or `*`

Easy!
```

---

#### 2.5 Test Your Blog Locally

```bash
hugo server
```

**Open browser and go to:** `http://localhost:1313`

**You should see your blog!**

Press `Ctrl+C` in terminal to stop the server.

---

### Part 3: Publish to Internet

#### 3.1 Create GitHub Account

1. Go to: https://github.com/signup
2. Enter email, password, username
3. Verify email
4. Free account is fine!

---

#### 3.2 Create GitHub Repository

1. Go to: https://github.com/new
2. **Repository name:** `my-blog`
3. **Visibility:** Public
4. **Don't check** "Add README" or ".gitignore"
5. Click "Create repository"

---

#### 3.3 Push Your Code to GitHub

**In your terminal (in the my-blog folder):**

```bash
# Configure git (replace with your info)
git config user.name "Your Name"
git config user.email "your-email@example.com"

# Create .gitignore file
cat > .gitignore << EOF
public/
resources/
.hugo_build.lock
.DS_Store
EOF

# Add all files
git add .

# Create first commit
git commit -m "Initial commit: My blog"

# Add GitHub as remote (replace YOUR-USERNAME)
git remote add origin https://github.com/YOUR-USERNAME/my-blog.git

# Push to GitHub
git branch -M main
git push -u origin main
```

**If it asks for authentication:**
- GitHub will prompt for username/password
- Or create a Personal Access Token at: https://github.com/settings/tokens

**Your code is now on GitHub!** View it at: `https://github.com/YOUR-USERNAME/my-blog`

---

### Part 4: Deploy to Netlify

#### 4.1 Create Netlify Account

1. Go to: https://app.netlify.com/signup
2. Click "Sign up with GitHub"
3. Authorize Netlify

---

#### 4.2 Import Your Site

1. Click "Add new site"
2. Click "Import an existing project"
3. Click "Deploy with GitHub"
4. Find and click your `my-blog` repository
5. **Build settings:**
   - Build command: (leave blank for now)
   - Publish directory: `public`
6. Click "Deploy my-blog"

**It will fail!** That's expected. We need to add configuration.

---

#### 4.3 Fix the Build

**In your terminal (my-blog folder):**

Create `netlify.toml` file:

```bash
cat > netlify.toml << EOF
[build]
  command = "hugo --gc --minify"
  publish = "public"

[context.production.environment]
  HUGO_VERSION = "0.146.0"
EOF
```

**Push this change:**

```bash
git add netlify.toml
git commit -m "Add Netlify configuration"
git push
```

**Netlify will automatically rebuild!**

In 30-60 seconds, your site will be live at: `https://random-name-123456.netlify.app`

---

### Part 5: Add Custom Domain

#### 5.1 Buy a Domain

**Recommended registrars:**
- **Namecheap:** https://www.namecheap.com
- **Porkbun:** https://porkbun.com
- **Cloudflare:** https://www.cloudflare.com/products/registrar/

**Choose a domain:** `yourname.com` or `yourname.me`

**Cost:** ~$10-15/year

**Buy it!** Follow the registrar's checkout process.

---

#### 5.2 Add Domain to Netlify

1. In Netlify, go to your site dashboard
2. Click "Domain management"
3. Click "Add domain"
4. Enter your domain: `yourdomain.com`
5. Click "Verify" → "Add domain"

---

#### 5.3 Configure DNS

**If you bought on Cloudflare:**

1. Go to Cloudflare dashboard
2. Click your domain
3. Click "DNS"
4. Click "Add record"
5. **Add these records:**

**Record 1:**
- Type: A
- Name: @
- IPv4 address: `75.2.60.5`
- Proxy status: OFF (grey cloud)
- Click Save

**Record 2:**
- Type: A
- Name: @
- IPv4 address: `99.83.190.102`
- Proxy status: OFF (grey cloud)
- Click Save

**Record 3:**
- Type: CNAME
- Name: www
- Target: `your-site-name.netlify.app` (from step 4.3)
- Proxy status: OFF (grey cloud)
- Click Save

**If you bought on Namecheap or other registrar:**

1. Go to your domain dashboard
2. Find "Advanced DNS" or "DNS Settings"
3. Add the same A and CNAME records as above

---

#### 5.4 Wait for DNS Propagation

**Time:** 10-60 minutes (usually ~20 minutes)

**Check status:**
1. Go to: https://dnschecker.org
2. Enter your domain
3. Select "A" type
4. Click Search
5. Wait for green checkmarks showing `75.2.60.5`

---

#### 5.5 Enable HTTPS

**In Netlify:**

1. Go to Domain management
2. Scroll to "HTTPS" section
3. Click "Verify DNS configuration"
4. Click "Provision certificate"
5. Wait 1-2 minutes

**Done!** Your site is now live with HTTPS at `https://yourdomain.com`

---

### Part 6: Writing Blog Posts

#### 6.1 Create a New Post

```bash
# In your my-blog folder
hugo new content/posts/my-second-post.md
```

#### 6.2 Edit the Post

Open `content/posts/my-second-post.md` and write your content:

```markdown
+++
date = '2025-12-27T12:00:00Z'
draft = false
title = 'My Second Post'
description = 'Another amazing post'
tags = ['blogging', 'writing']
+++

## This is my second post!

I'm getting the hang of this blogging thing.

Here's what I learned today...
```

#### 6.3 Preview Locally

```bash
hugo server
```

Open: `http://localhost:1313`

See your new post!

#### 6.4 Publish to Website

```bash
# Stop the server (Ctrl+C)

# Save your changes
git add .
git commit -m "Add new blog post"
git push
```

**Wait 30 seconds.** Your post is now live on your website!

---

## Summary of Tools Used

| Tool | Purpose | Cost |
|------|---------|------|
| Hugo | Generate website from text files | Free |
| Git | Track changes to your files | Free |
| GitHub | Store code online, backup | Free |
| Netlify | Host website, auto-deploy | Free |
| Cloudflare/Namecheap | Buy domain, manage DNS | $10-15/year |
| Let's Encrypt | SSL certificate (HTTPS) | Free |

**Total ongoing cost: $10-15/year** (just the domain)

---

# How to Update Your Blog

## Daily Workflow

### Writing a New Post

1. **Create post:**
   ```bash
   hugo new content/posts/my-post-title.md
   ```

2. **Edit the file** with your favorite text editor

3. **Preview:**
   ```bash
   hugo server
   ```
   Open: `http://localhost:1313`

4. **Publish:**
   ```bash
   git add .
   git commit -m "Add new post: My Post Title"
   git push
   ```

5. **Wait 30 seconds** - your post is live!

---

### Editing an Existing Post

1. **Open the file:** `content/posts/post-name.md`

2. **Make changes**

3. **Preview:**
   ```bash
   hugo server
   ```

4. **Publish:**
   ```bash
   git add .
   git commit -m "Update post: Post Name"
   git push
   ```

---

### Changing Site Configuration

**Edit:** `hugo.toml`

**Examples:**
- Change site title
- Update bio
- Add/remove social links
- Change theme settings

**Publish changes:**
```bash
git add hugo.toml
git commit -m "Update site configuration"
git push
```

---

### Adding Images to Posts

1. **Create folder:** `static/images/`

2. **Copy image** to that folder (e.g., `photo.jpg`)

3. **In your post:**
   ```markdown
   ![Description](/images/photo.jpg)
   ```

4. **Publish:**
   ```bash
   git add .
   git commit -m "Add images to post"
   git push
   ```

---

## Markdown Cheat Sheet

```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*
***Bold and italic***

[Link text](https://example.com)

![Image alt text](/images/photo.jpg)

- Bullet point 1
- Bullet point 2
- Bullet point 3

1. Numbered item 1
2. Numbered item 2
3. Numbered item 3

> This is a blockquote
> Great for highlighting quotes

`inline code`

\`\`\`python
def hello():
    print("Hello, world!")
\`\`\`

---

Horizontal line above
```

---

# Troubleshooting Guide

## Common Issues and Solutions

### Issue 1: "hugo: command not found"

**Problem:** Hugo is not installed or not in PATH

**Solution:**
- **Verify installation:** `hugo version`
- **Reinstall Hugo** following installation steps
- **Windows:** Check PATH environment variable includes Hugo

---

### Issue 2: "Theme not found"

**Problem:** PaperMod theme not installed correctly

**Solution:**
```bash
git submodule update --init --recursive
```

Or re-add the theme:
```bash
git submodule add --force https://github.com/adityatelange/hugo-PaperMod themes/PaperMod
```

---

### Issue 3: "Port already in use" when running hugo server

**Problem:** Another process is using port 1313

**Solution:**
```bash
# Use a different port
hugo server --port 1314
```

Or find and kill the process using port 1313:
- **Windows:** `netstat -ano | findstr :1313`
- **Mac/Linux:** `lsof -ti:1313 | xargs kill`

---

### Issue 4: Changes not showing on website after push

**Problem:**
- Git push failed
- Netlify build failed
- Cached browser

**Solution:**

1. **Check git push succeeded:**
   ```bash
   git status
   ```
   Should say "nothing to commit, working tree clean"

2. **Check Netlify build:**
   - Go to Netlify dashboard
   - Click "Deploys"
   - Check if latest deploy succeeded
   - If failed, read error logs

3. **Clear browser cache:**
   - Hard refresh: `Ctrl+Shift+R` (Windows/Linux) or `Cmd+Shift+R` (Mac)

---

### Issue 5: SSL Certificate won't provision

**Problem:** DNS not configured correctly

**Solution:**

1. **Verify DNS records in Cloudflare/registrar:**
   - A record: @ → 75.2.60.5
   - A record: @ → 99.83.190.102
   - CNAME: www → your-site.netlify.app
   - Proxy status: OFF (grey cloud)

2. **Check DNS propagation:**
   - https://dnschecker.org
   - Enter your domain
   - Look for green checkmarks

3. **In Netlify:**
   - Click "Verify DNS configuration"
   - Wait for success
   - Click "Provision certificate"

4. **Wait 10-30 minutes** for DNS to fully propagate

---

### Issue 6: "This site can't be reached"

**Problem:** DNS not configured or not propagated

**Solution:**

1. **Check DNS records** (see Issue 5)

2. **Wait for propagation** (up to 48 hours, usually 30 minutes)

3. **Try:**
   - `http://yourdomain.com` (without https)
   - `https://your-site.netlify.app` (should always work)

---

### Issue 7: Build fails with "Error: unable to locate config file"

**Problem:** Running commands from wrong directory

**Solution:**
```bash
# Make sure you're in the my-blog directory
cd ~/my-blog

# Then run hugo commands
hugo server
```

---

### Issue 8: Images not showing

**Problem:** Wrong path or images not committed

**Solution:**

1. **Verify image location:**
   - Images should be in: `static/images/`
   - Reference in posts as: `/images/filename.jpg`

2. **Commit images:**
   ```bash
   git add static/images/
   git commit -m "Add images"
   git push
   ```

3. **Check image path in markdown:**
   ```markdown
   ![Alt text](/images/photo.jpg)
   ```
   NOT: `![Alt text](static/images/photo.jpg)`

---

### Issue 9: Post not appearing

**Problem:** Post is marked as draft

**Solution:**

**In your post file**, change:
```markdown
+++
draft = true  ← Change this
+++
```

To:
```markdown
+++
draft = false  ← To this
+++
```

Then commit and push.

---

### Issue 10: Site looks broken (no CSS)

**Problem:**
- Wrong baseURL
- Build error

**Solution:**

1. **Check `hugo.toml`:**
   ```toml
   baseURL = 'https://yourdomain.com/'  ← Must match your actual domain
   ```

2. **Rebuild site:**
   ```bash
   # Local test
   hugo server

   # If that works, push to deploy
   git add .
   git commit -m "Fix baseURL"
   git push
   ```

---

## Getting Help

**Resources:**
- **Hugo Documentation:** https://gohugo.io/documentation/
- **PaperMod Theme Docs:** https://github.com/adityatelange/hugo-PaperMod/wiki
- **Netlify Docs:** https://docs.netlify.com/
- **Hugo Discourse Forum:** https://discourse.gohugo.io/

**Debug checklist:**
1. Does it work locally? (`hugo server`)
2. Is code pushed to GitHub? (`git status`)
3. Did Netlify build succeed? (check dashboard)
4. Is DNS configured correctly? (dnschecker.org)
5. Clear browser cache and try again

---

# Conclusion

## What You've Learned

You now understand:
- ✅ Static site generators (Hugo)
- ✅ Version control (Git & GitHub)
- ✅ Continuous deployment (Netlify)
- ✅ DNS and domain management
- ✅ SSL certificates and HTTPS
- ✅ Modern web development workflow

## Your Blog Setup

You have a professional blog that:
- ✅ Costs only $10-15/year (domain)
- ✅ Updates automatically when you push to GitHub
- ✅ Is fast, secure, and reliable
- ✅ You fully own and control

## Next Steps

**Content:**
- Start writing regularly
- Develop your voice
- Share your knowledge and experiences

**Customization:**
- Explore PaperMod theme options
- Customize colors and fonts
- Add custom pages (About, Contact)

**Growth:**
- Share posts on social media
- Engage with readers
- Build your online presence

**Advanced:**
- Add analytics (Google Analytics, Plausible)
- Add comments (Disqus, Utterances)
- SEO optimization
- Newsletter integration

---

## Final Thoughts

Building a blog is just the beginning. The real value comes from:
- **Writing consistently**
- **Sharing your unique perspective**
- **Connecting with readers**
- **Learning and growing**

Your blog is now live at **https://piyushdadheech.com** - the world is waiting to hear what you have to say.

Happy writing! ✍️

---

**Created by:** Piyush Dadheech
**Date:** December 27, 2025
**Built with:** Hugo, GitHub, Netlify, and Claude Code

---

*This guide is comprehensive but web technologies evolve. If you find outdated information, consult the official documentation for each tool.*
