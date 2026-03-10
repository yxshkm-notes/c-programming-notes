# C Program Structure 🏗️

!!! abstract "What You'll Learn"
    - ✅ How a C program is structured from top to bottom
    - ✅ What `#include <stdio.h>` actually means
    - ✅ The role of `main()` function
    - ✅ How header files and modules work
    - ✅ How to split your code into multiple files
    - ✅ How the compilation process works

---

## 📖 Introduction

Every C program follows a specific **structure**. Just like a building has a foundation, walls, and a roof — a C program has a specific order that must be followed.

```
     ┌─────────────────────────────────────────┐
     │         ANATOMY OF A C PROGRAM          │
     ├─────────────────────────────────────────┤
     │  1. Comments          // description    │
     │  2. Header Files      #include <stdio.h>│
     │  3. Macros / Constants#define PI 3.14   │
     │  4. Global Variables  int count = 0;    │
     │  5. Function Prototypes int add(int, int)│
     │  6. main() Function   int main() { }    │
     │  7. Other Functions   int add(...) { }  │
     └─────────────────────────────────────────┘
```

---

## 🔍 The Simplest C Program

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

Even this tiny program has **4 key parts**. Let's break each one down:

```
#include <stdio.h>     ← 1. Header File
                       
int main() {           ← 2. main() Function
    printf("Hello!");  ← 3. Statement
    return 0;          ← 4. Return Value
}
```

---

## 🧩 Part 1 — Comments

Comments are **notes for humans** — the compiler completely ignores them.

### Single-line Comment

```c
// This is a single-line comment
int age = 20;  // This stores the age
```

### Multi-line Comment

```c
/*
   This is a multi-line comment.
   You can write as many lines as you want.
   Great for describing functions or sections.
*/
int main() {
    // code here
}
```

!!! tip "Good Practice"
    Always write comments to explain **why** you wrote the code, not just **what** it does.
    ```c
    // BAD comment
    x = x + 1;  // adds 1 to x

    // GOOD comment
    x = x + 1;  // move to next index after processing current element
    ```

---

## 📦 Part 2 — Header Files (`#include`)

Header files are **pre-written C code** that gives your program extra abilities.

### Syntax

```c
#include <filename.h>   // Standard library (system header)
#include "filename.h"   // Your own custom header file
```

### How it Works

```
     Your Program               stdio.h
     ┌──────────────┐          ┌────────────────────┐
     │ #include     │ ──copy──>│ printf declaration  │
     │ <stdio.h>    │          │ scanf declaration   │
     │              │          │ FILE declaration    │
     │ int main() { │          │ ...and more         │
     │   printf()   │          └────────────────────┘
     │ }            │
     └──────────────┘
```

!!! info "What does `#include` actually do?"
    `#include` is a **preprocessor directive**. Before compiling, the C preprocessor literally **copies and pastes** the entire contents of the header file into your program. That's why you can use `printf` — its declaration is pasted in from `stdio.h`.

---

## 📚 Common Standard Header Files

```
     ┌─────────────────────────────────────────────────────────┐
     │              STANDARD HEADER FILES IN C                 │
     ├──────────────┬──────────────────────────────────────────┤
     │ Header File  │ What It Provides                         │
     ├──────────────┼──────────────────────────────────────────┤
     │ stdio.h      │ printf, scanf, FILE, fopen, fclose       │
     │ stdlib.h     │ malloc, free, exit, atoi, rand           │
     │ string.h     │ strlen, strcpy, strcat, strcmp           │
     │ math.h       │ sqrt, pow, sin, cos, abs, ceil, floor    │
     │ ctype.h      │ isalpha, isdigit, toupper, tolower       │
     │ time.h       │ time, clock, difftime, strftime          │
     │ limits.h     │ INT_MAX, INT_MIN, CHAR_MAX               │
     │ float.h      │ FLT_MAX, DBL_MAX, FLT_MIN               │
     │ stdbool.h    │ bool, true, false                        │
     │ assert.h     │ assert() for debugging                   │
     └──────────────┴──────────────────────────────────────────┘
```

### Examples of Each Header File

=== "stdio.h"
    ```c
    #include <stdio.h>

    int main() {
        printf("Hello!\n");          // Print output

        int num;
        scanf("%d", &num);           // Read input

        FILE *f = fopen("file.txt", "r");  // File operations
        fclose(f);

        return 0;
    }
    ```

