# How to Update the Site

## Local Development

Start the dev server:

```bash
npm run dev
```

Site runs at `http://localhost:4321`

## Making Changes

### Edit Site Config

Update `src/config.ts`:

```typescript
export const SITE = {
  website: "https://thefern.dev/",
  author: "0xTheFern",
  title: "0xTheFern",
  description: "Your site description",
  // ...
};
```

### Edit Social Links

Update `src/constants.ts`:

```typescript
export const SOCIALS: Social[] = [
  {
    name: "GitHub",
    href: "https://github.com/yourusername",
    linkTitle: "GitHub",
    icon: IconGitHub,
  },
  // Add more...
];
```

### Edit About Page

Edit `src/pages/about.md`

### Edit Navigation

Edit `src/components/Header.astro` to add/remove nav items.

## Publishing Changes

After making changes:

```bash
git add .
git commit -m "Your commit message"
git push
```

GitHub Actions will automatically build and deploy.

## Build Locally

To test the production build:

```bash
npm run build
npm run preview
```

## Common Tasks

| Task | Command |
|------|---------|
| Start dev server | `npm run dev` |
| Build for production | `npm run build` |
| Preview production build | `npm run preview` |
| Format code | `npm run format` |
| Lint code | `npm run lint` |
