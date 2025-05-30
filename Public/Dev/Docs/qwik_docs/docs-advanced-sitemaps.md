# https://qwik.dev/docs/advanced/sitemaps/

[Original link](https://qwik.dev/docs/advanced/sitemaps/)

# Generating Sitemaps

## Generating Sitemaps in SSG

By default, when Static Site Generated (SSG) pages are built, a sitemap is generated for the site. The sitemap.xml is automatically generated based on the pages that were built. This means that if you have a page that is not built, it will not be included in the sitemap.

### Configuration

The sitemap can be configured using the adapter's vite config file. The example below is configuring the Cloudflare adapter. The default sitemap file path is sitemap.xml, but you can use the sitemapOutFile option to change the file path.

```
plugins: [
    cloudflarePagesAdapter({
      ssg: {
        include: ['/*'],
        origin: 'https://qwik.dev',
        sitemapOutFile: 'sitemap.xml',
      },
    }),
  ]
```

The include option is used to specify which pages should be built, which also adds them to the sitemap. Any pages added to the exclude option will also exclude them from the sitemap.

The origin option is used to specify the origin of the site and is used to generate the absolute URLs for the sitemap.

### robots.txt

Depending on your site setup, you'll probably want to add a robots.txt file to your site. This can be done by adding a robots.txt file to the public directory. Any file in the public directory is treated as a static file and deploy alongside the build. The following is an example of a public/robots.txt file:

```
User-agent: *
Allow: /
 
Sitemap: https://<YOUR_HOSTNAME>/sitemap.xml
```

Note the added Sitemap directive to the robots.txt file which tells search engines where to find the sitemap for your site. Be sure to replace <YOUR_HOSTNAME> with the hostname of your site.

## Generating Dynamic Sitemaps in SSR

In addition to generating sitemaps for Static Site Generation (SSG), you can also generate sitemaps dynamically with Server-Side Rendering (SSR). This is useful if your site has content that is not known at build time or is frequently updated.

To generate a dynamic sitemap in SSR, you can create a route that serves a dynamic-sitemap.xml file based on your site’s routes and other dynamic content. Below is an example of how to set this up.

### Create a Sitemap Function

First, create a function that generates the sitemap XML based on the routes you want to include. You can create this function in a file such as src/routes/dynamic-sitemap.xml/create-sitemap.ts:

```
// src/routes/dynamic-sitemap.xml/create-sitemap.ts
 
export interface SitemapEntry {
  loc: string;
  priority: number;
}
 
export function createSitemap(entries: SitemapEntry[]) {
  const baseUrl = "https://<YOUR_HOSTNAME>";
 
  return `
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
${entries.map(
  (entry) => `
    <url>
        <loc>${baseUrl}${entry.loc.startsWith("/") ? "" : "/"}${entry.loc}</loc>
        <priority>${entry.priority}</priority>
    </url>`,
)}
</urlset>`.trim();
}
```

### Set Up a Route for the Dynamic Sitemap

Next, set up a route that will use the sitemap function to generate the sitemap dynamically. Create a file like src/routes/dynamic-sitemap.xml/index.tsx:

```
// src/routes/dynamic-sitemap.xml/index.tsx
 
import type { RequestHandler } from "@builder.io/qwik-city";
import { routes } from "@qwik-city-plan";
import { createSitemap } from "./create-sitemap";
 
export const onGet: RequestHandler = (ev) => {
  const siteRoutes = routes
    .map(([route]) => route as string)
    .filter(route => route !== "/");  // Exclude the '/' route
 
  const sitemap = createSitemap([
    { loc: "/", priority: 1 },  // Manually include the root route
    ...siteRoutes.map((route) => ({
      loc: route,
      priority: 0.9,  // Default priority, adjust as needed
    })),
  ]);
 
  const response = new Response(sitemap, {
    status: 200,
    headers: { "Content-Type": "text/xml" },
  });
 
  ev.send(response);
};
```

This route dynamically creates the sitemap XML based on the routes in your Qwik City application.

### robots.txt

To ensure that search engines know where to find your dynamic sitemap, you should also add or update your robots.txt file. Add the following line to your robots.txt file, which is typically located in your public directory:

```
User-agent: *
Allow: /
 
# Uncomment the following line and replace <unindexedFolder> with the actual folder name you want to disallow
# Disallow: /<unindexedFolder>/
 
Sitemap: https://<YOUR_HOSTNAME>/dynamic-sitemap.xml
```

Be sure to replace <YOUR_HOSTNAME> with your actual site URL.

This setup will dynamically generate and serve a dynamic.sitemap.xml whenever it is requested, keeping it up to date with the latest routes and changes to your site.

### Contributors

Thanks to all the contributors who have helped make this documentation better!
