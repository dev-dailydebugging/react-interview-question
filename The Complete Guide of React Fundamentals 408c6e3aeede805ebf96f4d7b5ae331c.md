# The Complete Guide of React Fundamentals

### Chapter 01 — React Fundamentals

## Introduction to React

React is an open-source JavaScript library used to build user interfaces (UIs), especially for web applications. It was originally developed at Facebook, now Meta.

Modern web applications contain many interactive elements, such as buttons, forms, navigation bars, search boxes, and dashboards. Managing all these elements becomes difficult as an application grows.

React solves this problem by allowing developers to divide a user interface into small, reusable building blocks called components.

Instead of manually updating every element on a webpage, developers describe what the UI should look like, and React manages the necessary updates when data changes.

For example, in an e-commerce application, the navbar, product cards, search bar, and shopping cart can all be created as separate React components.

**In simple words:** React helps us build complex, interactive user interfaces in a structured and reusable way.

---

## Understanding Why React Is Used

Before React, developers commonly used JavaScript and DOM manipulation to create interactive web applications. Although this approach works, managing a large number of UI elements and their changing data can become difficult.

React introduces a component-based approach that makes UI development more organized.

Each component is responsible for describing a particular part of the interface. These components can be reused, combined, and maintained independently.

React also follows a declarative programming approach. This means we describe what the interface should display for the current data, rather than manually specifying every DOM operation required to update it.

For example, when a user clicks a counter button, the displayed number changes. React allows us to update the component's state, then renders the updated UI as needed.

This makes it easier to build applications that contain frequently changing data.

---

## React and JavaScript

JavaScript is a programming language, whereas React is a JavaScript library designed to help build user interfaces.

JavaScript provides the fundamental programming features needed to build applications, including variables, functions, objects, arrays, conditions, loops, and asynchronous operations.

React uses JavaScript to define components, process data, handle events, and describe how the interface should appear.

Consider the following JavaScript example:

```
document.querySelector("h1").textContent =
  "Hello World";
```

Here, JavaScript directly selects an HTML element and changes its text.

In React, we describe the desired output inside a component:

```
function App() {
  return <h1>Hello World</h1>;
}
```

React manages rendering this component into the UI.

Both approaches can build interactive interfaces, but React provides a structured way to manage UI rendering as applications become more complex.

**Important:** React does not replace JavaScript. A strong understanding of JavaScript makes learning React much easier.

---

## Component-Based Architecture

A component is a reusable piece of a user interface. React applications are built by combining components to create larger interfaces.

Think of a website as a collection of building blocks. Each block represents a particular part of the UI.

For example, a shopping website may contain a Navbar component, a SearchBar component, multiple ProductCard components, and a Footer component.

Each component can be developed separately and then combined to create the complete page.

A simple React component looks like this:

```
function Welcome() {
  return <h1>Welcome to React</h1>;
}
```

Here, `Welcome` is a function component that describes a heading.

We can use this component inside another component:

```
function App() {
  return (
    <div>
      <Welcome />
      <Welcome />
    </div>
  );
}
```

The same component is reused twice without duplicating its implementation.

This approach improves code reusability, organization, and maintainability. Modern React development primarily uses function components.

---

## JSX — JavaScript XML

JSX is a syntax extension for JavaScript that allows us to write HTML-like markup inside JavaScript code.

It makes React components easier to read because the UI structure and related component logic can be kept together.

For example:

```
function App() {
  const name = "React";

  return <h1>Hello, {name}!</h1>;
}
```

In this example, `<h1>` represents the heading, while `{name}` inserts the value of a JavaScript expression into the JSX.

Although JSX looks similar to HTML, it follows its own syntax rules.

In JSX, we use `className` instead of `class`, close elements properly, and return a single parent element or a Fragment when necessary.

JSX is not HTML written directly inside JavaScript. Development tools transform JSX into JavaScript that React can use.

**Remember:** JSX describes the structure of the UI, while JavaScript provides the logic and data used by the component.

---

## How React Works

React follows a declarative approach to building user interfaces.

First, developers create components that describe the UI. React renders these components to determine what should appear on the screen.

When relevant data changes, React can render the affected components again. It then uses a process called reconciliation to determine what changes are necessary compared with the previous rendered output.

React DOM commits the required changes to the browser's DOM.

For example, imagine a counter displaying the number `0`. When the user clicks a button, the counter changes to `1`.

Instead of manually finding the heading or button and changing its text, we update the component's state. React then renders the updated output and updates the DOM when necessary.

Not every render causes a DOM update. React may render a component without needing to change the actual DOM.

This approach allows developers to focus on describing the UI instead of manually managing every DOM operation.

---

## Understanding the Virtual DOM

The Virtual DOM is a common term used to describe React's in-memory representation of the UI.

When a component renders, React produces a description of what the UI should look like. If the output changes during a later render, React uses reconciliation to determine the differences and identify the necessary updates.

React DOM then commits the required changes to the browser's actual DOM.

This process helps React manage UI updates systematically.

However, the Virtual DOM is not simply a complete copy of the browser DOM, and it does not guarantee that every update will be faster than manual DOM manipulation. Actual performance depends on the work being performed and how the application is structured.

**In simple words:** React determines what needs to change in the UI and manages those updates for us.

---

## Props — Passing Data Between Components

Props, short for properties, allow one component to pass data to another component, typically from a parent to a child.

They make components reusable because the same component can display different information depending on the props it receives.

For example, a Greeting component can receive a person's name:

```
function Greeting({ name }) {
  return <h2>Hello, {name}!</h2>;
}
```

We can use it with different values:

```
<Greeting name="Rahul" />
<Greeting name="Priya" />
```

The component displays a different greeting for each name.

In a real application, a ProductCard component might receive a product's name, price, and image through props.

Props are read-only from the receiving component's perspective. The component should not directly modify them.

**Remember:** Props are used to pass data into components and make them reusable.

---

