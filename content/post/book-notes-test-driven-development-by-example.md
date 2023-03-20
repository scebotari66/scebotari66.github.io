---
title: "Book Notes: Test Driven Development By Example"
date: 2019-08-10T17:48:06+03:00
tags: ["book notes", "testing", "tdd"]
---
I have recently finished reading the ["Test Driven Development By Example"](https://www.goodreads.com/book/show/387190.Test_Driven_Development) book by Kent Beck. It has been sitting on my shelf for a very long time. I have bought it after reading about the [#tddisdead](https://dhh.dk/2014/tdd-is-dead-long-live-testing.html) "movement".

The author invites you to code along, which I did. Even if I did not write a single line of Java code in my life, I went to install [IntelliJ IDEA](https://www.jetbrains.com/idea/) and dived in. This was painful at times, but in the end, I managed to keep up. It also forced me to slow down and better "absorb" the presented concepts.

I did not become an avid TDD practitioner in the end, but I often find myself resorting to it when I feel stuck.

# My notes
Test Driven Development is the practice of driving development with automated tests.

The basic idea behind TDD is not new. Before a programmer starts working on a task, usually they already have in mind the inputs and outputs. What TDD does is that it *"takes this age-old idea, mixes it with modern languages and programming environments, and cooks up a tasty stew guaranteed to satisfy your appetite for clean code that works-now"*.  

The end goal of TDD is clean code that works, by first solving the "that works" part of the problem, and then the "clean code" part.

The first rule of TDD is to write new code only if tests fail. The second rule of TDD is to eliminate duplication.

The steps that follow on from the rules (aka TDD mantra) are:

  - **Red**  - write a test that does not pass
  - **Green** - make the test work quickly
  - **Refactor** - clean the code

When we write a test, we imagine the perfect interface. Tests will demonstrate the presence of code we are confident will accomplish our goal.

TDD is a way of managing fear during programming. It induces courage. Courage to clearly interact with your code, colleagues, and users.

TDD is an awareness of the gap between decision and feedback during programming, and techniques to control that gap.

TDD is not about taking teeny-tiny steps, it's about being able to take teeny-tiny steps. If you can make steps too small, you can certainly make steps the right size. If you only take larger steps, you'll never know if smaller steps are appropriate. TDD is a steering process - a little this way, a little that way. There is no right step size, now and forever.

When you practice TDD, you shouldn't be striving for perfection. By saying everything two ways - both as code and as tests - the goal is to reduce the defects enough to move forward with confidence. From time to time a defect will slip through. When that happens, learn your lesson about the test you should have written and move on.

You will often be implementing TDD in code that doesn't have adequate tests. When you don't have enough tests, you are bound to come across refactorings that aren't supported by tests. You could make a refactoring mistake and the tests would all still run. In this case, you should write the tests you wish you had. If you don't, you will eventually break something while refactoring. Then you'll get bad feelings about refactoring and stop doing it so much. Then your design will deteriorate.

TDD's view on tests is pragmatic. In TDD, the tests are a means to an end - the end being code in which we have great confidence. Write tests until fear is transformed into boredom.

One of the great frustrations of many programmers is starting a project with great excitement, then watching the code base decay over time. A year later, all they want is nothing more than dump the now-smelly code and get on to the next project. TDD enables programmers to gain confidence in the code over time. As tests accumulate (and the testing practices improve), there is more confidence in the behavior of the system. As the design is refined, more and more changes become possible.

The customers also appreciate the effects of TDD on the product. A new release of the system just meant more functionality, not a host of new defects to identify among all of their old bugs.

It is common to end up with about the same number of lines of test code as model code when implementing TDD. For TDD to make economic sense, you will need to be able to either write twice as many lines per day as before or write half as many lines for the same functionality.

TDD can be used as a way to strive for perfection, but that isn't its most effective use. In a big system, the parts that are touched all the time should be absolutely rock solid, so that daily changes can be made confidently. As we drift out to the periphery of the system, to parts that don't change often, the tests can be spottier and the design uglier without interfering with the programmers' confidence.

 The order of implementing the tests is important. The next test you decide to implement should teach you something and you should be confident that you can make it work. If you get stuck, then maybe it is a good idea to consider backing up two steps.

With automated, when you start to feel stress, you should run the tests. Running the tests immediately will give you a good feeling and reduces the number of errors you make, which further reduces the stress.

Make the tests so fast to run that you can run them by yourself, and run them often. That way you can catch errors before anyone else sees them.

The more stress you feel, the less likely you are to test enough. When you know you haven't tested enough, you add to your stress. Positive feedback loop. Once again, there needs to be a way to break the loop.

The most important item in the physical setup that you would use for TDD is a "really nice" chair, skimping on the rest of the furniture if necessary. 


### Red bar patterns
Red bar patterns are about when you write tests, where you write tests, and when you stop writing tests.

|   |   |
|---|---|
| One step test  | Pick a test that you are confident you can implement and that will teach you something |
| Starter test | Test a variant of an operation that does not do anything, which will make you think about the inputs, outputs, and where does the operation belong |
| Explanation test  | Explain things in term of tests |
| Learning test  | Learn to use third-party libraries/packages by writing exploration tests on them |
| Another test  | Stay focused on the current test and add other test ideas to the test list |
| Regression test  | When a bug is detected, write a test that fails that bug  |

### Green bar patterns

|   |   |
|---|---|
| Fake it  | Return a constant, then once you have a running test, gradually transform the constant into an expression using variables |
| Obvious implementation | Just implement |
| Triangulate  | Abstract when you have to or more examples |
| One to many | When dealing with collections, implement first without collection (single item), then make it work for the entire set |
