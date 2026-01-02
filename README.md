# Tuner-G Website

Professional, compact website for Tuner-G iOS guitar tuner app.

## 🎨 Design Specifications

### Color Palette
Color scheme derived from the iOS app's neumorphic design system:

- **Primary Dark Background**: `#212123` (app background)
- **Surface Dark**: `#2C2C2E` (cards, elevated surfaces)
- **Accent Green**: `#33D98C` (in-tune indicator)
- **Text Primary**: `#FFFFFF` (dark mode)
- **Text Secondary**: `#A8A8A8` (dark mode)

### Typography
- **Font Family**: System font stack (-apple-system, BlinkMacSystemFont, Segoe UI)
- **Headings**: 700 weight, tight letter-spacing
- **Body**: 18px base, 1.6 line-height
- **Design Philosophy**: Clean, professional, no AI-generated gradients

## 📁 File Structure

```
tuner-g-website/
├── index.html          # Landing page
├── privacy.html        # Privacy policy (App Store required)
├── contact.html        # Contact form
├── css/
│   └── style.css      # All styles, mobile-first responsive
├── js/
│   └── (empty)        # Reserved for future features
├── assets/
│   └── (empty)        # For app icons, screenshots
└── README.md          # This file
```

## 🚀 Deployment

### GitHub Pages Setup

1. **Create GitHub Repository**
   ```bash
   cd /Users/max/Develop/tuner-g/tuner-g-website
   git init
   git add .
   git commit -m "Initial website commit"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/tuner-g-website.git
   git push -u origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings → Pages
   - Source: Deploy from branch `main`
   - Folder: `/ (root)`
   - Save

3. **Custom Domain / Subdomain**

   **Option A: Use Subdomain (Recommended - Free!)**
   - Use existing domain: `tunerg.master-tempo.com`
   - See **[SUBDOMAIN_SETUP.md](SUBDOMAIN_SETUP.md)** for complete guide
   - **Saves $10-15/year** by using existing domain

   **Option B: Buy New Domain**
   - Add CNAME file with domain: `tunerg.app`
   - Configure DNS with your domain provider
   - **Cost**: $10-15/year

### Alternative: Netlify

1. **Deploy to Netlify**
   ```bash
   # Install Netlify CLI
   npm install -g netlify-cli

   # Deploy
   cd /Users/max/Develop/tuner-g/tuner-g-website
   netlify deploy --prod
   ```

2. **Configuration**
   - Build command: (none - static site)
   - Publish directory: `./`

## 🔧 Customization

### Update Contact Form
Replace form action in `contact.html`:
```html
<!-- Option 1: Formspree (recommended, free tier available) -->
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">

<!-- Option 2: Netlify Forms (if deploying to Netlify) -->
<form name="contact" method="POST" data-netlify="true">
```

### Update Support Email
Replace placeholder email in:
- `contact.html`: Direct email link
- `privacy.html`: Contact information section

### Add App Store Badge
After app submission approval:
1. Get badge from: https://developer.apple.com/app-store/marketing/guidelines/
2. Replace in `index.html`:
   ```html
   <div class="app-store-badge">
       <a href="YOUR_APP_STORE_URL">
           <img src="assets/app-store-badge.svg" alt="Download on App Store">
       </a>
   </div>
   ```

### Add App Icon
1. Export app icon from Xcode Assets catalog
2. Place in `assets/` directory
3. Update `index.html` hero section:
   ```html
   <div class="app-icon">
       <img src="assets/app-icon.png" alt="Tuner-G App Icon">
   </div>
   ```

## 📱 Privacy Policy Compliance

The `privacy.html` file includes:
- ✅ Microphone usage explanation (required for App Store)
- ✅ AdMob non-personalized ads disclosure
- ✅ In-app purchase details
- ✅ No data collection statement
- ✅ UserDefaults API disclosure (CA92.1)
- ✅ Contact information
- ✅ GDPR/CCPA compliance statements

**App Store Connect Requirement:**
Add privacy policy URL: `https://YOUR_DOMAIN/privacy.html`

## 🎯 Features

- **Responsive Design**: Mobile-first, works on all devices
- **Fast Loading**: No frameworks, vanilla HTML/CSS
- **Accessible**: Semantic HTML, ARIA labels where needed
- **SEO Optimized**: Meta tags, Open Graph protocol
- **Professional**: Clean design, no AI-generated gradients
- **App Store Ready**: Privacy policy meets Apple requirements

## 📝 Content Updates

### Landing Page Features
Update features in `index.html` to match final app capabilities.

### Privacy Policy
Update "Last Updated" date when making changes to privacy practices.

### Contact Information
Ensure email addresses are active and monitored.

## 🌐 Browser Compatibility

Tested and compatible with:
- Safari (iOS and macOS)
- Chrome
- Firefox
- Edge

Uses modern CSS features with fallbacks for older browsers.

## 📊 Performance

- **No JavaScript frameworks**: Pure HTML/CSS for instant loading
- **Minimal CSS**: ~400 lines, well-organized
- **No external dependencies**: Self-contained
- **Optimized for mobile**: Fast on all connections

## 🔗 Next Steps

1. [ ] Set up support email: `support@tunerg.app`
2. [ ] Create GitHub repository and deploy
3. [ ] Configure custom domain (optional)
4. [ ] Set up contact form service (Formspree/Netlify)
5. [ ] Add app screenshots to landing page
6. [ ] Add App Store badge after submission approval
7. [ ] Update privacy policy URL in App Store Connect
8. [ ] Test all links and forms

## 📄 License

This website design is part of the Tuner-G project.
