# Writing Your First Test

Now that we have our environment set up, we want to start a new project and demonstrate the project works by writing a very small test.

First, let's lay out the project.

### Laying Out a Ruby Project

We should all have a directory to store our code projects. I personally use `~/Projects` but it's completely up to you. Make sure you know how to find this directory both via the terminal and via your operating systems file explorer.

Inside our project directory, we want to create a directory to hold this exercise. Let's call it  `ruby-game-of-life-tdd`.

Next, we want to add a few directories and files to make up a small Ruby project. Below is how I recommend laying out a project:

```
lib/  # Directory to store your projects source code.
test/ # Directory to store your projects test code.
 - all.rb # Ruby code to run your tests.
README.md # File to state the project's goals and how to use it.
Gemfile # Ruby code to declare what our project needs to run.
```

These files and directores are enough to get started. The project structure I started with is [my first commit on github.](https://github.com/zspencer/test-driving-conways-game-of-life-in-ruby-code/tree/bd6afa9e12f8195cd34662230304a6c50a335596)


### Installing A Testing Framework

We are going to use the `minitest` testing [framework](http://glossary.codeunion.io/framework) to run our tests. To make `minitest` available in our code we need to install the `minitest` [gem](http://glossary.codeunion.io/gem). To install a gem, we add it's name and the version we want to our projects `Gemfile`. Open up the projects `Gemfile` in an editor and write the following ruby code:

```ruby
# Where to install gems from.
# https://rubygems.org is a popular gem host.
source 'https://rubygems.org'

# Declare we want the gem named "minitest" version 5.4.3.
# Just like books, gems get "re-published" with changes.
# The version number lets us "lock in" which revision
# we want to use.
gem('minitest', '5.4.3')
```

Next we'll install `bundler`, a gem used to install a project's gems. Talk about inception! A gem to install gems! In your terminal type:

```shell
$ gem install bundler
Fetching: bundler-1.7.8.gem (100%)
Successfully installed bundler-1.7.8
Parsing documentation for bundler-1.7.8
Installing ri documentation for bundler-1.7.8
Done installing documentation for bundler after 2 seconds
1 gem installed
```

Finally, we tell bundler to install the gems listed in our `Gemfile`. In your terminal, type:

```shell
$ bundle install
Fetching gem metadata from https://rubygems.org/.........
Installing minitest 5.4.3
Using bundler 1.7.8
Your bundle is complete!
Use `bundle show [gemname]` to see where a bundled gem is installed.
```

Now that we have `minitest` installed we can write our first test!

### Writing a Failing Test

The first part of TDD is "Red", so let's write a test that we expect to fail. This:

* Proves ruby and minitest are working correctly
* Shows us what failing tests look like
* Starts us on the test-driven development process.

Open up `test/all.rb` in your editor and insert the following code:

```ruby
# Tells ruby to look for a file named `minitest/autorun`
# in the directories that are part of the $LOAD_PATH.
# In this case it's probably finding it inside of the gem
# directory.
require 'minitest/autorun'

# Define a class to collect all of our tests.
# The `<` syntax indicates the class on the left of
# the arrow "is a" MiniTest::Test.
class TestGameOfLife < MiniTest::Test
  # Define a test method that we hope will fail.
  # MiniTest expects test methods to start with `test_`.
  def test_failing_test
    # Fail the test if the number 1 is not equal to the number 2.
    assert_equal(1, 2)
  end
end
```

For a more in-depth look at this code, read [the first RED commit message I wrote on github](https://github.com/zspencer/test-driving-conways-game-of-life-in-ruby-code/commit/a6689260fffdaf8171d060d83c2c7fbde09a1e51).

To run this code, run `bundle exec ruby test/all.rb` in your terminal. This prints the following:

```
$ bundle exec ruby test/all.rb
Run options: --seed 24794

# Running:

F

Finished in 0.001144s, 874.1259 runs/s, 874.1259 assertions/s.

  1) Failure:
TestGameOfLife#test_failing_test [test/all.rb:5]:
Expected: 1
  Actual: 2

1 runs, 1 assertions, 1 failures, 0 errors, 0 skips
```

As you practice test driven development, you will want to familiarize yourself with how to read test failure output. It is absolutely critical to pinpoint what test failed and why.

Here's the two things my eyes lock on to as I run the tests:

```
TestGameOfLife#test_failing_test [test/all.rb:5]:
```

This tells us what file the test that failed is in and what line the test in on. It also tells us what component (`GameOfLife`) and which use case (`test_failing_test`) failed.

```
Expected: 1
  Actual: 2
```

These two lines tell us *why* the test failed. When we write and run a red test we want to have an idea of why the test will fail. This allows us to verify the test failed for the right reasons before we implement the code. I can't tell you how many times I've written a test, ignored the message, wrote the code, then burned an hour trying to figure out why the test wouldn't pass only to discover the test was failing for a reason I had not anticipated!

In this case, the test is failing because 1 can never equal 2! Change the test so that it passes and re-run the test.

(Hint: Change the 1 on line 5 in `test/all.rb` to 2 or vice-versa)

```
$ bundle exec ruby test/all.rb
Run options: --seed 21169

# Running:

.

Finished in 0.001176s, 850.3401 runs/s, 850.3401 assertions/s.

1 runs, 1 assertions, 0 failures, 0 errors, 0 skips
```

Hooray! This is what a passing test suite looks like! No scary error messages! Self hi-five!


### Conclusion

What we've just done is:

* Wrote our first bit of test code.
* Ran the test code with `bundle exec ruby test/all.rb`
* Watched the test fail.
* Made the test pass. (By changing the assertion)
* Watched the test pass!

Pat yourself on the back! You're ready to start test driving Conway's Game of Life!

#### Reference Code
I took copious notes while writing the code this book follows.
Make sure you read the book, the notes and the code!

Feel free [to leave comments asking questions](https://github.com/blog/622-inline-commit-notes)! I'll respond as quickly as I can!


* [RED - Wire up our testing framework](https://github.com/zspencer/test-driving-conways-game-of-life-in-ruby-code/commit/a6689260fffdaf8171d060d83c2c7fbde09a1e51)

