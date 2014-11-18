# Conway's Game of Life in Ruby

Conway's Game of Life is a simulation of a simple ecosystem populated with
highly social mythical creatures called "cons." These creatures follow four
rules governing their life, death, and re-production:

* A con with fewer than two neighbors dies of loneliness :(
* A con with two or three neighbors lives to see a nother day. Yay! The power of
  friendship!
* A con is born into any empty space surrounded by exactly three cons.
* A con with four or more neighbors dies, as if from overpopulation.


These rules are applied at the end of each day, and repeat for the duration of
the simulation.

This book guides us through test driving a Game of Life simulator in Ruby. This
provides some experience:

* Using test driven development to allow a design to emerge.
* Adhering to the four rules of simple design.
* Using an outside-in approach to writing tests.

## Test Driven Development

Test driven development (TDD) is where we write a test to demonstrate a use case
for our code before we write the implementing code. Strict TDD adherents
advocate writing a single test, watching it fail, quickly writing code to make
it pass, then stepping back and refactoring the code to improve its design.
This is known as the red green refactor cycle.

When some of us hear the phrase "red green," we think of a Canadian TV show
featuring a duo who solve problems with an abundance of duct tape. Traditionally
these antics would consist of building a makeshift tool for a some questionable
purpose. My personal favorite was a car mounted harpoon which latches onto
passing semi trucks to save on gas. Invariably, these devices are composed
primarily of duct tape and house hold items and while they frequently work for a
short while, fail in a hilarious manner.

I'm confident if Red and Green had diligently refactored as they built these
contraptions their adventures would have had far fewer spectacular failures.
Thankfully, we can learn from their experience and continuously refactor our
code as we write our tests.

Refactoring is the secret sauce of TDD. When we take regular opportunities to
improve the design of our code without stepping out of a productive flow of
adding new functionality it allows us to improve our code's quality while adding
new features. An added benefit is that by frequently changing the design of our
code we become better at designing our code for change.

## The Four Rules of Simple Design

The four rules of simple design are a powerful tool for guiding the design of
our code as it emerges. The rules are:

* All the tests pass.
* The code expresses every idea we need to express.
* There is no duplication of behavior or configuration.
* There are few parts.

Over the course of a career in software development, there are have many
conversations about whether something is complex or simple. Using these rules as
a guide provides an objective framework for discussing the simplicity of code
and helps reduce the subjectivity of these debates.

## Outside-In Development

Most computer programs have a user interface which is responsible for ensuring
people may accomplish the work they need with the computer program.  This is the
"outside" of a program, as most work is done through this interface.

Outside-in software development is a technique for writing code focused on users
use cases. It involves writing tests that interact with software either through
the user interface itself or through the same API that the user interface uses
to interact with the rest of the code.

This technique helps keep code simple by ensuring no code exists that doesn't
meet a user's use case.

Outside-in development is not the only way to build well-designed software.
There is also inside-out development, which focuses on independently building
components and assembling them into a larger piece of software.

Outside-in development works best when groups of people or individuals own a
vertical slice of some software's functionality; while inside-out works best
when teams need to share components.

A reasonable criticism of outside-in development is it may de-emphasize the need
to extract small, well tested components; which may result in a big ball of mud
code base.
