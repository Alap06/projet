# Project Structure — Diary Marketplace

This document explains the organization of the codebase for the Diary Marketplace project.

## Overview

The project is built using **TanStack Start**, a full-stack framework for React that provides server-side rendering (SSR), streaming, and a powerful routing system.

## Directory Layout

```
projet/
├── .github/              # GitHub Actions (if any)
├── .wrangler/            # Cloudflare Wrangler cache
├── dist/                 # Production build output (generated)
├── node_modules/         # Dependencies
├── src/                  # Source code
│   ├── assets/           # Static assets (images, etc.)
│   ├── components/       # React components
│   │   └── ui/           # Shadcn UI components (reusable)
│   ├── context/          # React Context providers (state management)
│   ├── data/             # Mock data and constants
│   ├── hooks/            # Custom React hooks
│   ├── lib/              # Utility functions and external integrations
│   ├── routes/           # File-based routing (TanStack Router)
│   │   ├── __root.tsx    # Root layout and shell
│   │   ├── index.tsx     # Landing page
│   │   └── ...           # Other pages
│   ├── router.tsx        # Router configuration
│   ├── routeTree.gen.ts  # Generated route tree (do not edit)
│   └── styles.css        # Main stylesheet (Tailwind 4)
├── components.json       # Shadcn UI configuration
├── eslint.config.js      # ESLint configuration
├── package.json          # Project metadata and dependencies
├── tsconfig.json         # TypeScript configuration
├── vite.config.ts        # Vite configuration
└── wrangler.jsonc        # Cloudflare configuration
```

## Key Architectural Decisions

1. **State Management**: Uses React Context (`AuthProvider`, `CartProvider`, etc.) for simplicity and local persistence where needed.
2. **Styling**: Uses **Tailwind CSS v4** with CSS variables for a modern, high-performance design system.
3. **Routing**: Uses **TanStack Router** for type-safe, file-based routing.
4. **Icons**: Uses **Lucide React** for consistent iconography.
5. **UI Components**: Uses **Shadcn UI** (Radix UI) for accessible and customizable components.

## Core Features

- **Marketplace**: Browse dishes, filter by region/category.
- **Cart & Checkout**: Multi-step checkout process.
- **Roles**:
  - **Client**: Browse and order.
  - **Cuisinier (Cook)**: Manage dishes and orders.
  - **Admin**: Validate new dishes and oversee the platform.
- **SSR**: Server-side rendering for SEO and performance.