## State — Managing Changing Data

State is data that a component remembers between renders. It is useful when information changes because of user interactions or other events.

Examples include a counter value, a menu's open or closed status, a form's input values, and the selected tab in a dashboard.

React provides the `useState` Hook to add state to function components.

```
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <button onClick={() => setCount(count + 1)}>
      Count: {count}
    </button>
  );
}
```

Here, `count` represents the current state value, `setCount` requests a state update, and `0` is the initial value.

When the button is clicked, the setter requests an update. React renders the component with the new value, and the displayed count changes.

State should be updated through its setter rather than by directly modifying the existing state value.

**Remember:** Props provide inputs to a component, while state stores data managed through React's state mechanism.

---

## Introduction to React Hooks

Hooks are functions that allow function components to use React features such as state, context, and effects.

Before Hooks were introduced, class components were commonly used when developers needed features such as local state and lifecycle methods. Hooks made it possible to use these features in function components.

The `useState` Hook manages component state. The `useEffect` Hook synchronizes a component with external systems, such as subscriptions or browser APIs. The `useContext` Hook reads values from React context, while `useRef` stores references that persist between renders.

React also provides Hooks such as `useMemo` and `useCallback`, which can help avoid repeated calculations or function recreation when appropriate.

Hooks must follow the Rules of Hooks. In particular, they should be called at the top level of function components or custom Hooks, rather than inside conditions or loops.

Beginners should first understand `useState` and `useEffect` before exploring more advanced Hooks.

---

## Understanding the React Ecosystem

React focuses on building user interfaces, but real-world applications often require additional tools for routing, state management, server communication, and application development.

These tools form part of the React ecosystem.

React Router helps manage navigation between views. Redux Toolkit provides tools for managing shared application state. TanStack Query helps manage server data, including fetching and caching. Vite provides development and build tooling for React projects.

Next.js is a React framework that provides additional features, including routing, different rendering strategies, and server-side capabilities.

These tools serve different purposes and are not all required for every project.

A beginner should focus on React fundamentals first, then learn additional tools as the requirements of their projects grow.

---

## Final Understanding

React provides a structured way to build interactive user interfaces through components, JSX, props, state, and declarative rendering.

Components divide an interface into reusable pieces. JSX describes the UI structure. Props pass data between components, while state represents changing data. Hooks provide access to React features, and React manages rendering and the necessary DOM updates.

Together, these concepts form the foundation of React development.

Once these fundamentals are clear, the next step is to build small projects, practise handling user interactions, work with APIs, and learn how to debug unexpected UI behaviour.

**Learning is not about memorizing every definition. It is about understanding how the concepts work together when you build something real.**

# **REACT Fundamentals — Basic Interview Questions with Answers**

## Q1. What is React, and why do we use it?

React is an open-source **JavaScript library** for building user interfaces. It was created by Facebook (now Meta) and is built around reusable pieces called **components**.

**Why we use it:**

- **Reusable components**: build a button or card once and use it everywhere.
- **Fast UI updates**: React updates only the parts of the page that changed.
- **Declarative style**: you describe *what* the UI should look like, and React handles *how* to update it.
- **Large ecosystem**: lots of libraries, tutorials, and jobs.
- **Easy to maintain**: a big UI is split into small parts.

## Q2. Is React a library or a framework?

React is officially a **library**.

- A **library** gives you tools for one job. React focuses on the **view layer** (the UI).
- A **framework** (like Angular) gives you a complete structure: routing, forms, HTTP, state management.

With React you choose the extra tools yourself (React Router, Redux, and so on). Frameworks built on React, like **Next.js**, add those pieces.

## Q3. What are the main features of React?

- **Component-based architecture**
- **JSX**: HTML-like syntax inside JavaScript
- **Virtual DOM**: efficient updates
- **One-way data flow**: parent to child through props
- **Hooks**: state and lifecycle in functional components
- **Declarative UI**
- **Large ecosystem**

## Q4. What is the difference between React and JavaScript?

| JavaScript | React |
| --- | --- |
| A **programming language** | A **library written in JavaScript** |
| Works in browsers and Node.js | Used to build user interfaces |
| Can be used without React | Cannot be used without JavaScript |
| Manipulates the DOM directly | Manages the DOM through the Virtual DOM |

## Q5. What is JSX, and why do we use it?

JSX (**JavaScript XML**) lets you write **HTML-like code inside JavaScript**.

jsx

```jsx
const name = "Aman";const element = <h1>Hello, {name}!</h1>;
```

**Why we use it:** UI and logic live together, you can embed JavaScript in `{ }`, and many errors are caught early.

**Important points:**

- Browsers can’t read JSX. **Babel** converts it to `React.createElement()` calls.
- Use `className` instead of `class`, and `htmlFor` instead of `for`.
- A component must return **one parent element** (or a Fragment `<></>`).

## Q6. What is a component in React?

A component is a **reusable, independent piece of UI**: a function (or class) that returns JSX.

jsx

```jsx
function Welcome({ name }) {  return <h1>Hello, {name}</h1>;}<Welcome name="Aman" />
```

- Names **must start with a capital letter**.
- Components receive data through **props**.
- Components can be nested to form a tree (`Navbar`, `Card`, `Footer`).

## Q7. What is the difference between functional and class components?

|  | Functional | Class |
| --- | --- | --- |
| Syntax | Plain function | ES6 class extending `React.Component` |
| State | `useState` | `this.state` / `this.setState()` |
| Lifecycle | `useEffect` | `componentDidMount`, etc. |
| `this` keyword | Not needed | Required |
| Today | **Standard** | Legacy |

jsx

```jsx
function Hello() { return <h1>Hello</h1>; }class Hello extends React.Component {  render() { return <h1>Hello</h1>; }}
```

Since Hooks (React 16.8), functional components can do everything class components can.

## Q8. What is the Virtual DOM, and how does it work?

