---
name: static-landing-page
description: Guide and best practices for generating fully responsive, static landing pages that can be directly hosted on GitHub Pages without any build steps.
---

# Static Landing Page Generator Skill

Use this skill when asked to create a landing page, marketing site, or app showcase that needs to be deployed easily on GitHub Pages or other static hosting providers, without the overhead of build tools or complex frameworks.

## 1. Core Tech Stack

- **Structure:** Semantic HTML5 (`index.html`, `privacy_policy.html`, etc.).
- **Styling:** Tailwind CSS integrated directly via CDN. No `npm`, `node_modules`, or build steps are required.
- **Interactivity:** Vanilla JavaScript. Do not use React, Vue, Svelte, or Flutter Web unless explicitly requested. 
- **Typography:** Google Fonts (e.g., `Inter`, `Outfit`, `Roboto`).
- **Icons & Graphics:** SVG graphics (preferred for crisp scaling, like QR codes) and local image assets.

## 2. Setup & Configuration

Include Tailwind via CDN and configure the theme directly in the `<head>` of the HTML document. This allows full customization of colors and fonts while keeping the project strictly static.

```html
<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Outfit:wght@600;700&display=swap" rel="stylesheet">

<!-- Tailwind CSS via CDN -->
<script src="https://cdn.tailwindcss.com"></script>

<!-- Tailwind Custom Configuration -->
<script>
    tailwind.config = {
        theme: {
            extend: {
                colors: {
                    background: '#0e1513',
                    primary: '#10b981',
                },
                fontFamily: {
                    sans: ['Inter', 'sans-serif'],
                    display: ['Outfit', 'sans-serif'],
                }
            }
        }
    }
</script>
```

## 3. Design Aesthetics & Best Practices

- **Rich Aesthetics:** Create a "premium" feel. Use dark modes (e.g., `#0e1513`), dynamic gradients (`text-gradient`, `radial-gradient` backgrounds), and vibrant primary colors.
- **Glassmorphism:** Use translucent backgrounds with backdrop blurs for navbars and cards to create depth.
  - *Example:* `bg-white/5 border border-white/10 backdrop-blur-md`
- **Condense Content:** Limit maximum width of the main content so it doesn't stretch too wide on desktop. `max-w-5xl` or `max-w-6xl` paired with generous horizontal padding (`px-8 sm:px-16 lg:px-24`) works best.
- **Micro-Animations:** Add CSS keyframes for floating elements, and hover states with translation (`hover:-translate-y-1 transition-transform`) for interactive elements.

## 4. Vanilla JS Interactivity

Use minimal Vanilla JS to bring the page to life. Standard implementations include:
- **Scroll Animations:** An `IntersectionObserver` or a simple scroll event listener to add `.active` classes to elements as they scroll into view (creating fade-up effects).
- **Sticky Navbar:** Adding a shadow or background blur to the navbar when the user scrolls down from the top.

## 5. File & Asset Structure

Since this is for GitHub Pages:
- All paths must be relative (e.g., `href="privacy_policy.html"`, `src="assets/images/logo.png"`).
- Never use absolute server paths like `/assets/...` because GitHub Pages often hosts sites in a subfolder (e.g., `username.github.io/repo-name/`), which will break absolute root paths.
- Ensure all pages share identical styling and navigation elements for consistency.
