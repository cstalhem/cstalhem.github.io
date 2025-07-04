# HTML Structure Improvement Recommendations

Based on analysis of the Hugo site at http://localhost:1313, here are the key issues and recommendations for improving HTML structure, accessibility, and best practices.

## Critical Issues

### 1. **Multiple H1 Tags** ✗
**Issue:** There are two H1 tags on the homepage:
- "Carl's Blog" (header/banner)
- "Latest posts" (main content)

**Fix:** Use proper heading hierarchy:
- `<h1>Carl's Blog</h1>` (site title, keep as H1)
- `<h2>Latest posts</h2>` (section heading, change to H2)

### 2. **Navigation Structure** ✗
**Issue:** Navigation links are wrapped in `<p>` tags instead of proper navigation markup.

**Fix:** Use semantic navigation:
```html
<nav aria-label="Main navigation">
  <ul>
    <li><a href="/">Home</a></li>
    <li><a href="/posts">Posts</a></li>
    <li><a href="/categories">Categories</a></li>
    <li><a href="/tags">Tags</a></li>
  </ul>
</nav>
```

### 3. **Generic Containers** ✗
**Issue:** Many `<div>` elements should be semantic HTML5 elements.

**Fix:** Use semantic structure:
```html
<article> <!-- for each blog post -->
  <header>
    <h3><a href="...">Post Title</a></h3>
    <time datetime="2025-07-02">Jul 2, 2025</time>
  </header>
  <p>Post excerpt...</p>
  <footer>
    <span>Category: <a href="...">TIL</a></span>
    <span>Tags: <a href="...">#claude-code</a>, ...</span>
  </footer>
</article>
```

## Accessibility Improvements

### 4. **Missing ARIA Labels**
**Fix:** Add proper labeling for screen readers:
```html
<nav aria-label="Main navigation">
<main aria-label="Blog posts">
<section aria-labelledby="latest-posts">
  <h2 id="latest-posts">Latest posts</h2>
```

### 5. **Proper Time Elements**
**Fix:** Use `<time>` elements with `datetime` attributes:
```html
<time datetime="2025-07-02">Jul 2, 2025</time>
```

### 6. **Skip Links**
**Fix:** Add skip navigation for keyboard users:
```html
<a href="#main-content" class="skip-link">Skip to main content</a>
```

## Content Structure Improvements

### 7. **Post Entries as Articles**
**Fix:** Each blog post should be an `<article>` with proper structure:
```html
<article>
  <header>
    <h3><a href="...">Post Title</a></h3>
    <time datetime="...">Date</time>
  </header>
  <p>Post summary</p>
  <footer>
    <p>Filed under: <a href="...">Category</a></p>
    <p>Tags: <a href="...">tag1</a>, <a href="...">tag2</a></p>
  </footer>
</article>
```

### 8. **Proper List Structure for Posts**
**Fix:** Wrap post entries in a list:
```html
<section aria-labelledby="latest-posts">
  <h2 id="latest-posts">Latest posts</h2>
  <ol> <!-- or <ul> if order doesn't matter -->
    <li><article>...</article></li>
    <li><article>...</article></li>
  </ol>
</section>
```

## SEO and Meta Improvements

### 9. **Meta Description**
**Fix:** Ensure each page has a proper meta description.

### 10. **Structured Data**
**Fix:** Consider adding JSON-LD structured data for blog posts.

## Implementation Priority

1. **High Priority:** Fix multiple H1 tags (change "Latest posts" to H2)
2. **High Priority:** Convert navigation to semantic `<nav>` structure
3. **Medium Priority:** Use `<article>` elements for blog posts
4. **Medium Priority:** Add proper `<time>` elements
5. **Low Priority:** Add ARIA labels and skip links

## Files to Modify

Since this is a Hugo site using the Typo theme, the main template files to modify are likely:
- `themes/typo/layouts/_default/baseof.html` (base template)
- `themes/typo/layouts/_default/list.html` (homepage/list template)
- `themes/typo/layouts/partials/header.html` (header/navigation)
- `themes/typo/layouts/partials/post-entry.html` (individual post entries)

**Note:** The most critical fix is changing "Latest posts" from H1 to H2 to establish proper heading hierarchy. This will significantly improve accessibility and SEO compliance.