The Virtual DOM is a **lightweight JavaScript copy** of the real DOM kept in memory.

1. **Render**: when state or props change, React builds a **new** Virtual DOM tree.
2. **Diffing**: it compares the new tree with the previous one.
3. **Reconciliation**: it updates **only the changed parts** of the real DOM.

If one item in a 1000-item list changes, React updates just that item.

## Q9. What is the difference between the Virtual DOM and the real DOM?

| Real DOM | Virtual DOM |
| --- | --- |
| The actual page structure in the browser | A JavaScript object copy in memory |
| Updates are **slow** | Updates are **fast** |
| Can re-render a lot of the page | Only **differences** are applied to the real DOM |
| Visible on screen | Not shown on screen |

The Virtual DOM doesn’t replace the real DOM. It decides the **minimum changes** needed.

## Q10. What is the difference between props and state?

| Props | State |
| --- | --- |
| Passed **from parent to child** | **Owned inside** the component |
| **Read-only** | **Can be changed** with the setter |
| Like function arguments | Like variables inside the component |

jsx

```jsx
function Child({ name }) {                  // props  return <p>Hello, {name}</p>;}function Parent() {  const [count, setCount] = useState(0);    // state  return (    <>      <Child name="Aman" />      <button onClick={() => setCount(count + 1)}>{count}</button>    </>  );}
```

## Q11. What is the purpose of the `useState` Hook?

`useState` lets a **functional component** store data that changes over time. When it changes, React **re-renders** the component.

jsx

```jsx
const [count, setCount] = useState(0);
```

- `count` is the current value, `setCount` updates it, and `0` is the initial value.
- Never change state directly (`count = 5`). Use the setter.
- For updates based on the previous value, use `setCount(prev => prev + 1)`.
- Call Hooks only at the **top level** of a component, not in loops or conditions.

## Q12. What is the difference between SPA and MPA?

| SPA (Single Page Application) | MPA (Multi Page Application) |
| --- | --- |
| Loads **one HTML page**, updates content dynamically | Loads a **new page** from the server per route |
| Fast navigation, no full reload | Full reload on each navigation |
| Routing on the client (React Router) | Routing on the server |
| Heavier first load | Lighter per-page load |
| SEO needs extra work | SEO is straightforward |
| Gmail, Google Maps | Traditional blogs, many shops |

## Q13. How does React update the user interface?

1. **Trigger**: state or props change (click, fetch response, timer).
2. **Render phase**: React calls your component again and builds a **new Virtual DOM**.
3. **Diffing**: it compares the new tree with the old one.
4. **Commit phase**: it applies only the **necessary changes** to the real DOM.
5. The browser repaints that part of the screen.

React also **batches** multiple state updates, and `key` props help it match list items during diffing.

## Q14. What is the difference between React and Next.js?

| React | Next.js |
| --- | --- |
| A **UI library** | A **framework built on React** |
| Add routing and SSR yourself | Routing and SSR are **built in** |
| Client-side rendering by default | **SSR, SSG, and CSR** |
| Needs React Router | **File-based routing** |
| SEO needs extra setup | **Better SEO** |
| Separate backend | Built-in **API routes** |

React is the engine, and Next.js is the whole car.

## Q15. What is the React ecosystem, and which tools are commonly used with React?

The React ecosystem is the set of **libraries and tools** used with React to build full applications.

| Purpose | Common tools |
| --- | --- |
| Project setup | **Vite**, Next.js |
| Routing | **React Router** |
| State management | **Redux Toolkit**, Zustand, Context API |
| Data fetching | **TanStack Query**, SWR, Axios |
| Styling | **Tailwind CSS**, CSS Modules, styled-components |
| UI libraries | **Material UI**, Chakra UI, shadcn/ui |
| Forms | **React Hook Form**, Formik |
| Testing | **Jest**, React Testing Library, Vitest |
| Mobile | **React Native** |
| Types | **TypeScript** |

# **REACT Fundamentals — Intermediate Interview Questions with Answers**

## Q1. What is the purpose of the `useEffect` Hook, and how does its dependency array work?

`useEffect` lets a component run **side effects**: work that happens outside rendering, such as fetching data, setting up timers, subscribing to events, or updating the document title. It runs **after** React has rendered and painted the component.

jsx

```jsx
useEffect(() => {  document.title = `Count:${count}`;  return () => {// cleanup (optional)  };}, [count]);
```

**The dependency array controls when the effect runs:**

| Dependency array | When the effect runs |
| --- | --- |
| Not provided | After **every** render |
| `[]` (empty) | Only **once**, after the first render |
| `[a, b]` | After the first render, and whenever `a` or `b` changes |

**Key points:**

- Include every value from the component that the effect uses (props, state, functions) in the array.
- The **cleanup function** runs before the effect re-runs and when the component unmounts. Use it to clear timers, remove listeners, or cancel subscriptions.
- In development with Strict Mode, React runs effects twice on mount to help you find missing cleanups.
- Avoid putting objects or arrays created inside the component in the array unless they are memoized, because they change on every render.

## Q2. What is the difference between `useEffect` and `useState`?

| `useState` | `useEffect` |
| --- | --- |
| Stores **data** that changes over time | Runs **side effects** |
| Changing it **triggers a re-render** | Runs **after** a render, and does not trigger one by itself |
| Returns `[value, setValue]` | Returns nothing (or a cleanup function) |
| Example: a counter, an input value | Example: fetching data, adding an event listener |

They are often used together:

jsx

```jsx
const [users, setUsers] = useState([]);useEffect(() => {  fetch("/api/users")    .then(res => res.json())    .then(data => setUsers(data));}, []);
```

`useEffect` fetches the data, and `useState` stores it so the UI can show it.

## Q3. What is the difference between controlled and uncontrolled components?

| Controlled | Uncontrolled |
| --- | --- |
| Form data is stored in **React state** | Form data is stored in the **DOM itself** |
| Value is set through `value` + `onChange` | Value is read with a **ref** when needed |
| React is the “single source of truth” | The DOM is the source of truth |
| Easier validation and instant feedback | Less code, good for simple forms |

