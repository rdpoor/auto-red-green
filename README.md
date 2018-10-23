# auto-red-green
Continuous testing with red-green growl reporting

## Why continuous testing?

When you're in the heat of development, it's a distraction to make a change to your 
source code, switch windows, run the tests and look at the results.  `auto-red-green`
is a tool that monitors your changes and automatically re-runs your test suite.  If
the tests complete without error, a small "growl" window is displayed with a green
icon.  If the tests have any errors, the growl window displays a red icon.

I've found this tool to be a remarkable boost to productivity: you can stay focused
on the changes you're making rather than switching contexts to run tests.

## About auto-red-green

auto-red-green is a tool for continuous testing under macOS.  Once launched, it 
monitors the file system inside your project directory and upon detecting a change, 
it will run a test suite of your choice.  When the test suite completes, it briefly 
displays a growl window showing a green bead for success or a red bead for failure.

## To install

1. Inside your project directory, create a sub-directory named `autotest` (or 
   actually any name of your choosing).
2. Copy this repository into the `autotest` directory.
3. Customize the `run-test` script file to run the test suite for your project.

## To run

In a shell window:

    cd $PROJECT_DIRECTORY/autotest
    ./autorun-tests

## Caveats

This is a tool I developed for personal use.  It works for my needs, but it should be
made more general.  The most glaring problems:

* **It is macOS specific**  With a bit of work, this could be tranformed into an 
OS-aware Python script so it could work equally well under Windows, Linux or macOS.

* **`growl-tests` expects Python `unittest`**  If you look at the last few lines of 
`grow-tests`, you'll see that it extracts the tail of the recorded log files and 
formats the text it finds there as part of the growl window message.  It currently 
expects output from Python's `unittest` package, but it should be possible to create 
adaptors for other test suites.

## In closing: comments and pull requests are welcome!

As mentioned, I've found `auto-red-green` to be a remarkable boost to productivity.  
But it could be much more general and less brittle.  You're invited to create issues 
and pull requests!
