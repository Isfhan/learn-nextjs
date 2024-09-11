# The Journey from Simple Websites to Next.js 14: How Web Development Evolved

A long time ago, when the internet was new, websites were like people walking on foot. This time was called **Web 1.0**, where websites were simple and basic—just like when humans only used their feet to travel.


### Stage 1: Web 1.0 - The Walking Age
![image](https://github.com/user-attachments/assets/ff229e37-154d-4f14-9d29-bdae8e583286)

In the beginning, websites were created using **HTML**, which is a simple language for making web pages. These websites were like walking everywhere—slow, simple, and everything had to be done by hand. If you wanted to change something, you had to open the file and change the code for every page. It was time-consuming, just like walking long distances!

#### Web 1.0
![image](https://github.com/user-attachments/assets/a246093b-16a9-4dca-9974-b1966098032c)

- **Features:** Only basic text and images.
- **Problem:** These websites were not interactive. Everything had to be done manually.



### Stage 2: CSS and JavaScript - The Horse and Cart Era
![image](https://github.com/user-attachments/assets/06d94a59-cdf0-42dc-8672-d4b08946257b)




Then, just like people learned to use horses and carts to travel faster, web developers learned to use **CSS** to make websites look better and **JavaScript** to add interactive features. This made websites a little more advanced, but it still took effort to manage everything.

#### Websites start looking better
![image](https://github.com/user-attachments/assets/2a0df598-1932-4ba3-972d-e7bef8d2a979)

- **Features:** Websites started looking better and became more interactive.
- **Problem:** Even though it was faster, it still wasn’t efficient enough for large websites.



### Stage 3: Backend Development - The Steam Engine Era
![image](https://github.com/user-attachments/assets/8f464280-af6e-4834-8631-feeb3c57fd9e)


As the world moved forward, people invented steam engines. In the web world, this was like the invention of **backend development** using tools like **PHP**. Instead of making pages one by one, websites could now connect to databases and create pages automatically. It was a huge improvement—just like trains made long-distance travel faster and easier.

#### Dynamic websites
![image](https://github.com/user-attachments/assets/24480e7f-9887-401f-bbae-83a19323839a)

- **Features:** Dynamic websites that could connect to databases and generate pages automatically.
- **Problem:** Even though it was powerful, it was also difficult to manage because the developers had to write both frontend and backend code.


### Stage 4: JavaScript Frameworks - Cars and Motorcycles Era
![image](https://github.com/user-attachments/assets/567cddd3-30e4-4086-a5d5-381158b4fc1e)


As people started using **cars** and **motorcycles**, travel became faster and more efficient. Similarly, web developers started using **JavaScript frameworks** like **React**, **Angular**, and **Vue**. These tools made it easy to build modern, dynamic websites—much like how cars made traveling more efficient.

#### Modren Js FrameWorks
![image](https://github.com/user-attachments/assets/7089640a-df0b-4453-8036-bca32e6c9406)

- **Features:** Easy-to-manage components and fast development.
- **Problem:** Although the frontend became easier, managing the backend separately was still a challenge.



### Stage 5: Full-Stack Frameworks - Airplane Era
![image](https://github.com/user-attachments/assets/dce6e0ef-3544-4aa6-9af8-5cdf1cfc714f)


After cars, people invented airplanes. Airplanes could cover long distances quickly, just like **Next.js** helped web developers build websites that were fast and efficient by combining both the frontend and backend.
**Next.js** allowed developers to build websites that were not only fast but also **dynamic** and **SEO-friendly**. It was like getting on a plane instead of driving a car—covering huge distances quickly and efficiently.

#### Next.js enters to solve react issues
![image](https://github.com/user-attachments/assets/92cb9c38-eb45-4b5c-a55d-caf58d605d52)

- **Features:** Server-side rendering, static site generation, and API routes—all in one place.
- **Problem:** Even though it’s powerful, you need to learn some new tools to use it properly.



### Stage 6: Next.js 14 - The Spaceship Era
![image](https://github.com/user-attachments/assets/c2f649bb-9e9c-4107-a5b5-deb3e95ba17a)



Now, with **Next.js 14**, we’ve entered the **spaceship** era of web development. This version brings even more flexibility, making it easy to build **hybrid websites**—some pages can be static (like a brochure), while others can be dynamic (like a real-time app). It’s like flying a spaceship, able to travel anywhere at top speed.

#### Next.js 14 with new features 
![image](https://github.com/user-attachments/assets/91e9f6ed-c26a-446f-8893-b5c959a34264)

- **New Features:** 
  - **App Router**: An easier way to manage routes in your web app.
  - **React Server Components**: Fetch data on the server, making pages load faster.
  - **Edge Functions**: APIs that work globally, making websites faster for users around the world.



### The Moral of the Story:

Just like transportation evolved from walking to space travel, web development also evolved from simple **HTML websites** to powerful frameworks like **Next.js 14**. Now, as web developers, we can build websites that are fast, scalable, and dynamic—using tools that make development easier, just like cars, planes, and spaceships make travel faster and more efficient.

In this course, you’ll learn how to fly the **spaceship** of **Next.js 14** and build amazing web applications that can take you anywhere you want in the digital world!


### Lets Create a "Hello World" App in Next.js 14

#### 1. **Installing Next.js 14**

Before we start, make sure you have **Node.js** installed. If not, you can download it from the official [Node.js website](https://nodejs.org/).

![image](https://github.com/user-attachments/assets/93c5b03f-d50b-45f7-a5ec-028f6163ee44)

To create a new Next.js project, we will use the following command:

```bash
npx create-next-app@latest hello-world-app
```

When you run this command, it will ask you a few questions:

- **Would you like to use TypeScript?** Choose either **yes** or **no** (for now, you can select **no** if you are not familiar with TypeScript).
- **Would you like to use ESLint?** This helps catch mistakes in your code. You can choose **yes** here.
- **Would you like to use Tailwind CSS?** Select **no** for now, as we are focusing on the basics.
- **Would you like to use the `src/` directory?** This helps organize your files better. Choose **yes**.
- **Would you like to use the App Router?** **Yes**, because we are using the latest **App Router** of Next.js 14.
- **Would you like to customize the default import alias?** Just press Enter to skip this.

![image](https://github.com/user-attachments/assets/dd651bad-9459-452b-96e0-57e99e752f6a)

After that, the project setup will begin. Once it’s finished, change into your project folder:

```bash
cd hello-world-app
```

Then, run the following command to start your development server:

```bash
npm run dev
```

Now open your browser and go to [http://localhost:3000](http://localhost:3000). You should see the default Next.js welcome page.



### Understanding the Folder Structure

When you open your project, you will see several files and folders. Here’s a simple explanation of the important ones:

- **/app**: This is the new folder where you’ll organize your pages using the **App Router**. You will create all your pages inside this folder.
- **/public**: This folder holds static files like images and icons. Any files here can be accessed directly in the browser.
- **/node_modules**: This folder contains all the libraries that your project is using. You don’t need to touch this.
- **package.json**: This file contains important information about your project, such as its name and the libraries it uses.
- **next.config.js**: This is where you can configure different settings for your Next.js app.
  


### Creating Your First Page – "Hello World"

Now, let’s create a simple **"Hello World"** page.

Go to the **/app** folder, and you’ll see a file called **page.tsx** or **page.js**. This is the default file for your homepage. You can delete the existing code and replace it with this:

```jsx
export default function Home() {
  return (
    <main>
      <h1>Hello World!</h1>
    </main>
  );
}
```

Now, if you go back to [http://localhost:3000](http://localhost:3000), you should see your **"Hello World!"** message displayed on the screen.



### App Router vs Page Router

Next.js 14 introduces a big change with the **App Router**. Earlier versions of Next.js used the **Page Router**. Let’s quickly look at the difference between them:

- **Page Router (Old)**:
  - Files were placed inside the **/pages** folder.
  - You had to use **getServerSideProps**, **getStaticProps**, and **getInitialProps** to fetch data.
  - Routing (navigating between pages) was handled by creating files like **index.js** for the home page and **about.js** for the "About" page.

- **App Router (New)**:
  - Now, you use the **/app** folder instead of **/pages**.
  - Data fetching is easier. You can use **React Server Components** to fetch data on the server, making pages faster.
  - The App Router also allows more flexibility, like **Server-Side Rendering (SSR)** and **Static Site Generation (SSG)** in one place.
  - You can now organize routes with folders. For example, creating a folder called **/app/about/page.js** will automatically create an "About" page at the URL **/about**.

In short, the **App Router** is the future. It’s easier, more powerful, and gives better performance.



### **Creating More Pages**

Let’s create another page using the **App Router**. This will be an "About" page.

1. Inside the **/app** folder, create a new folder called **about**.
2. Inside the **about** folder, create a file named **page.js** (or **page.tsx** if you’re using TypeScript).
3. Add the following code to **about/page.js**:

```jsx
export default function About() {
  return (
    <main>
      <h1>About Us</h1>
      <p>This is the about page of our Next.js 14 app!</p>
    </main>
  );
}
```

Now, if you go to [http://localhost:3000/about](http://localhost:3000/about), you will see the "About Us" page.
