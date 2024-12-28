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

### Chapter 2 - Styling

- How to add a global CSS file to your application.
- Two different ways of styling: Tailwind and CSS modules.
- How to conditionally add class names with the clsx utility package.

**Global CSS:**

Defined in `/app/ui/global.css` and imported in `/app/layout.tsx`
You can import `global.css` in any component however, it's commone to add it to your top-level component i.e. the root layout.

**Tailwind:**

Tailwind is a CSS framework that speeds up the development process by allowing you to quickly write utility classes directly in your TSX markup.

Although the CSS styles are shared globally, each class is singularly applied to each element. This means if you add or delete an element, you don't have to worry about maintaining separate stylesheets, style collisions, or the size of your CSS bundle growing as your application scales.

**CSS Modules**

If you prefer writing traditional CSS rules or keeping your styles separate from your JSX - CSS Modules are a great alternative.
CSS Modules allow you to scope CSS to a component by automatically creating unique class names, so you don't have to worry about style collisions as well.

**clsx**

clsx is a library that lets you toggle class names conditionally.

```tsx
import clsx from 'clsx';
 
export default function InvoiceStatus({ status }: { status: string }) {
  return (
    <span
      className={clsx(
        'inline-flex items-center rounded-full px-2 py-1 text-sm',
        {
          'bg-gray-100 text-gray-500': status === 'pending',
          'bg-green-500 text-white': status === 'paid',
        },
      )}
    >
    // ...
  );
}
```

**Other styling solutions**

In addition to the approaches we've discussed, you can also style your Next.js application with:
- Sass which allows you to import .css and .scss files.
- CSS-in-JS libraries such as styled-jsx, styled-components, and emotion.

