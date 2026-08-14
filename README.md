_This projet was made by Nour Mina as part of the IDS Fintech Backend Training Program_ <br> <br>
_website: https://nourminaa-todo-frontend-react-tsx/_ <br>
_github repo: https://github.com/nourrminaa/todo-frontend-react-tsx_ <br>

# 1. Task Tracker

No backend & no database: everything lives in the browser's `localStorage`, so the tasks are still there next time the page is opened (on the same browser & same computer) built with **React + TypeScript + Vite**.

## 2. What it does

- Add new tasks
- Edit a task's text
- Delete a task
- Check a task off as completed / uncheck it
- Filter the list by **All**, **Incomplete** or **Completed**
- Everything is saved to `localStorage`

## 3. Project structure

```
todo-app/
├── index.html              the one HTML page
├── src/
│   ├── main.tsx            entry point: renders <App /> into #root
│   ├── App.tsx             owns all the state, talks to localStorage
│   ├── App.css
│   ├── index.css           shared styles
│   ├── types.ts            shared TypeScript types (Task, FilterType)
│   └── components/
│       ├── TaskForm.tsx    "add a new task" input + button
│       ├── FilterBar.tsx   the All / Incomplete / Completed tabs
│       ├── TaskList.tsx    maps tasks to TaskItem
│       ├── TaskItem.tsx    one task row (checkbox, edit, delete)
│       └── *.css           one stylesheet file per component
├── package.json
└── vite.config.ts
```

## 4. How the data flows

1. `App.tsx` holds the **only** copy of the task list, in a `useState<Task[]>([])`
2. On the very first render, a `useEffect` with an empty `[]` dependency array reads any saved tasks out of `localStorage`
3. Every time the task list changes, a second `useEffect` (dependency array `[tasks]`) writes the current list back into `localStorage`
4. `App` passes the task list (or a filtered version of it) and handler functions (`addTask`, `toggleTask`, `deleteTask`,`editTask`) down to its children as **props**. This is called the "Lifting State Up" pattern child components never touch `localStorage` or hold their own copy of the tasks, they just call the function they were given
5. `TaskItem` does keep one small piece of _local_ state (`isEditing`), because nothing outside that single row needs to know about it.

## 5. Requirements & how to run it

```bash
node - v; # check you have Node.js installed
```

5.1. Install the dependencies:

```
npm install
```

5.2. Start the local dev server:

```
npm run dev
```

5.3. Open the URL it prints in your terminal in your browser and tada.

</br>_end._
