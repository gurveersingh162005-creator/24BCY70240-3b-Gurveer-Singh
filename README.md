# 📚 Library Management System (Next.js + TypeScript)

A modern **Library Management System** built with **Next.js App Router, TypeScript, Tailwind CSS v4 and React Hooks**.
This project demonstrates **CRUD operations, search functionality, local storage persistence, and modern UI design**.

---

# 🚀 Live Features

✨ Add new books
🔍 Search books instantly
❌ Remove books
💾 Data saved in LocalStorage (persists after refresh)
🎨 Modern Glassmorphism UI
⚡ Built with Next.js App Router + Tailwind v4

---

# 🛠 Tech Stack

| Technology      | Purpose          |
| --------------- | ---------------- |
| Next.js 14      | React Framework  |
| TypeScript      | Type Safety      |
| Tailwind CSS v4 | Styling          |
| React Hooks     | State Management |
| LocalStorage    | Data Persistence |
| pnpm            | Package Manager  |

---

# 📁 Project Structure

```
library-management/
│
├── app/
│   ├── favicon.ico
│   ├── globals.css
│   ├── layout.tsx
│   └── page.tsx
│
├── components/
│   ├── BookCard.tsx
│   ├── BookForm.tsx
│   └── SearchBar.tsx
│
├── types/
│   └── Book.ts
│
├── tailwind.config.ts
├── postcss.config.js
└── package.json
```

---

# ⚙️ Installation & Setup

## 1️⃣ Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/library-management-nextjs.git
cd library-management-nextjs
```

## 2️⃣ Install Dependencies

```bash
pnpm install
```

## 3️⃣ Run Development Server

```bash
pnpm dev
```

Open 👉 http://localhost:3000

---

# 🧠 Core Concepts Implemented

## 📌 1. TypeScript Model

`types/Book.ts`

```ts
export interface Book {
  id: number;
  title: string;
  author: string;
}
```

This defines the structure of each book object.

---

## 📌 2. React State Management

Main state stored in **app/page.tsx**

```tsx
const [books, setBooks] = useState<Book[]>([]);
const [search, setSearch] = useState("");
```

We manage:

* Book list
* Search query

---

## 📌 3. Local Storage Persistence 💾

Books are saved in browser storage.

### Load books on startup

```tsx
useEffect(() => {
  const savedBooks = localStorage.getItem("books");
  if (savedBooks) {
    setBooks(JSON.parse(savedBooks));
  } else {
    setBooks([
      { id: 1, title: "The Great Gatsby", author: "F. Scott Fitzgerald" },
      { id: 2, title: "To Kill a Mockingbird", author: "Harper Lee" },
      { id: 3, title: "1984", author: "George Orwell" },
    ]);
  }
}, []);
```

### Save books whenever updated

```tsx
useEffect(() => {
  localStorage.setItem("books", JSON.stringify(books));
}, [books]);
```

---

## 📌 4. CRUD Operations

### ➕ Add Book

```tsx
const addBook = (title: string, author: string) => {
  const newBook: Book = {
    id: Date.now(),
    title,
    author,
  };
  setBooks([...books, newBook]);
};
```

---

### ❌ Remove Book

```tsx
const removeBook = (id: number) => {
  setBooks(books.filter((book) => book.id !== id));
};
```

---

### 🔍 Search Books

```tsx
const filteredBooks = books.filter((book) =>
  book.title.toLowerCase().includes(search.toLowerCase())
);
```

---

# 🎨 UI Design

The UI uses **Tailwind CSS v4** and Glassmorphism effects.

Example card style:

```tsx
<div className="bg-white/90 backdrop-blur-xl shadow-xl rounded-3xl p-6">
```

---

# 📷 Application Screens

### 🏠 Main Page

* Search bar
* Add book form
* Book listing

---

# 🎯 Learning Outcomes

This project demonstrates:

* React functional components
* Next.js App Router structure
* Tailwind v4 setup
* Component-based architecture
* State management with hooks
* Persistent client-side storage
* Modern UI design principles
