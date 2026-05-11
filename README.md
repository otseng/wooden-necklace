# Portfolio Blog Starter

A modern, minimal portfolio website with an integrated blog system. Built with [Next.js](https://nextjs.org) App Router, TypeScript, and Tailwind CSS.

## Features

- **MDX & Markdown Support** — Write blog posts with JSX components
- **SEO Optimized** — Automatic sitemap, robots.txt, JSON-LD structured data
- **RSS Feed** — Subscribe via `/rss`
- **Dynamic OG Images** — Auto-generated social preview images
- **Syntax Highlighting** — Code blocks with `sugar-high`
- **Tailwind CSS v4** — Latest utility-first styling (alpha)
- **Analytics** — Vercel Speed Insights & Web Analytics built-in
- **Geist Font** — Vercel's modern sans-serif and mono typefaces
- **Dark Mode** — Automatic via `prefers-color-scheme`

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | [Next.js](https://nextjs.org) 16 (App Router) |
| Language | [TypeScript](https://www.typescriptlang.org) 5 |
| Styling | [Tailwind CSS](https://tailwindcss.com) v4.0.0-alpha.13 |
| Fonts | [Geist](https://vercel.com/font) |
| Content | [next-mdx-remote](https://github.com/hashicorp/next-mdx-remote) |
| Syntax | [sugar-high](https://github.com/huozhi/sugar-high) |
| Package Mgr | [pnpm](https://pnpm.io) |

## Quick Start

### Prerequisites

- Node.js 18+
- [pnpm](https://pnpm.io/installation)

### Install

```bash
# Clone the template
pnpm create next-app --example https://github.com/vercel/examples/tree/main/solutions/blog my-portfolio

cd my-portfolio
pnpm install
```

### Run

```bash
pnpm dev        # Development server at http://localhost:3000
pnpm build      # Production build
pnpm start      # Production server
```

## Project Structure

```
app/
├── blog/
│   ├── [slug]/         # Dynamic blog post pages
│   ├── posts/          # MDX content files
│   ├── page.tsx        # Blog listing
│   └── utils.ts        # Post parsing & utilities
├── components/
│   ├── footer.tsx      # Site footer
│   ├── mdx.tsx         # Custom MDX components
│   ├── nav.tsx         # Top navigation
│   └── posts.tsx       # Blog post list
├── og/
│   └── route.tsx       # Dynamic OG image generation
├── rss/
│   └── route.ts        # RSS feed endpoint
├── global.css          # Tailwind + prose styles
├── layout.tsx          # Root layout
├── page.tsx            # Home page
├── robots.ts           # robots.txt
└── sitemap.ts          # sitemap.xml
```

## Writing Blog Posts

Create a new `.mdx` file in `app/blog/posts/`:

```mdx
---
title: 'Your Post Title'
publishedAt: '2024-01-15'
summary: 'A brief description for listings and RSS.'
---

Your content here. Supports **Markdown** and <CustomComponents />.
```

Posts are automatically discovered, sorted by date, and rendered.

## Customization Checklist

- [ ] **Domain**: Update `baseUrl` in `app/sitemap.ts`
- [ ] **Metadata**: Edit title/description in `app/layout.tsx`
- [ ] **Navigation**: Adjust links in `app/components/nav.tsx`
- [ ] **Footer**: Update links and copyright in `app/components/footer.tsx`
- [ ] **Home Page**: Personalize `app/page.tsx`
- [ ] **Content**: Add your own posts in `app/blog/posts/`

## OG Images

Dynamic Open Graph images are generated at `/og?title=Your+Title`.

## Deployment

Optimized for [Vercel](https://vercel.com):

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/vercel/examples/tree/main/solutions/blog)

## License

MIT
