# Css-Animation-Revision
# CSS Animation — Revision Notes

Personal revision notes on CSS animations, based on the course **"Learn to Make Animations Using CSS" by Swaraj Singh**.
📎 Course reference: [Notion link](https://app.notion.com/p/Learn-to-Make-Animations-Using-CSS-by-Swaraj-Singh-3ac69b6210fc8092b3d4e7d10f277cb2?source=copy_link)

> Note: The Notion page above requires login/JS to view, so its exact content isn't reproduced here — this README covers the core CSS animation concepts and my own project notes. Feel free to expand each section with details copied over manually from the Notion doc.

---

## 📚 Core Concepts Covered

### 1. `transition`
- Animates a property change smoothly between two states (e.g. on `:hover`, `:focus`, class toggle).
- Syntax: `transition: property duration timing-function delay;`
- Best for simple state changes (color, transform, opacity).

### 2. `transform`
- `translate()`, `translateX()`, `translateY()`
- `rotate()`, `rotateX()`, `rotateY()`, `rotateZ()`
- `scale()`, `scaleX()`, `scaleY()`
- `skew()`
- Combine multiple transforms in one declaration: `transform: translateX(50px) rotate(45deg);`

### 3. `@keyframes`
- Defines multi-step animations (not just start/end like transitions).
- Syntax:
  ```css
  @keyframes slideIn {
    0%   { transform: translateX(-100%); opacity: 0; }
    100% { transform: translateX(0); opacity: 1; }
  }
  ```
- Applied via the `animation` shorthand property.

### 4. `animation` shorthand
```css
animation: name duration timing-function delay iteration-count direction fill-mode;
```
- `iteration-count`: number or `infinite`
- `direction`: `normal | reverse | alternate | alternate-reverse`
- `fill-mode`: `none | forwards | backwards | both`
- `animation-play-state`: `running | paused` (useful for pause-on-hover effects)

### 5. Timing functions
- `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out`
- Custom curves via `cubic-bezier(x1, y1, x2, y2)`

### 6. Performance tips
- Animate `transform` and `opacity` where possible (GPU-accelerated, avoids layout reflow).
- Avoid animating `width`, `height`, `top`, `left` directly for smoother performance — use `transform: translate()` instead.
- Use `will-change: transform;` sparingly for heavy animations.

---

## 🛠️ Projects

### 1. Carousel Rotation (CSS-only)
A rotating image/card carousel built purely with CSS `@keyframes` and `transform: rotate()` / `translate()` / `perspective`.

**Key ideas used:**
- `perspective` on the parent container for a 3D rotation effect.
- Each carousel item positioned with `transform: rotateY(angle) translateZ(distance)`.
- `@keyframes` to auto-rotate the whole carousel, or `:hover`/`animation-play-state: paused` to pause on interaction.
- `transform-style: preserve-3d;` on the carousel container so child transforms render in 3D space.

**Folder:** `/carousel-rotation`
*(add your actual file structure and a short demo GIF/screenshot here)*

---

### 2. Marquee Animation (CSS-only)
A scrolling text/image marquee effect recreated without JavaScript.

**Key ideas used:**
- A flex container with duplicated content (so the loop looks seamless).
- `@keyframes` moving content via `transform: translateX()` from `0%` to `-100%`.
- `animation: marquee 15s linear infinite;`
- Pause on hover using `animation-play-state: paused;`
- Handling overflow with `overflow: hidden;` on the wrapper.

**Folder:** `/marquee-animation`
*(add your actual file structure and a short demo GIF/screenshot here)*

---

## ✅ Revision Checklist
- [x] `transition` basics
- [x] `transform` functions
- [x] `@keyframes` + `animation` shorthand
- [x] Carousel rotation project
- [x] Marquee animation project
- [ ] Scroll-triggered animations (`@scroll-timeline` / Intersection Observer + CSS)
- [ ] `animation-composition` / advanced keyframe chaining
- [ ] Accessibility: `prefers-reduced-motion` media query

---

## ♿ Accessibility Note (to add to projects)
Respect users who prefer reduced motion:
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

---

## 📌 Next Steps
- Paste full notes/screenshots from the Notion course into the relevant sections above.
- Add live demo links (CodePen / Vercel / GitHub Pages) for both projects.
- Add screenshots or a short GIF for each project folder.