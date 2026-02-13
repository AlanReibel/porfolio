# Performance & SEO Stack Documentation

## ⚡ Web Performance Optimization

### Core Web Vitals

**LCP (Largest Contentful Paint)**
- Target: <2.5 seconds
- Optimization:
  - Lazy load images
  - Preload critical resources
  - Minify CSS/JS
  - Use CDN

**FID (First Input Delay)**
- Target: <100 milliseconds
- Optimization:
  - Break up long JavaScript
  - Code splitting
  - Web Workers for heavy tasks
  - Reduce main thread work

**CLS (Cumulative Layout Shift)**
- Target: <0.1
- Optimization:
  - Reserve space for ads/images
  - Avoid injecting content above
  - Use transform for animations
  - Font-display: swap

### Performance Checklist

```markdown
## Assets
- [ ] Images optimized (WebP, AVIF)
- [ ] Lazy loading for images
- [ ] Font loading optimized
- [ ] CSS/JS minified
- [ ] Code splitting enabled

## Network
- [ ] Gzip/Brotli compression
- [ ] HTTP/2 or HTTP/3
- [ ] CDN configured
- [ ] Caching headers set
- [ ] Service worker

## Rendering
- [ ] Critical CSS inlined
- [ ] JavaScript deferred
- [ ] Preload critical fonts
- [ ] No render-blocking resources
```

### Implementation Examples

**Image Optimization:**
```html
<picture>
  <source srcset="image.avif" type="image/avif">
  <source srcset="image.webp" type="image/webp">
  <img 
    src="image.jpg" 
    alt="Description"
    loading="lazy"
    width="400"
    height="300"
  />
</picture>
```

**Font Loading:**
```css
@font-face {
  font-family: 'Open Sans';
  src: url('font.woff2') format('woff2');
  font-display: swap;
}
```

**Preload & Prefetch:**
```html
<!-- Preload critical resources -->
<link rel="preload" as="script" href="critical.js">
<link rel="preload" as="image" href="hero.webp">

<!-- Prefetch non-critical -->
<link rel="prefetch" href="next-page.js">
```

**Resource Hints:**
```html
<!-- DNS prefetch -->
<link rel="dns-prefetch" href="//cdn.example.com">

<!-- Preconnect -->
<link rel="preconnect" href="//fonts.googleapis.com">
<link rel="preconnect" href="//fonts.gstatic.com" crossorigin>
```

## 🔍 SEO Optimization

### Technical SEO

**Robots.txt:**
```
User-agent: *
Allow: /
Disallow: /admin/
Disallow: /api/

Sitemap: https://example.com/sitemap.xml
```

**Sitemap.xml:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://example.com</loc>
    <lastmod>2025-02-13</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>
</urlset>
```

**Meta Tags:**
```html
<head>
  <!-- Basic -->
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="description" content="Page description">
  <meta name="keywords" content="keyword1, keyword2">
  
  <!-- Open Graph (Social) -->
  <meta property="og:title" content="Title">
  <meta property="og:description" content="Description">
  <meta property="og:image" content="image.jpg">
  <meta property="og:url" content="https://example.com">
  
  <!-- Twitter -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="Title">
  <meta name="twitter:image" content="image.jpg">
  
  <!-- Canonical -->
  <link rel="canonical" href="https://example.com/page">
</head>
```

### Schema Markup

**Article Schema:**
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Article Title",
  "description": "Description",
  "image": "image.jpg",
  "datePublished": "2025-02-13",
  "author": {
    "@type": "Person",
    "name": "Author Name"
  }
}
```

**Organization Schema:**
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Company",
  "url": "https://example.com",
  "logo": "logo.png",
  "sameAs": [
    "https://twitter.com/company",
    "https://linkedin.com/company/company"
  ]
}
```

### On-Page SEO

**Heading Structure:**
```html
<h1>Main Page Topic</h1>
<h2>Subtopic 1</h2>
<h3>Sub-subtopic</h3>
<h2>Subtopic 2</h2>
```

**URL Structure:**
```
✅ Good: example.com/blog/how-to-optimize-seo
❌ Bad:  example.com/post?id=123
```

**Content Optimization:**
```
- Natural keyword usage (1-2% density)
- Readability (short paragraphs, lists)
- Word count (1500+ for guides)
- Internal linking
- Fresh content
```

## 📊 Monitoring & Tools

### Google Tools
- **Google Analytics** - Traffic & behavior
- **Google Search Console** - Indexing & performance
- **PageSpeed Insights** - Performance audit
- **Mobile-Friendly Test** - Mobile usability

### Performance Tools
- **Lighthouse** - Automated audits
- **WebPageTest** - Detailed waterfall
- **GTmetrix** - Recommendations
- **Chrome DevTools** - Real-time debugging

### Monitoring Code

```javascript
// Web Vitals tracking
import { getCLS, getFID, getFCP, getLCP, getTTFB } from 'web-vitals';

const vitals = {
  cls: 0,
  fid: 0,
  fcp: 0,
  lcp: 0,
  ttfb: 0
};

getCLS(metric => { vitals.cls = metric.value; });
getFID(metric => { vitals.fid = metric.value; });
getFCP(metric => { vitals.fcp = metric.value; });
getLCP(metric => { vitals.lcp = metric.value; });
getTTFB(metric => { vitals.ttfb = metric.value; });

// Send to analytics
fetch('/api/vitals', {
  method: 'POST',
  body: JSON.stringify(vitals)
});
```

## 🎯 Performance Budget

```yaml
Bundle Sizes:
  JavaScript: 100 KB
  CSS: 30 KB
  Images: 200 KB
  Fonts: 50 KB

Load Times:
  First Contentful Paint: 1.5s
  Largest Contentful Paint: 2.5s
  Time to Interactive: 3.5s

Metrics:
  Lighthouse Score: >90
  Core Web Vitals: All Green
  Time Budget: <100ms per route
```

---

**Last Updated:** February 13, 2025
