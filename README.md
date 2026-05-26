# Velvet Pour

> A scroll-driven animated landing page built with React 19 and GSAP.
> 
[![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=white)](https://react.dev)
[![GSAP](https://img.shields.io/badge/GSAP-3.14-88CE02?style=flat-square&logo=greensock&logoColor=white)](https://gsap.com)
[![Vite](https://img.shields.io/badge/Vite-7-646CFF?style=flat-square&logo=vite&logoColor=white)](https://vitejs.dev)
[![TailwindCSS](https://img.shields.io/badge/Tailwind-4-38BDF8?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)](./LICENSE)
[![Status](https://img.shields.io/badge/Status-Portfolio%20Project-orange?style=flat-square)](#)

---

# About The Project

Velvet Pour is an immersive single-page marketing website for a premium cocktail bar.

The project is a focused engineering study in scroll-driven animation architecture — specifically the intersection of:

- GSAP ScrollTrigger
- React component lifecycle
- Video scrubbing
- CSS mask animations
- SplitText animations
- Scroll-pinned sections

The core technical challenge was coordinating multiple concurrent animation systems without degrading performance or leaking animation state across React renders.

This project demonstrates how GSAP can operate outside React's reconciler while still integrating safely through the `useGSAP` hook and GSAP context cleanup.

> This is a portfolio and learning project — not a production system.

---

# Live Demo

| Resource | Link |
|---|---|
| Live Site | [Live](https://mojito-website-alpha.vercel.app/) |

---

# Project Type

**Frontend SPA · Animation Engineering · Portfolio / Marketing Site**

- Static Site
- Client-Side Rendered
- No Backend
- No Database
- No Authentication

---

# Project Status

## Functional Prototype

Core animations and interactions are fully implemented and working.

The project is not actively maintained. Known issues and technical debt are documented transparently below.

---

# Why I Built This

The primary goal was to deeply study scroll-driven animation architecture beyond tutorial-grade implementations.

Key engineering objectives:

- Understand GSAP ScrollTrigger internals
- Implement Apple-style video scrubbing
- Study React lifecycle integration with DOM-mutating animation libraries
- Explore CSS mask animation techniques
- Learn Tailwind CSS v4 architecture
- Build a visually polished project suitable for technical interviews

---

# Features

## Core Features

- Scroll-scrubbed hero video
- SplitText animations
- CSS mask reveal effects
- Scroll-pinned sections
- Circular cocktail carousel
- Parallax decorative elements
- Scroll-triggered navbar blur
- Mobile-aware animation configuration

---

## Engineering Features

- `useGSAP()` lifecycle integration
- Automatic GSAP cleanup via contexts
- Centralized plugin registration
- Runtime breakpoint detection
- ScrollTrigger optimization
- Modular animation configuration

---


# Tech Stack

## Frontend

| Technology | Version | Purpose |
|---|---|---|
| React | 19 | UI rendering |
| GSAP | 3.14 | Animation engine |
| @gsap/react | 2.1 | React lifecycle integration |
| Tailwind CSS | 4 | Utility-first styling |
| react-responsive | 10 | Runtime breakpoint detection |
| Vite | 7 | Build tooling |

---

# Architecture

This is a purely client-side rendered static application.

```text
Browser
   ↓
index.html
   ↓
main.jsx
   ↓
App.jsx
   ↓
React Components
   ↓
GSAP ScrollTrigger
   ↓
DOM Mutations
```

---

# Component Structure

```text
App.jsx
├── Navbar
├── Hero
├── Cocktails
├── About
├── Art
├── Menu
└── Contact
```

---

# Animation Flow

```text
useGSAP()
   ↓
GSAP Context
   ↓
ScrollTrigger
   ↓
DOM Style Mutations
   ↓
requestAnimationFrame
```

---

# Folder Structure

```text
velvet-pour/
├── constants/
│   └── index.js
├── public/
│   ├── images/
│   ├── fonts/
│   └── videos/
├── src/
│   ├── components/
│   ├── App.jsx
│   ├── main.jsx
│   └── index.css
├── index.html
├── vite.config.js
├── eslint.config.js
└── package.json
```

---

# Screenshots

| Preview | Description |
|---|---|
| <img width="1898" height="864" alt="image" src="https://github.com/user-attachments/assets/72fb3815-d325-4cb7-92da-dc7bf1734f12" /> | Hero Section |
| <img width="1903" height="873" alt="image" src="https://github.com/user-attachments/assets/99b8cf4b-f337-4df3-b312-3473ca1ec0d0" /> | Video Scrub Animation |
| <img width="1896" height="866" alt="image" src="https://github.com/user-attachments/assets/8f77ce91-f942-49ad-8440-7d1e12b3dd26" /> | CSS Mask Reveal |
| <img width="1897" height="864" alt="image" src="https://github.com/user-attachments/assets/edf04c11-a93a-4cf2-8ae7-048819b8b4b8" /> | Cocktail Carousel |
| <img width="1904" height="864" alt="image" src="https://github.com/user-attachments/assets/eff3f20b-769e-404d-9fb6-eeefb347636b" /> | Contact / Footer |

---

# Installation

## Prerequisites

- Node.js >= 20.19.0

---

## Clone Repository

```bash
git clonehttps://github.com/Heramb1221/velvet-pour

cd velvet-pour
```

---

## Install Dependencies

```bash
npm install
```

---

## Start Development Server

```bash
npm run dev
```

---

## Build Production Bundle

```bash
npm run build
```

---

## Preview Production Build

```bash
npm run preview
```

---

# Usage

Velvet Pour is a scroll-driven single-page experience.

| Section | Interaction | Animation |
|---|---|---|
| Hero | Scroll | Video scrub + parallax |
| Cocktails | Scroll | Leaf animations |
| About | Scroll | SplitText animations |
| Art | Scroll | Pinned mask reveal |
| Menu | Click | Carousel transitions |
| Contact | Scroll | Footer animations |

---

# Performance Considerations

## Optimized Areas

- GSAP batches DOM writes
- Shared passive scroll listener
- Tailwind CSS v4 tree-shaking
- Minimal React state usage

---

# Technical Debt

| Area | Debt |
|---|---|
| CSS Architecture | Massive monolithic CSS file |
| Animation Patterns | Duplicated logic |
| Font Loading | Render-blocking |
| Image Pipeline | No optimization |
| TypeScript | Missing |
| Testing | No coverage |
| Error Handling | No boundaries |

---

## Challenges Faced

### Video Scrub Timing

The GSAP tween targeting `video.currentTime` could not be created until the browser exposed the video's metadata through the `loadedmetadata` event. Since `video.duration` remains unavailable before metadata loading completes, the ScrollTrigger responsible for synchronizing scroll position with video playback had to be registered asynchronously after metadata initialization. Coordinating this asynchronous browser event with the otherwise synchronous GSAP setup inside `useGSAP()` required careful sequencing to avoid undefined duration values and broken scrub behavior.

---

### GSAP Cleanup in React

React 18+ `StrictMode` intentionally invokes effects twice during development to help identify side-effect bugs. Without GSAP's context-based cleanup system provided by `useGSAP()`, this behavior would register duplicate `ScrollTrigger` instances and duplicate timelines, resulting in doubled animations, inconsistent scroll behavior, and memory leaks. GSAP's context system automatically scopes animations and destroys them during cleanup, preventing stale animation instances from persisting across React re-renders and development-mode remounts.

---

### Mobile ScrollTrigger Configuration

`ScrollTrigger` configurations involving `pin: true` behaved differently across desktop and mobile devices because mobile browsers dynamically resize the viewport when browser toolbars expand or collapse. The difference between `100vh` and `100dvh` caused inconsistencies in trigger start/end calculations, especially for pinned sections. A single hardcoded configuration was unreliable across devices, so runtime breakpoint detection using `react-responsive` was implemented to branch animation configurations dynamically for mobile and desktop environments.

---

### CSS Mask Animation

Animating CSS mask properties such as `mask-size` and `mask-position` required understanding how GSAP handles non-standard CSS properties internally. Initially, it was unclear whether a dedicated plugin was necessary for mask interpolation. After reviewing GSAP internals documentation, it became clear that GSAP's core engine can animate interpolatable CSS properties directly without additional plugins. This allowed smooth mask reveal animations driven entirely through standard GSAP tweens.

---

# What I Learned

- GSAP context system
- ScrollTrigger internals
- Video scrubbing architecture
- React reconciler limitations
- Tailwind CSS v4 architecture
- DOM mutation strategies
- Scroll-based animation optimization

---

# Repository Philosophy

This project is learning-oriented with production-inspired architecture.

The goal was not to ship a production cocktail website.

The goal was to:

- Build technically interesting animation systems
- Make genuine engineering decisions
- Document tradeoffs honestly
- Create strong interview discussion material

Known flaws are intentionally documented instead of hidden.

---

# License

MIT License.

> GSAP is used under the GSAP Standard License.  
> Commercial deployment requires a Club GSAP membership.

---

# Contact

**Heramb Chaudhari**

[![GitHub](https://img.shields.io/badge/GitHub-Heramb1221-black?style=for-the-badge&logo=github)](https://github.com/Heramb1221)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Heramb%20Chaudhari-blue?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/heramb-chaudhari)

[![Email](https://img.shields.io/badge/Email-hchaudhari1221%40gmail.com-red?style=for-the-badge&logo=gmail)](mailto:hchaudhari1221@gmail.com)

--- 

> Built as a focused engineering study in:
> - Scroll-driven animation architecture
> - GSAP + React integration
> - Video scrubbing systems
> - High-performance frontend animation
