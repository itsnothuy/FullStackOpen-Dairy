# Day Study Log — Part 1a: Introduction to React — 2025-10-01

Repository: **itsnothuy/FullStackOpen-Dairy**  
Course: [Full Stack Open](https://fullstackopen.com/en/) → Part 1a: [Introduction to React](https://fullstackopen.com/en/part1/introduction_to_react)

---

## What I accomplished today
- ✅ Initialized a React app with **Vite** (`npm create vite@latest introdemo -- --template react`; `npm install`; `npm run dev`) and verified it served at **http://localhost:5173** by default (auto-bumps if busy).  
- ✅ Simplified the starter to minimal **`main.jsx`** and **`App.jsx`** and rendered `<App />` to `#root`.
- ✅ Practiced **JSX basics** (embedding JS with `{{ }}`, closing tags like `<br />`, one parent element, and using **Fragments** `<>...</>`).
- ✅ Built a **Hello** component and composed multiple components inside `App`.
- ✅ Passed **props** (hard-coded strings and evaluated expressions) and logged them to the console.
- ✅ Confirmed common pitfalls: component names must start with **capital letters**; you **can’t render objects** directly; keep the **console** open while coding.
- ✅ Read & annotated the official Part 1a material; captured reproducible evidence and a self‑quiz for tomorrow.

_Support & proofs for the items above are in the sections below._

---

## Code evidence (what’s in my editor)

### Minimal entry — `src/main.jsx`
```jsx
import ReactDOM from 'react-dom/client'
import App from './App'

ReactDOM.createRoot(document.getElementById('root')).render(<App />)
```

### Minimal component — `src/App.jsx` (Hello world)
```jsx
const App = () => {
  return (
    <div>
      <h1>Greetings</h1>
      <p>Hello world</p>
    </div>
  )
}

export default App
```

### Multiple components + props
```jsx
const Hello = (props) => {
  console.log(props) // proof in console
  return (
    <p>
      Hello {props.name}, you are {props.age} years old.
    </p>
  )
}

const App = () => {
  const name = 'Peter'
  const age = 10

  return (
    <div>
      <h1>Greetings</h1>
      <Hello name="Maya" age={26 + 10} />
      <Hello name={name} age={age} />
    </div>
  )
}

export default App
```

### Fragments to avoid extra DOM wrappers
```jsx
const App = () => {
  const name = 'Peter'
  const age = 10

  return (
    <>
      <h1>Greetings</h1>
      <Hello name="Maya" age={26 + 10} />
      <Hello name={name} age={age} />
      <Footer />
    </>
  )
}
```

### Common error demo — “Objects are not valid as a React child”
```jsx
const App = () => {
  const friends = [
    { name: 'Peter', age: 4 },
    { name: 'Maya',  age: 10 }
  ]

  return (
    <div>
      {/* ❌ wrong: tries to render an object */}
      {/* <p>{friends[0]}</p> */}

      {/* ✅ right: render primitive values */}
      <p>{friends[0].name} {friends[0].age}</p>
      <p>{friends[1].name} {friends[1].age}</p>
    </div>
  )
}
```

### Capitalization matters
```jsx
// ❌ wrong: lowercased name becomes a built-in HTML element <footer>
const footer = () => <div>created by me</div>

// ✅ right: custom component is PascalCase
const Footer = () => <div>created by me</div>

const App = () => (
  <div>
    <Footer />
  </div>
)
```

---

## Repro steps (so anyone can verify what I did)
1) **Create & run a Vite React app**
```bash
npm create vite@latest introdemo -- --template react
cd introdemo
npm install
npm run dev
# Expected: local dev server at http://localhost:5173 (or next free port)
```
2) **Minimal render**
   - Replace `src/main.jsx` and `src/App.jsx` with the snippets above.
   - Confirm that the page shows **Greetings** and **Hello world**.
3) **Props & console proof**
   - Implement the `Hello` component; pass `{name}` and `{age}` from `App`.
   - Keep **DevTools → Console** open; verify the logged `props` objects.
4) **Fragments & single root**
   - Wrap siblings in `<>...</>`; ensure no extra wrapper `<div>` is added to the DOM.
5) **Intentional errors to learn**
   - Try rendering `{friends[0]}` to trigger the “objects not valid” error; fix by rendering fields.
   - Try `<footer />` vs `<Footer />` to observe the capitalization behavior.

---

## Mermaid evidence (component tree)
```mermaid
graph TD
  A[App] --> B[Hello (Maya, 36)]
  A[App] --> C[Hello (Peter, 10)]
  A[App] --> D[Footer]
```
> GitHub renders Mermaid in Markdown; this diagram stays text‑based.

---

## Exercises progress (Part 1a)
- **1.1 Course Information (step 1):** Created app structure; rendered course name + parts + totals in one component.
- **1.2 Course Information (step 2):** Refactored into components: **Header**, **Content** (with three **Part** children), and **Total**. Data still lives in `App` and is passed via props.

**Project folders (planned as I continue Part 1):**
```
part1/
  courseinfo/
  unicafe/
  anecdotes/
```
*(Each subfolder is a separate Vite app unless otherwise specified in later parts.)*

---

## Today’s TIL (highlights)
- **JSX** is JavaScript with an HTML‑like syntax; you embed expressions in `{{ }}` and must close tags like `<br />`. A component can only return **one** parent element (use **Fragments** `<>...</>` to group siblings).  
- **Props** let parents pass data down to children; values can be strings or any evaluated JS (numbers, objects, functions).  
- **Capitalization** rule: lowercase names are treated as built‑in HTML tags; **PascalCase** names refer to your components.  
- **Do not render objects** directly—render their fields or map them to elements.  
- **Keep the console open**—React + ESLint warnings and red stack traces are your fastest feedback loop.

---

## Self‑quiz for tomorrow (retrieval practice)
1) Why can’t components return two adjacent JSX elements without a wrapper? How do **Fragments** fix this?
2) What’s the difference between `<footer />` and `<Footer />` in JSX?
3) What happens if you try to render `{friends[0]}`? How do you fix it?
4) Show two ways to pass values to `Hello`: a literal string and an **expression**.
5) What port does Vite use by default, and how do you change it if it’s busy or you need a fixed port?

---

## Commit suggestions
```bash
docs(part1): add day log for Part 1a (intro to React)
docs(part1): add Mermaid component tree for 1.1–1.2
chore(part1): scaffold courseinfo/unicafe/anecdotes directories
```

---

## References (for repo readers)
- Full Stack Open — Part 1a: **Introduction to React**  
  https://fullstackopen.com/en/part1/introduction_to_react
- React docs — **Writing markup with JSX**  
  https://react.dev/learn/writing-markup-with-jsx
- React docs — **Passing props to a component**  
  https://react.dev/learn/passing-props-to-a-component
- React docs — **Fragments (`<>...</>`)**  
  https://react.dev/reference/react/Fragment
- Vite docs — **server.port (default 5173)** and dev server options  
  https://vite.dev/config/server-options
- My annotated reading (PDF): _Fullstack part1 — Introduction to React_ (attached in this repo for proof)