=== "stdlib.h"
    ```c
    #include <stdlib.h>

    int main() {
        // Dynamic memory
        int *arr = (int*)malloc(5 * sizeof(int));
        free(arr);

        // Random number
        int r = rand() % 100;   // 0 to 99

        // String to number
        int n = atoi("42");

        // Exit program
        exit(0);
    }
    ```

=== "string.h"
    ```c
    #include <string.h>
    #include <stdio.h>

    int main() {
        char str1[] = "Hello";
        char str2[] = "World";
        char result[50];

        printf("Length: %lu\n", strlen(str1));   // 5
        strcpy(result, str1);                     // Copy
        strcat(result, str2);                     // Concat
        printf("Result: %s\n", result);           // HelloWorld

        return 0;
    }
    ```

=== "math.h"
    ```c
    #include <math.h>
    #include <stdio.h>

    int main() {
        printf("sqrt(16) = %.1f\n",  sqrt(16));   // 4.0
        printf("pow(2,8) = %.0f\n",  pow(2, 8));  // 256
        printf("ceil(4.2)= %.1f\n",  ceil(4.2));  // 5.0
        printf("floor(4.9)= %.1f\n", floor(4.9)); // 4.0
        printf("abs(-10) = %d\n",    abs(-10));    // 10

        return 0;
    }
    ```

=== "ctype.h"
    ```c
    #include <ctype.h>
    #include <stdio.h>

    int main() {
        char ch = 'a';

        printf("%d\n", isalpha(ch));    // 1 (true)
        printf("%d\n", isdigit('5'));   // 1 (true)
        printf("%c\n", toupper(ch));    // A
        printf("%c\n", tolower('Z'));   // z

        return 0;
    }
    ```

=== "stdbool.h"
    ```c
    #include <stdbool.h>
    #include <stdio.h>

    int main() {
        bool isLoggedIn = true;
        bool isAdmin    = false;

        if (isLoggedIn) {
            printf("Welcome!\n");
        }

        printf("Admin: %s\n", isAdmin ? "Yes" : "No");

        return 0;
    }
    ```

---

## 🏷️ Part 3 — Macros & Constants (`#define`)

Macros define **constants or shortcuts** that are replaced before compilation.

```c
#include <stdio.h>

#define PI        3.14159
#define MAX_SIZE  100
#define SQUARE(x) ((x) * (x))   // Macro function

int main() {
    float area = PI * SQUARE(5);

    printf("Area of circle: %.2f\n", area);  // 78.54
    printf("Max size:       %d\n",  MAX_SIZE);

    return 0;
}
```

!!! warning "Macros vs const"
    ```c
    #define MAX 100        // Macro — no type, no semicolon
    const int MAX = 100;   // Constant — has type, safer to use
    ```
    Prefer `const` over `#define` for constants — it's type-safe and easier to debug.

---

## 🌍 Part 4 — Global Variables

Variables declared **outside all functions** — accessible from anywhere in the program.

```c
#include <stdio.h>

int count = 0;          // Global variable
char appName[] = "MyApp";

void increment() {
    count++;            // Can access global variable
}

int main() {
    printf("App: %s\n", appName);
    increment();
    increment();
    increment();
    printf("Count: %d\n", count);  // 3
    return 0;
}
```

!!! warning "Use Global Variables Carefully"
    Global variables can be changed from **anywhere** in the program, making bugs hard to find. Use them only when necessary.

---

## 📋 Part 5 — Function Prototypes

A **declaration** of a function before it is defined — tells the compiler the function exists.

```c
#include <stdio.h>

// ── Function Prototypes ─────────────────────────
int  add(int a, int b);
void printResult(int result);
float average(int arr[], int size);

// ── main() ──────────────────────────────────────
int main() {
    int result = add(10, 20);
    printResult(result);
    return 0;
}

// ── Function Definitions ────────────────────────
int add(int a, int b) {
    return a + b;
}

void printResult(int result) {
    printf("Result: %d\n", result);
}
```

!!! info "Why do we need prototypes?"
    C reads code **top to bottom**. If you call `add()` in `main()` but define it below `main()`, the compiler won't know what `add` is yet. A prototype solves this by declaring the function early.

---

## 🚀 Part 6 — The `main()` Function

The `main()` function is the **entry point** of every C program. Execution always starts here.

```c
int main() {
    // Your code goes here
    return 0;
}
```

### What does `return 0` mean?

