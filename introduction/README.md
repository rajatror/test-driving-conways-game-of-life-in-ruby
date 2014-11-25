# Conway's Game of Life in Ruby

Conway's Game of Life is a simulation of a simple ecosystem populated with
social creatures called "cons." These creatures follow four rules governing
their life, death, and re-production:

* A con with fewer than two neighbors dies of loneliness.
* A con with two or three neighbors lives to see another day. Yay! The power of
  friendship!
* A con is born into an empty space surrounded by three cons.
* A con with four or more neighbors dies, due to overcrowding.

These rules are applied on a daily basis and repeat for the duration of the
simulation.

Together, we will build a Game of Life simulator in Ruby using the test driven
development methodology. This will grant some experience:

* Using test driven design to allow a design to emerge.
* Adhering to the four rules of simple design.
* Using an outside-in approach to writing tests.

## Test Driven Design

Test driven design (TDD) is where we write a test to demonstrate a use case
for our code before we write the implementing code. Strict TDD adherents
advocate writing a single test, watching it fail, quickly writing code to make
it pass, then stepping back and refactoring the code to improve its design.
This is known as the red green refactor cycle.

When some of us hear the phrase "red green," we think of a Canadian TV show
featuring a duo who solve problems with an abundance of duct tape. These antics
consist of building a makeshift tool for a some questionable purpose. My
personal favorite was a car mounted harpoon which latches onto passing semi
trucks to save on gas. Invariably, these devices are composed primarily of duct
tape and house hold items and they frequently work for a short while before
failing in a hilarious manner.

I'm confident if Red and Green had diligently refactored as they built these
contraptions their adventures would have had far fewer spectacular failures.
Thankfully, we can learn from their experience and continuously refactor our
code as we write it.

Refactoring is the secret sauce of TDD. When we take regular opportunities to
improve the design of our code without stepping out of a productive flow, we may
improve our code's quality while adding new features. An added benefit is by
frequently changing the design of our code we become better at designing our
code for change.

## The Four Rules of Simple Design

The four rules of simple design are a powerful tool for guiding the design of
our code as it emerges. The rules are:

* All the tests pass.
* The code expresses every idea we need to express.
* There is no duplication of behavior or configuration.
* There are few parts.

Over the course of a career in software, we have many conversations
about whether something is complex or simple. Using these rules as a guide
provides an objective framework for discussing the simplicity of code and helps
reduce the subjectivity of these debates.

## Outside-In Development

Many computer programs have a user interface people use to do work. This is the
"outside" of a program. User input is entered into the interface, processed by
the program, and the result is presented via the interface.

Outside-in software development focuses on use cases. It involves writing tests
that exercise software in a way a user would through the user interface itself
or through code that sits just beneath the user interface.

This technique of writing tests for use cases helps keep code simple by:

* Allowing us to remove code that doesn't need to exist by removing it and
  checking if the use cases break.
* Providing a "safety net" as we remove duplication or introduce new ideas.

Pure outside-in development can have some disadvantages:

* It can be hard to find what code causes a failing use case, since there aren't
  as many checks written for the internal components.
* Checks which interact directly with the user interface and/or outside services
  such as databases and remote APIs get slow quickly.
* If the developer does not spend time extracting sub-components they may wind
  up with a "big ball of mud" software design.

To mitigate these concerns it's helpful to write an outside-in use case, extract
a sub-component, test drive the behavior of the sub-component, then write the
next outside-in use case. This provides your code with both user-facing use
cases to demonstrate your code does what it's supposed to **and** low-level unit
tests which help find code behaving badly.
