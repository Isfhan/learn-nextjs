# React Fundamentals with TypeScript: Building a Todo App Step by Step (Vite Edition)

Welcome to our beginner-friendly guide to building a Todo App using React and TypeScript with Vite! We'll break this down into easy-to-follow steps, explaining each concept along the way. This tutorial will help you learn React fundamentals that are also applicable to Next.js development.

### 1. Introduction to React

#### What is React?

![React Logo](https://github.com/user-attachments/assets/1e80571e-6d88-427b-ad23-5f8f6810f15c)

- React is a JavaScript library for building user interfaces.
- It lets you create reusable components to build your app.

#### Why Use React?

- React is easy to learn and understand.
- It has a very active community where you can contribute and get help when needed.
- There are many job opportunities for React developers.
- React is perfect for developing Single Page Applications (SPAs).
- React Native allows you to develop native mobile apps.
- Large websites like Instagram, Facebook, and Reddit use React for front-end development.

Key benefits:
- **Reusable Components**: Build once, use many times.
- **Efficient Updates**: React updates only what needs to change on your page.
- **Large Community**: Lots of resources and support available.

### 2. Setting Up Your Project with Vite

#### Step 1: Install Node.js and npm
1. Go to [nodejs.org](https://nodejs.org/)
2. Download and install Node.js (npm comes with it)

#### Step 2: Create a New React App with TypeScript using Vite

![image](https://github.com/user-attachments/assets/2f8f8ee5-3bab-4a08-8c63-cee030668886)


Open your command prompt or terminal and run:

```bash
npm create vite@latest todo-app -- --template react-ts
cd todo-app
npm install
npm run dev
```

This will:
- Create a new React project with TypeScript using Vite
- Move into the project folder
- Install the necessary dependencies
- Start the development server

Your app will open in a browser at `http://localhost:5173`.

### 3. Understanding the Project Structure

In the `src/` folder, you'll find:
- `main.tsx`: The entry point of your application
- `App.tsx`: The main App component
- `vite-env.d.ts`: TypeScript declaration file for Vite

Open `src/App.tsx` and replace its content with:

```tsx
import React from 'react'

function App(): JSX.Element {
  return (
    <div>
      <h1>Todo App</h1>
    </div>
  )
}

export default App
```

#### Understanding Components
- The `App` function is a component.
- Components are like building blocks for your web page.
- They help organize and reuse code.

### 4. Adding Todo Functionality

#### Step 1: Set Up State for Todos
Update `src/App.tsx`:

```tsx
import React, { useState } from 'react'

interface Todo {
  text: string
  completed: boolean
}

function App(): JSX.Element {
  const [todos, setTodos] = useState<Todo[]>([])
  const [newTodo, setNewTodo] = useState<string>('')

  return (
    <div>
      <h1>Todo App</h1>
    </div>
  )
}

export default App
```

**Explanation:**
- `useState` is a React hook that lets us add state to our component.
- `todos` will store our list of todo items.
- `newTodo` will store the current value of the input field.

### Step 2: Add a Form to Create Todos
Update the return statement in `src/App.tsx`:

```tsx
return (
  <div>
    <h1>Todo App</h1>
    <input
      type="text"
      value={newTodo}
      onChange={(e) => setNewTodo(e.target.value)}
      placeholder="Enter todo"
    />
    <button onClick={handleAddTodo}>Add Todo</button>
  </div>
)
```

Add the `handleAddTodo` function:

```tsx
const handleAddTodo = (): void => {
  if (newTodo.trim() !== '') {
    const newTodoItem: Todo = { text: newTodo, completed: false }
    setTodos([...todos, newTodoItem])
    setNewTodo('')
  }
}
```

**Explanation:**
- The input field is connected to the `newTodo` state.
- `handleAddTodo` adds a new todo to the list when the button is clicked.

### 5. Enhancing the Todo List

#### Step 1: Display the Todo List
Add this to your return statement, after the button:

```tsx
<ul>
  {todos.map((todo, index) => (
    <li key={index}>
      <span style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}>
        {todo.text}
      </span>
    </li>
  ))}
</ul>
```

#### Step 2: Add Ability to Complete Todos
Update the `<li>` in your list:

```tsx
<li key={index}>
  <span
    style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
    onClick={() => handleToggleComplete(index)}
  >
    {todo.text}
  </span>
</li>
```

Add the `handleToggleComplete` function:

```tsx
const handleToggleComplete = (index: number): void => {
  const updatedTodos = todos.map((todo, i) =>
    i === index ? { ...todo, completed: !todo.completed } : todo
  )
  setTodos(updatedTodos)
}
```

#### Step 3: Add Ability to Delete Todos
Update the `<li>` in your list again:

```tsx
<li key={index}>
  <span
    style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
    onClick={() => handleToggleComplete(index)}
  >
    {todo.text}
  </span>
  <button onClick={() => handleDeleteTodo(index)}>Delete</button>
</li>
```

Add the `handleDeleteTodo` function:

```tsx
const handleDeleteTodo = (index: number): void => {
  const updatedTodos = todos.filter((_, i) => i !== index)
  setTodos(updatedTodos)
}
```

### 6. Styling the App

Create a new file `src/App.css` and add:

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
}

.container {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

input,
button {
  padding: 10px;
  margin: 5px 0;
}

input {
  width: calc(100% - 22px);
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  background-color: #0070f3;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0051bb;
}

ul {
  padding: 0;
}

li {
  list-style: none;
  margin: 5px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f9f9f9;
  padding: 10px;
  border-radius: 4px;
}

li span {
  cursor: pointer;
}

.delete-btn {
  background-color: #ff4d4f;
  margin-left: 10px;
}

.delete-btn:hover {
  background-color: #ff7875;
}
```

Import the CSS in `src/App.tsx`:

```tsx
import './App.css'
```

Update the outer `<div>` in your `App` component to include the `container` class:

```tsx
<div className="container">
  {/* ... existing content ... */}
</div>
```

### 7. Conclusion and Next Steps

Congratulations! You've built a functional Todo App using React and TypeScript with Vite. Here's what you've learned:

- **Components**: The building blocks of React apps
- **State**: Managing data within a component using hooks
- **Events**: Handling user interactions
- **Lists and Keys**: Displaying and managing lists of items
- **Conditional Rendering**: Changing display based on conditions
- **Styling**: Basic CSS to improve the look of your app

These concepts are fundamental to React and will be valuable when working with Next.js as well. To further improve your skills and prepare for Next.js, try:

1. **Adding a feature to edit existing todos**: This will help you understand more complex state updates.
2. **Saving todos to local storage**: This introduces the concept of side effects, which you can implement using the `useEffect` hook.
3. **Creating separate components for the todo list and todo items**: This will help you understand component composition and prop passing.
4. **Implementing server-side rendering**: While Vite doesn't support this out of the box like Next.js does, you can research how server-side rendering works and why it's beneficial.
5. **Exploring routing**: Next.js has a file-based routing system. You can experiment with a library like React Router to understand routing concepts.

Remember, practice makes perfect. Keep building and exploring React, and you'll be well-prepared for diving into Next.js!
