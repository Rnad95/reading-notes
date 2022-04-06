# Read: 19 - Spring and Sockets

## Introduction

---
purely functional programming usually designates a programming paradigm—a style of building the structure and elements of computer programs—that treats all computation as the evaluation of mathematical functions.

![](https://miro.medium.com/max/1400/1*1yVFdiXsp3u40OZfCrG14A.png
)
## Difference between pure and impure functional programming

---
The functional when it uses some concepts of functional programming, such as first-class functions and higher-order functions.  

First-class function need not be purely functional, as they may use techniques from the imperative paradigm such as arrays or methods that use mutable cells, which update their state as side effects. The exact difference between pure and impure functional programming is a matter of controversy.

- Pure Function always produce the same results when given the same parameter meanwhile the impure maube produce different result.

- The pure `never` has a side effect, the Impure has.

![](https://i.ytimg.com/vi/NmLRWv4oiJE/hqdefault.jpg)

## Properties of purely functional programming

---

1- Strict versus non-strict evaluation

- In particular, it ensures that the programmer does not have to consider in which order programs are evaluated, since eager evaluation will return the same result as lazy evaluation. However, it is still possible that an eager evaluation may not terminate while the lazy evaluation of the same program halts.

2- Parallel computing

- It simplifies parallel computing since two purely functional parts of the evaluation never interact. Parallel computing is a type of computation in which many calculations or processes are carried out simultaneously.

3- Data structures

- Purely functional data structures are often represented in a different way than their imperative counterparts. Therefore, purely functional data structures can be used in languages which are non-functional, but they may not be the most efficient tool available, especially if persistency is not required.

![](https://www.modernescpp.com/images/blog/Functional/TheDefinition/CharakteristikenFunktionaleProgrammierungEng.png)

## Purely functional language

---

A purely functional language is a language which only admits purely functional programming. Purely functional programs can however be written in languages which are not purely functional.
