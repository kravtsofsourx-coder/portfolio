# Project Presentation Template

A minimal HTML/CSS template for presenting design projects. Based on the Flowerpot App Figma design (node 73-19600). Two files, zero dependencies beyond a Google Fonts request.

---

## File structure

```
project-template/
├── template-flowerpot.html  ← page markup
├── styles.css      ← all styles
└── images/         ← create this folder and place your images here
    ├── hero.png
    ├── section-visual.png
    └── section-content.png
```

---

## How to use for a new project

1. Copy the entire `project-template/` folder and rename it using the project slug (e.g. `tehko/`).
2. Rename `template-flowerpot.html` to match the folder name (e.g. `tehko/tehko.html`). Always use the project slug as the filename — never `index.html` — so every case page has a unique, identifiable name.
3. Create an `images/` subfolder inside and add your exported images.
4. Open the renamed HTML file and:
   - Update `<title>` and the `<meta name="description">` tag.
   - Update the `lang` attribute on `<html>` if needed (`uk` / `en`).
   - Replace placeholder text in every section.
   - Replace `src` attributes on `<img>` tags with your image filenames.
5. Make sure the floating **Back** button is present directly before `<main class="page">` — it is required on every case page. Keep the `<svg>` arrow inside it.
6. Add or remove Section 3 / Section 4 blocks as needed — each is a self-contained `<section>`.

---

## Sections

### Section 1 — Hero
```html
<section class="section section--hero">
  <h1 class="h1">Project Title</h1>
  <img class="section-image" src="images/hero.png" alt="Hero image"/>
</section>
```
- Centered H1 (48 px).
- One full-width hero image.
- Designed for a **1024 × 640 px** image, but any aspect ratio works.

---

### Section 2 — Goals
```html
<section class="section section--goals">
  <h2 class="h2">Goals & Objectives</h2>
  <p class="text-big">Body text at 32 px...</p>
</section>
```
- Centered H2 (40 px).
- Large body text (32 px), left-aligned, full column width.
- No image.

---

### Section 3 — Visual (heading + image only)
```html
<section class="section section--visual">
  <h2 class="h2">Section Title</h2>
  <img class="section-image" src="images/section-visual.png" alt=""/>
</section>
```
- Centered H2 (40 px).
- One image, no body text.
- Image height is flexible — height is determined by the image itself.

---

### Section 4 — Content (heading + body text + image)
```html
<section class="section section--content">
  <h2 class="h2">Section Title</h2>
  <div class="text-body">
    <p>First paragraph...</p>
    <p>Second paragraph...</p>
  </div>
  <img class="section-image" src="images/section-content.png" alt=""/>
</section>
```
- Centered H2 (40 px).
- Regular body text (22 px), left-aligned.
- Multiple `<p>` tags get 12 px gap between them automatically.
- Image below the text.

---

### Section 5 — Multi-block (heading + repeatable text + image blocks)

Use this when one topic contains several findings or sub-sections, each with bullet text and an image beneath it. The H2 appears once at the top; the text+image block repeats as many times as needed.

```html
<section class="section section--multi">
  <h2 class="h2">Section Title</h2>

  <!-- Option A: bullet list -->
  <div class="section-block">
    <ul class="text-body text-body--list">
      <li>First finding or insight.</li>
      <li>Second finding or insight.</li>
    </ul>
    <img class="section-image" src="images/block-1.png" alt=""/>
  </div>

  <!-- Option B: plain paragraph text -->
  <div class="section-block">
    <div class="text-body">
      <p>First paragraph of plain body text.</p>
      <p>Second paragraph of plain body text.</p>
    </div>
    <img class="section-image" src="images/block-2.png" alt=""/>
  </div>
</section>
```

CSS to add to `styles.css`:
```css
.section--multi {
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.section-block {
  display: flex;
  flex-direction: column;
  gap: 32px;
}

.text-body--list {
  padding-left: 24px;
  list-style: disc;
}

.text-body--list li + li {
  margin-top: 12px;
}
```

- The H2 is optional — omit it if the section has no overall title.
- Each `.section-block` is self-contained: duplicate or remove blocks freely.
- Gap between blocks is 32 px (same as inner gap); gap between sections remains 80 px.

---

## Design tokens

| Token        | Value                    | Usage                        |
|--------------|--------------------------|------------------------------|
| Color        | `#1a1a1a`                | All text                     |
| Background   | `#ffffff`                | Page background              |
| Font family  | Google Sans, Medium (weight 500) | All text               |
| H1           | 48 px / line-height 1.4  | Hero title                   |
| H2           | 40 px / line-height 1.2  | Section headings             |
| Text big     | 32 px / line-height 1.4  | Goals section body           |
| Text body    | 22 px / line-height 1.4  | Content section body         |
| Section gap  | 80 px                    | Vertical space between sections |
| Inner gap    | 32 px                    | Space between elements inside a section |
| Paragraph gap | 12 px                   | Between `<p>` tags in `.text-body` |
| Content width | 1024 px max-width       | All sections and images      |

---

## Image guidelines

- **Width:** always export at **1024 px wide**.
- **Height:** varies by content — any height works.
- **Format:** PNG for UI screenshots; JPEG for photography.
- Place images in the `images/` subfolder next to `index.html`.
- The `section-image` class sets `width: 100%` so images scale down on smaller screens.

---

## Responsive breakpoints

| Breakpoint   | Max-width | Key changes                                      |
|--------------|-----------|--------------------------------------------------|
| Desktop      | —         | Full sizes as defined in design tokens above     |
| Tablet       | 991 px    | H1→40 px, H2→34 px, text-big→26 px, text-body→20 px |
| Mobile       | 767 px    | H1→32 px, H2→28 px, text-big→22 px, text-body→18 px |
| Small mobile | 479 px    | H1→26 px, H2→22 px, text-big→18 px, text-body→16 px |

---

## Swapping the font

The template uses **Google Sans** loaded via Google Fonts (same as the main portfolio).

1. In `index.html`, replace the Google Fonts `<link>` with a link to your desired font.
2. In `styles.css`, update `font-family` in the `body` rule.

---

## Navigation — Back button

The template includes a floating **Back** button fixed to the bottom-center of the screen. It is already present in the HTML — no extra work needed:

```html
<a href="../index.html" class="back-button" aria-label="Back to home">
  <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
    <path d="M12.5 15L7.5 10L12.5 5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
  </svg>
  Back
</a>
```

Place this directly before `<main class="page">` inside `<body>`. The button stays visible at all times as the user scrolls and links back to the portfolio home page.

---

## Adding more sections

- **Another Section 3** (image only): duplicate the `section--visual` block and update the `src`.
- **Another Section 4** (text + image): duplicate the `section--content` block, update text and `src`.
- **Another Section 5** (multi-block): duplicate the `section--multi` block; add or remove `.section-block` divs inside it as needed.
- Sections stack vertically with 80 px gap automatically.