jsx

```jsx
// Controlledconst [name, setName] = useState("");<input value={name} onChange={e => setName(e.target.value)} />// Uncontrolledconst inputRef = useRef();<input ref={inputRef} defaultValue="Aman" />// read later: inputRef.current.value
```

File inputs (`<input type="file" />`) are always uncontrolled.

## Q4. What is prop drilling, and how can you avoid it?

Prop drilling means passing props through **several layers of components** just to reach a deeply nested child, even though the middle components don’t use the data.

jsx

```jsx
<App user={user}>  <Layout user={user}>    <Sidebar user={user}>      <Avatar user={user} />   {/* only this one needs it */}
```

**Problems:** messy code, hard to refactor, and easy to break.

**How to avoid it:**

- **Context API**: share the data directly with any descendant.
- **State management libraries**: Redux Toolkit, Zustand.
- **Component composition**: pass components as `children` instead of passing data down many levels.
- **Keep state close** to where it’s used.

Note that passing props through one or two levels is perfectly fine. Prop drilling is only a problem when it gets deep.

## Q5. What is the Context API, and when should you use it?

The Context API lets you **share data across the component tree** without passing props manually at every level.

jsx

```jsx
import { createContext, useContext, useState } from "react";const ThemeContext = createContext();function App() {  const [theme, setTheme] = useState("light");  return (    <ThemeContext.Provider value={{ theme, setTheme }}>      <Page />    </ThemeContext.Provider>  );}function Button() {  const { theme, setTheme } = useContext(ThemeContext);  return <button onClick={() => setTheme("dark")}>{theme}</button>;}
```

**Steps:** create the context, wrap components in a `Provider`, and read the value with `useContext`.

**Use it for** data needed by many components: theme, logged-in user, language, and so on.

**Limitation:** when the context value changes, **every component that consumes it re-renders**. For frequently changing, complex global state, a dedicated library (Redux Toolkit, Zustand) is often a better fit.

## Q6. What is the difference between `useRef` and `useState`?

| `useState` | `useRef` |
| --- | --- |
| Changing it **triggers a re-render** | Changing `.current` **does not** trigger a re-render |
| Value is used for what appears on screen | Value is used for things that shouldn’t affect the UI |
| Updated through the setter | Updated by assigning to `ref.current` |
| Snapshot per render | Same object persists across renders |

**Common uses of `useRef`:**

- Accessing a DOM element (focus an input, measure size)
- Storing a value that must persist without re-rendering (timer IDs, previous values)

jsx

```jsx
const inputRef = useRef(null);<input ref={inputRef} /><button onClick={() => inputRef.current.focus()}>Focus</button>
```

## Q7. What are custom Hooks, and why do we use them?

A custom Hook is a **JavaScript function whose name starts with `use`** and that calls other Hooks inside it. It lets you **reuse stateful logic** across components.

jsx

```jsx
function useLocalStorage(key, initialValue) {  const [value, setValue] = useState(() => {    const saved = localStorage.getItem(key);    return saved ? JSON.parse(saved) : initialValue;  });  useEffect(() => {    localStorage.setItem(key, JSON.stringify(value));  }, [key, value]);  return [value, setValue];}// Usageconst [name, setName] = useLocalStorage("name", "");
```

**Why we use them:**

- Avoid repeating the same logic in many components.
- Keep components small and readable.
- Easy to test and share.

**Rules:** the name must start with `use`, and they follow the Rules of Hooks. Each component that calls a custom Hook gets its **own separate state**. Hooks share logic, not data.

## Q8. What is the purpose of keys when rendering lists in React?

Keys help React **identify which items changed, were added, or were removed** in a list, so it can update the DOM efficiently and correctly.

jsx

```jsx
{todos.map(todo => (  <li key={todo.id}>{todo.text}</li>))}
```

**Rules:**

- Keys must be **unique among siblings** (not globally unique).
- Keys must be **stable**: the same item should keep the same key.
- Use a unique ID from your data (like `todo.id`).

**Why avoid the array index as a key?** If items are reordered, inserted, or deleted, the index changes. React may then mix up items, causing wrong UI state (such as input values appearing in the wrong row) and wasted renders. The index is acceptable only for static lists that never change order.

Keys are not passed as props. A component can’t read its own `key`.

## Q9. What is conditional rendering, and how can you implement it?

Conditional rendering means **showing different UI depending on a condition**, such as logged in or not, loading or loaded.

jsx

```jsx
// 1. if / early returnif (loading) return <Spinner />;// 2. Ternary operator{isLoggedIn ? <Dashboard /> : <Login />}// 3. Logical AND (&&){hasError && <ErrorMessage />}// 4. Variablelet content;if (items.length === 0) content = <p>No items</p>;else content = <List items={items} />;return <div>{content}</div>;
```

**Watch out:** with `&&`, a value of `0` renders as `0` on screen. Use `{count > 0 && <Badge />}` instead of `{count && <Badge />}`. Returning `null` from a component renders nothing.

## Q10. What is lifting state up in React?

Lifting state up means **moving state to the closest common parent** of the components that need it, so they can share it. The parent passes the data down as props and passes functions down to let children update it.

jsx

```jsx
function Parent() {  const [text, setText] = useState("");  return (    <>      <Input text={text} onChange={setText} />      <Preview text={text} />    </>  );}
```

Here `Input` and `Preview` are siblings and can’t share state directly, so the state lives in `Parent`.

**Why:** it keeps a single source of truth and keeps related components in sync. If lifting goes too many levels, consider Context or a state library.

## Q11. What are `React.memo`, `useMemo`, and `useCallback`, and how do they differ?

All three are **performance optimizations** that avoid unnecessary work.

