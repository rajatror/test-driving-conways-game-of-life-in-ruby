# Setting Up a Development Environment

Now that we have a high level grasp of Conway's game of life, test driven design, refactoring, the rules of simple design, and outside-in development it's time to get our machine ready. For those of you with a Ruby environment installed already, feel free to jump to [Getting Comfy With the Terminal](#getting-comfy-with-the-terminal)


### Setting up a Ruby Environment
Ruby comes with most Macs and is possible to install on Linux and Windows as well. It is also possible to avoid installing anything and use an online development environment, such as Cloud9 IDE.

#### With Cloud9 IDE (Free and Online, Recommended for Novices)

There are many reasons to use an online development environment instead of running one on your computer. In fact, if it takes more than an hour getting ruby working on your computer I'd strongly suggest using [Cloud9](https://c9.io) as you get comfortable with programming. Cloud9 provides a "Google Docs" like interface for editing and running code from your browser.

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

Congratulations! You've set up a ruby environment you can access anywhere with an Internet connection! Now skip ahead to
[Getting Comfy With the Terminal](#getting-comfy-with-the-terminal).


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

Then you will need to install Ruby. The easiest way to do this is by using the [Rails Installer](http://railsinstaller.org/en) project. For a more detailed installation guide, RailsBridge has [an excellent guide](http://docs.railsbridge.org/installfest/macintosh?back=choose_your_operating_system). Once you've completed the installation instructions, it's time to [get comfy with the terminal](#getting-comfy-with-the-terminal).

#### On Windows

Most Windows machines do not come with Ruby installed. For those of you with Windows machines, I would recommend following RailsBridge's [Ruby for Windows Ruby  installation guide.](http://docs.railsbridge.org/installfest/windows). Once you've completed the installation instructions, familiarize yourself with the Windows terminal.

<INSERT HELPFUL COMMANDS HERE>

#### On Linux
For those of you running Linux, I leave it to you to find the installation instructions for your chosen distribution.

### Getting Comfy With The Terminal
![An elegant weapon for a more civilized age](http://static.tvtropes.org/pmwiki/pub/images/your_fathers_lightsaber.jpg)

Your terminal is one of your most important tools as a software developer. It looks intimidating at first (and it is!), but that decreases with familiarity. Let's take some time to get familiar with your terminal.

The following instructions create a sandbox project to play around in with ruby:
* `mkdir ~/Projects` - Create a directory to store your ruby code.
* `cd ~/Projects` - Navigate your terminal to your Projects directory. The `~` symbol is shorthand for "My User Directory". `~/Projects` expands to `/Users/<your-username>/Projects`.
* `pwd` - Prints out the directory you are in in your terminal.
* `mkdir ./sandbox` - Creates a directory named 'sandbox' in the current working directory. `./` is shorthand for "Where I am now!"
* `ls -l` - Shows all the files in the current directory
* `cd ./sandbox` - Moves into the sandbox directory
* `touch ./happy_place.rb` - Creates an empty file named "happy_place.rb" in your current directory.
* Open `~/Projects/snadbox/happy_place.rb` in your preferred code editor. I prefer [Atom](https://atom.io) or [Sublime Text](http://www.sublimetext.com).
* Write some code and save the file. If you're not sure what code to write, how about `puts "I AM DOING PROGRAMMING!"`?
* `ruby ./happy_place.rb` - Tells the `ruby` program to run the code stored in `./happy_place.rb`.
* `cd ..` Moves "up" a directory, bringing your terminal back to `~/Projects/`
* `pwd` - Should show you `/Users/<your-username>/Projects

Congrats! now that you're familiar with the terminal, let's write our first test!

