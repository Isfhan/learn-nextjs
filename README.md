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
