# Writing Your First Test

Now that we have a high level grasp of Conway's game of life, test driven design, refactoring, the rules of simple design, and outside-in development it's time to get our machine ready. For those of you with a Ruby environment installed already, feel free to jump to the section heading [Laying Out a Ruby Project] (#laying-out-a-ruby-project)

To do this we need to:

1. Make Ruby available by installing it to our computer.
2. Create a project.
3. Write a failing test and run it to see the tests are working.


### Installing Ruby on Your Computer

#### With Cloud9 IDE (Free and Online)

For those of you without a personal computer, unable to install Ruby on your machine, or somewhat nervous about the whole thing, I recommend a free, online Ruby environment provided by [Cloud9](https://c9.io). Cloud9 provides a "Google Docs" like interface for editing and running code from your browser.

To get started:

1. Signup for Cloud9.
2. Go to your Dashboard.
3. Click the green "Create New Workspace" button.
4. Select "Custom" from the set of options.
5. Give it a name! (Something like "unobtrusive-buffalo" or "your-name-does-tdd-in-ruby"
6. Click "Create"
7. Wait a moment as it creates your environment for you.
8. Click the workspace name (It's in a drawer on the left-hand side of the screen)
9. Click the green "Start Editing" button
10. Familiarize yourself with the editor.
    * Run `irb` in the [terminal](https://docs.c9.io/run_an_application.html#method-2:-from-the-terminal)
    * Create a new ruby file, name it "yo.rb" and save it with the contents `puts "Hi there!"`
    * Run `ruby yo.rb` from the terminal.

Congrats! You've set up a ruby environment you can access anywhere with an Internet connection! Feel free to skip ahead to [Laying Out a Ruby Project](#laying-out-a-ruby-project).


#### On a Mac

For those of you on a recent Mac, you likely already have Ruby installed and available. Open up your `terminal` app (Found in /Applications/Utilities) and type `ruby --version` then hit the `return` key. You should see something like this:

```bash
$ ruby --version
ruby 2.1.2p95 (2014-05-08 revision 45877) [x86_64-darwin13.0]
```

(Note: A `$` is a conventional indicator for your terminal prompt, it is not something to type)

If instead, you see:

```
$ ruby --version
bash: ruby: command not found
```

Then you will need to install Ruby. The easiest way to do this is by using the [Rails Installer](http://railsinstaller.org/en) project. For a more detailed installation guide, RailsBridge has [an excellent guide](http://docs.railsbridge.org/installfest/macintosh?back=choose_your_operating_system). Once you've completed the installation instructions, familiarize yourself with the `terminal` app on OS X:
* `mkdir ~/Projects` - Create a directory to store your ruby code.
* `cd ~/Projects` - Navigate your terminal to your Projects directory. The `~` symbol is shorthand for "My User Directory". `~/Projects` expands to `/Users/<your-username>/Projects`.
* `pwd` - Prints out the directory you are in in your terminal.
* `mkdir ./sandbox` - Creates a directory named 'sandbox' in the current working directory. `./` is shorthand for "Where I am now!"
* `ls` - Shows all the files in the current directory
* `cd ./sandbox` - Moves into the sandbox directory
* `touch ./happy_place.rb` - Creates an empty file named "happy_place.rb" in your current directory.
* Open `~/Projects/snadbox/happy_place.rb` in your preferred code editor. I prefer [Atom](https://atom.io) or [Sublime Text](http://www.sublimetext.com).
* Write some code and save the file. If you're not sure what to write, how about `puts "I AM DOING PROGRAMMING!"`?
* `ruby ./happy_place.rb` - Tells the `ruby` program to run the code stored in `./happy_place.rb`.
* `cd ..` Moves "up" a directory, bringing your terminal back to `~/Projects/`
* `pwd` - Should show you `/Users/<your-username>/Projects

Congrats! now that you're familiar with the terminal, move on to [Laying Out a Ruby Project](#laying-out-a-ruby-project)

#### On Windows

Most Windows machines do not come with Ruby installed. For those of you with Windows machines, I would recommend following RailsBridge's [Ruby for Windows Ruby  installation guide.](http://docs.railsbridge.org/installfest/windows). Once you've completed the installation instructions, familiarize yourself with the Windows terminal.

<INSERT HELPFUL COMMANDS HERE>

#### On Linux
For those of you running Linux, I leave it to you to find the installation instructions for your chosen distribution.

### Laying Out a Ruby Project

Now that you have a `~/Projects` directory to store your code, you'll want to create a directory to store your code as you work through this book. Create one and name it something like `ruby-tdd-conways-game-of-life`. Next, we want to set up the file structure:

```
lib/  # Directory to store your projects source code.
test/ # Directory to store your projects test code.
  all.rb # Ruby code to run your tests.
README # File to state the project's goals and how to use it.
Gemfile # Ruby code to declare what our project needs to run.
```

This structure should be enough for us to get started. If you would like to see the file system structure I started with, you can [peruse my first commit on github.](https://github.com/zspencer/test-driving-conways-game-of-life-in-ruby-code/tree/bd6afa9e12f8195cd34662230304a6c50a335596)

Because we want to use the `minitest` gem to run our tests, we'll want to add it to the `Gemfile`. Open up the `Gemfile` in your editor and ensure it's contents look like this:

```ruby
source 'https://rubygems.org'

gem 'minitest', '5.4.3'
```

Now, we'll want to install `bundler`, a tool used to install the gems we want to use in our project.

```
$ gem install bundler
Fetching: bundler-1.7.8.gem (100%)
Successfully installed bundler-1.7.8
Parsing documentation for bundler-1.7.8
Installing ri documentation for bundler-1.7.8
Done installing documentation for bundler after 2 seconds
1 gem installed
```

Then, we tell bundler to install the gems declared in our `Gemfile`.

```
$ bundle install
Fetching gem metadata from https://rubygems.org/.........
Installing minitest 5.4.3
Using bundler 1.7.8
Your bundle is complete!
Use `bundle show [gemname]` to see where a bundled gem is installed.
```

Now we have `minitest` installed! Let's write our first test!

### Writing a Failing Test

Now that we're ready to roll we should write a test that we expect to fail. This:

* Proves ruby and minitest are working correctly
* Shows us what failing tests look like
* Primes us for the test-driven development process.


Open up the file `test/all.rb` in your editor and insert the following code:

```ruby
require 'minitest/autorun'

class TestGameOfLife < MiniTest::Test
  def test_failing_test
    assert_equal(1, 2)
  end
end
```
For a line-by-line breakdown of the code, read [the first failing commit I wrote on github](https://github.com/zspencer/test-driving-conways-game-of-life-in-ruby-code/commit/a6689260fffdaf8171d060d83c2c7fbde09a1e51?diff=unified).

To run this code, run `bundle exec ruby test/all.rb` in your terminal. This should print the following:

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

This failure message is telling us that the test at line number 5  in `test/all.rb` did not pass. Why? Because we asserted that 1 is equal to 2! As you practice test driven development, you will want to familiarize yourself with how to read test failure output. It is absolutely critical to pinpointing what test failed and why. Here's the two things my eyes lock on to as I run the tests:

```
TestGameOfLife#test_failing_test [test/all.rb:5]:
```

This line tells us what file the test is in and what line the test is on. It also tells us what component (`GameOfLife`) and which use case (`test_failing_test`) failed.

```
Expected: 1
  Actual: 2
```

These two lines tell us *why* the test failed. When we first write a test, we want to have an idea of why the test will fail so that we can verify it's failing for the right reasons before we go and implement the code. I can't tell you how many times I've written a test, ignored the message, wrote the code, then burnd an hour trying to figure out why the test wouldn't pass only to discover that the test was failing for a reason I had not anticipated!

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

Ah! Yes, no scary failure messages! Hooray! Self-hi-five!

### Conclusion

What we've just done is:

* Set up an environment for writing ruby code.
* Wrote our first bit of test code.
* Ran the test code with `bundle exec ruby test/all.rb`
* Watched the test fail.
* Made the test pass. (By changing the assertion)
* Watched the test pass!

Pat yourself on the back! You're ready to start test driving the problem at hand!

#### Reference Code

* [RED - Wire up our testing framework](https://github.com/zspencer/test-driving-conways-game-of-life-in-ruby-code/commit/a6689260fffdaf8171d060d83c2c7fbde09a1e51)

(Hint: I took copious notes while writing the code this book follows. Make sure you read the notes and the code! Feel free [to leave comments asking questions](https://github.com/blog/622-inline-commit-notes)! I'll respond ASAP!)
