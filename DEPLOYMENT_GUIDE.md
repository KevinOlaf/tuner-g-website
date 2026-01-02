# Tuner-G Website Deployment Guide

Quick deployment guide for getting the Tuner-G website live on GitHub Pages.

## Prerequisites

- [x] Website files created and tested locally
- [ ] GitHub account
- [ ] Git installed on your machine
- [ ] Support email address ready (e.g., support@tunerg.app)

---

## Deployment Steps

### 1. Create GitHub Repository

```bash
# Navigate to website directory
cd /Users/max/Develop/tuner-g/tuner-g-website

# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial Tuner-G website deployment"

# Create main branch
git branch -M main
```

### 2. Create Remote Repository

**Option A: Using GitHub CLI (Recommended)**
```bash
# Install GitHub CLI if not already installed
brew install gh

# Login to GitHub
gh auth login

# Create repository and push
gh repo create tuner-g-website --public --source=. --push
```

**Option B: Using GitHub Web Interface**
1. Go to https://github.com/new
2. Repository name: `tuner-g-website`
3. Visibility: Public (required for free GitHub Pages)
4. Do NOT initialize with README (we already have one)
5. Click "Create repository"

Then push your local repository:
```bash
git remote add origin https://github.com/YOUR_USERNAME/tuner-g-website.git
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to repository on GitHub
2. Click **Settings** (gear icon)
3. Scroll to **Pages** section (left sidebar)
4. Under "Source":
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**

GitHub will display: "Your site is published at `https://YOUR_USERNAME.github.io/tuner-g-website/`"

**Note**: Initial deployment takes 1-5 minutes.

### 4. Configure Custom Domain (Optional)

If you own a domain (e.g., `tunerg.app`):

**A. Update DNS Settings**

Add these DNS records with your domain provider:

```
Type    Name    Value
CNAME   www     YOUR_USERNAME.github.io
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
```

**B. Configure in GitHub**

1. Repository Settings → Pages
2. Under "Custom domain", enter: `tunerg.app`
3. Click **Save**
4. Wait for DNS check (can take up to 24 hours)
5. Enable "Enforce HTTPS" checkbox once DNS propagates

**C. Add CNAME File**

Create file at root:
```bash
echo "tunerg.app" > CNAME
git add CNAME
git commit -m "Add custom domain"
git push
```

---

## Post-Deployment Configuration

### Update Contact Form

**Option 1: Formspree (Recommended)**

1. Sign up at https://formspree.io (free tier: 50 submissions/month)
2. Create new form, get form ID
3. Update `contact.html`:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
4. Commit and push changes

**Option 2: Netlify Forms (if using Netlify instead)**

1. Deploy to Netlify instead of GitHub Pages
2. Add attribute to form:
   ```html
   <form name="contact" method="POST" data-netlify="true">
   ```

### Set Up Support Email

**Create Email Address**
- Domain email: `support@tunerg.app` (if you have domain)
- Or Gmail: `tunerg.support@gmail.com`

**Update Website**
Replace placeholder in:
- `contact.html` line 72: `<a href="mailto:support@tunerg.app">`
- `privacy.html` line 155: `<a href="mailto:support@tunerg.app">`

```bash
# Find and replace
find . -name "*.html" -type f -exec sed -i '' 's/support@tunerg.app/YOUR_ACTUAL_EMAIL/g' {} +

# Commit changes
git add .
git commit -m "Update support email address"
git push
```

### Add App Store Badge

After app is approved:

1. Get marketing assets from Apple:
   - https://developer.apple.com/app-store/marketing/guidelines/
   - Download "Download on App Store" badge

2. Place badge in `assets/`:
   ```bash
   # Example with SVG
   cp ~/Downloads/app-store-badge.svg assets/
   ```

3. Update `index.html` (around line 48):
   ```html
   <div class="app-store-badge">
       <a href="https://apps.apple.com/app/idYOUR_APP_ID">
           <img src="assets/app-store-badge.svg" alt="Download on the App Store">
       </a>
   </div>
   ```

4. Commit and push:
   ```bash
   git add assets/app-store-badge.svg index.html
   git commit -m "Add App Store download badge"
   git push
   ```

---

## Updating App Store Connect

Once website is live, update App Store Connect:

1. Go to https://appstoreconnect.apple.com
2. Select Tuner-G app
3. Navigate to **App Information**
4. Under **Privacy Policy URL**, enter:
   - GitHub Pages: `https://YOUR_USERNAME.github.io/tuner-g-website/privacy.html`
   - Custom domain: `https://tunerg.app/privacy.html`
