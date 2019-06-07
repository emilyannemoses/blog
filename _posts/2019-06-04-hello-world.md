---
layout: post
title:  "Hello world: Python, Ruby, JavaScript"
---

A "Hello world" program is known as the most basic program one can create in any programming language. In this post, I'm going to show you how to create a "Hello world" program in Python, JavaScript and Ruby. 

The next installment will be the "Hello world" program in C++ and Go.

<h1>Python</h1>

Python is an interpreted language, which means all we need to write a program in it is to download the lanugage and start up the interpreter.

We'll be using the Python interpreter in <i>interactive mode</i>, which means we'll be writing a single statement and the interpreter will be executing only that line.

First download Python3: [Scroll to the bottom and Click on your operating system][download-python]

Once it has installed, the folder name should be something like "Python 3.7" Now locate the program called IDLE within that folder and open it.

This should open the Python 3.7.3 Shell.

We start writing Python scripts after the > > > prompt.

Type the following:

```python
>>> print("Hello world")
```

And press enter.

The string Hello world should have printed out.

Congratulations! You coded your first program in Python.

<h1>Ruby</h1>

You may already have Ruby installed on your computer. Depending on which operating system you're using, open your terminal emulator to check:

- macOS: open your Terminal application
- Linux: open up a shell
- Windows: open Command Prompt

And type `which Ruby`  If it gives you a path name such as /usr/bin/ruby, that means you already have Ruby installed. If it doesn't, that means you have to [install Ruby][download-ruby]

Now that we've confirmed we have Ruby, we can use IRB which stands for Interactive Ruby, similar to Python's IDLE.

For macOS and Linux users, simply type `irb` into your Terminal or shell. For Windows users, open Interactive Ruby from the Ruby section of your Start Menu.

Now type:

```ruby
puts "Hello world"
```

`puts` is just like Python's `print()` statement.

Congratulations! You've written your first program in Ruby!

<h1>JavaScript</h1>

JavaScript, similarly to Python and Ruby, as an interpreter called Node.  We can [download node here][download-node]

Open your operating system's terminal emulator and type `node`

This should look familiar!

Now type:

```javascript
console.log("Hello world")
```

It should print Hello world to the console.

Congratulations, you've written your first program in JavaScript using Node!

<h4>BUT LET'S NOT STOP THERE!</h4>

Since JavaScript is a browser-based language, that is, it is interpreted by every web browser in existence, we can print Hello world directly to our browser.

For this, [download Chrome][download-chrome] if you don't already have it.

Once you open the Chrome browser, right-click on the browser window and choose `Inspect` from the dropdown menu.

A window should open up. Now, at the top of that window you should see an Elements tab and a Console tab.  Click the Console tab.

Does this look familiar at all?  After the `>` start writing your JavaScript:

```javascript
console.log("Hello world")
```

And press enter.

You should see Hello world printed to that Console.

But, there's a cooler thing we could do!

Try typing this:

```javascript
document.write("Hello world")
```

Press enter, and check out the browser page.  It should be a blank page with Hello world on it!

You just manipulated the DOM (Document Object Model) with JavaScript using the JS Console. Congratulations!

Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr"><a href="https://twitter.com/hashtag/learntocode?src=hash&amp;ref_src=twsrc%5Etfw">#learntocode</a> - Check out how easy it is to execute <a href="https://twitter.com/hashtag/HelloWorld?src=hash&amp;ref_src=twsrc%5Etfw">#HelloWorld</a> apps in three different languages, <a href="https://twitter.com/hashtag/Python?src=hash&amp;ref_src=twsrc%5Etfw">#Python</a> <a href="https://twitter.com/hashtag/Ruby?src=hash&amp;ref_src=twsrc%5Etfw">#Ruby</a> and <a href="https://twitter.com/hashtag/javascript?src=hash&amp;ref_src=twsrc%5Etfw">#javascript</a> <br><br>****<a href="https://twitter.com/hashtag/E4Everything?src=hash&amp;ref_src=twsrc%5Etfw">#E4Everything</a><br>****<a href="https://t.co/U2eO3nOj3y">https://t.co/U2eO3nOj3y</a></p>&mdash; Emily Anne Moses (@emilyannemoses) <a href="https://twitter.com/emilyannemoses/status/1136979168024039424?ref_src=twsrc%5Etfw">June 7, 2019</a></blockquote>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


<span><a href="https://eamoses.github.io/blog/2019/06/03/vocabulary-continued.html" style="float:left;">Previous: Vocabulary Continued</a><a href="https://eamoses.github.io/blog/2019/06/05/hello-world-continued.html" style="float:right;">Next: Hello world Continued</a></span>

[download-python]: https://www.python.org/downloads/release/python-373/

[download-vscode]: https://code.visualstudio.com/download

[download-ruby]: https://www.ruby-lang.org/en/documentation/installation/

[download-node]: https://nodejs.org/en/download/

[download-chrome]: https://www.google.com/chrome/browser/