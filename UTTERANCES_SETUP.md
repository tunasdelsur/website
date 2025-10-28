# Utterances Comments Setup Guide

## ✅ Implementation Complete!

The Utterances commenting system has been integrated into your Hugo blog. Comments will automatically appear at the end of all blog posts in both English and Portuguese sections.

## 🔧 Final Configuration Required

To activate comments, you need to complete these steps:

### Step 1: Choose Your Comments Repository

Decide which GitHub repository will store the comments as Issues:
- **Option A:** Use this website's repository (if it's public)
- **Option B:** Create a separate public repository for comments

### Step 2: Install Utterances GitHub App

1. Go to https://github.com/apps/utterances
2. Click **"Install"**
3. Select the repository you chose in Step 1
4. Grant permissions (the app needs access to create Issues)

### Step 3: Configure Your Repository

Edit `config/_default/params.yaml` and update line 69:

```yaml
repo: "YOUR-USERNAME/YOUR-REPO-NAME"
```

**Example:**
```yaml
repo: "fredericovelho/tunasdelsur-comments"
```

### Step 4: Enable GitHub Issues

Make sure your chosen repository has Issues enabled:
1. Go to your repository on GitHub
2. Click **Settings** tab
3. Scroll to **Features** section
4. Ensure **Issues** checkbox is checked

### Step 5: Test It!

1. Build and serve your site locally:
   ```bash
   hugo server
   ```

2. Navigate to any blog post (e.g., `/post/get-started/`)

3. You should see the comments section at the bottom

4. Try posting a test comment - it will create a GitHub Issue automatically!

## 📋 How It Works

- **Each blog post** gets its own GitHub Issue based on the URL pathname
- **First comment** on a post automatically creates the Issue
- **Comments are stored** as comments on that GitHub Issue
- **Theme automatically matches** your site's light/dark mode preference
- **Users must log in** with GitHub to comment (prevents spam)
- **You can moderate** comments directly on GitHub Issues
- **Multilingual support** - Works on both English (`/en/post/`) and Portuguese (`/pt/post/`) blog posts
- **Translated headings** - "Comments" in English, "Comentários" in Portuguese

## 🎨 Customization Options

You can customize the comments behavior in `config/_default/params.yaml`:

```yaml
comments:
  provider: utterances
  utterances:
    repo: "username/repo"              # Your GitHub repository
    issue_term: pathname               # How to map posts to issues (pathname, title, url, etc.)
    theme: preferred-color-scheme      # Theme (automatically matches site theme)
    label: "💬 comments"               # Label added to GitHub Issues
    crossorigin: anonymous             # Security setting
```

### Styling

The comments section automatically matches your Hugo Blox theme:
- Uses the same `prose` typography classes as your content
- Adapts to light and dark modes automatically
- Follows the emerald theme color scheme
- Uses proper spacing (`mt-16 sm:mt-20`) to match other sections

### Available Themes:
- `preferred-color-scheme` - Matches user's system preference (recommended)
- `github-light` - Always light theme
- `github-dark` - Always dark theme
- `github-dark-orange`, `icy-dark`, `dark-blue`, `photon-dark`, etc.

### Issue Term Options:
- `pathname` - Uses URL path (recommended, most reliable)
- `url` - Uses full URL
- `title` - Uses page title
- `og:title` - Uses Open Graph title

## 🌐 Multilingual Behavior

**Important:** Each language version of a post has its own separate comment thread:
- English posts (`/en/post/example/`) will have their own GitHub Issue
- Portuguese posts (`/pt/post/example/`) will have a separate GitHub Issue

This is because Utterances uses the URL pathname to create Issues. If you want all language versions to share the same comments, you would need to use `issue_term: title` instead of `pathname` in the config (and ensure post titles are identical across languages).

## 🚫 Disabling Comments on Specific Posts

To disable comments on a specific blog post, add to its front matter:

```yaml
---
title: My Post
comments: false
---
```

## 🔍 Troubleshooting

**Comments not showing?**
- Check that `repo` is set in `config/_default/params.yaml`
- Verify Utterances app is installed on your repository
- Ensure the repository is public
- Check that GitHub Issues are enabled

**Getting permission errors?**
- Make sure Utterances app has access to the repository
- Repository must be public for Utterances to work

**Want to see all comments?**
- Go to your GitHub repository
- Click on the **Issues** tab
- All comments appear as Issues with the "💬 comments" label

## 📚 Additional Resources

- [Utterances Official Site](https://utteranc.es/)
- [Utterances GitHub](https://github.com/utterance/utterances)
- [Hugo Blox Documentation](https://docs.hugoblox.com/)

---

**Note:** Comments will only appear on posts (content in `/content/*/post/`), not on other page types like publications, events, or the home page.