5. Under **Support URL**, enter:
   - GitHub Pages: `https://YOUR_USERNAME.github.io/tuner-g-website/contact.html`
   - Custom domain: `https://tunerg.app/contact.html`
6. Click **Save**

---

## Making Updates

### Content Changes

1. Edit files locally
2. Test in browser (`file:///Users/max/Develop/tuner-g/tuner-g-website/index.html`)
3. Commit changes:
   ```bash
   git add .
   git commit -m "Description of changes"
   git push
   ```
4. GitHub Pages auto-deploys (1-5 minutes)

### Privacy Policy Updates

When updating privacy policy:
1. Update "Last Updated" date in `privacy.html`
2. Make content changes
3. Commit with descriptive message
4. Users visiting the page see updated content immediately

---

## Testing Checklist

Before announcing website publicly:

- [ ] All pages load correctly
- [ ] Navigation links work
- [ ] Contact form submits successfully
- [ ] Privacy policy displays completely
- [ ] Mobile responsive (test on phone)
- [ ] Support email address works
- [ ] No broken links or images
- [ ] HTTPS enabled (if using custom domain)
- [ ] Fast loading (< 2 seconds)
- [ ] Readable on different browsers

**Test URLs:**
- Home: `/`
- Privacy: `/privacy.html`
- Contact: `/contact.html`

---

## Troubleshooting

### Site Not Loading
- Wait 5 minutes after enabling Pages
- Check GitHub Actions tab for deployment status
- Verify branch and folder settings

### 404 Errors
- Ensure all links use relative paths
- Check file names are lowercase
- Verify files are committed and pushed

### Custom Domain Not Working
- Wait up to 24 hours for DNS propagation
- Use `dig tunerg.app` to check DNS records
- Ensure CNAME file is in repository root

### Form Not Submitting
- Verify Formspree form ID is correct
- Check form method is POST
- Test with different email addresses

### Styling Issues
- Hard refresh browser (Cmd+Shift+R)
- Check CSS file path is correct
- Verify no typos in class names

---

## Performance Optimization

### After Adding Images

When you add app screenshots or icons:

1. **Optimize Images**
   ```bash
   # Install imagemagick
   brew install imagemagick

   # Resize and compress
   convert app-icon.png -resize 512x512 -quality 85 assets/app-icon.png
   ```

2. **Add Lazy Loading**
   ```html
   <img src="assets/screenshot.png" loading="lazy" alt="Description">
   ```

3. **Use WebP Format**
   ```bash
   # Convert PNG to WebP
   cwebp -q 85 screenshot.png -o screenshot.webp
   ```

---

## Analytics (Optional)

If you want to track visitors (privacy-respecting):

### Plausible Analytics (Recommended)

1. Sign up at https://plausible.io (paid, privacy-focused)
2. Add snippet before `</head>`:
   ```html
   <script defer data-domain="tunerg.app" src="https://plausible.io/js/script.js"></script>
   ```

### CloudFlare Web Analytics (Free)

1. Sign up at https://cloudflare.com
2. Enable Web Analytics
3. Add snippet to all pages

**Note**: Avoid Google Analytics to maintain privacy focus.

---

## Security

### HTTPS
- Automatically enabled by GitHub Pages
- Enforce HTTPS in repository settings
- Custom domains: Enable after DNS propagation

### Content Security Policy (Optional)

Add to `<head>` for enhanced security:
```html
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self'; style-src 'self' 'unsafe-inline'; script-src 'self' https://formspree.io">
```

---

## Backup

### Create Backup
```bash
# Create backup of repository
cd /Users/max/Develop/tuner-g
tar -czf tuner-g-website-backup-$(date +%Y%m%d).tar.gz tuner-g-website/

# Store securely
mv tuner-g-website-backup-*.tar.gz ~/Backups/
```

### GitHub Already Backs Up
- All commits are stored
- Can revert to any previous version
- Clone repository to restore

---

## Support Contacts

### GitHub Pages Documentation
- https://docs.github.com/en/pages

### Domain Configuration
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

### Formspree Support
- https://help.formspree.io

---

## Quick Reference

**Live Site URL** (after deployment):
- GitHub Pages: `https://YOUR_USERNAME.github.io/tuner-g-website/`
- Custom Domain: `https://tunerg.app`

**Repository URL**:
- `https://github.com/YOUR_USERNAME/tuner-g-website`

**Support Email**:
- `support@tunerg.app` (or your configured email)

**Update Command**:
```bash
cd /Users/max/Develop/tuner-g/tuner-g-website
git add .
git commit -m "Your update description"
git push
```

---

**Last Updated**: January 2, 2026
**Deployment Status**: Ready for production
**Estimated Time**: 15-30 minutes (excluding DNS propagation)
