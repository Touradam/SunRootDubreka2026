# AdamaWebsiteStyle
## Complete UI/UX Design System & Implementation Guide

**Version:** 1.0  
**Design Name:** Midnight Champagne  
**Philosophy:** Premium dark interface with sophisticated gold accents, smooth animations, and immersive 3D effects

---

## Table of Contents
1. [Design Philosophy](#design-philosophy)
2. [Color System](#color-system)
3. [Typography](#typography)
4. [Layout Structure](#layout-structure)
5. [Components](#components)
6. [Animations & Effects](#animations--effects)
7. [Interactive Behaviors](#interactive-behaviors)
8. [Responsive System](#responsive-system)
9. [Complete Code Patterns](#complete-code-patterns)
10. [Implementation Checklist](#implementation-checklist)

---

## Design Philosophy

### Core Principles
1. **Two-Page Architecture**
   - **Page 1 (Main)**: Clean, high-level overview with interactive elements
   - **Page 2 (Details)**: Comprehensive execution details and requirements

2. **Progressive Disclosure**
   - Show essential information first
   - Reveal details through interaction (flips, clicks, hovers)
   - Never overwhelm with information density

3. **Premium Feel**
   - Sophisticated color palette (dark + gold)
   - Smooth, physics-based animations
   - Generous spacing and breathing room
   - Subtle luxury touches throughout

4. **Engagement Through Motion**
   - 3D tilt effects on hover
   - Card flip interactions
   - Floating background elements
   - Spotlight following cursor
   - Particles drifting gently

---

## Color System

### Primary Palette (Exact Values)

```css
/* Gold accent colors */
--gold: #c4a35a;
--gold-light: #e2c887;
--gold-dark: #9a7b3c;
--gold-glow: rgba(196, 163, 90, 0.35);

/* Dark backgrounds */
--ink: #0c0c0f;              /* Page background */
--ink-raised: #12121a;        /* Elevated sections */
--surface: #18181f;           /* Card backgrounds */
--surface-hover: #1f1f28;     /* Hover states */

/* Borders */
--border: rgba(255, 255, 255, 0.08);
--border-gold: rgba(196, 163, 90, 0.25);

/* Text colors */
--text: #eceae4;              /* Primary text */
--text-muted: #9c9a94;        /* Secondary text */
--text-dim: #6b6963;          /* Tertiary text */
```

### Usage Guidelines

**Gold Usage:**
- Primary CTA buttons
- Important text emphasis
- Icons and decorative elements
- Active states and selections
- Glow effects

**Background Layers:**
```css
/* Layer 1: Page base */
background: var(--ink);

/* Layer 2: Sections */
background: var(--ink-raised);

/* Layer 3: Cards */
background: var(--surface);

/* Layer 4: Interactive hover */
background: var(--surface-hover);
```

**Text Hierarchy:**
```css
/* Headings */ 
color: var(--text);

/* Body text */
color: var(--text-muted);

/* Labels, meta info */
color: var(--text-dim);

/* Emphasis */
color: var(--gold);
```

### Gradient Patterns

**Primary Button Gradient:**
```css
background: linear-gradient(
  135deg, 
  var(--gold-light) 0%, 
  var(--gold) 50%, 
  var(--gold-dark) 100%
);
```

**Hero Glow:**
```css
background: radial-gradient(
  ellipse 70% 50% at 50% -10%, 
  rgba(196, 163, 90, 0.18) 0%, 
  transparent 55%
);
```

**Card Background Gradient:**
```css
background: linear-gradient(
  145deg, 
  #1f1f28 0%, 
  #12121a 100%
);
```

**Flipped Card Gold Glow:**
```css
background: linear-gradient(
  145deg, 
  rgba(196, 163, 90, 0.12) 0%, 
  #12121a 45%
);
```

---

## Typography

### Font Stack

```css
/* Display font (headings) */
--font-display: 'Outfit', system-ui, sans-serif;

/* Body font (paragraphs) */
--font-body: 'DM Sans', system-ui, sans-serif;

/* Math/technical */
--font-math: 'Cambria Math', 'Times New Roman', Georgia, serif;
```

### Font Loading (Exact CDN Links)

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700&family=Outfit:wght@500;600;700&display=swap" rel="stylesheet" />
```

### Type Scale & Styles

```css
/* H1 - Page Hero */
h1 {
  font-family: var(--font-display);
  font-size: clamp(2rem, 5vw, 3.5rem);
  font-weight: 700;
  line-height: 1.1;
  letter-spacing: -0.02em;
  color: var(--text);
  margin: 0 0 1.5rem;
}

/* H2 - Section Title */
h2 {
  font-family: var(--font-display);
  font-size: clamp(1.75rem, 3vw, 2.25rem);
  font-weight: 600;
  line-height: 1.15;
  letter-spacing: -0.02em;
  color: var(--text);
  margin: 0 0 1rem;
}

/* H3 - Card Title */
h3 {
  font-family: var(--font-display);
  font-size: 1.125rem;
  font-weight: 600;
  line-height: 1.2;
  letter-spacing: -0.01em;
  color: var(--text);
  margin: 0 0 0.625rem;
}

/* Body Text (Lead) */
.lead {
  font-family: var(--font-body);
  font-size: clamp(1.0625rem, 2vw, 1.25rem);
  color: var(--text-muted);
  line-height: 1.7;
}

/* Body Text (Regular) */
p {
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--text-muted);
  line-height: 1.65;
}

/* Small Text */
small {
  font-size: 0.875rem;
}

/* Eyebrow Labels */
.eyebrow {
  font-family: var(--font-display);
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  color: var(--gold);
}
```

---

## Layout Structure

### Container System

```css
.container {
  max-width: 76rem;
  margin: 0 auto;
  padding: 0 1.25rem;
}

@media (min-width: 640px) {
  .container {
    padding: 0 2rem;
  }
}

/* Content width constraints */
.max-w-3xl { max-width: 48rem; margin-left: auto; margin-right: auto; }
.max-w-4xl { max-width: 56rem; margin-left: auto; margin-right: auto; }
.max-w-5xl { max-width: 64rem; margin-left: auto; margin-right: auto; }
```

### Section Spacing

```css
.section {
  padding: 5.5rem 0;
  position: relative;
}

@media (min-width: 768px) {
  .section {
    padding: 6.5rem 0;
  }
}
```

### Grid Systems

```css
/* 2-column grid */
.grid-2 {
  display: grid;
  gap: 1.25rem;
}

@media (min-width: 768px) {
  .grid-2 {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }
}

/* 3-column grid */
.grid-3 {
  display: grid;
  gap: 1.5rem;
}

@media (min-width: 768px) {
  .grid-3 {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* 4-column grid */
.grid-4 {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.25rem;
}

@media (min-width: 768px) {
  .grid-4 {
    grid-template-columns: repeat(4, 1fr);
  }
}
```

---

## Components

### 1. Buttons

#### Primary Button (Gold Gradient)

```css
.btn-primary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.875rem 1.75rem;
  border-radius: 0.75rem;
  font-family: var(--font-body);
  font-size: 0.9375rem;
  font-weight: 600;
  letter-spacing: 0.01em;
  background: linear-gradient(135deg, var(--gold-light) 0%, var(--gold) 50%, var(--gold-dark) 100%);
  color: #0c0c0f;
  border: none;
  box-shadow: 0 4px 24px var(--gold-glow);
  cursor: pointer;
  transition: transform 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              box-shadow 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 28px var(--gold-glow);
}

.btn-primary:active {
  transform: translateY(0);
}
```

#### Secondary Button (Outlined)

```css
.btn-secondary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.875rem 1.75rem;
  border-radius: 0.75rem;
  font-family: var(--font-body);
  font-size: 0.9375rem;
  font-weight: 600;
  letter-spacing: 0.01em;
  background: transparent;
  color: var(--gold);
  border: 1.5px solid rgba(196, 163, 90, 0.25);
  cursor: pointer;
  transition: transform 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              background 0.2s cubic-bezier(0.4, 0, 0.2, 1),
              border-color 0.2s cubic-bezier(0.4, 0, 0.2, 1),
              color 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.btn-secondary:hover {
  transform: translateY(-2px);
  background: rgba(196, 163, 90, 0.06);
  border-color: var(--gold);
  color: var(--gold-light);
}
```

#### Button Group

```css
.btn-group {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  justify-content: center;
  align-items: center;
}

@media (min-width: 640px) {
  .btn-group {
    flex-direction: row;
  }
}
```

#### Ripple Effect on Click

```javascript
// Add .btn-shine class to buttons for ripple effect
function initButtonRipple() {
  document.querySelectorAll('.btn-shine').forEach((btn) => {
    btn.addEventListener('click', (e) => {
      const rect = btn.getBoundingClientRect();
      const ripple = document.createElement('span');
      ripple.className = 'btn-ripple';
      ripple.style.left = `${e.clientX - rect.left}px`;
      ripple.style.top = `${e.clientY - rect.top}px`;
      btn.appendChild(ripple);
      setTimeout(() => ripple.remove(), 600);
    });
  });
}
```

```css
.btn-shine {
  position: relative;
  overflow: hidden;
}

.btn-ripple {
  position: absolute;
  width: 8px;
  height: 8px;
  margin: -4px 0 0 -4px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.45);
  animation: btnRipple 0.6s cubic-bezier(0.4, 0, 0.2, 1) forwards;
  pointer-events: none;
}

@keyframes btnRipple {
  to {
    transform: scale(24);
    opacity: 0;
  }
}
```

### 2. Cards

#### Basic Card

```css
.card {
  background: var(--surface);
  padding: 2rem;
  border-radius: 1rem;
  border: 1px solid var(--border);
  transition: border-color 0.25s cubic-bezier(0.4, 0, 0.2, 1), 
              transform 0.25s cubic-bezier(0.4, 0, 0.2, 1), 
              box-shadow 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.card:hover {
  border-color: rgba(196, 163, 90, 0.25);
  transform: translateY(-3px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
}
```

#### Flip Card (3D Transform)

**HTML Structure:**
```html
<article class="roadmap-card roadmap-card--flip tilt-card" data-phase="1" tabindex="0">
  <div class="roadmap-card-flipper">
    <div class="roadmap-card-face roadmap-card-front">
      <!-- Front content -->
    </div>
    <div class="roadmap-card-face roadmap-card-back">
      <!-- Back content with details -->
    </div>
  </div>
</article>
```

**CSS:**
```css
.roadmap-card--flip {
  min-height: 11.5rem;
  perspective: 1000px;
  cursor: pointer;
}

.roadmap-card-flipper {
  position: relative;
  width: 100%;
  min-height: 11.5rem;
  transform-style: preserve-3d;
  transition: transform 0.65s cubic-bezier(0.4, 0.2, 0.2, 1);
}

.roadmap-card--flip.is-flipped .roadmap-card-flipper {
  transform: rotateY(180deg);
}

.roadmap-card-face {
  position: relative;
  width: 100%;
  min-height: 11.5rem;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  border-radius: 1.25rem;
}

.roadmap-card-front {
  display: flex;
  gap: 1rem;
  padding: 1.25rem;
  background: linear-gradient(145deg, #1f1f28 0%, #12121a 100%);
  border: 1px solid rgba(196, 163, 90, 0.34);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.25);
}

.roadmap-card-back {
  position: absolute;
  inset: 0;
  transform: rotateY(180deg);
  padding: 1.25rem;
  background: linear-gradient(145deg, rgba(196, 163, 90, 0.12) 0%, #12121a 45%);
  border: 1px solid rgba(196, 163, 90, 0.45);
  box-shadow: 0 4px 24px rgba(196, 163, 90, 0.35);
  overflow-y: auto;
}
```

**JavaScript:**
```javascript
function initFlipCards() {
  document.querySelectorAll('.roadmap-card--flip').forEach(card => {
    card.addEventListener('click', (e) => {
      if (e.target.closest('.roadmap-flip-close')) {
        card.classList.remove('is-flipped');
        return;
      }
      card.classList.toggle('is-flipped');
    });
    
    card.addEventListener('keydown', (e) => {
      if (e.key === 'Enter' || e.key === ' ') {
        e.preventDefault();
        card.classList.toggle('is-flipped');
      }
      if (e.key === 'Escape') {
        card.classList.remove('is-flipped');
      }
    });
  });
}
```

#### Stats Pill Card

```css
.roadmap-stats-pill {
  display: flex;
  align-items: stretch;
  min-width: 16rem;
  background: var(--surface);
  border: 1px solid rgba(196, 163, 90, 0.32);
  border-radius: 1.25rem;
  overflow: hidden;
  transition: transform 0.15s cubic-bezier(0.4, 0, 0.2, 1), 
              box-shadow 0.25s cubic-bezier(0.4, 0, 0.2, 1), 
              border-color 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.roadmap-stats-pill:hover {
  border-color: var(--gold);
  box-shadow: 0 4px 24px rgba(196, 163, 90, 0.35);
}

.roadmap-stats-col {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 1rem 1.25rem;
}

.roadmap-stats-value {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--gold-light);
}

.roadmap-stats-label {
  font-size: 0.9375rem;
  color: var(--text);
}

.roadmap-stats-divider {
  width: 1px;
  background: rgba(196, 163, 90, 0.28);
}
```

### 3. Countdown Timer

**HTML:**
```html
<div class="countdown-wrap" id="countdown-wrap" hidden>
  <span class="countdown-label">Starts in</span>
  <div class="countdown-timer" id="countdown-timer"></div>
</div>
```

**CSS:**
```css
.countdown-wrap {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-top: 1rem;
  padding: 0.75rem 1.25rem;
  background: rgba(196, 163, 90, 0.08);
  border: 1px solid rgba(196, 163, 90, 0.25);
  border-radius: 1rem;
  width: fit-content;
}

.countdown-label {
  font-size: 0.8125rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--gold);
}

.countdown-timer {
  display: flex;
  align-items: center;
  gap: 0.35rem;
  font-family: var(--font-display);
}

.countdown-unit {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 2.5rem;
}

.countdown-unit strong {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--gold-light);
  line-height: 1;
}

.countdown-unit small {
  font-size: 0.625rem;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: var(--text-dim);
  margin-top: 0.15rem;
}

.countdown-sep {
  color: var(--gold-dark);
  font-weight: 700;
  font-size: 1.125rem;
  margin-bottom: 0.75rem;
}
```

**JavaScript:**
```javascript
function initCountdown(targetDateISO) {
  const wrap = document.getElementById('countdown-wrap');
  const timer = document.getElementById('countdown-timer');
  if (!wrap || !timer) return;

  const target = new Date(targetDateISO);
  if (isNaN(target.getTime()) || target.getTime() <= Date.now()) {
    wrap.remove();
    return;
  }

  wrap.hidden = false;

  function update() {
    const now = Date.now();
    const diff = target - now;
    if (diff <= 0) {
      wrap.remove();
      return;
    }

    const days = Math.floor(diff / 86400000);
    const hours = Math.floor((diff % 86400000) / 3600000);
    const mins = Math.floor((diff % 3600000) / 60000);
    const secs = Math.floor((diff % 60000) / 1000);

    timer.innerHTML = `
      <span class="countdown-unit"><strong>${days}</strong><small>days</small></span>
      <span class="countdown-sep">:</span>
      <span class="countdown-unit"><strong>${String(hours).padStart(2, '0')}</strong><small>hrs</small></span>
      <span class="countdown-sep">:</span>
      <span class="countdown-unit"><strong>${String(mins).padStart(2, '0')}</strong><small>min</small></span>
      <span class="countdown-sep">:</span>
      <span class="countdown-unit"><strong>${String(secs).padStart(2, '0')}</strong><small>sec</small></span>
    `;
  }

  update();
  setInterval(update, 1000);
}

// Usage: initCountdown('2026-07-10T19:00:00-07:00');
```

### 4. Phase Navigation Pills

**HTML:**
```html
<div class="roadmap-phase-nav" id="roadmap-phase-nav"></div>
```

**CSS:**
```css
.roadmap-phase-nav {
  display: flex;
  flex-wrap: wrap;
  gap: 0.625rem;
  margin-bottom: 1.25rem;
}

.roadmap-phase-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem 0.5rem 0.5rem;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 999px;
  color: var(--text-muted);
  font-family: var(--font-body);
  font-size: 0.875rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              border-color 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              background 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              box-shadow 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              color 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.roadmap-phase-btn:hover {
  border-color: rgba(196, 163, 90, 0.25);
  color: var(--text);
  transform: translateY(-2px);
}

.roadmap-phase-btn.is-active {
  background: rgba(196, 163, 90, 0.12);
  border-color: var(--gold);
  color: var(--gold-light);
  box-shadow: 0 4px 24px rgba(196, 163, 90, 0.35);
}

.roadmap-phase-btn-num {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 1.75rem;
  height: 1.75rem;
  border-radius: 50%;
  background: rgba(196, 163, 90, 0.06);
  color: var(--gold);
  font-family: var(--font-display);
  font-size: 0.8125rem;
  font-weight: 800;
  transition: background 0.2s cubic-bezier(0.4, 0, 0.2, 1), 
              color 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.roadmap-phase-btn.is-active .roadmap-phase-btn-num {
  background: var(--gold);
  color: var(--ink);
}
```

### 5. Info Bar

```css
.roadmap-footer-bar {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem 2rem;
  padding: 1rem 1.5rem;
  background: var(--surface);
  border: 1px solid rgba(196, 163, 90, 0.22);
  border-radius: 999px;
  font-size: 0.9375rem;
}

.roadmap-footer-bar p {
  margin: 0;
  color: var(--gray-600);
}

.roadmap-footer-bar strong {
  color: var(--gold);
}

@media (max-width: 900px) {
  .roadmap-footer-bar {
    border-radius: 1rem;
    flex-direction: column;
    gap: 0.5rem;
  }
}
```

### 6. Checklist

```css
.check-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.check-list li {
  display: flex;
  align-items: flex-start;
  gap: 0.75rem;
  margin-bottom: 0.625rem;
  color: var(--text-muted);
  font-size: 0.9375rem;
}

.check-list svg {
  width: 1.125rem;
  height: 1.125rem;
  color: var(--gold);
  flex-shrink: 0;
  margin-top: 0.2rem;
}
```

---

## Animations & Effects

### Core Animation Variables

```css
:root {
  --ease: cubic-bezier(0.4, 0, 0.2, 1);
}
```

### 1. Fade Up Animation

```css
@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.reveal-item {
  opacity: 0;
  animation: fadeUp 0.65s var(--ease) both;
}

/* Staggered timing */
.reveal-stagger .reveal-item:nth-child(1) { animation-delay: 0s; }
.reveal-stagger .reveal-item:nth-child(2) { animation-delay: 0.08s; }
.reveal-stagger .reveal-item:nth-child(3) { animation-delay: 0.16s; }
.reveal-stagger .reveal-item:nth-child(4) { animation-delay: 0.24s; }
```

### 2. Scroll Reveal

**CSS:**
```css
.reveal-on-scroll {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.6s var(--ease), transform 0.6s var(--ease);
}

.reveal-on-scroll.is-visible {
  opacity: 1;
  transform: translateY(0);
}
```

**JavaScript:**
```javascript
function initScrollReveal() {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
          observer.unobserve(entry.target);
        }
      });
    },
    { threshold: 0.15, rootMargin: '0px 0px -40px 0px' }
  );

  document.querySelectorAll('.reveal-on-scroll').forEach((el) => {
    observer.observe(el);
  });
}
```

### 3. 3D Tilt Effect (Mouse Tracking)

**CSS:**
```css
.tilt-card {
  transform: perspective(800px) rotateX(var(--tilt-x, 0deg)) rotateY(var(--tilt-y, 0deg));
  transition: transform 0.15s cubic-bezier(0.4, 0, 0.2, 1);
}
```

**JavaScript:**
```javascript
function initTiltCards() {
  document.querySelectorAll('.tilt-card').forEach((card) => {
    card.addEventListener('pointermove', (e) => {
      const rect = card.getBoundingClientRect();
      const x = (e.clientX - rect.left) / rect.width - 0.5;
      const y = (e.clientY - rect.top) / rect.height - 0.5;
      card.style.setProperty('--tilt-x', `${y * -6}deg`);
      card.style.setProperty('--tilt-y', `${x * 6}deg`);
    });

    card.addEventListener('pointerleave', () => {
      card.style.setProperty('--tilt-x', '0deg');
      card.style.setProperty('--tilt-y', '0deg');
    });
  });
}
```

### 4. Spotlight Effect (Cursor Following)

**HTML:**
```html
<div class="roadmap-bg">
  <div class="roadmap-spotlight" id="roadmap-spotlight"></div>
</div>
```

**CSS:**
```css
.roadmap-spotlight {
  position: absolute;
  inset: 0;
  opacity: 0;
  transition: opacity 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  background: radial-gradient(
    600px circle at var(--spot-x, 50%) var(--spot-y, 50%),
    rgba(196, 163, 90, 0.12) 0%,
    transparent 60%
  );
  pointer-events: none;
}
```

**JavaScript:**
```javascript
function initSpotlight() {
  const hero = document.querySelector('.roadmap-hero');
  const spotlight = document.getElementById('roadmap-spotlight');
  if (!hero || !spotlight) return;

  let raf = null;
  hero.addEventListener('pointermove', (e) => {
    if (raf) cancelAnimationFrame(raf);
    raf = requestAnimationFrame(() => {
      const rect = hero.getBoundingClientRect();
      const x = e.clientX - rect.left;
      const y = e.clientY - rect.top;
      spotlight.style.setProperty('--spot-x', `${x}px`);
      spotlight.style.setProperty('--spot-y', `${y}px`);
      spotlight.style.opacity = '1';
    });
  });

  hero.addEventListener('pointerleave', () => {
    spotlight.style.opacity = '0';
  });
}
```

### 5. Floating Particles

**HTML:**
```html
<div class="roadmap-particles" id="roadmap-particles"></div>
```

**CSS:**
```css
.roadmap-particles {
  position: absolute;
  inset: 0;
  pointer-events: none;
}

.roadmap-particle {
  position: absolute;
  width: 3px;
  height: 3px;
  border-radius: 50%;
  background: var(--gold-light);
  animation: particleFloat linear infinite;
}

@keyframes particleFloat {
  0%, 100% {
    transform: translate(0, 0) scale(1);
    opacity: 0.2;
  }
  50% {
    transform: translate(12px, -28px) scale(1.4);
    opacity: 0.7;
  }
}
```

**JavaScript:**
```javascript
function initParticles() {
  const container = document.getElementById('roadmap-particles');
  if (!container) return;

  const count = 18;
  for (let i = 0; i < count; i += 1) {
    const p = document.createElement('span');
    p.className = 'roadmap-particle';
    p.style.left = `${Math.random() * 100}%`;
    p.style.top = `${Math.random() * 100}%`;
    p.style.animationDelay = `${Math.random() * 8}s`;
    p.style.animationDuration = `${6 + Math.random() * 10}s`;
    p.style.opacity = `${0.15 + Math.random() * 0.35}`;
    container.appendChild(p);
  }
}
```

### 6. Floating Background Elements (Equations/Icons)

**HTML Structure:**
```html
<div class="roadmap-equations" id="roadmap-equations"></div>
```

**CSS:**
```css
.roadmap-equations {
  position: absolute;
  inset: 0;
  pointer-events: none;
  overflow: hidden;
  z-index: 0;
}

.roadmap-equation {
  position: absolute;
  display: flex;
  align-items: center;
  gap: 0.35em;
  font-family: 'Cambria Math', 'Times New Roman', Georgia, serif;
  font-size: calc(0.875rem * var(--eq-size, 1));
  line-height: 1;
  color: rgba(196, 163, 90, 0.14);
  white-space: nowrap;
  will-change: left, top, transform, opacity;
  user-select: none;
}

.roadmap-equation .math-sym {
  font-style: italic;
  font-weight: 500;
}

.roadmap-equation .math-op {
  font-style: normal;
  font-weight: 600;
}
```

**JavaScript (Drifting Animation):**
```javascript
const floatingElements = [
  {
    html: '<span class="math-sym">V</span><span class="math-op">=</span><span class="math-sym">I</span><span class="math-op">·</span><span class="math-sym">R</span>',
    x: 6, y: 18, size: 1.35, rot: -8, duration: 22,
  },
  // ... more elements
];

function renderFloatingElements(containerId, elements) {
  const container = document.getElementById(containerId);
  if (!container || !elements?.length) return;

  container.innerHTML = elements
    .map(
      (el) => `
    <span
      class="roadmap-equation"
      style="left: ${el.x}%; top: ${el.y}%; --eq-size: ${el.size}; transform: rotate(${el.rot}deg);"
      data-x="${el.x}"
      data-y="${el.y}"
      data-rot="${el.rot}"
    >${el.html}</span>
  `
    )
    .join('');
}

const driftStates = [];

function initElementDrift() {
  document.querySelectorAll('.roadmap-equation').forEach((el) => {
    driftStates.push({
      el,
      x: parseFloat(el.dataset.x),
      y: parseFloat(el.dataset.y),
      rot: parseFloat(el.dataset.rot),
      vx: (Math.random() - 0.5) * 0.009,
      vy: (Math.random() - 0.5) * 0.008,
      vRot: (Math.random() - 0.5) * 0.02,
      bounds: { minX: 1, maxX: 86, minY: 4, maxY: 82 },
      opacity: 0.45 + Math.random() * 0.35,
      vOpacity: (Math.random() - 0.5) * 0.0015,
    });
  });

  function tick() {
    driftStates.forEach((s) => {
      // Random velocity changes
      if (Math.random() < 0.008) {
        s.vx += (Math.random() - 0.5) * 0.004;
        s.vy += (Math.random() - 0.5) * 0.004;
        s.vRot += (Math.random() - 0.5) * 0.012;
      }

      // Clamp velocities
      s.vx = Math.max(-0.014, Math.min(0.014, s.vx));
      s.vy = Math.max(-0.014, Math.min(0.014, s.vy));
      s.vRot = Math.max(-0.035, Math.min(0.035, s.vRot));

      // Update positions
      s.x += s.vx;
      s.y += s.vy;
      s.rot += s.vRot;
      s.opacity += s.vOpacity;
      s.opacity = Math.max(0.35, Math.min(0.85, s.opacity));
      if (s.opacity <= 0.38 || s.opacity >= 0.82) s.vOpacity *= -1;

      // Bounce off edges
      const { minX, maxX, minY, maxY } = s.bounds;
      if (s.x <= minX || s.x >= maxX) {
        s.vx *= -1;
        s.x = Math.max(minX, Math.min(maxX, s.x));
      }
      if (s.y <= minY || s.y >= maxY) {
        s.vy *= -1;
        s.y = Math.max(minY, Math.min(maxY, s.y));
      }

      // Apply to DOM
      s.el.style.left = `${s.x}%`;
      s.el.style.top = `${s.y}%`;
      s.el.style.transform = `rotate(${s.rot}deg)`;
      s.el.style.opacity = String(s.opacity);
    });

    requestAnimationFrame(tick);
  }

  requestAnimationFrame(tick);
}
```

### 7. SVG Hotspot Highlight

**CSS:**
```css
.roadmap-hotspot {
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--w);
  height: var(--h);
  padding: 0;
  border: none;
  border-radius: 8.75%;
  background: transparent;
  cursor: pointer;
  pointer-events: auto;
  transition: background 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

.roadmap-hotspot::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  border: 2px solid transparent;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.35s cubic-bezier(0.4, 0, 0.2, 1);
}

.roadmap-hotspot.is-active {
  background: rgba(196, 163, 90, 0.07);
}

.roadmap-hotspot.is-active::after {
  opacity: 1;
  border-color: rgba(196, 163, 90, 0.55);
  box-shadow: 0 0 24px rgba(196, 163, 90, 0.2);
  animation: hotspotHighlight 2.6s ease-in-out infinite;
}

.roadmap-hotspot.is-active.is-entering::after {
  animation: hotspotSelectIn 0.55s cubic-bezier(0.34, 1.4, 0.64, 1) both,
    hotspotHighlight 2.6s ease-in-out 0.55s infinite;
}

@keyframes hotspotSelectIn {
  0% {
    opacity: 0;
    transform: scale(0.94);
    border-color: rgba(226, 200, 135, 0);
    box-shadow: 0 0 0 rgba(196, 163, 90, 0);
  }
  100% {
    opacity: 1;
    transform: scale(1);
    border-color: rgba(226, 200, 135, 0.75);
    box-shadow: 0 0 32px rgba(196, 163, 90, 0.3);
  }
}

@keyframes hotspotHighlight {
  0%, 100% {
    border-color: rgba(196, 163, 90, 0.45);
    box-shadow: 0 0 18px rgba(196, 163, 90, 0.15);
  }
  50% {
    border-color: rgba(226, 200, 135, 0.8);
    box-shadow: 0 0 34px rgba(196, 163, 90, 0.32);
  }
}
```

### 8. Accessibility: Reduced Motion

**Always include:**
```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

**Check in JavaScript:**
```javascript
function prefersReducedMotion() {
  return window.matchMedia('(prefers-reduced-motion: reduce)').matches;
}

// Use before applying animations
if (!prefersReducedMotion()) {
  initParticles();
  initSpotlight();
  // ... other motion effects
}
```

---

## Interactive Behaviors

### 1. Phase Navigation System

Coordinates buttons, SVG hotspots, and card states:

```javascript
function setActivePhase(phaseId) {
  // Highlight buttons
  document.querySelectorAll('.roadmap-phase-btn').forEach((btn) => {
    btn.classList.toggle('is-active', Number(btn.dataset.phase) === phaseId);
  });

  // Highlight SVG hotspots
  document.querySelectorAll('.roadmap-hotspot').forEach((hotspot) => {
    const isMatch = Number(hotspot.dataset.phase) === phaseId;
    hotspot.classList.toggle('is-active', isMatch);
    if (isMatch) {
      hotspot.classList.add('is-entering');
      setTimeout(() => hotspot.classList.remove('is-entering'), 600);
    }
  });

  // Flip cards
  flipPhaseCard(phaseId, true);
}

function clearActivePhase() {
  document.querySelectorAll('.is-active, .is-entering').forEach((el) => {
    el.classList.remove('is-active', 'is-entering');
  });
  document.querySelectorAll('.is-flipped').forEach((el) => {
    el.classList.remove('is-flipped');
  });
}
```

### 2. Modal System

**HTML:**
```html
<div class="beta-modal-root" id="my-modal" hidden>
  <div class="beta-modal-overlay">
    <div class="beta-modal">
      <button type="button" class="beta-modal-dismiss" aria-label="Close">&times;</button>
      <h3>Modal Title</h3>
      <p>Modal content</p>
    </div>
  </div>
</div>
```

**CSS:**
```css
.beta-modal-root[hidden] {
  display: none;
}

.beta-modal-root:not([hidden]) {
  position: fixed;
  inset: 0;
  z-index: 300;
}

.beta-modal-overlay {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.25rem;
  background: rgba(12, 12, 15, 0.85);
  backdrop-filter: blur(4px);
}

.beta-modal {
  position: relative;
  width: 100%;
  max-width: 28rem;
  padding: 2rem;
  background: var(--surface);
  border: 1px solid rgba(196, 163, 90, 0.25);
  border-radius: 1.25rem;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4), 0 4px 24px rgba(196, 163, 90, 0.35);
  animation: fadeUp 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.beta-modal-dismiss {
  position: absolute;
  top: 0.75rem;
  right: 0.75rem;
  width: 2.25rem;
  height: 2.25rem;
  padding: 0;
  border: none;
  border-radius: 50%;
  background: transparent;
  color: var(--text-muted);
  font-size: 1.5rem;
  cursor: pointer;
}

.beta-modal-dismiss:hover {
  color: var(--text);
  background: rgba(196, 163, 90, 0.12);
}
```

**JavaScript:**
```javascript
function openModal(modalId) {
  const modal = document.getElementById(modalId);
  if (!modal) return;
  modal.removeAttribute('hidden');
  document.body.classList.add('beta-modal-open');
}

function closeModal(modalId) {
  const modal = document.getElementById(modalId);
  if (!modal) return;
  modal.setAttribute('hidden', '');
  document.body.classList.remove('beta-modal-open');
}

// Prevent body scroll when modal open
body.beta-modal-open {
  overflow: hidden;
}
```

---

## Responsive System

### Breakpoints

```css
/* Mobile first approach */
/* Default: Mobile (<640px) */

/* Small tablet */
@media (min-width: 640px) { }

/* Tablet */
@media (min-width: 768px) { }

/* Desktop switch point */
@media (min-width: 901px) { }

/* Large desktop */
@media (min-width: 1024px) { }
```

### Mobile vs Desktop Patterns

**SVG Roadmap (Desktop only):**
```css
.roadmap-svg-frame {
  display: block;
}

.roadmap-cards-mobile {
  display: none;
}

@media (max-width: 900px) {
  .roadmap-svg-frame {
    display: none;
  }

  .roadmap-cards-mobile {
    display: flex;
    flex-direction: column;
    gap: 1rem;
  }
}
```

**Stacked Cards (Mobile):**
```css
.roadmap-card--offset {
  margin-left: 0;
}

@media (max-width: 900px) {
  .roadmap-card--offset {
    margin-left: 1.5rem;
  }
}
```

---

## Complete Code Patterns

### Full Page Structure (Landing Page)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Project Name</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700&family=Outfit:wght@500;600;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="css/styles.css" />
</head>
<body>
  <main class="roadmap-page">
    <section class="roadmap-hero">
      <!-- Background effects -->
      <div class="roadmap-bg">
        <div class="roadmap-spotlight" id="roadmap-spotlight"></div>
        <div class="roadmap-particles" id="roadmap-particles"></div>
        <div class="roadmap-equations" id="roadmap-equations"></div>
      </div>

      <!-- Header -->
      <div class="container roadmap-header reveal-stagger">
        <div class="roadmap-header-text">
          <p class="roadmap-eyebrow reveal-item">Category · Type</p>
          <h1 class="reveal-item">Main Title</h1>
          <p class="roadmap-subtitle reveal-item">Subtitle description</p>
          <p class="cohort-start-banner reveal-item">
            Important Date: <strong>Friday, July 10, 2026</strong>
          </p>
          <div class="countdown-wrap reveal-item" id="countdown-wrap" hidden>
            <span class="countdown-label">Starts in</span>
            <div class="countdown-timer" id="countdown-timer"></div>
          </div>
        </div>
        <div class="roadmap-stats-pill reveal-item tilt-card">
          <div class="roadmap-stats-col">
            <span class="roadmap-stats-value">1 Month</span>
            <span class="roadmap-stats-label">Duration</span>
          </div>
          <div class="roadmap-stats-divider"></div>
          <div class="roadmap-stats-col">
            <span class="roadmap-stats-value">4 Phases</span>
            <span class="roadmap-stats-label">Stages</span>
          </div>
        </div>
      </div>

      <!-- Phase Navigation -->
      <div class="container roadmap-phase-nav reveal-on-scroll" id="roadmap-phase-nav"></div>

      <!-- Visual Roadmap -->
      <div class="container roadmap-visual-wrap reveal-on-scroll">
        <div class="roadmap-svg-frame" id="roadmap-svg-frame">
          <img class="roadmap-svg-desktop" src="assets/roadmap.svg" alt="Project Roadmap" />
          <div class="roadmap-hotspots" id="roadmap-hotspots"></div>
          <div class="roadmap-flip-overlays" id="roadmap-flip-overlays"></div>
        </div>
        <div class="roadmap-cards-mobile" id="roadmap-cards-mobile"></div>
      </div>

      <!-- Info Bar -->
      <div class="container reveal-on-scroll">
        <div class="roadmap-footer-bar">
          <p><strong>Schedule:</strong> Details here</p>
          <p><strong>Tools:</strong> List of tools</p>
        </div>
      </div>

      <!-- CTA -->
      <div class="container roadmap-cta-row reveal-on-scroll">
        <div class="btn-group">
          <button class="btn btn-primary btn-shine">Primary Action</button>
          <a href="details.html" class="btn btn-secondary">Learn More</a>
        </div>
      </div>
    </section>
  </main>

  <script src="js/data.js"></script>
  <script src="js/interactions.js"></script>
  <script src="js/main.js"></script>
</body>
</html>
```

### Full Page Structure (Details Page)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Details | Project Name</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500;0,9..40,600;0,9..40,700&family=Outfit:wght@500;600;700&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="css/styles.css" />
</head>
<body>
  <main>
    <!-- Page Hero -->
    <section class="page-hero">
      <div class="container text-center max-w-4xl">
        <h1>Page Title</h1>
        <p class="lead">Brief introduction paragraph</p>
      </div>
    </section>

    <!-- Requirements -->
    <section class="section section-white">
      <div class="container max-w-4xl">
        <div class="section-header text-center">
          <span class="section-eyebrow">Requirements</span>
          <h2 class="section-title">What You Need</h2>
          <p class="section-intro">Brief description</p>
        </div>
        <ul class="check-list">
          <li>
            <svg fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
            </svg>
            <span>Requirement 1</span>
          </li>
          <!-- More items -->
        </ul>
      </div>
    </section>

    <!-- Team Profile -->
    <section class="section section-white">
      <div class="container max-w-4xl text-center">
        <span class="section-eyebrow">Team</span>
        <h2 class="section-title">Meet The Team</h2>
        <div id="instructor-card-mount" class="instructor-card-wrap"></div>
      </div>
    </section>

    <!-- Final CTA -->
    <section class="section section-white">
      <div class="container text-center max-w-4xl">
        <h2 class="section-title">Ready to Start?</h2>
        <div class="btn-group">
          <a href="index.html" class="btn btn-primary">Get Started</a>
          <a href="index.html" class="btn btn-secondary">Back to Home</a>
        </div>
      </div>
    </section>
  </main>

  <script src="js/data.js"></script>
  <script src="js/main.js"></script>
</body>
</html>
```

### Data Configuration Template

```javascript
// js/data.js

// Project metadata
const projectMetadata = {
  name: 'Project Name',
  tagline: 'One-line description',
  copyright: 'Your Organization',
  logoPath: 'assets/logo.svg'
};

// Countdown event
const primaryEvent = {
  date: '2026-07-10T19:00:00-07:00',
  label: 'Launch Date',
  description: 'Friday, July 10, 2026 · 7:00 PM PST'
};

// Roadmap phases (3-6 recommended)
const roadmapPhases = [
  {
    id: 1,
    tag: 'Phase 1',
    title: 'Phase Title',
    lead: 'Brief description',
    icon: '01',
    outcome: 'What users achieve',
    summary: 'One sentence summary',
    sessions: [
      'Step 1: Description',
      'Step 2: Description',
      'Step 3: Description'
    ],
    sessionDetails: [
      {
        label: 'S1',
        day: 'Week 1',
        type: 'Type',
        title: 'Session Title',
        description: 'Full description'
      }
    ]
  },
  // ... more phases
];

// SVG hotspot coordinates (percentages based on viewBox)
const roadmapHotspots = [
  { phase: 1, x: 5.9, y: 32.7, w: 20, h: 34.4 },
  { phase: 2, x: 28.6, y: 49.1, w: 20, h: 34.4 },
  // ... coordinates for each phase
];

// Floating background elements (optional)
const floatingElements = [
  {
    html: '<span class="math-sym">Element</span>',
    x: 10,
    y: 20,
    size: 1.2,
    rot: 5,
    duration: 25
  },
  // ... more elements
];

// Team profile
const teamProfile = {
  name: 'Name',
  role: 'Title',
  organization: 'Company',
  photo: 'assets/photo.jpg',
  tagline: 'Click to learn more',
  bio: [
    'Bio paragraph 1',
    'Bio paragraph 2'
  ],
  highlights: [
    'Achievement 1',
    'Achievement 2'
  ]
};
```

---

## Implementation Checklist

### Phase 1: Setup
- [ ] Create folder structure (css/, js/, assets/)
- [ ] Add font links to HTML head
- [ ] Set up CSS variables with exact color values
- [ ] Configure viewport and meta tags

### Phase 2: Core Styles
- [ ] Implement typography system
- [ ] Create button components (.btn-primary, .btn-secondary)
- [ ] Build card components (.card, .roadmap-card)
- [ ] Set up grid systems (.grid-2, .grid-3, .grid-4)
- [ ] Create container and spacing utilities

### Phase 3: Landing Page Structure
- [ ] Build hero section with background effects container
- [ ] Add header with title, subtitle, stats pill
- [ ] Create phase navigation pills
- [ ] Set up SVG roadmap frame
- [ ] Add mobile card stack
- [ ] Create info bar
- [ ] Add CTA section

### Phase 4: Details Page Structure
- [ ] Build page hero section
- [ ] Create requirements checklist
- [ ] Add team profile flip card
- [ ] Build outcomes section
- [ ] Add final CTA

### Phase 5: Interactive Features
- [ ] Implement countdown timer
- [ ] Add flip card interactions
- [ ] Create 3D tilt effect
- [ ] Build phase navigation system
- [ ] Sync buttons, hotspots, and cards
- [ ] Add scroll reveal animations

### Phase 6: Visual Effects
- [ ] Implement spotlight (cursor following)
- [ ] Add floating particles
- [ ] Create drifting background elements
- [ ] Build SVG hotspot highlights
- [ ] Add button ripple effect

### Phase 7: Data Configuration
- [ ] Fill projectMetadata
- [ ] Configure primaryEvent
- [ ] Define roadmapPhases (3-6 phases)
- [ ] Map roadmapHotspots coordinates
- [ ] Set up teamProfile
- [ ] Optional: Add floatingElements

### Phase 8: Polish
- [ ] Test all animations
- [ ] Verify reduced motion support
- [ ] Check keyboard navigation
- [ ] Test screen reader compatibility
- [ ] Validate color contrast
- [ ] Test on mobile, tablet, desktop
- [ ] Cross-browser testing

### Phase 9: Optimization
- [ ] Minify CSS and JavaScript
- [ ] Optimize images (WebP format)
- [ ] Add loading states
- [ ] Implement lazy loading for images
- [ ] Check performance metrics

### Phase 10: Launch
- [ ] Final accessibility audit
- [ ] Test all interactions
- [ ] Verify countdown timer
- [ ] Check all links
- [ ] Deploy to hosting

---

## Quick Start Template

### Minimal Landing Page (5 minutes)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Project</title>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Outfit:wght@500;600;700&display=swap" rel="stylesheet" />
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    
    :root {
      --gold: #c4a35a;
      --ink: #0c0c0f;
      --surface: #18181f;
      --text: #eceae4;
      --text-muted: #9c9a94;
    }
    
    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--ink);
      color: var(--text);
      line-height: 1.65;
    }
    
    .container {
      max-width: 76rem;
      margin: 0 auto;
      padding: 0 2rem;
    }
    
    .hero {
      padding: 6rem 0;
      text-align: center;
    }
    
    h1 {
      font-family: 'Outfit', sans-serif;
      font-size: 3rem;
      font-weight: 700;
      margin-bottom: 1.5rem;
    }
    
    .lead {
      font-size: 1.25rem;
      color: var(--text-muted);
      margin-bottom: 2rem;
    }
    
    .btn-primary {
      display: inline-block;
      padding: 0.875rem 1.75rem;
      background: linear-gradient(135deg, #e2c887 0%, #c4a35a 50%, #9a7b3c 100%);
      color: #0c0c0f;
      border-radius: 0.75rem;
      font-weight: 600;
      text-decoration: none;
      transition: transform 0.2s;
    }
    
    .btn-primary:hover {
      transform: translateY(-2px);
    }
  </style>
</head>
<body>
  <main>
    <section class="hero">
      <div class="container">
        <h1>Your Project Title</h1>
        <p class="lead">A brief description of what makes your project amazing</p>
        <a href="#" class="btn-primary">Get Started</a>
      </div>
    </section>
  </main>
</body>
</html>
```

---

## Support & Resources

### Browser Compatibility
- Chrome/Edge: Full support
- Firefox: Full support
- Safari: Full support (use -webkit- prefixes for backdrop-filter)
- Mobile browsers: Full support

### Performance Targets
- First Contentful Paint: < 1.5s
- Largest Contentful Paint: < 2.5s
- Total page weight: < 500KB (excluding fonts)
- JavaScript execution: < 100ms

### Accessibility Standards
- WCAG 2.1 AA compliance
- Keyboard navigation for all interactive elements
- Screen reader tested (NVDA, JAWS)
- Color contrast minimum 4.5:1
- Touch targets minimum 44×44px

---

## Conclusion

This style guide captures the complete **AdamaWebsiteStyle** design system. Every color, animation timing, layout pattern, and interaction behavior has been documented with exact values and implementation code.

**Key Characteristics:**
- Premium dark theme with sophisticated gold accents
- Smooth, physics-based animations
- 3D tilt effects and card flips
- Interactive phase navigation
- Countdown timer urgency
- Two-page architecture (overview + details)
- Mobile-responsive and accessible

**To implement this style on a new project:**
1. Copy the CSS variables and core styles
2. Set up the HTML structure following the templates
3. Configure your project data in `data.js`
4. Initialize the interactive features
5. Test across devices and browsers

This design system creates a memorable, engaging user experience that communicates professionalism and attention to detail while remaining accessible and performant.

---

**Version:** 1.0  
**Last Updated:** 2026  
**Author:** Adama Touré / Tourdam AI Lab  
**Design Name:** Midnight Champagne
