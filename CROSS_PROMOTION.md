# Cross-Promotion Setup

Cross-promotion links between Beat-Master and Tuner-G apps.

## ✅ Tuner-G Website (Complete)

All three pages now include footer link to Beat-Master:

```html
<p style="margin-top: 8px; font-size: 14px; color: #A8A8A8;">
    Also check out: <a href="https://master-tempo.com" style="color: #33D98C;">Beat-Master</a> - Professional metronome app
</p>
```

**Pages updated:**
- ✅ index.html
- ✅ privacy.html
- ✅ contact.html

---

## 📋 Beat-Master Website (To Do)

Add reverse link in Beat-Master footer to promote Tuner-G:

### HTML Snippet to Add

```html
<p style="margin-top: 8px; font-size: 14px; color: #A8A8A8;">
    Also check out: <a href="https://tunerg.master-tempo.com" style="color: #YOUR_ACCENT_COLOR;">Tuner-G</a> - Precision guitar tuner
</p>
```

**Replace `#YOUR_ACCENT_COLOR`** with Beat-Master's accent color.

### Where to Add

In the **footer section** of:
- Home page
- Privacy policy page
- Contact page
- Any other main pages

### Example Footer Structure

```html
<footer>
    <div class="container">
        <div class="footer-content">
            <div>
                <p class="copyright">&copy; 2026 Beat-Master. All rights reserved.</p>
                <!-- ADD THIS -->
                <p style="margin-top: 8px; font-size: 14px; color: #A8A8A8;">
                    Also check out: <a href="https://tunerg.master-tempo.com" style="color: #YOUR_ACCENT_COLOR;">Tuner-G</a> - Precision guitar tuner
                </p>
            </div>
            <ul class="footer-links">
                <li><a href="privacy.html">Privacy Policy</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </div>
    </div>
</footer>
```

---

## 🎯 Benefits

**User Value:**
- Musicians often need both a metronome AND tuner
- Natural product discovery
- Complete music practice toolkit

**SEO Benefits:**
- Internal linking between related tools
- Improved domain authority
- Better search rankings for music tools

**Brand Synergy:**
- Unified music tools ecosystem
- Professional brand image
- Cross-app user retention

---

## 📱 iOS App Cross-Promotion (Future)

Consider adding in-app promotions:

### In Tuner-G iOS App

Add settings section or about screen:
```swift
Link(destination: URL(string: "https://master-tempo.com")!) {
    HStack {
        Image(systemName: "metronome")
        VStack(alignment: .leading) {
            Text("Beat-Master")
                .font(.headline)
            Text("Professional metronome app")
                .font(.caption)
                .foregroundStyle(.secondary)
        }
    }
}
```

### In Beat-Master iOS App

Add similar link to Tuner-G:
```swift
Link(destination: URL(string: "https://tunerg.master-tempo.com")!) {
    HStack {
        Image(systemName: "tuningfork")
        VStack(alignment: .leading) {
            Text("Tuner-G")
                .font(.headline)
            Text("Precision guitar tuner")
                .font(.caption)
                .foregroundStyle(.secondary)
        }
    }
}
```

---

## 🎨 Design Consistency

**Color Coordination:**

**Tuner-G:**
- Accent: #33D98C (green - in-tune indicator)
- Background: #212123 (dark charcoal)

**Beat-Master:**
- Use your existing accent color
- Maintain consistent design language

**Font Styling:**
- Keep cross-promo text smaller (14px)
- Subtle color (#A8A8A8 for text)
- Accent color for links only

---

## 📊 Tracking (Optional)

### URL Parameters for Analytics

**From Tuner-G to Beat-Master:**
```html
<a href="https://master-tempo.com?ref=tunerg">Beat-Master</a>
```

**From Beat-Master to Tuner-G:**
```html
<a href="https://tunerg.master-tempo.com?ref=beatmaster">Tuner-G</a>
```

Then track `?ref` parameter in analytics to measure cross-promotion effectiveness.

---

## ✅ Checklist

### Tuner-G Website
- [x] Add Beat-Master link to index.html
- [x] Add Beat-Master link to privacy.html
- [x] Add Beat-Master link to contact.html

### Beat-Master Website
- [ ] Add Tuner-G link to home page
- [ ] Add Tuner-G link to privacy page
- [ ] Add Tuner-G link to contact page
- [ ] Add Tuner-G link to other main pages

### iOS Apps (Future)
- [ ] Add Beat-Master link in Tuner-G settings/about
- [ ] Add Tuner-G link in Beat-Master settings/about

---

## 🔄 Maintenance

**Update frequency:**
- Review links quarterly
- Update descriptions if app features change
- Monitor click-through rates (if using tracking params)

**A/B Testing Ideas:**
- Test different link placements
- Try different wording
- Experiment with icon additions

---

**Status**:
- ✅ Tuner-G → Beat-Master links added
- ⏳ Beat-Master → Tuner-G links (pending)

**Next**: Add reverse links to Beat-Master website
