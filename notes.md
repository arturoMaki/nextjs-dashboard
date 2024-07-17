## Topics

- Folder structure in Nextjs
- CSS styling
  - Tailwind 
  - CSS Modules 
  - CLSX

- [Fonts optimization](https://nextjs.org/docs/app/building-your-application/optimizing/fonts):
  
  -  downloaded as static assets during build time

- [Next Image Component:](https://nextjs.org/docs/app/building-your-application/optimizing/images)
  
  - Preventing layout shift automatically when images are loading.
  - Resizing images to avoid shipping large images to devices with a smaller viewport.
    - **Warning**: Dynamic await import() or require() are not supported. The import must be static so it can be analyzed at build time.
  - Lazy loading images by default (images load as they enter the viewport).
  - Serving images in modern formats, like WebP and AVIF, when the browser supports it. 

- File-System Routing
  
  - page.tsx
  - loading.tsx
  - layout.tsx
  
    - children props
    - [Partial rendering](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#4-partial-rendering)
    - Soft navigation
    - RootLayout 
      - `/app/layout.tsx`
      - `<html>` and `<body>` tags, and add metadata.
  
- Client Side Routing `<Link />`
  
  - automatically code splits your application by route segments
  -  (Only in PROD) whenever `<Link>` components appear in the browser's viewport, Next.js automatically prefetches the code for the linked route in the background. By the time the user clicks the link, the code for the destination page will already be loaded in the background, and this is what makes the page transition near-instant.
  
-  Data Fetching
 
    -  Api Layer
    -  Waterfall or Parallel data fetching
  
- Component Rendering
  
  - Static Rendering 
    -  Build time 
    -  No data needed or data accross users
    -  Benefits:
        - Faster Websites
        - Reduce Server Load
        - SEO
  
  - Dynamic Rendering
    - Data is render server side at request time
    - Real time data
      - User specific content 
      - Access request time information (cookies, URL params, tokens)
    - Streaming
      - page lebel - loading.tsx
      - component lebel - Suspense
  
  - Partial Prerendering
    - Prerender the static parts of your route and defer the dynamic parts until the user requests them.
    - The Suspense fallback is embedded into the initial HTML file along with the static content. At build time (or during revalidation), the static content is prerendered to create a static shell. The rendering of dynamic content is postponed until the user requests the route.
    - Requiere `export const experimental_ppr = true;` on your layout file.

- URL search params in SSR components
  
  - Benefits:
    - Bookmarkable and Shareable URLs
    - Server-Side Rendering and Initial Load
    - Analytics and Tracking
    - Client side navigation prevent to rerender the page when the URL changes
  - Features:
    - useSearchParams
    - usePathname
    - useRoute
  
- Server Actions
  
  - Run asynchronous code directly on the server 
  - Functions that can be invoke into Client or Server Components
  - [Security solution](https://nextjs.org/blog/security-nextjs-server-components-actions):
    - POST request
    - encrypted closures
    - strict input checks
    - error message hashing
    - host restrictions
  - Best practice to use server actions to mutate date in forms
  
- Catching Error
  
  - [error.tsx](https://nextjs.org/docs/app/api-reference/file-conventions/error) catches errors in your route segments, and show a fallback UI to the user.
    - It serves as a catch-all for unexpected errors 
    - needs to be a Client Component.
    - It accepts two props:
      - error: This object is an instance of JavaScript's native Error object.
      - reset: This is a function to reset the error boundary. When executed, the function will try to re-render the route segment.
  - [notFound](https://nextjs.org/docs/app/api-reference/functions/not-found) function and [not-found.tsx](https://nextjs.org/docs/app/api-reference/file-conventions/not-found) file to handle 404 errors (for resources that don’t exist).
    - notFound will take precedence over error.tsx, so you can reach out for it when you want to handle more specific errors
  
- Authentication vs. Authorization 