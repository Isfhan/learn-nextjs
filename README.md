# **React Fundamentals with TypeScript: Building a Todo App**

Welcome to our exciting journey into the world of React with TypeScript. Think of this as a fun cooking class where we'll prepare a delicious dish called a "Todo App." You've already got the basic ingredients—HTML, CSS, and TypeScript. Now, let's mix them together to create something amazing!

### **What is React?**

Before we start cooking, let's understand what our main ingredient is.

**React** is a **JavaScript library** (we'll use TypeScript) that helps us build user interfaces for websites. Think of React as a set of tools that makes it easier to build complex web pages by breaking them into small, reusable pieces called **components**.

### **Why Use React?**

- **Reusable Components**: Like reusing a favorite recipe, you can use components in different parts of your app.
- **Fast Performance**: React updates only the parts of the web page that need to change, making it quick.
- **Strong Community**: Many people use React, so there are lots of resources and help available.

### **Setting Up Your Workspace**

#### **Step 1: Install Node.js and npm**

Just like you need a kitchen to cook, you need **Node.js** and **npm** to work with React.

- **Node.js** allows us to run JavaScript on our computer, outside of a web browser.
- **npm** (Node Package Manager) helps us install and manage code packages.

You can download both from [nodejs.org](https://nodejs.org/).

#### **Step 2: Create a New React App with TypeScript**

Open your command prompt or terminal and type the following commands:

```bash
npx create-react-app todo-app --template typescript
cd todo-app
npm start
```

- **`npx create-react-app todo-app --template typescript`**: This creates a new React project named **todo-app** with TypeScript support.
- **`cd todo-app`**: Moves into the project directory.
- **`npm start`**: Starts the development server. Your app will open in a browser at `http://localhost:3000`.

### **Understanding the Project Structure**

In your project folder, you'll see several files and folders. Let's understand the important ones:

- **`src/`**: This folder contains all the source code for your app.
  - **`App.tsx`**: The main component where we'll write our code.
  - **`index.tsx`**: The entry point of our app; it renders the **`App`** component.
- **`public/`**: Contains static files like images and the HTML template.

### **Building the Todo App**

Now, let's start building our Todo App step by step.

#### **Step 1: Cleaning Up**

Let's remove some unnecessary files to keep things simple.

- Delete all files in the **`src/`** folder except for **`App.tsx`** and **`index.tsx`**.

In **`src/App.tsx`**, delete all the existing code and start fresh:

```tsx
// File: src/App.tsx
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

- This code simply displays "Todo App" on the page.

#### **Step 2: Understanding Components**

Our **`App`** function is a **component**. Think of a component as a small part of your web page, like a button, a form, or a list. Components help us organize our code and reuse it.

#### **Step 3: Setting Up State with useState**

We need a place to store our todos (the list items). We'll use **state** for that.

In **`src/App.tsx`**, add the following:

```tsx
// File: src/App.tsx
import React, { useState } from 'react';

function App(): JSX.Element {
  const [todos, setTodos] = useState<string[]>([]);

  return (
    <div>
      <h1>Todo App</h1>
    </div>
  );
}

export default App;
```

**Explanation:**

- **`useState`** is a special function (a **hook**) that allows us to add state to our component.
- **`todos`** is an array that will hold our list of todo items.
- **`setTodos`** is a function that lets us update the **`todos`** array.
- We initialize **`todos`** as an empty array of strings.

#### **Step 4: Adding a Form to Add Todos**

We need a way for the user to add new todos. We'll add an input field and a button.

In **`src/App.tsx`**, update the code to include the form:

```tsx
// File: src/App.tsx
function App(): JSX.Element {
  const [todos, setTodos] = useState<string[]>([]);
  const [newTodo, setNewTodo] = useState<string>('');

  const handleAddTodo = (): void => {
    if (newTodo.trim() !== '') {
      setTodos([...todos, newTodo]);
      setNewTodo('');
    }
  };

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
}
```

**Explanation:**

- **`newTodo`**: A piece of state to hold the current value of the input field.
- **`setNewTodo`**: Function to update **`newTodo`**.
- **`handleAddTodo`**: Function that runs when the "Add Todo" button is clicked.
  - It checks if **`newTodo`** is not empty.
  - Adds **`newTodo`** to the **`todos`** array.
  - Clears the input field by setting **`newTodo`** back to an empty string.
- **`<input>`**: The text field where the user types a new todo.
  - **`value={newTodo}`**: Links the input field to our state.
  - **`onChange`**: Updates **`newTodo`** whenever the user types.
- **`<button>`**: When clicked, calls **`handleAddTodo`**.

#### **Step 5: Displaying the List of Todos**

Let's show the todos on the screen so the user can see them.

Update **`src/App.tsx`** to display the todos:

```tsx
// File: src/App.tsx
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

    <ul>
      {todos.map((todo, index) => (
        <li key={index}>{todo}</li>
      ))}
    </ul>
  </div>
);
```

**Explanation:**

- **`<ul>`**: An unordered list to display the todos.
- **`todos.map(...)`**: Loops through each todo in the **`todos`** array.
  - **`todo`**: The current todo item in the loop.
  - **`index`**: The position of the todo in the array.
- **`<li>`**: List item that displays the todo.
  - **`key={index}`**: Helps React keep track of list items and update them efficiently.

#### **Step 6: Marking Todos as Completed**

Let's allow users to mark todos as completed by clicking on them.

First, we need to update our **`todos`** state to hold more information about each todo. In **`src/App.tsx`**, define a **Todo** interface:

```tsx
// File: src/App.tsx
interface Todo {
  text: string;
  completed: boolean;
}

const [todos, setTodos] = useState<Todo[]>([]);
```

**Explanation:**

- **`Todo`** interface defines the shape of a todo item.
  - **`text`**: The text of the todo.
  - **`completed`**: A boolean indicating if the todo is completed.

Update **`handleAddTodo`** in **`src/App.tsx`** to create a new todo with this structure:

```tsx
// File: src/App.tsx
const handleAddTodo = (): void => {
  if (newTodo.trim() !== '') {
    const newTodoItem: Todo = { text: newTodo, completed: false };
    setTodos([...todos, newTodoItem]);
    setNewTodo('');
  }
};
```

Update the list rendering in **`src/App.tsx`**:

```tsx
// File: src/App.tsx
<ul>
  {todos.map((todo, index) => (
    <li
      key={index}
      style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
      onClick={() => handleToggleComplete(index)}
    >
      {todo.text}
    </li>
  ))}
</ul>
```

Add **`handleToggleComplete`** function in **`src/App.tsx`**:

```tsx
// File: src/App.tsx


const handleToggleComplete = (index: number): void => {
  const updatedTodos = todos.map((todo, i) =>
    i === index ? { ...todo, completed: !todo.completed } : todo
  );
  setTodos(updatedTodos);
};
```

#### **Step 7: Removing Todos**

Let's add a button to delete todos from the list.

Update the list rendering in **`src/App.tsx`**:

```tsx
// File: src/App.tsx
<li
  key={index}
  style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
>
  <span onClick={() => handleToggleComplete(index)}>{todo.text}</span>
  <button onClick={() => handleDeleteTodo(index)}>Delete</button>
</li>
```

Add **`handleDeleteTodo`** function in **`src/App.tsx`**:

```tsx
// File: src/App.tsx
const handleDeleteTodo = (index: number): void => {
  const updatedTodos = todos.filter((_, i) => i !== index);
  setTodos(updatedTodos);
};
```

Now, users can remove todos by clicking the "Delete" button next to them.

---

### **Styling the App**

Let's make our app look nice by adding some basic styles.

Create a **CSS** file named **`App.css`** in the **`src/`** folder:

```css
/* File: src/App.css */

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

Import this CSS file into **`src/App.tsx`**:

```tsx
// File: src/App.tsx
import './App.css';
```

Now your app should have a cleaner, more organized look!

### **Understanding What We've Done**

Let's recap the key concepts we've learned:

- **Components**: Building blocks of a React app. Our **`App`** function is a component.
- **State**: A way to store data in a component. We used **`useState`** to manage our list of todos and the input field value.
- **Props**: Short for "properties," used to pass data between components (we didn't use them extensively here but they're important).
- **Events**: We handled user interactions like clicks and input changes using event handlers like **`onClick`** and **`onChange`**.
- **Lists and Keys**: We displayed a list of todos using **`map`** and provided a unique **`key`** for each item.
- **Conditional Rendering**: We used conditions to change the style of completed todos.
- **Functions**: We wrote functions to add, toggle, and delete todos.

---

### **Conclusion**

**Mubarak ho!** (Congratulations!) You've built a functional Todo App using React and TypeScript. By building this app, you've learned the basics of React development.
Remember, practice makes perfect. Try adding new features to your app, like editing todos or saving them to local storage so they persist when you refresh the page.
