# Next.js Routing

### What is Routing?

Imagine you're in Lahore, and you want to visit different places in the city. You need a map to know which roads to take to reach your destination. In web development, routing is like that map. It tells your application which content to show when a user visits different parts of your website.

![image](https://github.com/user-attachments/assets/dd8d8edc-b848-433c-8ef6-b050c79dae4f)

### Real-world Example:

Think of a popular Pakistani e-commerce website like Daraz. When you visit daraz.pk, you see the home page. If you click on "motherboard," the URL changes to **daraz.pk/motherboard**, and you see a different page. This is routing in action!
Next.js uses a file-system based router, which means the structure of your files and folders determines the routes in your application. Here's a quick overview of how it works:

### Understanding Routes

A route is like an address for a specific page on your website. In Next.js, we create routes by organizing our files and folders in a specific way.

### File-based Routing in Next.js 14

Next.js 14 uses a file-based routing system. This means that the structure of your files and folders determines the routes of your application.
**Folders as Routes**: Each folder in the `app` directory represents a route segment. For example, a folder named `dashboard` will create a route `/dashboard`.

Let's look at a simple example:

```
app/
├── page.tsx
├── about/
│   └── page.tsx
└── products/
    ├── page.tsx
    └── [id]/
        └── page.tsx
```

In this structure:
- `/` shows the content of `app/page.tsx`
- `/about` shows the content of `app/about/page.tsx`
- `/products` shows the content of `app/products/page.tsx`
- `/products/123` shows the content of `app/products/[id]/page.tsx` (where 123 is the product ID)

### Types of Routes in Next.js

1. Page Routes
2. Nested Routes
3. Dynamic Routes
4. Route Groups
5. Catch-all Routes
6. Optional Catch-all Routes
7. Parallel Routes
8. Intercepting Routes

Each of these routing techniques serves different purposes and can be combined to create flexible and powerful routing structures in your Next.js applications. The key is to choose the right technique (or combination of techniques) based on your specific requirements and the complexity of your application.

### Next.js Routing Conventions

To better understand how Next.js handles routing, it's important to know about some special files and conventions:

#### Special Files in Next.js

Next.js uses special files to make your website work smoothly. Here are the main ones:

1. `layout.tsx`: This file creates a shared look for a group of pages.
2. `page.tsx`: This is where you put the main content of each page.
3. `loading.tsx`: This shows a loading message or spinner while your page is getting ready.
4. `not-found.tsx`: This shows a message when a page can't be found.
5. `error.tsx`: This handles errors and shows a nice message to users.

#### How Pages Are Built

Next.js builds your pages in a specific order:

1. It starts with the `layout.tsx`
2. Then it adds any error handling (`error.tsx`)
3. Next comes the loading screen (`loading.tsx`)
4. Finally, it puts in the main content (`page.tsx`)

If you have pages inside other pages, it builds them from the outside in.

#### Keeping Files Together

Next.js lets you keep all the files for a page in the same folder. This includes the main page file, any special components, and even CSS files. It's like keeping all your tools for one job in the same toolbox.

This organization helps you:
- Find files easily
- Understand how your page works
- Keep things tidy

Remember, only the `page.tsx` file becomes a web address. The other files are just there to help build that page.

By understanding these routing conventions, you can create well-organized and efficient Next.js applications that are easy to maintain and scale.


### 1. Page Routes

Page routes are the simplest and most common form of routing, directly corresponding to your file structure.

**When to use:** For pages with fixed content that don't need dynamic data from the URL.

**Code Example:**
```typescript
// app/page.tsx
export default function Home() {
  return <h1>Welcome to our company!</h1>
}

// app/about/page.tsx
export default function About() {
  return <h1>About Us</h1>
}

// app/contact/page.tsx
export default function Contact() {
  return <h1>Contact Us</h1>
}
```

**How to access:**
- Home page: `http://yourdomain.com/`
- About page: `http://yourdomain.com/about`
- Contact page: `http://yourdomain.com/contact`

### 2. Nested Routes

Nested routes allow you to create hierarchical page structures, reflecting more complex site architectures.

**When to use:** When you need to organize your content in a hierarchical structure, such as for product categories or documentation sections.

**Code Example:**
```typescript
// app/products/page.tsx
export default function Products() {
  return <h1>All Products</h1>
}

// app/products/electronics/page.tsx
export default function Electronics() {
  return <h1>Electronics Products</h1>
}

// app/products/electronics/computers/page.tsx
export default function Computers() {
  return <h1>Computer Products</h1>
}
```

**How to access:**
- All Products: `http://yourdomain.com/products`
- Electronics: `http://yourdomain.com/products/electronics`
- Computers: `http://yourdomain.com/products/electronics/computers`

### 3. Dynamic Routes

Dynamic routes allow you to create pages that can handle variable parameters in the URL.

**When to use:** When you need to create pages that display content based on URL parameters.

**Code Example:**
```typescript
// app/products/[id]/page.tsx
export default function Product({ params }: { params: { id: string } }) {
  return <h1>Product Details for product {params.id}</h1>
}
```

**How to access:**
- Product page: `http://yourdomain.com/products/1234` (where 1234 is the product ID)

### 4. Route Groups

Route groups allow you to organize routes without affecting the URL structure.

**When to use:** When you want to organize your route files without affecting the URL structure, often used for sections of a site.

**Code Example:**
```typescript
// app/(admin)/dashboard/page.tsx
export default function AdminDashboard() {
  return <h1>Admin Dashboard</h1>
}

// app/(admin)/users/page.tsx
export default function UserManagement() {
  return <h1>User Management</h1>
}
```

**How to access:**
- Admin Dashboard: `http://yourdomain.com/dashboard`
- User Management: `http://yourdomain.com/users`

Note that "admin" doesn't appear in the URL.

### 5. Catch-all Routes

Catch-all routes can handle an unknown number of path segments.

**When to use:** When you need to handle an unknown number of path segments, such as for a hierarchical documentation site.

**Code Example:**
```typescript
// app/docs/[...slug]/page.tsx
export default function Doc({ params }: { params: { slug: string[] } }) {
  return <h1>Documentation for: {params.slug.join('/')}</h1>
}
```

**How to access:**
- Documentation page: `http://yourdomain.com/docs/react/hooks/usestate`

### 6. Optional Catch-all Routes

Similar to catch-all routes, but also matches the parent path.

**When to use:** When you want to handle both the root path and nested paths with the same component.

**Code Example:**
```typescript
// app/blog/[[...slug]]/page.tsx
export default function Blog({ params }: { params: { slug?: string[] } }) {
  if (!params.slug) {
    return <h1>All Blog Posts</h1>
  }
  return <h1>Blog Posts for: {params.slug.join('/')}</h1>
}
```

**How to access:**
- All blog posts: `http://yourdomain.com/blog`
- Filtered blog posts: `http://yourdomain.com/blog/2023/06`

### 7. Parallel Routes

Parallel routes allow you to simultaneously render multiple pages in the same layout.

**When to use:** When you need to show multiple independent components in the same layout, often used for dashboards or split views.

**Code Example:**
```typescript
// app/layout.tsx
export default function DashboardLayout(props: {
  children: React.ReactNode
  feed: React.ReactNode
  notifications: React.ReactNode
}) {
  return (
    <>
      {props.children}
      {props.feed}
      {props.notifications}
    </>
  )
}

// app/@feed/page.tsx
export default function Feed() {
  return <div>Feed Content</div>
}

// app/@notifications/page.tsx
export default function Notifications() {
  return <div>Notifications Content</div>
}
```

**How to access:**
- Dashboard with parallel routes: `http://yourdomain.com/dashboard`

### 8. Intercepting Routes

Intercepting routes allow you to intercept a route and show different content while keeping the original URL.

**When to use:** When you want to display a different view (like a modal) while keeping the user on the current page.

**Code Example:**
```typescript
// app/gallery/page.tsx
export default function Gallery() {
  return <h1>Photo Gallery</h1>
}

// app/gallery/(..)photo/[id]/page.tsx
export default function PhotoModal({ params }: { params: { id: string } }) {
  return <div>Photo Modal for photo {params.id}</div>
}
```

**How to access:**
- Gallery page: `http://yourdomain.com/gallery`
- Photo modal: `http://yourdomain.com/gallery/photo/1234` (where 1234 is the photo ID)
### Combining Techniques: E-commerce Site Example

Often, you'll need to combine these techniques for more complex routing scenarios.

**Code Example:**
```typescript
// app/shop/[...categories]/page.tsx
export default function Category({ params }: { params: { categories: string[] } }) {
  return <h1>Category: {params.categories.join(' > ')}</h1>
}

// app/shop/[...categories]/[productId]/page.tsx
export default function Product({ params }: { params: { categories: string[], productId: string } }) {
  return (
    <>
      <h1>Category: {params.categories.join(' > ')}</h1>
      <h2>Product ID: {params.productId}</h2>
    </>
  )
}
```

**How to access:**
- Category page: `http://yourdomain.com/shop/electronics/computers`
- Product page: `http://yourdomain.com/shop/electronics/computers/laptops/1234` (where 1234 is the product ID)

By combining these routing techniques, you can create flexible and powerful routing structures in your Next.js applications. The key is to choose the right technique (or combination of techniques) based on your specific requirements and the complexity of your application.
