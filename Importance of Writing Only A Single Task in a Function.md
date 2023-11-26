---
title: "Importance of Writing Only A Single Task in a Function"
seoTitle: "Importance of Writing Only A Single Task in a Function"
seoDescription: "Importance of Writing Only A Single Task in a Function"
datePublished: Sun May 07 2023 17:36:51 GMT+0000 (Coordinated Universal Time)
cuid: clhdp4luk000a09l8biaa9ub0
slug: importance-of-writing-only-a-single-task-in-a-function
tags: software-development, python, software-engineering, code-quality, data-engineering

---

I will be talking about the importance of writing only a single task in a function based on my recent experience in a project I was involved with. I was engaged in making some updates to simulation software for transport and logistics, and I noticed that the transport and logistics department, which was supposed to use the software, was not using it because they couldn’t update it to meet their current needs and developers engaged previously had a hard time at maintaining the project. It was immediately apparent that the software was difficult to maintain because many tasks were lumped into each function, making the functions monolithic. It was surprising to learn that the company that developed the project is a well-known software consulting company, and as such, I did not expect them to deliver such poorly written code.

Apart from software projects meeting the functional and non-functional requirements in terms of deliverables, organisations should also have minimum standards in terms of code quality. This is very important because poor code quality will ultimately have a negative impact on the maintainability of a software project. The solution to their problems was writing only a single task in a function.

Some of the benefits of doing this are:

1. It reduces the code complexity of functions.
    
2. Reduce code coupling
    
3. Makes code readable, easier to understand and maintain
    
4. Improves code quality
    
5. Encourages the adoption of test-driven software development
    

## Reduction of Code Complexity of Functions

Writing only a single task in a function reduces the function code complexity by simply reducing the number of lines of code of the function. Another way the complexity is reduced is that it reduces the nesting of conditional statements or program loop statements. 

## Reduce Code Coupling

It decouples the tasks that could have been coupled in one function into separate functions, which improves the reuse functions.

## Make Code Readable, Easier to Understand and Maintain

Reducing code complexity and coupling are the major factors for improving code readability and understandability, consequently improving code maintainability. 

## Improve Code Quality

Improved readability, understandability and maintainability of code are key to improved code quality. 

## Encourage The Adoption of Test-Driven Software Development

By writing only a single task in a function, it is easier to write tests for each task represented by a function. This makes it possible to adopt a test-driven software development approach.
