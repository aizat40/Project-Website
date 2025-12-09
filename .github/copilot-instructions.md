# Eco-Match Website - Copilot Instructions

## Project Overview

**Eco-Match** is a sustainability-focused website built from the Poseify modeling agency template. The site promotes upcycling and zero-waste innovations. This is a static, single-page application using HTML5, Bootstrap, and jQuery.

**Tech Stack:**
- HTML5 (9 main pages + 404 error page)
- Bootstrap 5 (customized via `css/bootstrap.min.css`)
- jQuery with custom JavaScript (`js/main.js`)
- Third-party libraries: Animate.css, WOW.js, Owl Carousel, Lightbox

---

## Architecture

### Page Structure
All HTML pages follow the same template pattern:

```
1. Spinner overlay (loading indicator) - controlled by main.js
2. Navigation bar (responsive Bootstrap navbar)
3. Page-specific header (carousel on index, breadcrumbs on others)
4. Main content sections
5. Back-to-top button
6. Asset references (CSS, JS, fonts via CDN)
```

### Key Pages
- **index.html**: Hero carousel with Eco-Match branding, featured content
- **about.html**: Company information and mission
- **service.html**: Service offerings (Smart Material Match, AI Idea Generator, tutorials)
- **contact.html**: Contact form and information
- **team.html**: Team/models showcase
- **testimonial.html**: Customer testimonials (uses Owl Carousel)
- **404.html**: Error page
- **industry.html**, **project.html**: Additional content pages

### Branding & Colors
- **Primary green**: `#89D289` (Eco-Match brand color)
- **Dark background**: Used for navbar with `bg-dark` class
- **Logo**: `img/logo.png` (40px × 90px, contains-fit styling)
- **Fonts**: Josefin Sans (display), Work Sans (body) via Google Fonts

---

## JavaScript Patterns

### Main Functionality (js/main.js)
1. **Spinner Control**: Removes `show` class from `#spinner` on page load (1ms delay)
2. **WOW.js Animation**: Initialized with `new WOW().init()` for scroll-triggered animations
3. **Sticky Navbar**: Adds `position-fixed bg-dark shadow-sm` classes on scroll >0px
4. **Back-to-Top Button**: Shows `.back-to-top` after scrolling 300px, animates to top with easing
5. **Carousel Initialization**: Owl Carousel for testimonials with autoplay, 1000ms speed, 1 item per view

### jQuery Usage Pattern
```javascript
(function ($) {
    "use strict";
    // All code wrapped in IIFE
})(jQuery);
```

### Data Attributes for Animation
- `class="wow fadeInUp"` - WOW.js animation classes
- `data-wow-delay="0.1s"` - Animation delay in increments (0.1s, 0.2s, 0.5s)

---

## CSS Conventions

### Custom Stylesheet (css/style.css)
- Organizes styles by component sections (Spinner, Button, Navbar, Header, etc.)
- Uses CSS variables via Bootstrap (e.g., `var(--bs-white)`, `var(--bs-light)`)
- Responsive breakpoints: `@media (max-width: 991.98px)` for tablet, `@media (min-width: 992px)` for desktop
- Fixed elements use z-index hierarchy: spinner (99999), navbar (9), back-to-top (99)

### Button Classes
- `.btn` - Base styling with transitions and border-radius: 50px
- `.btn-square`, `.btn-sm-square`, `.btn-lg-square` - Icon buttons with fixed dimensions
- `.btn-primary`, `.btn-outline-primary` - Color variants

### Common Class Patterns
- `container-fluid` vs `container` - Full-width or responsive max-width
- `py-5`, `px-5`, `mb-4` - Bootstrap spacing utilities
- `.animated`, `.slideInDown`, `.fadeInUp` - Animate.css classes (paired with WOW.js)

---

## External Libraries Integration

### Bootstrap 5
- Customized minified version (`css/bootstrap.min.css`)
- Navbar components with dropdown menus
- Carousel component for hero sections
- Grid system (`.row`, `.col-md-*`, `.col-lg-*`)

### Animate.css + WOW.js
- Applied together for viewport-triggered animations
- Common animations: `slideInDown`, `fadeInUp`, `fadeInRight`
- Delays increment (0.1s → 0.2s → 0.5s) for staggered effects

### Owl Carousel
- Used for testimonial carousels (`js/owl.carousel.min.js`)
- Config: autoplay, smartSpeed 1000ms, looping, single item, dots navigation
- CSS: `lib/owlcarousel/assets/owl.carousel.min.css`

### Lightbox
- Gallery image viewer (`lib/lightbox/js/lightbox.min.js`)
- CSS: `lib/lightbox/css/lightbox.min.css`

### Font Awesome & Bootstrap Icons
- Font Awesome 7.0.0 via CDN for brand/custom icons
- Bootstrap Icons 1.4.1 for semantic icons
- Usage: `<i class="fa-regular fa-face-smile"></i>` pattern

---

## Development Workflow

### No Build Process
This is a static site with no build step. Changes are applied directly:
1. Edit HTML, CSS, or JS files directly
2. Refresh browser to test
3. Minified library files already in `lib/` directory

### Common Tasks
- **Update branding**: Change `#89D289` color in style.css, update logo in `img/`
- **Add animations**: Use Animate.css classes with WOW.js data attributes
- **Create new page**: Copy existing page template, update navbar links across all pages
- **Modify content**: Edit HTML sections, maintain responsive grid structure

### Testing Approach
- Manual browser testing (no automated tests present)
- Responsive testing needed: Check navbar behavior at mobile breakpoint (991.98px)
- Check spinner dismissal and scroll animations on page load

---

## Navigation & Consistency Requirements

### Menu Structure
All pages must update the navbar's `#navbarCollapse` to set `active` class on current page:
```html
<a href="about.html" class="nav-item nav-link active">About</a> <!-- on about.html -->
```

### Cross-Page Links
Services dropdown links point to multiple pages - maintain this consistency:
- Smart Material Match → service.html
- AI Idea Generator → testimonial.html  
- Expert Tutorials → 404.html

---

## Known Constraints

1. **Template Remnants**: Old Poseify branding titles in some page `<title>` tags - update to "Eco-Match"
2. **Inconsistent Navbar**: index.html has custom logo implementation; other pages use text-based branding
3. **Favicon Inconsistency**: about.html/service.html reference non-existent `img/favicon.ico` instead of `img/logo.png`
4. **Static Content**: No backend or database - all content is hardcoded HTML

---

## Code Quality Notes

- All pages include charset `utf-8` and viewport meta tags
- Spinner and WOW.js initialized on every page for consistency
- CSS uses semantic class naming (e.g., `.service-item`, `.page-header`)
- Escape special characters in HTML entities when needed
