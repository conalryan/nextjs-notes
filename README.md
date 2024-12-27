# Next.js Notes

## Workspace Setup

```bash
pnpm init
```

```bash
echo "packages:\n  - \"packages/*\"" >> pnpm-workspace.yaml
```

## Packages

### 01 - Next.js Dashboard

`npx create-next-app@latest packages/01-nextjs-dashboard --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example" --use-pnpm`

`pnpm create next-app@latest packages/01-nextjs-dashboard --example "https://github.com/vercel/next-learn/tree/main/dashboard/starter-example"`

**Folder Structure:**

- /app: Contains all the routes, components, and logic for your application, this is where you'll be mostly working from.
- /app/lib: Contains functions used in your application, such as reusable utility functions and data fetching functions.
- /app/ui: Contains all the UI components for your application, such as cards, tables, and forms. To save time, we've pre-styled these components for you.
- /public: Contains all the static assets for your application, such as images.

Config Files: You'll also notice config files such as `next.config.js` at the root of your application. Most of these files are created and pre-configured when you start a new project using `create-next-app`. You will not need to modify them in this course.

**TypeScript:**

We're manually declaring the data types, but for better type-safety, we recommend `Prisma` or `Drizzle`, which automatically generates types based on your database schema.
Next.js detects if your project uses TypeScript and automatically installs the necessary packages and configuration. Next.js also comes with a TypeScript plugin
for your code editor, to help with auto-completion and type-safety.

**Run the app:**

`pnpm -F 01-nextjs-dashboard dev`
