# React Fundamentals with TypeScript: Building a Todo App Step by Step

Welcome to our beginner-friendly guide to building a Todo App using React and TypeScript! We'll break this down into easy-to-follow steps, explaining each concept along the way.

### 1. Introduction to React

#### What is React?
- React is a JavaScript library for building user interfaces.
- It lets you create reusable components to build your app.

#### Why Use React?
- **Reusable Components**: Build once, use many times.
- **Efficient Updates**: React updates only what needs to change on your page.
- **Large Community**: Lots of resources and support available.

### 2. Setting Up Your Project

#### Step 1: Install Node.js and npm
1. Go to [nodejs.org](https://nodejs.org/)
2. Download and install Node.js (npm comes with it)

#### Step 2: Create a New React App with TypeScript
Open your command prompt or terminal and run:

```bash
npx create-react-app todo-app --template typescript
cd todo-app
npm start
```

This will:
- Create a new React project with TypeScript
- Move into the project folder
- Start the development server

Your app will open in a browser at `http://localhost:3000`.

#### 3. Creating the Basic App Structure

### Step 1: Clean Up the Project
1. In the `src/` folder, delete all files except `App.tsx` and `index.tsx`.
2. Open `src/App.tsx` and replace its content with:

```tsx
import React from 'react';

function App(): JSX.Element {
  return (
    <div>
      <h1>Todo App</h1>
    </div>
  );
}

export default App;
```

#### Step 2: Understanding Components
- The `App` function is a component.
- Components are like building blocks for your web page.
- They help organize and reuse code.

### 4. Adding Todo Functionality

#### Step 1: Set Up State for Todos
Update `src/App.tsx`:

```tsx
import React, { useState } from 'react';

interface Todo {
  text: string;
  completed: boolean;
}

function App(): JSX.Element {
  const [todos, setTodos] = useState<Todo[]>([]);
  const [newTodo, setNewTodo] = useState<string>('');

  return (
    <div>
      <h1>Todo App</h1>
    </div>
  );
}

export default App;
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
);
```

Add the `handleAddTodo` function:

```tsx
const handleAddTodo = (): void => {
  if (newTodo.trim() !== '') {
    const newTodoItem: Todo = { text: newTodo, completed: false };
    setTodos([...todos, newTodoItem]);
    setNewTodo('');
  }
};
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
  );
  setTodos(updatedTodos);
};
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
  const updatedTodos = todos.filter((_, i) => i !== index);
  setTodos(updatedTodos);
};
```

### 6. Styling the App

Create a new file `src/App.css` and add:

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
}

div {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  background-color: #fff;
}

input,
button {
  padding: 10px;
  margin: 5px 0;
}

li {
  list-style: none;
  margin: 5px 0;
  display: flex;
  justify-content: space-between;
}

li span {
  cursor: pointer;
}

button {
  margin-left: 10px;
}
```

Import the CSS in `src/App.tsx`:

```tsx
import './App.css';
```

### 7. Conclusion and Next Steps

Congratulations! You've built a functional Todo App using React and TypeScript. Here's what you've learned:

- **Components**: The building blocks of React apps
- **State**: Managing data within a component
- **Events**: Handling user interactions
- **Lists and Keys**: Displaying and managing lists of items
- **Conditional Rendering**: Changing display based on conditions
- **Styling**: Basic CSS to improve the look of your app

To further improve your skills, try:
- Adding a feature to edit existing todos
- Saving todos to local storage so they persist after page refresh
- Creating separate components for the todo list and todo items

Remember, practice makes perfect. Keep building and exploring React!
