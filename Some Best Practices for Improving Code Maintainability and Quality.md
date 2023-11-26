---
title: "Some Best Practices for Improving Code Maintainability and Quality"
seoTitle: "Some Best Practices for Improving Code Maintainability and Quality"
datePublished: Sun May 07 2023 12:57:48 GMT+0000 (Coordinated Universal Time)
cuid: clhdf5rbg000008jye42khxwi
slug: some-best-practices-for-improving-code-maintainability-and-quality
tags: python, best-practices, software-engineering, code-quality, code-maintainability

---

I will discuss my experience while maintaining simulation software written in Python. I was engaged in making some updates to simulation software for transport and logistics, and I noticed that the transport and logistics department, which was supposed to use the software, was not using it because they couldn’t update it to meet their current needs and developers engaged previously had a hard time at maintaining the project. It was immediately apparent that the software was difficult to maintain because many tasks were lumped into each function, making the functions monolithic. It was surprising to learn that the company that developed the project is a well-known software consulting company, and as such, I did not expect them to deliver such poorly written code.

Apart from software projects meeting the functional and non-functional requirements in terms of deliverables, organisations should also have minimum standards in terms of code quality. This is very important because poor code quality will ultimately negatively impact the maintainability of a software project. 

When the project was no longer being used because it was difficult to update it to meet current needs, it was regarded as a failed project by those in charge of transport and logistics. This shows the impacts of not following best practices in software engineering in software projects. The developers of the project failed to, as much as possible, make sure that each function in the software performs only one task. The functions had many lines of code, making reading and understanding the code very difficult. The monolithic functions had higher complexity which made them difficult to maintain. Also, because of the many tasks in each function, there is high code coupling, often resulting in spaghetti code that is hard to understand. Reusing the code for the many tasks embedded within each function was also impossible. Because many tasks were lumped into each function, it was difficult to write tests for a function that would simultaneously test the functionality of the many tasks embedded in one function. This made it practically impossible to adopt a test-driven software development approach.
