## Topics

- Folder structure in Nexts
- CSS styling: Tailwind - CSS Modules - CLSX -
- [Fonts optimization](https://nextjs.org/docs/app/building-your-application/optimizing/fonts):
  
  -  downloaded as static assets during build time
- [Next Image Component:](https://nextjs.org/docs/app/building-your-application/optimizing/images)
  
  - Preventing layout shift automatically when images are loading.
  - Resizing images to avoid shipping large images to devices with a smaller viewport.
    - **Warning**: Dynamic await import() or require() are not supported. The import must be static so it can be analyzed at build time.
  - Lazy loading images by default (images load as they enter the viewport).
  - Serving images in modern formats, like WebP and AVIF, when the browser supports it. 
- File-system Routing
  
  - page.tsx
  - loading.tsx
  - layout.tsx
  
    - children prop
    - [Partial rendering](https://nextjs.org/docs/app/building-your-application/routing/linking-and-navigating#4-partial-rendering)
    - Soft navigation
    - RootLayout `/app/layout.tsx`
      - <html> and <body> tags, and add metadata.
  - <Link /> component - client side routing
    -  <Link> components appear in the browser's viewport, Next.js automatically prefetches the code for the linked route in the background.
-  Data Fetching
 
    -  Api Layer
    -  Waterfall - Parallel data fetching
- Component Rendering
  - Static Rendering - Build time - No data pages or data accross users
     - Faster Websites
     - Reduce Server Load
     - SEO
  - Dynamic Rendering
    - Data is render server side at request time
    - Real time data - User specifc content - Access request time information (cookies, URL params, tokens)
    - Streaming
      - page lebel - loading.tsx
      - component lebel - Suspense
  - Partial Prerendering
    - prerender the static parts of your route and defer the dynamic parts until the user requests them 