| Tool | What it memoizes | Purpose |
| --- | --- | --- |
| `React.memo` | A whole **component** | Skips re-rendering if its props haven’t changed |
| `useMemo` | A **computed value** | Avoids recalculating an expensive result |
| `useCallback` | A **function** | Keeps the same function reference between renders |

jsx

```jsx
// React.memoconst Child = React.memo(function Child({ name }) {  return <p>{name}</p>;});// useMemoconst total = useMemo(() => items.reduce((a, b) => a + b.price, 0), [items]);// useCallbackconst handleClick = useCallback(() => doSomething(id), [id]);
```

**How they work together:** `React.memo` compares props, and functions or objects are new on every render. So passing a normal function to a memoized child breaks the optimization. `useCallback` (or `useMemo`) keeps the reference stable.

**Warning:** don’t use them everywhere. They add overhead, so use them only when you’ve found a real performance problem.

## Q12. What is the difference between client-side routing and traditional page navigation?

| Traditional (server-side) navigation | Client-side routing |
| --- | --- |
| Browser requests a **new HTML page** from the server on each link click | JavaScript **swaps the content** without a full reload |
| Full page reload | No full reload |
| Slower transitions | Faster, app-like feel |
| State is lost on every navigation | App state can be preserved |
| Server decides the route | The router in the browser decides |

In React, **React Router** does client-side routing. It changes the URL using the History API and renders the matching component, without asking the server for a new page.

jsx

```jsx
<Link to="/about">About</Link>   // client-side navigation<a href="/about">About</a>       // full page reload
```

**Trade-offs:** SEO and first load need extra care (SSR or pre-rendering), and the server must be configured to serve `index.html` for all routes.

## Q13. What are error boundaries, and what types of errors can they catch?

An error boundary is a component that **catches JavaScript errors in its child component tree**, logs them, and shows a **fallback UI** instead of crashing the whole app.

**Important:** error boundaries must be **class components** (using `componentDidCatch` and `getDerivedStateFromError`). There is no Hook version. Libraries like `react-error-boundary` provide a ready-made one.

jsx

```jsx
class ErrorBoundary extends React.Component {  state = { hasError: false };  static getDerivedStateFromError() { return { hasError: true }; }  componentDidCatch(error, info) { console.error(error, info); }  render() {    return this.state.hasError ? <h2>Something went wrong.</h2> : this.props.children;  }}
```

| Catches | Does NOT catch |
| --- | --- |
| Errors during **rendering** | **Event handler** errors (use `try/catch`) |
| Errors in **lifecycle methods** | **Asynchronous code** (`setTimeout`, promises) |
| Errors in **constructors** of child components | **Server-side rendering** errors |
|  | Errors thrown in the **error boundary itself** |

## Q14. What is the difference between local state, global state, and server state?

| Type | What it is | Typical tools |
| --- | --- | --- |
| **Local state** | Data used by **one component** (or a few close ones) | `useState`, `useReducer` |
| **Global state** | Data shared across **many parts of the app** | Context API, Redux Toolkit, Zustand |
| **Server state** | Data that **lives on the server** and is fetched into the UI | TanStack Query, SWR |

**Examples:**

- Local: whether a dropdown is open, the value of an input.
- Global: logged-in user, theme, shopping cart.
- Server: list of products, user profile from an API.

**Why server state is special:** it’s owned by someone else, can become **stale**, and needs caching, refetching, loading, and error handling. Dedicated tools handle that, so you don’t have to copy API data into Redux or `useState` by hand.

**Rule of thumb:** start with local state, lift it up only when needed, and use global state only for truly shared data.

## Q15. What happens when a React component re-renders, and how can you optimize unnecessary renders?

**A re-render happens when:**

- The component’s **state** changes.
- Its **props** change (because the parent re-rendered).
- A **context** it consumes changes.
- Its **parent re-renders** (by default, all children re-render too).

**What happens:**

1. React calls the component function again.
2. It builds a new Virtual DOM tree and **compares** it to the previous one.
3. Only the **real differences** are applied to the DOM.

A re-render doesn’t always mean the DOM changes, but the function still runs, which can be costly.

**How to optimize:**

- **`React.memo`**: skip re-rendering a child if props are unchanged.
- **`useMemo` / `useCallback`**: keep values and functions stable.
- **Move state down**: keep state close to where it’s used, so fewer components re-render.
- **Split components**: isolate the parts that change often.
- **Use proper `key`s** in lists.
- **Lazy loading** with `React.lazy` and `Suspense`.
- **Virtualize long lists** (react-window).
- **Avoid creating new objects or arrays in JSX** when passing them to memoized children.
- 

# **REACT Fundamentals — Advanced Interview Questions with Answers**

## Q1. How does React’s reconciliation algorithm work, and what is the role of the Virtual DOM?

**Role of the Virtual DOM:** it is a lightweight JavaScript representation (a tree of objects describing the UI). On every update, React builds a new tree and compares it with the previous one, instead of touching the real DOM directly.

**Reconciliation** is the process of comparing the two trees and working out the **minimum changes** needed for the real DOM. A general tree comparison is very expensive, so React uses two assumptions to make it fast (roughly O(n)):

1. **Elements of different types produce different trees.** If `<div>` becomes `<span>`, or `<A />` becomes `<B />`, React destroys the old subtree (unmounting it and losing its state) and builds a new one.
2. **Keys identify stable items in lists.** Elements with the same key between renders are treated as the same item, so they can be moved instead of re-created.

**What happens for each node:**

- **Same type:** React keeps the existing DOM node or component instance, updates only the changed props/attributes, then recurses into the children.
- **Different type:** unmount the old one, mount the new one.
- **Lists:** compare children by `key` (without keys, by position).

jsx

```jsx
// State is lost here, because the type changes from <input> to <p>{isEditing ? <input /> : <p>Text</p>}
```

After diffing, React applies all the changes to the DOM in one **commit** step.

## Q2. What is React Fiber, and how does it improve React’s rendering process?

