# Tuner-G Website - Quick Start Checklist

## 🚀 5-Minute Setup

### Step 1: Preview Locally (Optional)
```bash
# Open in browser
open index.html
# Or use Python simple server
python3 -m http.server 8000
# Then visit: http://localhost:8000
```

### Step 2: Deploy to GitHub Pages
```bash
cd /Users/max/Develop/tuner-g/tuner-g-website

# Initialize and deploy
git init
git add .
git commit -m "Initial Tuner-G website"
git branch -M main

# Option A: Using GitHub CLI (easiest)
gh repo create tuner-g-website --public --source=. --push

# Option B: Manual
# 1. Create repo at github.com/new
# 2. Then:
git remote add origin https://github.com/YOUR_USERNAME/tuner-g-website.git
git push -u origin main
```

### Step 3: Enable GitHub Pages
1. Go to repository on GitHub
2. Settings → Pages
3. Source: `main` branch, `/ (root)` folder
4. Save

**Your site is live at**: `https://YOUR_USERNAME.github.io/tuner-g-website/`

---

## 🌐 Subdomain Setup (Recommended)

**Using existing domain `master-tempo.com`?**

See **[SUBDOMAIN_SETUP.md](SUBDOMAIN_SETUP.md)** for complete instructions to set up:
- `tunerg.master-tempo.com` (recommended)
- DNS configuration
- CNAME setup
- Cost savings: $10-15/year!

---

## ✅ Essential Configuration (10 minutes)

### 1. Set Up Support Email
Replace `support@tunerg.app` in:
- `contact.html` (line 72)
- `privacy.html` (line 155)

```bash
# Quick find/replace
sed -i '' 's/support@tunerg.app/YOUR_EMAIL/g' contact.html privacy.html

git commit -am "Update support email"
git push
```

### 2. Configure Contact Form
1. Sign up at https://formspree.io (free)
2. Create form, copy form ID
3. Update `contact.html` line 47:
   ```html
   <form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
4. Commit and push

### 3. Update App Store Connect
1. Go to https://appstoreconnect.apple.com
2. Your app → App Information
3. Add URLs:
   - Privacy Policy: `https://YOUR_USERNAME.github.io/tuner-g-website/privacy.html`
   - Support URL: `https://YOUR_USERNAME.github.io/tuner-g-website/contact.html`

---

## 📱 After App Approval (5 minutes)

### Add App Store Badge
1. Download badge from Apple: https://developer.apple.com/app-store/marketing/guidelines/
2. Place in `assets/` folder
3. Update `index.html` (around line 48):
   ```html
   <div class="app-store-badge">
       <a href="https://apps.apple.com/app/idYOUR_APP_ID">
           <img src="assets/app-store-badge.svg" alt="Download on the App Store">
       </a>
   </div>
   ```
4. Commit and push

---

## 🎯 Optional Enhancements

### Custom Domain Setup
**If you own `tunerg.app`:**

1. Add DNS records:
   ```
   Type    Name    Value
   CNAME   www     YOUR_USERNAME.github.io
   A       @       185.199.108.153
   ```

2. Add to repository:
   ```bash
   echo "tunerg.app" > CNAME
   git add CNAME
   git commit -m "Add custom domain"
   git push
   ```

3. GitHub: Settings → Pages → Custom domain → `tunerg.app`
4. Wait for DNS (up to 24 hours)
5. Enable "Enforce HTTPS"

### Add App Icon
```bash
# Export from Xcode, place in assets/
cp ~/path/to/app-icon.png assets/

# Update index.html hero section
# Add before <h1>:
<img src="assets/app-icon.png" alt="Tuner-G" style="width: 120px; margin-bottom: 24px;">

git add assets/app-icon.png index.html
git commit -m "Add app icon"
git push
```

---

## 📋 Pre-Launch Checklist

- [ ] Website deployed and live
- [ ] All pages load correctly (home, privacy, contact)
- [ ] Support email configured and tested
- [ ] Contact form submissions working
- [ ] Privacy Policy URL added to App Store Connect
- [ ] Support URL added to App Store Connect
- [ ] Mobile responsive (test on phone)
- [ ] No broken links
- [ ] HTTPS enabled
- [ ] Fast loading (< 2 seconds)

---

## 🆘 Troubleshooting

**Site not loading?**
- Wait 5 minutes after enabling Pages
- Check Settings → Pages for deployment status

**404 errors?**
- Verify all file names are lowercase
- Check relative paths in links

**Form not working?**
- Verify Formspree form ID
- Check email in Formspree settings

**Slow loading?**
- Hard refresh: Cmd+Shift+R (Mac) / Ctrl+F5 (Windows)
- Check browser console for errors

---

## 📚 Documentation

- **README.md** - Project overview
- **DESIGN_SPEC.md** - Complete design documentation
- **DEPLOYMENT_GUIDE.md** - Detailed deployment steps
- **PROJECT_SUMMARY.md** - Full project summary

---

## 🎉 You're Done!

**Live Site**: `https://YOUR_USERNAME.github.io/tuner-g-website/`

**Next**: Submit app to App Store with privacy policy URL!

---

**Questions?** Check the documentation files above or:
- GitHub Pages: https://docs.github.com/en/pages
- Formspree: https://help.formspree.io

**Deployment Time**: ~15 minutes
**Status**: Ready to launch! 🚀
