# RightDirect (rdgcc.com) Homepage Recreation

A full-fidelity, content-driven recreation of the [RightDirect (rdgcc.com)](https://rdgcc.com/) homepage built with **Astro** as the front-end framework and **Sanity** as the Headless CMS.

---

## 🏗️ Architecture & Stack

- **Framework**: Astro (v4+) with Component Architecture (`.astro`, `.tsx`)
- **CMS**: Sanity Headless CMS (`@sanity/client`, `@sanity/image-url`, `sanity`)
- **Styling**: Tailwind CSS with RightDirect brand color system (`#004681`, `#00345F`, `#2C2C2C`, `#F8F9FA`)
- **Interactive CMS Studio**: Integrated Sanity Studio accessible at `/studio`

---

## 📄 Core Content Schemas Defined in Sanity

1. **`homePage`** (`src/sanity/schemas/homePage.ts`): Singleton document driving page SEO, hero, track record, service pillars, methodology steps, case studies, and CTAs.
2. **`siteSettings`** (`src/sanity/schemas/siteSettings.ts`): Site-wide title, default meta description, brand logo, and global booking links.
3. **`heroSection`** (`src/sanity/schemas/heroSection.ts`): Main headline, subtitle text, primary/secondary CTA labels & links, and hero artwork image.
4. **`trackRecord` & `statItem`** (`src/sanity/schemas/trackRecord.ts`): Section headings and dynamic stat counters (`70+ Clients`, `90+ Projects`, `10+ Industries`).
5. **`servicePillar`** (`src/sanity/schemas/servicePillar.ts`): Core service cards (`Accelerate Go-to-Market`, `Enhance Digital Presence`, `Elevate Customer Experience`, `Modernise Workplace`).
6. **`processStep`** (`src/sanity/schemas/processStep.ts`): 4-step execution methodology (`Discover & Diagnose`, `Design & Align`, `Build & Launch`, `Optimize & Scale`).
7. **`caseStudy`** (`src/sanity/schemas/caseStudy.ts`): Client success stories (`Veeve`, `Alderman & Company`, `Anuta Networks`, `ICF Bengaluru`, `Understorey`).
8. **`brandLogo`**: Logo marquee carousel for trusted global brands (`Understorey`, `ICF`, `A&CO`, `CMS IT Services`, `IDBI`, `Veeve`, `Pearson`, `L&T`, `GyanSYS`, `Kristal`).

---

## 💻 Project Structure

```
Right-Direct/
├── .env                              # Sanity environment variables
├── .env.example                      # Sample configuration template
├── astro.config.mjs                  # Astro configuration (Tailwind + React)
├── sanity.config.ts                  # Sanity Studio configuration
├── package.json                      # Project dependencies & scripts
├── tailwind.config.mjs               # Tailwind custom theme & animations
├── tsconfig.json                     # TypeScript compiler options
└── src/
    ├── components/
    │   ├── Header.astro              # Navigation header with mega dropdowns & mobile drawer
    │   ├── Hero.astro                # Dynamic Hero section with Sanity content & graphics
    │   ├── TrackRecord.astro         # Statistic counters section (70+ Clients, 90+ Projects, etc.)
    │   ├── ServicesGrid.astro        # Interactive core pillars grid with hover glow effects
    │   ├── ProcessSteps.astro        # 4-step execution methodology
    │   ├── SuccessStories.astro      # Client case studies grid with image overlays
    │   ├── TrustedBrands.astro       # Infinite scrolling logo marquee carousel
    │   ├── CtaBanner.astro           # Bottom conversion banner
    │   ├── Footer.astro              # Footer links, branding, and copyright
    │   ├── StudioApp.tsx             # Embedded Sanity Studio React component
    │   └── CmsIndicator.astro        # Floating badge linking to live Sanity Studio
    ├── layouts/
    │   └── Layout.astro              # Main HTML shell with SEO meta, OpenGraph, & fonts
    ├── lib/
    │   └── sanity.ts                 # Sanity client, image builder & GROQ data fetcher with fallbacks
    ├── pages/
    │   ├── index.astro               # Dynamic homepage rendering Sanity data
    │   ├── 404.astro                 # Custom 404 error page
    │   ├── studio.astro              # Sanity CMS Studio editor route (/studio)
    │   └── services/
    │       └── [slug].astro          # Service detail pages
    └── sanity/
        └── schemas/                  # Sanity content type schema definitions
            ├── siteSettings.ts
            ├── heroSection.ts
            ├── trackRecord.ts
            ├── servicePillar.ts
            ├── processStep.ts
            ├── caseStudy.ts
            ├── homePage.ts
            └── index.ts
```

---

## ⚡ How Content Management Works

1. **Live Sanity Studio**: Visit `/studio` to open the embedded Sanity Studio directly inside the app.
2. **GROQ Data Fetcher**: `getHomePageData()` executes GROQ queries against Sanity.
3. **Resilient Fallback Provider**: If the Sanity dataset is loading, offline, or unconfigured, the app falls back seamlessly to pre-populated live content data, ensuring **100% uptime and zero broken components**.

---

## 🚀 Running the Project Locally

```bash
# Install dependencies
npm install

# Start local Astro development server
npm run dev

# Open in browser
# Homepage: http://localhost:4321
# Sanity Studio: http://localhost:4321/studio
```

## 📦 Setup Instructions

1. Install Node.js (≥ 18) and npm.
2. Copy `.env.example` to `.env` and fill in Sanity credentials (optional).
3. Install project dependencies:

   ```bash
   npm install --legacy-peer-deps
   ```

4. Start the development server:

   ```bash
   npm run dev
   ```

5. Open http://localhost:4321 in your browser. The Sanity Studio is available at http://localhost:4321/studio.

## 🏗️ Project Architecture Overview

- **Framework**: Astro v4+ (component‑based, SSR/SSG hybrid).
- **CMS**: Sanity v3 (headless, content‑driven).
- **Styling**: Tailwind CSS with a custom brand palette.
- **Components**: Located in `src/components/` (`.astro` and `.tsx` files).
- **Pages**: `src/pages/` contains route‑based `.astro` files (`index.astro`, `404.astro`, `studio.astro`, dynamic service pages).
- **Data Layer**: `src/lib/sanity.ts` provides a typed Sanity client and GROQ fetch helpers.
- **Layouts**: `src/layouts/Layout.astro` wraps pages with SEO meta, fonts, and global styles.

## 🛠️ Assumptions Made During Development

- The project runs on a machine with internet access to fetch npm packages and Sanity data.
- If the Sanity dataset is unavailable, the app falls back to static demo content bundled in the repo.
- Environment variables are read from a `.env` file; missing variables default to the fallback data.
- Only modern browsers (Chrome ≥ 100, Edge, Firefox) are targeted; no legacy IE support.
- Tailwind’s JIT compiler is used, so a `tailwind.config.mjs` file must be present.
- The `astro` CLI is invoked via the local `node_modules/.bin` binary; it is not assumed to be globally installed.