Fiber is the **internal reconciliation engine** introduced in React 16. It is a rewrite of how React represents components and performs rendering work.

**The problem it solved:** the old reconciler (the “stack reconciler”) worked recursively and could not be interrupted. A big update would block the main thread, causing janky UI.

**How Fiber works:**

- Each component becomes a **fiber**: a plain JavaScript object (a unit of work) holding its type, props, state, and pointers to its parent, child, and sibling.
- Rendering is broken into **small units of work** that can be **paused, resumed, prioritized, or thrown away**.
- Work is split into two phases:
    - **Render phase** (can be interrupted): React works out what changed.
    - **Commit phase** (synchronous, cannot be interrupted): React applies the changes to the DOM and runs effects.

**What it enables:**

- **Time slicing**: rendering in small chunks so the browser stays responsive.
- **Priorities**: urgent updates (typing, clicks) can jump ahead of less urgent ones.
- **Concurrent features**: `useTransition`, `useDeferredValue`, and Suspense improvements.
- Better error handling (error boundaries).

You never use Fibers directly. They are an implementation detail that makes the features above possible.

## Q3. What is the difference between `useEffect` and `useLayoutEffect`?

|  | `useEffect` | `useLayoutEffect` |
| --- | --- | --- |
| When it runs | **After** the browser paints the screen | **After** DOM updates but **before** the browser paints |
| Blocks painting? | No | **Yes** (synchronous) |
| Typical use | Data fetching, subscriptions, timers, logging | Measuring DOM size/position, preventing visual flicker |
| Server rendering | Fine | Gives a warning (does nothing on the server) |

jsx

```jsx
useLayoutEffect(() => {  const { height } = ref.current.getBoundingClientRect();  setHeight(height);   // updated before the user sees the first paint}, []);
```

**Rule of thumb:** use `useEffect` by default. Switch to `useLayoutEffect` only when you read layout from the DOM and update something based on it, and you see a **visual flicker** with `useEffect`. Overusing `useLayoutEffect` delays painting and hurts performance.

## Q4. What are stale closures in React, and how can you avoid them?

A **stale closure** happens when a function (an effect, a timer callback, an event handler) **captures old values** of state or props from the render in which it was created, and keeps using them after newer values exist.

jsx

```jsx
function Counter() {  const [count, setCount] = useState(0);  useEffect(() => {    const id = setInterval(() => {      console.log(count);       // always logs 0 (stale!)      setCount(count + 1);      // always sets 1    }, 1000);    return () => clearInterval(id);  }, []);                        // empty array: effect never sees new count}
```

**How to avoid it:**

1. **Use the functional update form** (no need to read the current value):

jsx

```jsx
   setCount(prev => prev + 1);
```

1. **Add all used values to the dependency array**, so the effect re-runs with fresh values (and clean up properly):

jsx

```jsx
   useEffect(() => { ... }, [count]);
```

1. **Use a ref to hold the latest value** (for long-lived callbacks like timers or listeners):

jsx

```jsx
   const countRef = useRef(count);   useEffect(() => { countRef.current = count; });// in the callback: countRef.current
```

1. Use the **`react-hooks/exhaustive-deps`** ESLint rule, which warns about missing dependencies.

## Q5. How does `React.memo` work, and when can it fail to prevent unnecessary re-renders?

`React.memo` wraps a component so React **skips re-rendering it when its props are the same** as last time. It compares props with a **shallow comparison** (`Object.is` on each prop).

jsx

```jsx
const Child = React.memo(function Child({ name }) {  return <p>{name}</p>;});
```

**When it fails to help:**

1. **New object, array, or function props on every render.** Their references change even when the content is the same:

jsx

```jsx
   <Child style={{ color: "red" }} onClick={() => doIt()} />   // new references each time
```

Fix with `useMemo` / `useCallback`, or define constants outside the component.

2. **Inline JSX `children`**: `children` is a new object each render.

3. **Context changes**: a memoized component that uses `useContext` still re-renders when that context value changes.

4. **Its own state changes**: `React.memo` only blocks re-renders caused by the **parent**.

5. **Cheap components**: the prop comparison itself costs time, so it can be wasted effort for simple components.

6. A custom comparison function can be passed as a second argument, but a wrong one causes stale UI bugs.

Also remember that the **React Compiler** (newer React versions) can add much of this memoization automatically.

## Q6. What are concurrent rendering and concurrent features in React?

**Concurrent rendering** (React 18+) means React can **prepare multiple versions of the UI at the same time and interrupt, pause, resume, or abandon a render** in progress. It builds on Fiber.

The key idea: not all updates are equally urgent.

- **Urgent updates:** typing, clicking, pressing. They must feel instant.
- **Non-urgent (transition) updates:** rendering a big filtered list, switching a tab. They can wait a little.

If an urgent update arrives while a slow render is in progress, React pauses the slow render, handles the urgent one first, and then continues.

**Concurrent features:**

- `useTransition` / `startTransition`
- `useDeferredValue`
- **Suspense** improvements (including streaming SSR)
- Automatic **batching** of state updates (inside promises, timeouts, and events)

**Note:** concurrent rendering is not turned on by “doing something”. In React 18+, it is used when you use `createRoot` and opt a state update into a transition (or use Suspense). Your code must be **pure and idempotent** because renders can happen more than once or be thrown away.

## Q7. What is the purpose of `useTransition` and `useDeferredValue`?

Both mark some UI work as **low priority**, so the UI stays responsive.

**`useTransition`** marks a **state update** as a non-urgent transition:

jsx

```jsx
const [isPending, startTransition] = useTransition();function handleChange(e) {  setQuery(e.target.value);              // urgent: input updates immediately  startTransition(() => {    setFilteredList(filter(e.target.value));   // non-urgent: can be interrupted  });}{isPending && <Spinner />}
```

**`useDeferredValue`** gives you a **delayed copy of a value** that lags behind during heavy rendering:

