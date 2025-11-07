# Phone-Only Rhinoplasty Landing Page

A fast, conversion-optimized, phone-only landing page for Dr. Dhir's rhinoplasty practice. All CTAs trigger phone calls - no forms, no external links, no widgets.

## Features

- ✅ **Phone-only**: All CTAs use `tel:` links
- ✅ **Sticky call button**: Always visible at the top
- ✅ **Hero bubble CTA**: Above the fold with clear call prompts
- ✅ **Responsive**: Mobile-first design, perfect on all devices
- ✅ **Fast**: Single HTML file with inline CSS/JS, local images
- ✅ **Accessible**: WCAG compliant, proper ARIA labels
- ✅ **SEO**: Configured for paid traffic (noindex, nofollow)
- ✅ **Analytics ready**: GTM and GA4 event tracking hooks

## File Structure

```
Dhir-phone-lp/
├── index.html          # Main landing page (single file)
├── assets/             # Local image files
│   ├── logo.png
│   ├── hero-image.jpg
│   └── gallery-1.jpg
└── README.md           # This file
```

## Quick Start

1. Open `index.html` in a web browser
2. All phone links are configured to call `(310) 780-1082` by default
3. Test on mobile device for best experience

## Configuration

### Changing the Phone Number

**Default number**: `+1 (310) 780-1082`

To change the default phone number, edit the JavaScript constants in `index.html`:

```javascript
const DEFAULT_PHONE = '+13107801082';  // E.164 format (no spaces, dashes, or parentheses)
const DEFAULT_PHONE_DISPLAY = '(310) 780-1082';  // Pretty format for display
```

**Using URL parameter**: You can override the phone number via URL parameter:

- `?tel=+13107801082` - Full E.164 format
- `?tel=(310)%20780-1082` - Formatted number (URL encoded)
- `?tel=3107801082` - 10 digits (automatically adds +1)

The script will:
1. Strip all non-digits
2. If 10 digits, prefix with `+1`
3. Format for display as `(XXX) XXX-XXXX`

### Enabling CallRail

CallRail is disabled by default. To enable:

1. Open `index.html`
2. Find the `<body>` tag at the top
3. Change `data-callrail="false"` to `data-callrail="true"`

```html
<body data-callrail="true">
```

4. Uncomment and configure the CallRail script at the bottom of the file (around line 680):

```javascript
if (useCallRail) {
  // Add your CallRail script here
  // Example:
  // (function(w,d,t,r,u){var f,n,i;w[u]=w[u]||[],f=function(){var o={ti:"YOUR_TRACKING_ID"};o.q=w[u],w[u]=new UET(o),w[u].push("pageLoad")},n=d.createElement(t),n.src=r,n.async=1,n.onload=n.onreadystatechange=function(){var s=this.readyState;s&&s!=="loaded"&&s!=="complete"||(f(),n.onload=n.onreadystatechange=null)},i=d.getElementsByTagName(t)[0],i.parentNode.insertBefore(n,i)})(window,document,"script","//bat.bing.com/bat.js","uetq");
}
```

When enabled, phone numbers will be wrapped in `<span class="cr-phone">` tags for CallRail tracking.

### Changing the Hero Image

1. Replace `assets/hero-image.jpg` with your new image
2. Keep the same filename, OR
3. Update the `background-image` URL in the CSS (around line 100):

```css
.hero::before {
  background-image: url('assets/your-new-image.jpg');
}
```

**Image recommendations**:
- Format: JPEG or WebP
- Size: 1200-2000px width
- File size: < 300KB for best performance
- Aspect ratio: 16:9 or 3:2 works well

### Updating Brand Colors

Edit the CSS variables at the top of the `<style>` block (around line 20):

```css
:root {
  --brand-900: #1a1a2e;      /* Dark text */
  --brand-700: #2d3561;      /* Medium dark */
  --accent-600: #00a8a8;     /* Primary accent (teal) */
  --accent-700: #008b8b;     /* Accent hover */
  --muted: #6b7280;          /* Secondary text */
  --bg: #ffffff;             /* Background */
  --bg-light: #f8f9fa;       /* Light background */
  --ring: #00a8a8;           /* Focus ring */
}
```

## Testing Checklist

### Functionality

