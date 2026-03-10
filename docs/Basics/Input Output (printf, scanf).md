# Input & Output in C 🖥️

!!! abstract "What You'll Learn"
    - ✅ How `printf()` works — displaying output
    - ✅ How `scanf()` works — reading user input
    - ✅ Format specifiers and their uses
    - ✅ Special characters (escape sequences)
    - ✅ Common mistakes and how to avoid them

---

## 📖 Introduction

Every program needs two things — **input** (data coming in) and **output** (data going out). In C, we use:

| Function | Purpose | Header File |
|----------|---------|-------------|
| `printf()` | Print output to the screen | `stdio.h` |
| `scanf()` | Read input from the keyboard | `stdio.h` |

To use these functions, always include this at the top of your program:

```c
#include <stdio.h>
```

!!! tip "What does stdio.h mean?"
    **stdio** stands for **St**an**d**ard **I**nput/**O**utput. It's a built-in C library that gives you access to `printf`, `scanf`, and many other I/O functions.

---

## 🖨️ printf() — Printing Output

`printf()` is used to **display text, numbers, and variables** on the screen.

### Basic Syntax

```c
printf("format string", variable1, variable2, ...);
```

### Your First Output

```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

**Output:**
```
Hello, World!
```

---

### Printing Variables

You can print variables using **format specifiers** — special placeholders that tell `printf` what type of value to print.

```c
#include <stdio.h>

int main() {
    int age       = 20;
    float height  = 5.9;
    char grade    = 'A';
    char name[]   = "Yashkm";

    printf("Name:   %s\n", name);
    printf("Age:    %d years\n", age);
    printf("Height: %.1f ft\n", height);
    printf("Grade:  %c\n", grade);

    return 0;
}
```

**Output:**
```
Name:   Yashkm
Age:    20 years
Height: 5.9 ft
Grade:  A
```

---

## 🏷️ Format Specifiers

Format specifiers tell `printf` and `scanf` **what type of data** to handle.

```
     ┌─────────────────────────────────────────────┐
     │           FORMAT SPECIFIER CHART            │
     ├──────────┬──────────────┬───────────────────┤
     │ Spec     │ Data Type    │ Example           │
     ├──────────┼──────────────┼───────────────────┤
     │  %d      │ int          │ 42                │
     │  %i      │ int          │ 42                │
     │  %f      │ float        │ 3.140000          │
     │  %.2f    │ float        │ 3.14              │
     │  %lf     │ double       │ 3.141592653589    │
     │  %c      │ char         │ A                 │
     │  %s      │ string       │ Hello             │
     │  %ld     │ long int     │ 1234567890        │
     │  %u      │ unsigned int │ 4294967295        │
     │  %o      │ octal        │ 52 (= 42 in dec)  │
     │  %x      │ hexadecimal  │ 2a (= 42 in dec)  │
     │  %e      │ scientific   │ 3.14e+00          │
     │  %p      │ pointer addr │ 0x7fff5fbff5ac    │
     │  %%      │ literal %    │ 100%              │
     └──────────┴──────────────┴───────────────────┘
```

### Format Specifier Examples

```c
#include <stdio.h>

int main() {
    int num = 42;

    printf("Decimal:     %d\n",  num);
    printf("Octal:       %o\n",  num);
    printf("Hexadecimal: %x\n",  num);
    printf("Uppercase:   %X\n",  num);

    float pi = 3.14159;
    printf("\nDefault float:    %f\n",   pi);
    printf("2 decimal places: %.2f\n",  pi);
    printf("Scientific:       %e\n",    pi);

    printf("\nLiteral percent: 100%%\n");

    return 0;
}
```

**Output:**
```
Decimal:     42
Octal:       52
Hexadecimal: 2a
Uppercase:   2A

Default float:    3.141590
2 decimal places: 3.14
Scientific:       3.141590e+00

Literal percent: 100%
```

---

## 🔢 Width & Precision Formatting

You can control **how wide** the output is and **how many decimal places** to show.

### Syntax

```
%[flags][width][.precision]specifier
```

### Width Formatting

```c
#include <stdio.h>

int main() {
    // Right-aligned (default)
    printf("%10d\n",  42);    //         42
    printf("%10s\n",  "Hi");  //         Hi

    // Left-aligned (use - flag)
    printf("%-10d|\n", 42);   // 42        |
    printf("%-10s|\n", "Hi"); // Hi        |

    // Zero padding
    printf("%010d\n", 42);    // 0000000042

    return 0;
}
```

**Output:**
```
        42
        Hi
42        |
Hi        |
0000000042
```

### Precision Formatting

```c
#include <stdio.h>

int main() {
    float price = 99.9999;

    printf("%.0f\n", price);   // 100
    printf("%.1f\n", price);   // 100.0
    printf("%.2f\n", price);   // 100.00
    printf("%.4f\n", price);   // 99.9999

    return 0;
}
```

---

## ⌨️ scanf() — Reading Input

`scanf()` reads **input from the keyboard** and stores it in variables.

### Basic Syntax

```c
scanf("format string", &variable1, &variable2, ...);
```

!!! warning "Don't forget the `&` (ampersand)!"
    The `&` gives `scanf` the **memory address** of the variable so it can store the value there. Forgetting `&` is one of the most common beginner mistakes!
    ```c
    int age;
    scanf("%d", age);   // ❌ WRONG — missing &
    scanf("%d", &age);  // ✅ CORRECT
    ```

### Reading Different Data Types

```c
#include <stdio.h>

int main() {
    int    age;
    float  height;
    char   grade;
    char   name[50];

    printf("Enter your name: ");
    scanf("%s", name);           // No & needed for strings/arrays

    printf("Enter your age: ");
    scanf("%d", &age);

    printf("Enter your height (ft): ");
    scanf("%f", &height);

    printf("Enter your grade: ");
    scanf(" %c", &grade);        // Note the space before %c

    printf("\n--- Your Details ---\n");
    printf("Name:   %s\n",   name);
    printf("Age:    %d\n",   age);
    printf("Height: %.1f\n", height);
    printf("Grade:  %c\n",   grade);

    return 0;
}
```

**Sample Run:**
```
Enter your name: Yashkm
Enter your age: 20
Enter your height (ft): 5.9
Enter your grade: A

--- Your Details ---
Name:   Yashkm
Age:    20
Height: 5.9
Grade:  A
```

---

### Reading Multiple Values at Once

```c
#include <stdio.h>

int main() {
    int x, y;

    printf("Enter two numbers (e.g. 10 20): ");
    scanf("%d %d", &x, &y);

    printf("You entered: %d and %d\n", x, y);
    printf("Sum: %d\n", x + y);

    return 0;
}
```

**Sample Run:**
```
Enter two numbers (e.g. 10 20): 10 20
You entered: 10 and 20
Sum: 30
```

---

## 🔤 Escape Sequences

Escape sequences are **special characters** that start with a backslash `\`.

```
     ┌──────────────────────────────────────────┐
     │         ESCAPE SEQUENCE TABLE            │
     ├─────────┬────────────────────────────────┤
     │  Code   │ Meaning                        │
     ├─────────┼────────────────────────────────┤
     │  \n     │ New line (Enter key)            │
     │  \t     │ Horizontal tab (4-8 spaces)     │
     │  \r     │ Carriage return                 │
     │  \\     │ Backslash ( \ )                 │
     │  \"     │ Double quote ( " )              │
     │  \'     │ Single quote ( ' )              │
     │  \0     │ Null character (end of string)  │
     │  \a     │ Alert / beep sound              │
     │  \b     │ Backspace                       │
     └─────────┴────────────────────────────────┘
```

### Escape Sequence Examples

```c
#include <stdio.h>

int main() {
    printf("Line 1\nLine 2\nLine 3\n");
    printf("\nTabbed:\tColumn1\tColumn2\n");
    printf("She said \"Hello!\"\n");
    printf("Path: C:\\Users\\Yashkm\\\n");
    printf("100%% Complete\n");

    return 0;
}
```

**Output:**
```
Line 1
Line 2
Line 3

Tabbed:	Column1	Column2
She said "Hello!"
Path: C:\Users\Yashkm\
100% Complete
```

---

## 🔄 How printf & scanf Work Together

Here's a complete, practical example combining everything:

### 🧮 Simple Student Report Card

```c
#include <stdio.h>

int main() {
    char name[50];
    int  math, science, english;
    float average;

    // ── Input ──────────────────────────────────
    printf("╔══════════════════════════════╗\n");
    printf("║     STUDENT REPORT CARD      ║\n");
    printf("╚══════════════════════════════╝\n\n");

    printf("Enter student name:       ");
    scanf("%s", name);

    printf("Enter Math marks (0-100): ");
    scanf("%d", &math);

    printf("Enter Science marks:      ");
    scanf("%d", &science);

    printf("Enter English marks:      ");
    scanf("%d", &english);

    // ── Processing ─────────────────────────────
    average = (math + science + english) / 3.0;

    // ── Output ─────────────────────────────────
    printf("\n╔══════════════════════════════╗\n");
    printf("║         RESULTS              ║\n");
    printf("╠══════════════════════════════╣\n");
    printf("║ Name:    %-20s║\n", name);
    printf("║ Math:    %-20d║\n", math);
    printf("║ Science: %-20d║\n", science);
    printf("║ English: %-20d║\n", english);
    printf("╠══════════════════════════════╣\n");
    printf("║ Average: %-20.2f║\n", average);
    printf("║ Grade:   ");

    if      (average >= 90) printf("A+ (Excellent!)      ║\n");
    else if (average >= 80) printf("A  (Very Good)       ║\n");
    else if (average >= 70) printf("B  (Good)            ║\n");
    else if (average >= 60) printf("C  (Average)         ║\n");
    else                    printf("F  (Fail)            ║\n");

    printf("╚══════════════════════════════╝\n");

    return 0;
}
```

**Sample Run:**
```
╔══════════════════════════════╗
║     STUDENT REPORT CARD      ║
╚══════════════════════════════╝

Enter student name:       Yashkm
Enter Math marks (0-100): 88
Enter Science marks:      92
Enter English marks:      85

╔══════════════════════════════╗
║         RESULTS              ║
╠══════════════════════════════╣
║ Name:    Yashkm             ║
║ Math:    88                 ║
║ Science: 92                 ║
║ English: 85                 ║
╠══════════════════════════════╣
║ Average: 88.33              ║
║ Grade:   A  (Very Good)     ║
╚══════════════════════════════╝
```

---

## ⚠️ Common Mistakes

### 1. Missing `&` in scanf

```c
int age;
scanf("%d", age);   // ❌ WRONG — undefined behavior
scanf("%d", &age);  // ✅ CORRECT
```

### 2. Wrong format specifier

```c
float price = 9.99;
printf("%d\n", price);    // ❌ WRONG — %d is for int
printf("%f\n", price);    // ✅ CORRECT
```

### 3. Missing `\n` causing messy output

```c
printf("Enter name: ");
printf("Enter age: ");
// Output: Enter name: Enter age:  ← all on one line!

printf("Enter name:\n");
printf("Enter age:\n");
// Output: Each on its own line ✅
```

### 4. Reading char after int with scanf

```c
int age;
char grade;

scanf("%d", &age);
scanf("%c", &grade);   // ❌ Reads leftover newline '\n'
scanf(" %c", &grade);  // ✅ Space before %c skips whitespace
```

!!! info "Why the space before `%c`?"
    When you press Enter after typing a number, `scanf` leaves a `\n` in the input buffer. The space before `%c` tells `scanf` to **skip any whitespace** (including that leftover newline) before reading the character.

---

## 🆚 printf vs scanf — Side by Side

```
  ┌─────────────────────────────────────────────────────┐
  │              printf vs scanf                        │
  ├───────────────────────┬─────────────────────────────┤
  │      printf()         │         scanf()             │
  ├───────────────────────┼─────────────────────────────┤
  │ Sends data OUT        │ Reads data IN               │
  │ to the screen         │ from the keyboard           │
  │                       │                             │
  │ printf("%d", num);    │ scanf("%d", &num);          │
  │                       │                             │
  │ No & needed           │ & required (except strings) │
  │                       │                             │
  │ Returns number of     │ Returns number of items     │
  │ characters printed    │ successfully read           │
  └───────────────────────┴─────────────────────────────┘
```

---

## 🔁 Other I/O Functions

Besides `printf` and `scanf`, C has simpler I/O functions:

### getchar() and putchar() — Single Character I/O

```c
#include <stdio.h>

int main() {
    char ch;

    printf("Type a character: ");
    ch = getchar();           // Read single character

    printf("You typed: ");
    putchar(ch);              // Print single character
    putchar('\n');

    return 0;
}
```

### puts() — Print a String with Auto Newline

```c
#include <stdio.h>

int main() {
    char message[] = "Hello, C Programming!";

    puts(message);  // Automatically adds \n at the end

    return 0;
}
```

---

## ✅ Quick Reference Summary

| Function | Use | Example |
|----------|-----|---------|
| `printf()` | Print to screen | `printf("Hello %d", 5);` |
| `scanf()` | Read from keyboard | `scanf("%d", &num);` |
| `getchar()` | Read one character | `char c = getchar();` |
| `putchar()` | Print one character | `putchar('A');` |
| `puts()` | Print string + newline | `puts("Hello");` |

---

!!! success "You're Ready!"
    Now you know how to take input and display output in C. These two functions — `printf` and `scanf` — are the foundation of almost every C program you'll ever write. Practice them well! 💪

!!! tip "Next Topic"
    Now that you can handle I/O, learn how to make decisions in your programs → **[Control Flow](Control Flow (if-else).md)**