jsx

```jsx
const deferredQuery = useDeferredValue(query);const results = useMemo(() => filter(deferredQuery), [deferredQuery]);
```

|  | `useTransition` | `useDeferredValue` |
| --- | --- | --- |
| You control | The **state update** (wrap the setter) | The **value** (wrap what you receive) |
| Use when | You own the code that sets state | The value comes from props or you can’t wrap the setter |
| Gives you | `isPending` flag | A deferred version of the value |

Neither one makes code faster by itself. They only **prioritize** the work. Heavy computations may still need memoization or a better algorithm.

## Q8. What is Suspense in React, and how does it work with lazy loading?

`Suspense` lets a component **wait for something** (code, data) and shows a **fallback UI** meanwhile.

**With lazy loading (code splitting):**

jsx

```jsx
import { lazy, Suspense } from "react";const Dashboard = lazy(() => import("./Dashboard"));function App() {  return (    <Suspense fallback={<Spinner />}>      <Dashboard />    </Suspense>  );}
```

**How it works:**

1. `React.lazy` takes a function that returns a dynamic `import()` (a promise).
2. When `Dashboard` first renders, its code isn’t loaded yet, so React “suspends” it (the promise is thrown internally).
3. The nearest `Suspense` boundary shows the `fallback`.
4. When the code finishes loading, React renders the real component.

**Benefits:** smaller initial bundle and faster first load. It is commonly used per **route** (route-level code splitting).

**Beyond lazy loading:** Suspense also works with data fetching in supporting libraries and frameworks (TanStack Query, Next.js, the `use` Hook), and supports **streaming SSR** and **nested boundaries** for loading UI. You can combine it with an **error boundary** to handle load failures.

## Q9. What is server-side rendering (SSR), and how does it differ from client-side rendering (CSR) and static site generation (SSG)?

|  | CSR | SSR | SSG |
| --- | --- | --- | --- |
| HTML generated | In the **browser** | On the **server, per request** | At **build time** |
| First load | Blank page until JS runs | Full HTML ready quickly | Full HTML, fastest (served from a CDN) |
| SEO | Weaker (needs JS) | **Good** | **Good** |
| Data freshness | Fresh (fetched in browser) | **Always fresh** | Can be stale until rebuilt |
| Server cost | Low | Higher | Very low |
| Best for | Dashboards, private apps | Dynamic, personalized, SEO-heavy pages | Blogs, docs, marketing pages |

**How SSR works:** the server renders the component to HTML and sends it. The browser shows content immediately, then JavaScript loads and **hydrates** the page to make it interactive.

**Related:** ISR (Incremental Static Regeneration, in Next.js) regenerates static pages in the background at set intervals, which gives static speed with updatable content.

## Q10. What is hydration in React, and what causes hydration errors?

**Hydration** is the process where React takes **server-rendered HTML** and attaches **event handlers and state** to it in the browser, making the static HTML interactive. React reuses the existing DOM instead of rebuilding it.

For this to work, the HTML React expects on the client must **match** the server’s HTML. A **hydration error** appears when it doesn’t.

**Common causes:**

- Using `window`, `localStorage`, or `document` during rendering (they exist only in the browser).
- **Time or random values** (`Date.now()`, `new Date()`, `Math.random()`) that differ between server and client.
- Different data on server and client (for example, user locale or timezone).
- **Invalid HTML nesting**, such as `<div>` inside `<p>`, or `<a>` inside `<a>`.
- Browser extensions modifying the HTML.
- Conditional rendering based on browser-only checks.

**How to fix:**

- Move browser-only logic into `useEffect` (runs only on the client), and render the same output first.
- Use a `mounted` state flag for client-only UI.
- Use `suppressHydrationWarning` for unavoidable single-element differences (such as timestamps).
- Use valid HTML structure and pass the same data to both server and client.

## Q11. What are Server Components, and how do they differ from Client Components?

**Server Components** (RSC) are components that run **only on the server**. Their code is never sent to the browser. They are the default in frameworks like the Next.js App Router.

**Client Components** are components that run in the browser (and are also pre-rendered on the server for the first load). They are marked with `"use client"` at the top of the file.

|  | Server Component | Client Component |
| --- | --- | --- |
| Runs on | Server only | Browser (and server for first HTML) |
| JavaScript sent to browser | **None** | Yes (adds to bundle size) |
| Can access | Database, file system, secrets directly | Browser APIs (`window`, `localStorage`) |
| Can use `useState`, `useEffect`, event handlers | **No** | **Yes** |
| Can be `async` and fetch data directly | **Yes** | No (use Hooks or libraries) |

jsx

```jsx
// Server Componentasync function Products() {  const products = await db.query("SELECT * FROM products");  return <ProductList products={products} />;}// Client Component"use client";function AddToCart() {  const [count, setCount] = useState(0);  return <button onClick={() => setCount(count + 1)}>Add</button>;}
```

**Benefits:** smaller bundles, secure server access, and faster loads.

**Rules:** a Client Component can’t import a Server Component directly (but can receive one as `children`), and props passed from server to client must be serializable.

## Q12. What is the difference between `useActionState`, `useOptimistic`, and `useFormStatus`?

These are React 19 Hooks for **forms and actions**.

| Hook | Purpose |
| --- | --- |
| **`useActionState`** | Manages the **state returned by an action** (such as a form submission): result, errors, and pending status |
| **`useOptimistic`** | Shows an **immediate, temporary UI update** while the real async action is still running |
| **`useFormStatus`** | Lets a **child component** read the **pending status of its parent `<form>`** |

jsx

```jsx
// useActionStateconst [state, formAction, isPending] = useActionState(  async (prevState, formData) => {    const error = await save(formData);    return error ? { error } : { success: true };  },  { error: null });<form action={formAction}>...</form>// useOptimisticconst [optimisticTodos, addOptimistic] = useOptimistic(  todos,  (current, newTodo) => [...current, { ...newTodo, sending: true }]);// useFormStatus (must be used inside a component rendered within <form>)function SubmitButton() {  const { pending } = useFormStatus();  return <button disabled={pending}>{pending ? "Saving..." : "Save"}</button>;}
```

