# 📘 C Programming Notes

> *"The only way to learn a new programming language is by writing programs in it."*
> — **Dennis Ritchie** (Creator of C)

A structured, beginner-to-advanced documentation for **C Programming** and **Data Structures & Algorithms (DSA)** — built with [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) and hosted on GitHub Pages.

🌐 **Live Site:** [yxshkm404.github.io/c-programming-notes](https://yxshkm404.github.io/c-programming-notes/)

![MkDocs](https://img.shields.io/badge/MkDocs-Material-blue?logo=materialformkdocs)
![GitHub Pages](https://img.shields.io/badge/Hosted-GitHub%20Pages-222?logo=github)
![License](https://img.shields.io/badge/License-MIT-green)
![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-orange)

---

## 📚 Topics Covered

<details>
<summary>🔵 Basics</summary>

- Data Types
- Input & Output (printf, scanf)
- Control Flow (if/else)
- Loops
- Functions
- Pointers
- Memory Management
- Strings
- Structs & Unions
- File I/O
- Preprocessors & Macros
- Bitwise Operators

</details>

<details>
<summary>📊 Complexity Analysis</summary>

- Big O, Big Θ, Big Ω
- Time & Space Complexity

</details>

<details>
<summary>⚙️ Algorithms</summary>

- Sorting
- Searching
- Recursion & Backtracking
- Dynamic Programming
- Greedy Algorithms
- Graph Algorithms

</details>

<details>
<summary>🗃️ Data Structures</summary>

- Arrays
- Stack
- Queue
- Trees
- Heap
- Graphs
- Linked List
- Hashing
- Trie

</details>

<details>
<summary>🏆 Practice Problems</summary>

- Easy 🟢
- Medium 🟡
- Hard 🔴

</details>

---

## 🛠️ Built With

| Tool | Purpose |
|------|---------|
| [MkDocs](https://www.mkdocs.org/) | Static site generator |
| [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) | Theme |
| [GitHub Pages](https://pages.github.com/) | Hosting |
| Markdown | Content writing |

---

## 🚀 Run Locally

Follow these steps to run the project on your machine:

### 1. Clone the repo
```bash
git clone https://github.com/yxshkm404/c-programming-notes.git
cd c-programming-notes
```

### 2. Create & activate virtual environment
```bash
python -m venv venv

# Mac/Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install mkdocs mkdocs-material
```

### 4. Preview locally
```bash
mkdocs serve
```
Open [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser.

### 5. Deploy to GitHub Pages
```bash
mkdocs gh-deploy
```

---

## 📁 Project Structure

```
c-programming-notes/
├── docs/
│   ├── index.md
│   ├── Basics/
│   │   ├── Data Types.md
│   │   ├── Input Output (printf, scanf).md
│   │   ├── Control Flow (if-else).md
│   │   ├── Loops.md
│   │   ├── Functions.md
│   │   ├── Pointers.md
│   │   ├── Memory Management.md
│   │   ├── Strings.md
│   │   ├── Structs & Unions.md
│   │   ├── File IO.md
│   │   ├── Preprocessors & Macros.md
│   │   └── Bitwise Operators.md
│   ├── Complexity Analysis/
│   │   ├── Big O, Big Θ, Big Ω.md
│   │   └── Time & Space Complexity.md
│   ├── Algorithms/
│   │   ├── Sorting.md
│   │   ├── Searching.md
│   │   ├── Recursion & Backtracking.md
│   │   ├── Dynamic Programming.md
│   │   ├── Greedy Algorithms.md
│   │   └── Graph Algorithms.md
│   ├── Data Structures/
│   │   ├── Arrays.md
│   │   ├── Stack.md
│   │   ├── Queue.md
│   │   ├── Trees.md
│   │   ├── Heap.md
│   │   ├── Graphs.md
│   │   ├── Linked List.md
│   │   ├── Hashing.md
│   │   └── Trie.md
│   └── Practice/
│       ├── easy.md
│       ├── medium.md
│       └── hard.md
├── mkdocs.yml
├── README.md
└── .nojekyll
```

---

## 🤝 Contributing

Contributions are welcome and appreciated! Whether it's fixing a typo, improving an explanation, or adding new examples — every bit helps. 🙌

### ✅ What You Can Contribute

- Fix typos or grammar mistakes
- Improve or simplify existing explanations
- Add better code examples
- Add missing topics or subtopics
- Fix broken links or formatting issues
- Add practice problems (Easy / Medium / Hard)

---

### 📋 Contribution Steps

**1. Fork the repository**

Click the **Fork** button at the top right of this page.

**2. Clone your fork**
```bash
git clone https://github.com/your-username/c-programming-notes.git
cd c-programming-notes
```

**3. Create a new branch**
```bash
git checkout -b your-branch-name
# Example: git checkout -b fix/pointers-typo
# Example: git checkout -b add/sorting-examples
```

**4. Set up the project locally**
```bash
python -m venv venv
source venv/bin/activate     # Mac/Linux
venv\Scripts\activate        # Windows

pip install mkdocs mkdocs-material
```

**5. Make your changes**

Edit the relevant `.md` file inside the `docs/` folder.

**6. Preview your changes**
```bash
mkdocs serve
```
Open [http://127.0.0.1:8000](http://127.0.0.1:8000) and verify everything looks correct.

**7. Commit your changes**
```bash
git add .
git commit -m "fix: corrected typo in Pointers.md"
```

**8. Push to your fork**
```bash
git push origin your-branch-name
```

**9. Open a Pull Request**

Go to the original repo on GitHub and click **"New Pull Request"**. Describe what you changed and why.

---

### 📝 Commit Message Format

Please follow this format for commit messages:

| Prefix | When to use |
|--------|-------------|
| `fix:` | Bug fix, typo correction |
| `add:` | New content or topic added |
| `update:` | Improving existing content |
| `remove:` | Removing outdated content |
| `style:` | Formatting changes only |

**Examples:**
```
fix: corrected ASCII table in Data Types.md
add: added merge sort example in Sorting.md
update: improved explanation of pointers
style: fixed code block formatting in Loops.md
```

---

### 🗂️ Writing Style Guide

To keep the docs consistent, please follow these guidelines when writing content:

- Use **simple, beginner-friendly language**
- Always include a **code example** for every concept
- Add **expected output** after every code block
- Use admonitions for tips, warnings, and notes:
  ```
  !!! tip "Title"
      Your tip here.

  !!! warning "Title"
      Your warning here.

  !!! info "Title"
      Your info here.
  ```
- Use **tables** for comparisons (e.g., float vs double)
- Keep code examples **short and focused**

---

### 🐛 Reporting Issues

Found a mistake or something that can be improved?

1. Go to the [Issues](https://github.com/yxshkm404/c-programming-notes/issues) tab
2. Click **"New Issue"**
3. Describe the problem clearly with the page name and what needs to be fixed

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

⭐ If you find this helpful, give it a star — it keeps the motivation going!