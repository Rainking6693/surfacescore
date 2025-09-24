# Google AdSense Integration Research

## Task Overview
Integrate Google AdSense into surfacescore.com by:
1. Ensuring ads.txt file is properly placed in root directory
2. Adding AdSense script to all HTML pages

## Current State Analysis

### ads.txt File
✅ **ALREADY EXISTS** - Found `ads.txt` in root directory with correct content:
```
google.com, pub-8248403820035955, DIRECT, f08c47fec0942fa0
```

### HTML Files Structure
Found the following HTML files that need AdSense script integration:
- `index.html` (main homepage)
- `about.html` 
- `help.html`
- `case-studies.html`
- `developer-resources.html`
- `privacy.html`
- `safari-optimization-guide.html`

### Current Head Structure Analysis
All HTML files follow a consistent pattern with:
- Comprehensive meta tags for SEO
- Open Graph and Twitter meta tags
- Apple-specific optimizations
- Structured data (JSON-LD)
- CSS and JavaScript includes
- Google Analytics already integrated

### AdSense Script Requirements
Need to add this script to the `<head>` section of each page:
```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-8248403820035955"
     crossorigin="anonymous"></script>
```

### Content Security Policy Considerations
Current CSP in index.html:
```html
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self' 'unsafe-inline' https://www.googletagmanager.com; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:; connect-src 'self' https://www.google-analytics.com; font-src 'self' https://fonts.gstatic.com;">
```

**NEEDS UPDATE** to include AdSense domains:
- `https://pagead2.googlesyndication.com` for script-src
- `https://googleads.g.doubleclick.net` for connect-src
- `https://tpc.googlesyndication.com` for img-src

## Implementation Strategy

1. **ads.txt**: ✅ Already correctly configured
2. **AdSense Script**: Add to all HTML files in the `<head>` section
3. **CSP Update**: Update Content Security Policy to allow AdSense domains
4. **Placement**: Insert script after existing Google Analytics but before closing `</head>` tag

## Files to Modify
- `index.html`
- `about.html`
- `help.html`
- `case-studies.html`
- `developer-resources.html`
- `privacy.html`
- `safari-optimization-guide.html`

## Next Steps
1. Create implementation plan
2. Update all HTML files with AdSense script
3. Update CSP headers
4. Verify implementation