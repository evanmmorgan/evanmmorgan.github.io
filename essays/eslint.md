---
layout: essay
type: essay
title: "ESLint and learning JavaScript"
# All dates must be YYYY-MM-DD format!
date: 2026-09-24
published: true
labels:
  - Questions
  - Quizzes
  - TypeScript
---
## My first time running ESLint

The first time I ran ESLint, all I saw on my screen was hundreds of red squiggly lines. It was like everything I did went wrong. I was shocked thinking my code wouldn’t work but ESLint was screaming at me to abide by the JavaScript coding standards. I had to go line by line through my program and learn that not every programming language has the same rules you have to follow. After learning about the coding standards, I can say they are definitely worth having even though they can be a bit tedious.  

## What are coding standards?

Coding standards are a set of rules that help developers create clean, readable code with fewer bugs. Many people think this is just spacing and indentation, but there are many more aspects of these standards such as using camel case for variables and functions, always using const or let instead of var to prevent scope related bugs, and using strict equality === instead of ==. Through these standards, I learned more than I thought I would about JavaScript.

## What ESLint taught me about JavaScript 

In JavaScript, it is considered a good practice to use type-safe equality operators which are === and !== instead of == and !=. The ESLint rule for this is called “eqeqeq”. [ESLint documentation](https://eslint.org/docs/latest/rules/eqeqeq) describes that == does type cohesion using something called the “Abstract Equality Comparison Algorithm”. This means that JavaScript converts both values to the same type before comparing them. These examples are considered true using == and false using ===:

```typescript
//All return true.
[] == false
[] == ![]
3 == "03"

//All return false.
[] === false
[] === ![]
3 === "03"
```

And if any of these comparisons are used in a statement it can be very difficult to spot and figure out what the problem is. So by using ===, we are checking both value and data type. By being forced to change this equality operator whenever I ran ESLint, it taught me about how I should be defining comparisons.

## Annoying parts

JavaScript is a great programming language, but it is different from other programming languages I’ve learned in college like Java and C. My ESLint configuration uses 2 space indentation instead of 4 spaces or a tab like in other programming languages I was used to, and I've had to go back and fix indentation issues in my code almost every time. Another rule I found annoying and honestly useless is the requirement for a new line at the end of every program file. There is probably an important reason for it, but it doesn’t make any sense to me personally. 

## It gets easier

Over the past couple weeks of learning JavaScript and TypeScript, the more programming I do, the easier it becomes overall because I am aware of what I can expect every time I run my file through ESLint. I now know that I should indent 2 spaces rather than 4, and that there is even an option to change tab size to 2, and you can use eslint --fix to fix a lot of errors automatically.

## Conclusion

Overall, coding standards are an important aspect if not the most important aspect of programming because it creates a guideline for developers to follow and make sure their code is correctly abiding by these rules. Not only does it make it easier for programmers to read each other's code, the standards help new programmers like me learn the language faster because by having to follow strict rules, we are required to have an understanding of what is and isn’t acceptable when it comes to following the rules.

# Use of AI

I used Claude code to outline this essay. All content and ideas are my own.
