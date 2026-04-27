# Deployment Guide — Diary Marketplace

This project is built with TanStack Start and is optimized for edge deployment, particularly on **Cloudflare Pages**.

## 1. Cloudflare Pages (Recommended)

Since the project already contains a `wrangler.jsonc`, Cloudflare Pages is the most straightforward deployment target.

### Prerequisites

- A Cloudflare account.
- [Wrangler CLI](https://developers.cloudflare.com/workers/wrangler/install-setup/) installed (`npm install -g wrangler`).

### Steps

1. **Connect to GitHub**: Link your repository to Cloudflare Pages.
2. **Configure Build Settings**:
   - **Framework Preset**: None (or select Vite if available).
   - **Build Command**: `npm run build`
   - **Build Output Directory**: `dist/client` (Note: TanStack Start output might vary based on config, but usually `dist` is the root).
3. **Environment Variables**:
   - Set `NODE_VERSION` to `20` or higher.
4. **Deploy**: Cloudflare will automatically build and deploy your project on every push.

## 2. Vercel

Vercel supports TanStack Start through the `@tanstack/react-start` adapter.

### Steps

1. Import your project into Vercel.
2. Vercel should detect the Vite/TanStack Start configuration automatically.
3. If not, set the build command to `npm run build` and output directory to `.output` or `dist`.

## 3. Manual Server (Node.js)

To run the production build on a standard VPS:

1. **Build**: `npm run build`
2. **Start**: `npm run start` (You may need to add this script to `package.json`).

### Adding Start Script

If you want to run on Node.js, add this to `package.json`:

```json
"scripts": {
  "start": "node dist/server/index.js"
}
```

## Environment Variables

Create a `.env` file in production (or set them in your dashboard):

| Variable       | Description                                      |
| -------------- | ------------------------------------------------ |
| `VITE_API_URL` | (Optional) URL of your backend API               |
| `DATABASE_URL` | (Future) If you move from mock data to a real DB |

## Best Practices for Production

1. **Clean Builds**: Always run `npm run clean` before a fresh production build.
2. **Type Checking**: Run `npm run typecheck` to ensure no hidden type errors.
3. **Linting**: Run `npm run lint` to ensure code quality.
4. **Images**: Ensure all images are optimized. The current project uses Unsplash URLs which are already optimized by their CDN.
