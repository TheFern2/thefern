# Initial Deployment to GitHub Pages

## Prerequisites

- GitHub repository (e.g., `github.com/yourusername/thefern`)
- Custom domain (e.g., `thefern.dev`) configured in Squarespace

## Step 1: Update Astro Config

Edit `astro.config.ts`:

```typescript
export default defineConfig({
  site: "https://thefern.dev", // Your custom domain
  // Remove or comment out 'base' if using custom domain
});
```

## Step 2: Create GitHub Actions Workflow

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: npm run build

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./dist

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Step 3: Add CNAME File

Create `public/CNAME` with your domain:

```
thefern.dev
```

## Step 4: Enable GitHub Pages

1. Go to your repo on GitHub
2. Settings → Pages
3. Source: **GitHub Actions**

## Step 5: Configure Custom Domain in GitHub

1. Settings → Pages → Custom domain
2. Enter `thefern.dev`
3. Check "Enforce HTTPS"

## Step 6: Configure DNS in Squarespace

Add these DNS records in Squarespace:

### For apex domain (thefern.dev)

Add 4 `A` records pointing to GitHub's IPs:

| Type | Host | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |

### For www subdomain

| Type | Host | Value |
|------|------|-------|
| CNAME | www | yourusername.github.io |

## Step 7: Deploy

```bash
git add .
git commit -m "Initial deployment setup"
git push origin main
```

## Verify

1. Wait a few minutes for GitHub Actions to complete
2. Check Actions tab for build status
3. Visit `https://thefern.dev`

## Troubleshooting

- **DNS not resolving**: DNS changes can take up to 48 hours
- **Build failing**: Check Actions tab for error logs
- **404 errors**: Ensure `public/CNAME` exists with correct domain
- **HTTPS not working**: Wait for GitHub to provision SSL certificate (can take up to 24 hours)
