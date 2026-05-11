# Portfolio Blog Starter - Project Guide

## Project Overview

This is a **Portfolio Blog Starter** - a modern, minimal personal portfolio website with an integrated blog system. It's built as a Next.js application using the App Router architecture and is optimized for performance, SEO, and developer experience.

The project serves as a complete template for developers who want to quickly set up a personal portfolio with blog capabilities, featuring MDX support for rich content, dynamic OG images, RSS feeds, and built-in analytics.

**Key Technologies:**
- **Framework:** Next.js 16.0.10 with App Router
- **Language:** TypeScript 5.x
- **Styling:** Tailwind CSS v4.0.0-alpha.13
- **Fonts:** Geist Sans & Mono (Vercel's font)
- **Content:** MDX/Markdown via next-mdx-remote
- **Syntax Highlighting:** sugar-high
- **Package Manager:** pnpm
- **Hosting:** Optimized for Vercel deployment
- **Analytics:** Vercel Analytics & Speed Insights

## Getting Started

### Prerequisites
- Node.js 18.x or later (recommended)
- pnpm package manager (`npm install -g pnpm`)

### Installation

1. Clone or create the project:
```bash
pnpm create next-app --example https://github.com/vercel/examples/tree/main/solutions/blog my-portfolio
cd my-portfolio
```

2. Install dependencies:
```bash
pnpm install
```

3. Start development server:
```bash
pnpm dev
```

4. Open http://localhost:3000 in your browser.

### Available Scripts
- `pnpm dev` - Start development server
- `pnpm build` - Build for production
- `pnpm start` - Start production server

### Testing
**Note:** No test suite is currently configured. Consider adding:
- Jest or Vitest for unit testing
- Playwright or Cypress for E2E testing
- React Testing Library for component testing

## Project Structure

```
.
├── app/                          # Next.js App Router root
│   ├── blog/                     # Blog section
│   │   ├── [slug]/               # Dynamic blog post pages
│   │   │   └── page.tsx          # Individual blog post view
│   │   ├── posts/                # MDX blog post content files
│   │   │   ├── vim.mdx
│   │   │   ├── spaces-vs-tabs.mdx
│   │   │   └── static-typing.mdx
│   │   ├── page.tsx              # Blog listing page
│   │   └── utils.ts              # Blog data fetching utilities
│   ├── components/               # Shared React components
│   │   ├── footer.tsx            # Site footer with links
│   │   ├── mdx.tsx               # MDX rendering with custom components
│   │   ├── nav.tsx               # Navigation bar
│   │   └── posts.tsx             # Blog posts list component
│   ├── og/                       # Open Graph image generation
│   │   └── route.tsx             # Dynamic OG image API route
│   ├── rss/                      # RSS feed
│   │   └── route.ts              # RSS feed generation API route
│   ├── global.css                # Global styles & Tailwind config
│   ├── layout.tsx                # Root layout (metadata, fonts, providers)
│   ├── not-found.tsx             # 404 error page
│   ├── page.tsx                  # Home page
│   ├── robots.ts                 # robots.txt generation
│   └── sitemap.ts                # sitemap.xml generation
├── package.json                  # Dependencies and scripts
├── pnpm-lock.yaml                # Lock file
├── postcss.config.js             # PostCSS with Tailwind plugin
├── tsconfig.json                 # TypeScript configuration
├── .gitignore                    # Git ignore rules
├── README.md                     # Project documentation
└── .continue/rules/              # Continue AI rules directory
    └── CONTINUE.md               # This file
```

## Development Workflow

### Coding Standards
- **TypeScript:** Used throughout with `.ts` and `.tsx` extensions
- **Components:** Server Components by default (Next.js App Router)
- **Styling:** Tailwind CSS utility classes with dark mode support
- **Imports:** Use `app/` prefix for internal imports (configured via `baseUrl` in tsconfig)

### Key Conventions
1. **Metadata:** Export `metadata` objects from page files for SEO
2. **Blog Posts:** Write in MDX format with YAML frontmatter:
   ```yaml
   ---
   title: 'Post Title'
   publishedAt: '2024-01-01'
   summary: 'Brief description'
   image?: '/optional-og-image.jpg'
   ---
   ```
3. **Components:** Use named exports for components; default exports for page components
4. **Dark Mode:** Uses `prefers-color-scheme` media query; classes with `dark:` prefix

### Content Management
Blog posts are stored as MDX files in `app/blog/posts/`. The system:
- Automatically discovers and parses MDX files
- Extracts frontmatter metadata
- Generates static pages at build time
- Sorts posts by publication date (newest first)

### Build and Deployment
1. **Static Generation:** Blog posts are pre-rendered via `generateStaticParams`
2. **SEO Optimization:** Automatic sitemap, robots.txt, and OG images
3. **Deployment:** Optimized for Vercel with zero-config deployment
4. **Analytics:** Automatic Web Vitals and usage tracking on Vercel

### Contribution Guidelines
1. Create new MDX files in `app/blog/posts/` for content
2. Update `baseUrl` in `app/sitemap.ts` for your domain
3. Customize metadata in `app/layout.tsx` for your branding
4. Modify navigation items in `app/components/nav.tsx`
5. Update footer links in `app/components/footer.tsx`

## Key Concepts

### App Router Architecture
- **Route Groups:** File-based routing with nested layouts
- **Server Components:** Default React components that render on the server
- **Route Handlers:** API routes using `route.ts` files for RSS and OG images
- **Dynamic Routes:** `[slug]` directories for blog posts

### Content Processing Pipeline
1. **MDX Files** → Frontmatter + Markdown content
2. **Parser** (`utils.ts`) → Structured data with metadata
3. **MDX Remote** (`mdx.tsx`) → React components with custom rendering
4. **Static Generation** → HTML at build time

### Custom MDX Components
The `CustomMDX` system provides enhanced rendering:
- **Headings:** Auto-generated anchor links for direct linking
- **Images:** Rounded corners with Next.js Image optimization
- **Links:** Smart routing (internal Next.js Link, external with `target="_blank"`)
- **Code Blocks:** Syntax highlighting via sugar-high
- **Tables:** Custom table component for data display

### SEO & Social Features
- **Dynamic OG Images:** Generated on-demand with title parameter
- **JSON-LD Schema:** Structured data for blog posts
- **RSS Feed:** XML feed for blog subscribers
- **Sitemap:** Automatic XML sitemap generation

## Common Tasks

### Adding a New Blog Post
1. Create a new `.mdx` file in `app/blog/posts/`
2. Add frontmatter:
   ```yaml
   ---
   title: 'Your Post Title'
   publishedAt: '2024-01-01'
   summary: 'Brief description of the post'
   ---
   ```
3. Write your content using Markdown/MDX
4. The post automatically appears in the blog listing

### Updating Site Metadata
Edit `app/layout.tsx`:
```typescript
export const metadata: Metadata = {
  title: {
    default: 'Your Name - Portfolio',
    template: '%s | Your Name',
  },
  description: 'Your personal description',
  // ... customize Open Graph, robots, etc.
}
```

### Adding a New Page
1. Create a directory in `app/` (e.g., `app/about/`)
2. Add `page.tsx` with your content
3. Optionally add `layout.tsx` for nested layouts
4. Add navigation link in `app/components/nav.tsx`

### Customizing Styles
- Global styles: `app/global.css`
- Tailwind classes: Use utility classes inline in components
- Custom CSS: Add to `global.css` with `.prose` prefix for content
- Dark mode: Use `dark:` prefix classes

### Changing the Base URL
Update `app/sitemap.ts`:
```typescript
export const baseUrl = 'https://your-domain.com'
```

This affects sitemap, OG images, RSS feed, and metadata.

## Troubleshooting

### Build Failures
- **MDX Parse Errors:** Check frontmatter format and YAML syntax
- **TypeScript Errors:** Run `pnpm build` locally to catch issues early
- **Missing Dependencies:** Ensure `pnpm install` completed successfully

### Content Not Appearing
- Verify MDX file is in `app/blog/posts/` directory
- Check `publishedAt` date is valid format (YYYY-MM-DD)
- Ensure frontmatter has `---` delimiters

### OG Images Not Working
- Check `baseUrl` is correctly set in `sitemap.ts`
- Verify `/og?title=Test` route responds with image
- Ensure deployment environment supports `next/og`

### Styling Issues
- Tailwind v4 is in alpha - expect potential breaking changes
- Dark mode uses system preference; test with OS dark mode enabled
- Custom `prose` styles in `global.css` override default Tailwind

### Development Server Issues
- Clear `.next/` directory: `rm -rf .next`
- Restart dev server after adding new files
- Check for port conflicts (default: 3000)

## References

### Official Documentation
- [Next.js Documentation](https://nextjs.org/docs)
- [Tailwind CSS v4 Alpha](https://tailwindcss.com/docs/v4-alpha)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [MDX Documentation](https://mdxjs.com/docs/)

### Vercel Resources
- [Next.js App Router](https://nextjs.org/docs/app)
- [Vercel Analytics](https://vercel.com/analytics)
- [Vercel Speed Insights](https://vercel.com/docs/speed-insights)
- [Geist Font](https://vercel.com/font)

### Related Tools
- [next-mdx-remote](https://github.com/hashicorp/next-mdx-remote)
- [sugar-high](https://github.com/huozhi/sugar-high) - Syntax highlighting
- [pnpm](https://pnpm.io/) - Package manager

### Deployment
- [Vercel Platform](https://vercel.com)
- [Deploying Next.js](https://nextjs.org/docs/app/building-your-application/deploying)

---

**⚠️ Important Notes:**
- Tailwind CSS v4 is currently in alpha - monitor for breaking changes
- The `baseUrl` must be updated for your production domain
- No authentication or CMS integration is included - this is a static site template
- Images referenced in blog posts should be placed in the `public/` directory

**Custom Rules:** You can create additional `.continue/rules/*.md` files in subdirectories for component-specific or feature-specific documentation.