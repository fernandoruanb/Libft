<p align="center">
  <img src="https://github.com/ayogun/42-project-badges/raw/main/covers/cover-libft-bonus.png" alt="Libft cover" width="100%">
</p>

<h1 align="center">
  <br>
  <a href="https://github.com/SEU_USUARIO/libft">
    <img src="https://github.com/ayogun/42-project-badges/raw/main/badges/libftm.png" alt="Libft badge" width="200">
  </a>
  <br>
  Libft
  <br>
</h1>

<h4 align="center">
  My first custom C library, built from scratch at <a href="https://www.42.fr/" target="_blank">École 42</a>.
</h4>

<p align="center">
  <img src="https://img.shields.io/badge/Final%20Score-125%2F125-00C853?style=for-the-badge" alt="Final Score 125/125">
  <img src="https://img.shields.io/badge/Language-C-00599C?style=for-the-badge&logo=c" alt="Language C">
  <img src="https://img.shields.io/badge/Build-Makefile-orange?style=for-the-badge" alt="Build Makefile">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge" alt="Status Completed">
</p>

<p align="center">
  <a href="#about-the-project">About</a> •
  <a href="#key-features">Key Features</a> •
  <a href="#main-objectives">Main Objectives</a> •
  <a href="#function-highlights">Function Highlights</a> •
  <a href="#how-to-use">How To Use</a> •
  <a href="#bonus-part">Bonus Part</a> •
  <a href="#team">Team</a>
</p>

---

<!-- Replace the path below with your own GIF -->
<!-- ![demo](./assets/libft-demo.gif) -->

## About the Project

**Libft** was the first major project I developed during my journey at **École 42**.

The main purpose of this project is to teach one of the most important principles in programming: not relying only on ready-made functions, but understanding how they work internally and being able to rebuild them from scratch.

As programmers, we often face limitations. Sometimes we are not allowed to use certain standard library functions, and sometimes the tools we need simply do not exist yet.

That is where **Libft** becomes valuable.

It represents the **first step toward programmer independence**: building a personal library of reusable functions that we fully understand, test, and control.

Over time, this library becomes a solid foundation for future C projects, helping us write code faster, with more confidence and a deeper understanding of memory, strings, pointers, and data structures.

---

## Key Features

- Reimplementation of essential **libc** functions
- Deep practice with **strings**, **memory**, and **pointers**
- Creation of a **static library** using **Makefile**
- Development of reusable utility functions for future projects
- Introduction to **dynamic memory allocation**
- Bonus implementation of **linked lists**
- Stronger understanding of low-level behavior in C

---

## Main Objectives

The **Libft** project helps develop essential skills such as:

- understanding how standard C library functions work internally
- manipulating memory safely and consciously
- handling strings without depending on external helpers
- creating reusable and modular code
- organizing C projects with a proper build system
- producing a static library that can be reused in later projects

---

## Function Highlights

Below are some of the most important ideas and functions explored during the project.

### `ft_atoi`

The prefix `ft` stands for **forty-two**, and it is used to avoid conflicts with the original standard library functions.

The function `ft_atoi` converts a string into an integer.

For example:

```c
"   +42abc"
```

becomes:

```c
42
```

This function is extremely useful because it teaches how textual data can be interpreted and transformed into numeric values that a program can use.

While implementing it, I also had to understand the concept of **integer overflow**. In a signed 32-bit integer, the maximum value is:

```c
2147483647
```

because:

```c
2^31 - 1 = 2147483647
```

Reimplementing `atoi` was not only about reproducing behavior, but about understanding how parsing works internally.

---

### `ft_strlen`

Another simple but fundamental function in the project is `ft_strlen`, which calculates the length of a string.

```c
size_t	ft_strlen(const char *s)
{
	size_t	length;

	length = 0;
	while (s[length] != '\0')
		length++;
	return (length);
}
```

This function is a great exercise for understanding how strings are represented in C: a sequence of characters ending with the null terminator `'\0'`.

Even though this implementation uses indexing, it naturally opens the door to deeper topics such as:

- pointer arithmetic
- memory traversal
- iteration through raw character sequences
- the relationship between arrays and pointers in C

Small functions like this are deceptively important because they strengthen the foundation needed for much more complex work later.

---

### Dynamic Memory and String Manipulation

A major part of **Libft** is learning how to work with dynamically allocated memory.

Some important examples are:

- `ft_strjoin`
- `ft_split`
- `ft_substr`
- `ft_strdup`

These functions taught me how to:

- allocate the correct amount of memory
- copy data safely
- avoid invalid accesses
- think carefully about ownership of allocated memory

One of the most important lessons in C is simple:

```c
malloc -> free
```

Anything allocated on the heap must eventually be released by the programmer.

This discipline is essential to avoid **memory leaks**, which are rigorously evaluated in 42 projects.

---

### `memcpy` vs `memmove`

At first glance, `memcpy` and `memmove` seem very similar, but they solve slightly different problems.

- `memcpy` is used to copy memory when the source and destination **do not overlap**
- `memmove` is designed to handle **overlapping memory regions safely**

This difference is crucial.

If memory areas overlap and `memcpy` is used, the result is undefined and data may be corrupted.  
`memmove`, on the other hand, preserves the original data by handling the copy in a safe direction depending on the situation.

Understanding this distinction helped me think more precisely about how memory behaves at a low level.

---

## Bonus Part

In the **bonus** section of Libft, I worked with **linked lists** using `structs` in C.

Some of the implemented functions include:

- `ft_lstnew`
- `ft_lstadd_front`
- `ft_lstadd_back`
- `ft_lstsize`
- `ft_lstdelone`
- `ft_lstclear`
- `ft_lstiter`
- `ft_lstmap`

This bonus part was extremely valuable because linked lists are one of the first dynamic data structures that really force us to think beyond arrays.

It also became useful in later 42 projects, where organizing data dynamically becomes much more important.

---

## How To Use

To compile the library, run:

```bash
make
```

This will generate the static library:

```bash
libft.a
```

If you also want the bonus part:

```bash
make bonus
```

### Example: compiling a program with Libft

Create your own file, for example `program.c`, include the header at the top:

```c
#include "libft.h"
```

Then compile it together with your library:

```bash
cc -Wall -Wextra -Werror program.c libft.a -I . -o my_program
```

### Notes

- `cc` is usually an alias for `gcc` or `clang`
- `-Wall -Wextra -Werror` enables strict compilation warnings
- `-I .` tells the compiler to search for headers in the current directory
- `-o my_program` defines the output executable name

If you want to test isolated functions during development, you can also compile only the files you need:

```bash
cc -Wall -Wextra -Werror ft_memcpy.c ft_memmove.c main.c -I . -o test_mem
```

This is useful for focused experiments while validating specific behaviors.

---

## Team

**Libft** is an individual project developed at **École 42**.

So this project was entirely built by me.

---

## Final Note

This project was much more than a simple library.

It was my first real step into understanding how C works under the hood: how strings are stored, how memory is manipulated, how functions can be rebuilt from first principles, and how a programmer can start creating their own tools instead of depending only on what already exists.

For me, **Libft** represents the beginning of true programming autonomy.

---
