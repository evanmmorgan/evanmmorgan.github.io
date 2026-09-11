# Type Errors and Timers

## Coming from Java

Before taking ICS 314, I had never touched JavaScript or TypeScript. In my previous classes we used Java to learn basic data types and structures, C for low-level programming, and Python for its simplicity and its ability to pull from outside libraries for quick projects. As we began learning JavaScript, then TypeScript, it felt a little odd transitioning over for the first week. By the end TypeScript was flagging errors before I ran anything which is the same kind of error checking I relied on in Java.

## What the type checker caught

I think that some of the attributes of TypeScript are very useful like type annotation. At first, I thought it was overly verbose to declare which type each variable is or a function should return. But I realized in comparison to JavaScript it can reduce a lot of careless errors at compile time. If you accidentally assign a number to something you want to be a string, TypeScript will make sure you know. 

```typescript
let city: string = 5;
// Error: Type 'number' is not assignable to type 'string'.
```
![Editor flagging a number assigned to a string variable](images/error.png)

The ES6 features like let/const replacing var also felt useful because using const stops you from accidentally reassigning a variable. Another great feature is type inference. For very basic variable definitions, like an increment variable, we don’t need to explicitly mention it is a number. Something like: 

```typescript
let count = 0;    // TypeScript infers number
count = "ten";    // Error: Type 'string' is not assignable to type 'number'.
```

## Coding against a timer

The course uses WODs or quizzes as short programming exercises you have to finish against a timer. I find these very useful for training my ability to program under a time constraint. For example, on the very first WindChill quiz, I felt completely lost and I was unable to finish in time and my code ended up being all wrong due to using the incorrect formula. I had no idea what I was doing, the code still felt abstract. Then a week later during the most recent quiz, which was to create a score system for a game of cornhole, I finished with fully functional code with 5 minutes to spare on the timer. The assignments we had doing a Jamba Juice program also helped me understand the overall structure that TypeScript code should have. I only attempted them once, but at the end I felt that if I had repeated the assignments I definitely would have completed them much faster.

## What I’ll do next

Overall, I think that TypeScript is a very useful language from a software engineering perspective because of the nature of its variable and function definitions. But it also isn’t overly verbose compared to a language like Java which in class we learned requires a main method and three keywords before even being able to run that main method. At first, the in class quizzes made me feel stressed, but now I feel like it’s a great way to practice writing clean code like doing a workout for your brain. In the next module I will also definitely be attempting the assignments multiple times in order to get Rx time and improve my programming skills even more. Finally, I hope that I will have the same learning experience with future in class quizzes and assignments.
	
	
