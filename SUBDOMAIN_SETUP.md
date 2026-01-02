# Tuner-G Website - Subdomain Setup Guide

Using `master-tempo.com` subdomain for Tuner-G website.

## 🎯 Recommended Subdomain

**Best Option**: `tunerg.master-tempo.com`

**Alternatives**:
- `tuner.master-tempo.com`
- `app.master-tempo.com`

**Final URLs will be**:
- Landing: `https://tunerg.master-tempo.com`
- Privacy: `https://tunerg.master-tempo.com/privacy.html`
- Contact: `https://tunerg.master-tempo.com/contact.html`

---

## 🚀 Quick Setup (15 minutes)

### Step 1: Deploy to GitHub Pages

```bash
cd /Users/max/Develop/tuner-g/tuner-g-website

git init
git add .
git commit -m "Initial Tuner-G website"
git branch -M main

# Create GitHub repository
gh repo create tuner-g-website --public --source=. --push
```

### Step 2: Enable GitHub Pages

1. Go to repository: `https://github.com/YOUR_USERNAME/tuner-g-website`
2. Click **Settings** → **Pages** (left sidebar)
3. Source: `main` branch, `/ (root)` folder
4. Click **Save**

Wait for initial deployment (1-5 minutes).

### Step 3: Configure DNS (Subdomain)

**A. Log into your domain registrar** (where you manage `master-tempo.com`)

**B. Add DNS Record:**

```
Type:   CNAME
Name:   tunerg
Value:  YOUR_USERNAME.github.io
TTL:    3600 (or default)
```

**Example DNS Configuration:**

| Type  | Name   | Value                          | TTL  |
|-------|--------|--------------------------------|------|
| CNAME | tunerg | YOUR_USERNAME.github.io        | 3600 |

**Common Registrars:**

**GoDaddy:**
1. Domain Settings → Manage DNS
2. Add Record → CNAME
3. Name: `tunerg`, Points to: `YOUR_USERNAME.github.io`

**Namecheap:**
1. Advanced DNS
2. Add New Record → CNAME
3. Host: `tunerg`, Target: `YOUR_USERNAME.github.io`

**Cloudflare:**
1. DNS → Add Record
2. Type: CNAME, Name: `tunerg`, Target: `YOUR_USERNAME.github.io`
3. Proxy status: DNS only (gray cloud)

### Step 4: Configure GitHub Pages Custom Domain

1. Repository Settings → Pages
2. Under "Custom domain", enter: `tunerg.master-tempo.com`
3. Click **Save**
4. Wait for DNS check (can take 5 minutes to 24 hours)
5. Once DNS propagates, enable **"Enforce HTTPS"** checkbox

### Step 5: Add CNAME File to Repository

```bash
cd /Users/max/Develop/tuner-g/tuner-g-website

echo "tunerg.master-tempo.com" > CNAME

git add CNAME
git commit -m "Add custom subdomain"
git push
```

**Important**: The CNAME file tells GitHub Pages which domain to serve.

---

## ✅ Verification

### Check DNS Propagation

```bash
# Check if DNS is configured correctly
dig tunerg.master-tempo.com

# Should show CNAME record pointing to YOUR_USERNAME.github.io
```

**Or use online tool**: https://www.whatsmydns.net/
- Enter: `tunerg.master-tempo.com`
- Type: CNAME
- Should show: `YOUR_USERNAME.github.io`

### Test Website

After DNS propagates:
1. Visit: `https://tunerg.master-tempo.com`
2. All pages should load with HTTPS
3. Navigation should work correctly

**Note**: DNS propagation can take:
- 5 minutes (typical)
- Up to 24 hours (rare)
- Usually works within 1 hour

---

## 📱 Update App Store Connect

Once subdomain is live with HTTPS:

1. Go to https://appstoreconnect.apple.com
2. Select Tuner-G app → App Information
3. Update URLs:
   - **Privacy Policy URL**: `https://tunerg.master-tempo.com/privacy.html`
   - **Support URL**: `https://tunerg.master-tempo.com/contact.html`
4. Click **Save**

---

## 🔧 Troubleshooting

### "DNS check unsuccessful" in GitHub

**Wait**: DNS can take up to 24 hours to propagate
**Check**: Run `dig tunerg.master-tempo.com` to verify CNAME
**Fix**: Ensure CNAME points to `YOUR_USERNAME.github.io` (not the full URL)

