# Next.js Routing and Navigation

### What is Routing?

Imagine you're in Lahore, and you want to visit different places in the city. You need a map to know which roads to take to reach your destination. In web development, routing is like that map. It tells your application which content to show when a user visits different parts of your website.

![image](https://github.com/user-attachments/assets/dd8d8edc-b848-433c-8ef6-b050c79dae4f)

### Real-world Example:

Think of a popular Pakistani e-commerce website like Daraz. When you visit daraz.pk, you see the home page. If you click on "motherboard," the URL changes to **daraz.pk/motherboard**, and you see a different page. This is routing in action!

### Understanding Routes

A route is like an address for a specific page on your website. In Next.js, we create routes by organizing our files and folders in a specific way.

### File-based Routing in Next.js 14

Next.js 14 uses a file-based routing system. This means that the structure of your files and folders determines the routes of your application.

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


### 1. Static Routes

Static routes are the simplest and most common form of routing, directly corresponding to your file structure.

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

### 2. Dynamic Routes

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

### 3. Route Groups

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

### 4. Catch-all Routes

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

### 5. Optional Catch-all Routes

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

### 6. Parallel Routes

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

### 7. Intercepting Routes

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
