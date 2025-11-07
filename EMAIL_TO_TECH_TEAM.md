Subject: Phone-Only Rhinoplasty Landing Page Ready for PMX Traffic

Hi Team,

The phone-only rhinoplasty landing page is ready to go live for PMX traffic.

**Live URL:** https://dhit-phone-lp.vercel.app/
**GitHub Repo:** https://github.com/shoutgeorge1/dhit-phone-lp

**What's Done:**
✅ Single-page HTML landing page (phone-only, no forms)
✅ All CTAs trigger phone calls via `tel:` links
✅ Mobile-optimized and responsive
✅ Fast loading (single file with inline CSS/JS)
✅ Images hosted locally in `/assets` folder
✅ Ready for CallRail integration

**Action Required - CallRail Setup:**

1. **Enable CallRail** in `index.html`:
   - Change line 557: `<body data-callrail="false">` to `<body data-callrail="true">`

2. **Add CallRail Script** (around line 799):
   - Uncomment the CallRail script placeholder
   - Add your CallRail tracking code

3. **Verify Phone Number Wrapping:**
   - When enabled, all phone numbers will be wrapped in `<span class="cr-phone">` tags
   - Default phone: `(310) 780-1082` (configurable via URL param `?tel=...`)

**Technical Notes:**
- Phone number can be overridden via URL: `?tel=+13107801082`
- All links are `tel:` only (no external links)
- Meta tags set to `noindex, nofollow` (paid traffic only)
- Analytics hooks ready for GTM/GA4

**Files:**
- `index.html` - Main landing page
- `assets/` - Local images (logo, hero, gallery)

Once CallRail is configured, this is ready for PMX traffic. Let me know if you need anything else.

Thanks!