- [ ] All call buttons trigger phone dialer on mobile
- [ ] Phone number displays correctly: `(310) 780-1082`
- [ ] URL parameter `?tel=+13107801082` works
- [ ] URL parameter `?tel=(310)%20780-1082` works
- [ ] URL parameter `?tel=3107801082` works (10 digits)
- [ ] Sticky bar remains visible when scrolling
- [ ] Sticky bar shows shadow when scrolled
- [ ] Page works with JavaScript disabled (basic functionality)
- [ ] All images load correctly
- [ ] Logo displays in sticky bar

### Mobile Testing

- [ ] Test on iPhone (Safari)
- [ ] Test on Android (Chrome)
- [ ] Hero section visible above the fold on iPhone 13/15
- [ ] Call buttons are at least 44px tall (tap target)
- [ ] Text is readable without zooming
- [ ] No horizontal scrolling
- [ ] Sticky bar call button is tappable without scrolling

### Desktop Testing

- [ ] Layout looks good on 1920x1080
- [ ] Layout looks good on 1366x768
- [ ] Call buttons work (opens default phone app)
- [ ] Hover states work on buttons
- [ ] Focus states visible when tabbing

### Accessibility

- [ ] All images have alt text
- [ ] All call buttons have aria-label attributes
- [ ] Color contrast ≥ 4.5:1 for text
- [ ] Focus outlines visible on all interactive elements
- [ ] Page is navigable with keyboard only
- [ ] Screen reader announces call buttons correctly

### Performance

- [ ] Lighthouse Performance ≥ 95
- [ ] Lighthouse Accessibility ≥ 95
- [ ] Lighthouse Best Practices ≥ 95
- [ ] Lighthouse SEO ≥ 90
- [ ] No external CSS/JS/fonts loaded
- [ ] Images are optimized (< 300KB each)

### Link Validation

- [ ] **NO** `href` values start with `http://` or `https://`
- [ ] **NO** `href` values start with `/` (relative paths)
- [ ] **ALL** `href` values start with `tel:`
- [ ] All links point to the same phone number

### Analytics (if configured)

- [ ] GTM dataLayer events fire on call button clicks
- [ ] GA4 events fire on call button clicks (if gtag exists)
- [ ] CallRail wraps phone numbers (if enabled)

## Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Safari (latest)
- ✅ Firefox (latest)
- ✅ Mobile Safari (iOS 12+)
- ✅ Chrome Mobile (Android 8+)

## Analytics Integration

The page includes hooks for Google Tag Manager and Google Analytics. Events fire automatically when call buttons are clicked:

**Google Tag Manager**:
```javascript
dataLayer.push({
  event: 'tel_click',
  tel: '+13107801082'
});
```

**Google Analytics**:
```javascript
gtag('event', 'click_to_call', {
  value: 1
});
```

These only fire if `dataLayer` or `gtag` are already present on the page (loaded via GTM/GA4).

## Content Guidelines

The page uses compliant, neutral language:
- ✅ "Board-certified surgeon"
- ✅ "Natural-looking results"
- ✅ "Personalized treatment plans"
- ✅ "Consultation"
- ❌ No exaggerated claims
- ❌ No surgery promises
- ❌ No before/after claims in copy

## Troubleshooting

### Phone links don't work on desktop
- This is expected - desktop browsers may not have a default phone app
- Test on actual mobile devices for real functionality

### Images not loading
- Check that `assets/` folder exists in the same directory as `index.html`
- Verify image filenames match exactly (case-sensitive)
- Check browser console for 404 errors

### CallRail not tracking
- Verify `data-callrail="true"` on `<body>` tag
- Check that CallRail script is uncommented and configured
- Verify phone numbers are wrapped in `<span class="cr-phone">` tags (inspect element)

### Phone number format incorrect
- Check that URL parameter is properly formatted
- Verify JavaScript phone normalization logic
- Check browser console for errors

## Deployment

1. Upload `index.html` to your web server
2. Upload `assets/` folder to the same directory
3. Ensure file permissions allow reading
4. Test on mobile device
5. Verify phone links work

**Recommended hosting**:
- Any static hosting (Netlify, Vercel, GitHub Pages)
- CDN for faster global delivery
- HTTPS required for best mobile experience

## Support

For issues or questions:
1. Check this README
2. Review browser console for errors
3. Test with JavaScript disabled to isolate issues
4. Validate HTML/CSS with online validators

## License

Internal use only - Dr. Dhir practice.


# dhit-phone-lp
# dhit-phone-lp