```
     ┌─────────────────────────────────────────┐
     │         RETURN VALUES OF main()          │
     ├───────────┬─────────────────────────────┤
     │ Value     │ Meaning                     │
     ├───────────┼─────────────────────────────┤
     │ return 0  │ Program ran successfully ✅  │
     │ return 1  │ Program ended with error ❌  │
     │ return -1 │ Program ended with error ❌  │
     └───────────┴─────────────────────────────┘
```

### main() with Command Line Arguments

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    printf("Number of arguments: %d\n", argc);

    for (int i = 0; i < argc; i++) {
        printf("Argument %d: %s\n", i, argv[i]);
    }

    return 0;
}
```

**Run:**
```bash
./program hello world
```

**Output:**
```
Number of arguments: 3
Argument 0: ./program
Argument 1: hello
Argument 2: world
```

---

## ⚙️ How C Compilation Works

Before your C code runs, it goes through **4 stages**:

```
     Source Code          Preprocessor        Compiler
     ┌──────────┐         ┌──────────┐        ┌──────────┐
     │ hello.c  │──────── │ Expands  │──────> │ Converts │
     │          │  Step 1 │ #include │        │ to       │
     │#include  │         │ #define  │        │ Assembly │
     │<stdio.h> │         │ macros   │        │ code     │
     └──────────┘         └──────────┘        └──────────┘
                                                    │ Step 3
                          Executable          Assembler + Linker
                          ┌──────────┐        ┌──────────┐
                          │ hello    │<─────  │ Combines │
                          │ (runs!)  │ Step 4 │ object   │
                          │          │        │ files    │
                          └──────────┘        └──────────┘
```

| Step | Stage | What Happens |
|------|-------|-------------|
| 1 | **Preprocessor** | Handles `#include`, `#define`, `#ifdef` |
| 2 | **Compiler** | Converts C code → Assembly code |
| 3 | **Assembler** | Converts Assembly → Machine code (`.o` file) |
| 4 | **Linker** | Combines object files → Final executable |

### Compile Commands

```bash
# Basic compile
gcc hello.c -o hello

# Run
./hello

# Compile with math library
gcc program.c -o program -lm

# Compile with warnings
gcc -Wall hello.c -o hello

# Compile multiple files
gcc main.c utils.c -o program
```

---

## 📂 Part 7 — Multiple File Structure (Modules)

For larger programs, you split code into **multiple files**. This is called **modular programming**.

### File Structure

```
my_project/
├── main.c        ← Entry point
├── math_utils.c  ← Math functions
├── math_utils.h  ← Math function declarations
├── string_utils.c
└── string_utils.h
```

### math_utils.h (Header File)

```c
// math_utils.h
// Guards prevent the file from being included twice
#ifndef MATH_UTILS_H
#define MATH_UTILS_H

int  add(int a, int b);
int  subtract(int a, int b);
int  multiply(int a, int b);
float divide(float a, float b);

#endif
```

### math_utils.c (Implementation File)

```c
// math_utils.c
#include "math_utils.h"

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int multiply(int a, int b) {
    return a * b;
}

float divide(float a, float b) {
    if (b == 0) return 0;
    return a / b;
}
```

### main.c (Main Program)

```c
// main.c
#include <stdio.h>
#include "math_utils.h"   // Your own header — use " " not < >

int main() {
    int a = 10, b = 5;

    printf("Add:      %d\n", add(a, b));
    printf("Subtract: %d\n", subtract(a, b));
    printf("Multiply: %d\n", multiply(a, b));
    printf("Divide:   %.1f\n", divide(a, b));

    return 0;
}
```

### Compile Multiple Files

```bash
gcc main.c math_utils.c -o program
./program
```

**Output:**
```
Add:      15
Subtract: 5
Multiply: 50
Divide:   2.0
```

!!! tip "Header Guards"
    Always use header guards (`#ifndef`) to prevent a header from being included more than once:
    ```c
    #ifndef MY_HEADER_H    // If not defined
    #define MY_HEADER_H    // Define it

    // ... your declarations ...

    #endif                 // End of guard
    ```

---

## 🧠 Complete Program — Putting It All Together

Here's a complete, well-structured C program using everything above:

```c
/*
 * Program: Student Grade Calculator
 * Author:  Yashkm
 * Date:    2024
 * Desc:    Calculates average and grade for a student
 */

// ── Header Files ────────────────────────────────
#include <stdio.h>
#include <string.h>

// ── Macros ──────────────────────────────────────
#define MAX_SUBJECTS  5
#define PASS_MARK     50

// ── Global Variables ────────────────────────────
int totalStudents = 0;

// ── Function Prototypes ─────────────────────────
float  calculateAverage(int marks[], int size);
char   getGrade(float average);
void   printReport(char name[], int marks[], int size);

// ── main() ──────────────────────────────────────
int main() {
    char name[50];
    int  marks[MAX_SUBJECTS];

    printf("╔══════════════════════════════════╗\n");
    printf("║    STUDENT GRADE CALCULATOR      ║\n");
    printf("╚══════════════════════════════════╝\n\n");

    printf("Enter student name: ");
    scanf("%s", name);

    printf("Enter %d subject marks:\n", MAX_SUBJECTS);
    for (int i = 0; i < MAX_SUBJECTS; i++) {
        printf("  Subject %d: ", i + 1);
        scanf("%d", &marks[i]);
    }

    totalStudents++;
    printReport(name, marks, MAX_SUBJECTS);

    printf("\nTotal students processed: %d\n", totalStudents);
    return 0;
}

// ── Function Definitions ────────────────────────
float calculateAverage(int marks[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) sum += marks[i];
    return (float)sum / size;
}

char getGrade(float average) {
    if (average >= 90) return 'A';
    if (average >= 80) return 'B';
    if (average >= 70) return 'C';
    if (average >= 60) return 'D';
    return 'F';
}

void printReport(char name[], int marks[], int size) {
    float avg   = calculateAverage(marks, size);
    char  grade = getGrade(avg);

    printf("\n┌──────────────────────────────────┐\n");
    printf("│ REPORT CARD                      │\n");
    printf("├──────────────────────────────────┤\n");
    printf("│ Name:    %-24s│\n", name);
    printf("├──────────────────────────────────┤\n");

    for (int i = 0; i < size; i++) {
        printf("│ Subject %d: %-22d│\n", i + 1, marks[i]);
    }

    printf("├──────────────────────────────────┤\n");
    printf("│ Average: %-24.2f│\n", avg);
    printf("│ Grade:   %-24c│\n", grade);
    printf("│ Status:  %-24s│\n", avg >= PASS_MARK ? "PASS ✅" : "FAIL ❌");
    printf("└──────────────────────────────────┘\n");
}
```

**Sample Output:**
```
╔══════════════════════════════════╗
║    STUDENT GRADE CALCULATOR      ║
╚══════════════════════════════════╝

Enter student name: Yashkm
Enter 5 subject marks:
  Subject 1: 85
  Subject 2: 90
  Subject 3: 78
  Subject 4: 92
  Subject 5: 88

┌──────────────────────────────────┐
│ REPORT CARD                      │
├──────────────────────────────────┤
│ Name:    Yashkm                  │
├──────────────────────────────────┤
│ Subject 1: 85                    │
│ Subject 2: 90                    │
│ Subject 3: 78                    │
│ Subject 4: 92                    │
│ Subject 5: 88                    │
├──────────────────────────────────┤
│ Average: 86.60                   │
│ Grade:   B                       │
│ Status:  PASS ✅                 │
└──────────────────────────────────┘

Total students processed: 1
```

---

## ✅ Quick Reference Summary

```
     ┌────────────────────────────────────────────────┐
     │        C PROGRAM STRUCTURE — CHEAT SHEET       │
     ├─────────────────────┬──────────────────────────┤
     │ Part                │ Example                  │
     ├─────────────────────┼──────────────────────────┤
     │ Comment             │ // single line           │
     │                     │ /* multi line */         │
     ├─────────────────────┼──────────────────────────┤
     │ Header File         │ #include <stdio.h>       │
     │ Custom Header       │ #include "myfile.h"      │
     ├─────────────────────┼──────────────────────────┤
     │ Macro               │ #define PI 3.14          │
     │ Macro Function      │ #define SQ(x) ((x)*(x)) │
     ├─────────────────────┼──────────────────────────┤
     │ Global Variable     │ int count = 0;           │
     ├─────────────────────┼──────────────────────────┤
     │ Function Prototype  │ int add(int a, int b);   │
     ├─────────────────────┼──────────────────────────┤
     │ main() Function     │ int main() { }           │
     ├─────────────────────┼──────────────────────────┤
     │ Return Value        │ return 0; // success     │
     └─────────────────────┴──────────────────────────┘
```

---

!!! success "You Now Understand C Program Structure!"
    You know what every line of a C program means — from `#include` to `return 0`. This is the foundation everything else builds on. 💪

!!! tip "Next Topic"
    Now that you understand structure, learn about the types of data you can store → **[Data Types](Data Types.md)**