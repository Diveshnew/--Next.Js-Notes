# Next.Js-Notes

### 1. Getting Started

>KeyTerms to Remember in this section:
```
Client components
Client-side Rendering (CSR)
Dynamic rendering
Node.js runtime 
Server components
Server-side Rendering (SSR)
Static rendering
Static Site Generation (SSG)
```

- Next.js is a framework for building fast, and search-engine friendly applications. 
- It includes a compiler for transforming and minifying JavaScript code, a Command-line 
Interface (CLI) for building and starting our application, and a Node.js runtime for 
running backend code. This enables full-stack development. 
- With Next.js, we can render our components on the server and return their content to 
the client. This technique is called Server-side Rendering (SSR) and makes our 
applications search-engine friendly. 
- To further improve performance, we can pre-render pages and components that have 
static data during the build and serve them whenever needed. This technique is called 
Static Site Generation (SSG).
- The new app router in `Next.js 13` makes it incredibly easy to create routes. We can 
define route segments by creating directories. To make a route public, we add a page 
file `(page.js, page.jsx, or page.tsx)` in the corresponding directory. 
- Next.js provides the Link component to enable client-side navigation. This means as 
the user navigates between pages, the new content is loaded quickly and smoothly 
without the entire page being reloaded. 
- Next.js 13 supports client and server components introduced in React 18. Client 
components are rendered on the client within a web browser. This technique is 
called `Client-side Rendering (CSR)` and it’s how traditional React apps work. Server 
components are rendered on the server within a Node.js runtime. This technique is 
called `Server-side Rendering (SSR)`.
- Server components lead to reduced bundle sizes, better performance, increased 
search engine visibility, and enhanced security. But they cannot handle browser 
events, access browser APIs, or use the state or effect hooks. These functionalities 
are only available in client components. So we should use them whenever possible 
unless we need interactivity.
- All the components and pages in the `/app` directory are server components by 
default. To make a component a client component, we add the ‘use client’ directive 
on top of the component file.
- Server components are great for fetching data because they don’t require extra 
server trips, making our application faster and more search-engine friendly. 
- Next.js enhances the `fetch()` function by adding automatic caching. This boosts 
performance and reduces the need to retrieve the same piece of data twice.
- In Next.js, components can be rendered at build time `(called Static Rendering)` or at 
request time `(called Dynamic Rendering)`. If we have pages or components with 
static data, we can pre-render them during build time to improve our application’s 
performance.

## `Key Commands`
```JavaScript
// Creating a new project
npx create-next-app
```
```JavaScript
// Running the dev server
npm run dev
```
```JavaScript
// Building the application
npm run build
```
```JavaScript
// Starting the application in production mode
npm start
```

### 2. Styling
> KeyTerms to Remember in this section:
```
CSS modules
Daisy UI
Global styles
PostCSS
Tailwind
```
- In Next.js projects, we define global styles in `/app/global.css`. Reserve this file for global 
styles that need to be applied across multiple pages and components. Avoid adding 
excessive styles to this file, as it can quickly grow out of hand and become difficult to 
maintain.
- In traditional CSS, if we define the same class in two different files, one will overwrite 
the other depending on the order in which these files are imported. CSS modules help us 
prevent this problem. A CSS module is a CSS file that is scoped to a page or component. 
- During the build process, Next.js uses a tool called PostCSS to transform our CSS class 
names and generate unique class names. This prevents clashes between different CSS 
classes across the application.
- `Tailwind` is a widely-used CSS framework for styling application. It offers a 
comprehensive set of small, reusable utility classes. We can combine these classes to 
create beautiful user interfaces.
- `DaisyUI` is a component library built on top of Tailwind. It provides a collection of predesigned and reusable components such as accordion, badge, car, etc.

### 3. Routing and Navigation
> KeyTerms to Remember in this section:
```
Client cache
Dynamic routes
Layout
Prefetching
```

- The new App router in Next.js uses convention over configuration to define routes. It 
looks for special files such as `page.tsx`, `layout.tsx`, `loading.tsx`, `route.tsx`, etc. 
- With the App router, we can colocate our pages and their building blocks (eg 
components, services, etc). This helps us better organize our projects as we can keep 
highly related files next to each other. No need to dump all the components in a 
centralized components directory. 
- A dynamic route is one that takes one or more parameters. To add parameters to our 
routes, we wrap directory names with square brackets `(eg [id])`. 
- In standard React applications, we use the state hook for managing component state. In 
server-rendered applications, however, we use query string parameters to keep state. 
This also allows us to bookmark our pages in specific state. For example, we can 
bookmark a filtered and sorted list of products.
- We use layout files `(layout.tsx)` to create UI that is shared between multiple pages. The 
root layout `(/app/layout.tsx)` defines the common UI for all our pages. We can create 
additional layouts for specific areas of our application `(eg /app/admin/layout.tsx)`.
- To provide smooth navigation between pages, the Link component prefetches the links 
that are in the viewport. 
-  As the user moves around our application, Next.js stores the page content in a cache on 
the client. So, if they revisit a page that already exists in the cache, Next.js simply grabs 
it from the cache instead of making a new request to the server. The client cache exists 
in the browser’s memory and lasts for an entire session. It gets reset when we do a full 
refresh.

## `File Convention`
```JavaScript
page.tsx
```
```JavaScript
layout.tsx
```
```JavaScript
loading.tsx
```
```JavaScript
not-found.tsx
```
```JavaScript
error.tsx
```

## `Accessing Route and Query String Parameters`
```Javascript
interface Props {
  params: { id: string },
  searchParams: { sortOrder: string }
}

export default function Home( { params, searchParams }: Props ){
}
```

### `Programmatic Navigation`
```Javascript
const router = useRouter();
router.push('/')
```