### HTTPS not available

**Cause**: DNS hasn't propagated yet
**Solution**: Wait for DNS propagation, then enable "Enforce HTTPS"
**Timeline**: Usually 15-60 minutes after DNS is visible

### Website shows 404

**Check CNAME file**: Should contain only `tunerg.master-tempo.com`
**Check GitHub Pages settings**: Custom domain should match exactly
**Verify DNS**: Run `dig tunerg.master-tempo.com`

### "Domain is already taken"

**Cause**: Another GitHub Pages site uses this domain
**Solution**: Ensure you own the domain and remove it from other repos

---

## 📊 Cost Comparison

| Option | Cost | Notes |
|--------|------|-------|
| **New Domain** | $10-15/year | tunerg.app, tunerg.com, etc. |
| **Subdomain** | $0 | Uses existing master-tempo.com ✅ |

**Savings**: $10-15/year by using subdomain!

---

## 🎯 Alternative Subdomains

If `tunerg` is too specific:

**Generic Options:**
- `app.master-tempo.com` - General app subdomain
- `tools.master-tempo.com` - If you plan more tools
- `tuner.master-tempo.com` - Clear and descriptive

**To change subdomain:**
1. Update DNS CNAME record
2. Update `CNAME` file in repository
3. Update GitHub Pages custom domain setting
4. Update App Store Connect URLs

---

## 🔐 Security & SSL

### HTTPS Certificate

GitHub Pages automatically provides:
- ✅ Free SSL certificate (Let's Encrypt)
- ✅ Automatic renewal
- ✅ Force HTTPS redirect

**No configuration needed** - it just works!

### DNS Security (Optional)

If using Cloudflare:
1. Can enable DDoS protection
2. Web Application Firewall (WAF)
3. Analytics
4. Page Rules

---

## 📝 DNS Record Examples

### Recommended: CNAME (Subdomain)

```
Type:   CNAME
Name:   tunerg
Target: YOUR_USERNAME.github.io
TTL:    3600
```

### Alternative: Apex Domain (Not Recommended)

If you wanted to use `master-tempo.com` directly (not recommended as it conflicts with main site):

```
Type:   A
Name:   @
Value:  185.199.108.153
        185.199.109.153
        185.199.110.153
        185.199.111.153
TTL:    3600
```

**But this would override your main site!** Stick with subdomain.

---

## 🔄 Future Updates

### Adding More Apps

If you add more apps later:

```
tunerg.master-tempo.com     → Tuner-G website
metronome.master-tempo.com  → Future metronome app
chords.master-tempo.com     → Future chord app
```

Each gets its own subdomain pointing to different GitHub Pages repos.

---

## 📋 Quick Reference

**Your Subdomain**: `tunerg.master-tempo.com`

**DNS Configuration**:
```
CNAME: tunerg → YOUR_USERNAME.github.io
```

**CNAME File Content**:
```
tunerg.master-tempo.com
```

**App Store URLs**:
- Privacy: `https://tunerg.master-tempo.com/privacy.html`
- Support: `https://tunerg.master-tempo.com/contact.html`

---

## ✅ Setup Checklist

- [ ] Deploy to GitHub Pages
- [ ] Enable Pages in repository settings
- [ ] Add CNAME DNS record at domain registrar
- [ ] Wait for DNS propagation (check with dig)
- [ ] Configure custom domain in GitHub Pages settings
- [ ] Add CNAME file to repository
- [ ] Wait for DNS check to pass
- [ ] Enable "Enforce HTTPS"
- [ ] Test all pages load correctly
- [ ] Update App Store Connect URLs

**Estimated Time**: 15-30 minutes (excluding DNS propagation wait)

---

## 🎉 Benefits of Subdomain Approach

**Cost**:
- ✅ $0 vs $10-15/year for new domain

**SEO**:
- ✅ Inherits domain authority from master-tempo.com
- ✅ All under same brand umbrella

**Management**:
- ✅ Single domain renewal
- ✅ Centralized DNS management
- ✅ Professional appearance

**Flexibility**:
- ✅ Easy to add more subdomains later
- ✅ Can always buy dedicated domain later if needed

---

**Setup Time**: 15-30 minutes
**Cost Savings**: $10-15/year
**Status**: Ready to configure!

**Next**: Follow steps above to set up `tunerg.master-tempo.com`