**Key points:**

- `useFormStatus` is imported from **`react-dom`**, and it works only in a component rendered **inside** a `<form>`.
- `useOptimistic` automatically reverts to the real value when the action finishes or fails.
- `useActionState` was previously called `useFormState`.

## Q13. How do you identify and fix performance bottlenecks in a large React application?

**Step 1: Measure first.** Never guess.

- **React DevTools Profiler**: shows which components render, how often, and why.
- **Chrome DevTools Performance tab**: finds long tasks and layout thrashing.
- **Lighthouse / Web Vitals** (LCP, INP, CLS): measures user-visible performance.
- **Bundle analyzers** (webpack-bundle-analyzer, `vite-bundle-visualizer`): shows large dependencies.

**Step 2: Fix the actual problem.**

| Problem | Fixes |
| --- | --- |
| Unnecessary re-renders | Move state down, split components, `React.memo`, `useMemo`, `useCallback`, stable props |
| Heavy calculations in render | `useMemo`, move to a Web Worker, better algorithms |
| Large lists | **Virtualization** (react-window, TanStack Virtual), pagination |
| Big bundle size | Code splitting (`React.lazy`, route-based), tree shaking, lighter libraries |
| Slow data loading | Caching (TanStack Query), prefetching, pagination, avoiding request waterfalls |
| Slow input / UI jank | `useTransition`, `useDeferredValue`, debouncing |
| Context causing re-renders | Split contexts, use selectors (Zustand), memoize context values |
| Large images | Lazy loading, modern formats, correct sizes |
| Slow first load | SSR/SSG, streaming, Server Components |

**Step 3: Re-measure** to confirm the improvement.

Premature optimization wastes time and complicates code. Fix the biggest measured bottleneck first.

## Q14. What are common causes of memory leaks in React, and how can you prevent them?

A memory leak happens when memory that is no longer needed can’t be freed because something still references it.

**Common causes and fixes:**

| Cause | Prevention |
| --- | --- |
| **Event listeners** not removed (`window.addEventListener`) | Remove them in the `useEffect` cleanup |
| **Timers** (`setInterval`, `setTimeout`) left running | `clearInterval` / `clearTimeout` in cleanup |
| **Subscriptions** (WebSocket, observables, store subscriptions) not closed | Unsubscribe or close in cleanup |
| **Async requests** finishing after unmount and updating state | Use `AbortController` to cancel fetches, or an `ignore` flag |
| Holding **large objects** in closures, refs, or global variables | Clear references, avoid storing huge data unnecessarily |
| **Third-party libraries** (charts, maps) not destroyed | Call their `destroy()` / `dispose()` in cleanup |
| Growing caches or global arrays that are never cleared | Limit cache size, clean up |

jsx

```jsx
useEffect(() => {  const controller = new AbortController();  fetch("/api/data", { signal: controller.signal })    .then(res => res.json())    .then(setData)    .catch(err => {      if (err.name !== "AbortError") console.error(err);    });  const onResize = () => setWidth(window.innerWidth);  window.addEventListener("resize", onResize);  return () => {    controller.abort();    window.removeEventListener("resize", onResize);  };}, []);
```

**Detect leaks:** use the Chrome DevTools **Memory tab** (heap snapshots) and watch memory grow while navigating between pages.

## Q15. How would you design a scalable React application with reusable components, state management, routing, error handling, and performance optimization?

**1. Project structure (feature-based):**

```
src/
  app/            // providers, router, global setup
  features/
    auth/         // components, hooks, api, state for one feature
    products/
    cart/
  components/     // shared reusable UI (Button, Modal, Input)
  hooks/          // shared custom hooks
  lib/            // API client, utilities
  pages/ (or routes/)
```

**2. Reusable components:**

- Small, single-purpose components built with **composition** (`children`, slots).
- A shared design system (Tailwind, Material UI, shadcn/ui) with consistent props.
- Presentational components separate from logic (put logic in custom Hooks).
- TypeScript for safe, documented props, and Storybook for documenting components.

**3. State management (use the right tool for each type):**

- **Local state:** `useState` / `useReducer`.
- **Server state:** TanStack Query (caching, refetching, loading and error states).
- **Global client state:** Context for simple cases, Zustand or Redux Toolkit for complex ones.
- **URL state:** search params for filters and pagination.
- **Form state:** React Hook Form.

**4. Routing:**

- React Router (or Next.js file-based routing).
- **Route-based code splitting** with `React.lazy` and `Suspense`.
- Protected routes for authentication and role-based access.
- Nested layouts, 404 pages.

**5. Error handling:**

- **Error boundaries** at the app level and around major sections.
- Handle API errors consistently (a central API client, interceptors, retries).
- User-friendly fallback UI and toasts.
- Error logging and monitoring (Sentry).
- Validate data (Zod) at boundaries.

**6. Performance optimization:**

- Code splitting, lazy loading, and bundle analysis.
- Memoization (`React.memo`, `useMemo`, `useCallback`) only where measured.
- List virtualization and pagination.
- Caching and prefetching of data.
- `useTransition` / `useDeferredValue` for heavy updates.
- SSR/SSG or Server Components when SEO and first load matter.
- Image and asset optimization, CDN.

**7. Quality and maintainability:**

- Automated testing: unit (Vitest/Jest), component (React Testing Library), end-to-end (Playwright/Cypress).
- ESLint, Prettier, and TypeScript, enforced in CI/CD.
- Accessibility (semantic HTML, ARIA, keyboard navigation).
- Environment configuration, security basics (avoid XSS, store tokens safely), and consistent coding conventions.

# 🚀 **Follow @daily.debugging for complete frontend resources and interview preparation.**