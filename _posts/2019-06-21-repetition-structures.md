---
layout: post
title:  "Repetition Structures"
---

The need to have programs perform the same task multiple times over is common, and it would be tedious to copy and paste the same code for as many times as you need to run it. That's where repetition structures come in.

<details>
    <br>
    <summary>The <code>while</code> loop</summary>
        The <code>while</code> loop is a condition-controlled loop. A condition controlled loop causes a statement, or set of statements to repeat as long as the condition is <code>true</code>.

        {% highlight python %}
        1 
        2 while condition_true:
        3    statement runs
        4    
        {% endhighlight %}

        {% highlight python %}
        1 number = 5
        2 while number <= 5:
        3    print("Your number is", number)
        4    number = int(input("Input another number: "))
        {% endhighlight %}

        Since this is a <i>prestest</i> loop, it first tests the condition before the loop is run. In the example, it has to test whether or not the variable <code>number</code> exists, and then determine whether the condition is <code>true</code>.

        <strong>Just be careful of <a href="https://en.wikipedia.org/wiki/Infinite_loop" target="_blank">infinite loops</a></strong>

    <br><br>
    </details>
<hr>
<details>
    <br>
    <summary>The <code>for</code> loop</summary>
        The <code>for</code> loop is a count-controlled loop. You'll choose to use this type of loop when you have to do something a specific amount of times.

        {% highlight python %}
        1 
        2 for variable in [value1, value2, value3]:
        3    statement runs through
        4    each value one by one
        {% endhighlight %}


        {% highlight python %}
        1 print('This program will display each number.')
        2 for num in [35, 66, 12, 1, 7, 0]:
        3    print(num)
        4    
        {% endhighlight %}

        The <code>for clause</code> assigns a variable that will take on the value depending on the statement we give it within the loop. First, <code>num</code> is assigned to the number 35, then on the second loop it is assigned to number 66 and so on until it executes each <i>iteration</i> of the list of numbers in the loop.

        The <code>range</code> method is an option to use with a <code>for clause</code> if you'd like to be specicic about your iterations.
        <br><br>
        You can pass it a single argument:
        <br>
        {% highlight python %}
        1 
        2 for num in range(5):
        3    print(num)
        4    
        {% endhighlight %}
        <br>
        This will print out 1 through 5. 
        <br><br>
        Two arguments:
        <br>
        {% highlight python %}
        1 
        2 for num in range(1, 5):
        3    print(num)
        4    
        {% endhighlight %}
        <br>
        In this case, it'll print out numbers 1-4 since we're telling it to start at 1 and go up-to but not including 5.
        <br><br>
        Or three arguments:
        <br>
        {% highlight python %}
        1 
        2 for num in range(1, 10, 2):
        3    print(num)
        4    
        {% endhighlight %}
        <br>
        The first argument is 1, so we'll start at 1. 
        The second argument is 10, so we'll go up to but not include 10.
        The third argument is 2 which is the step value. This means that the number 2 will be added to each successive number in the sequence.
        <br><br>
        It will print out the numbers 1, 3, 5, 7, 9.

    <br><br>
    </details>
<hr>
<details>
    <br>
    <summary>Using an <code>accumulator</code></summary>
        Calculating a running total to show how an <code>accumulator</code> functions.
    <br><br>
    </details>
<hr>
<details>
    <br>
    <summary>Using a <code>sentinel</code></summary>
        A <code>sentinel</code> is a special value that marks the end of a sequence of values.
    <br><br>
    </details>
<hr>
<details>
    <br>
    <summary>Input validation loops</summary>
        A quick ditty on catching "bad" data before it enters the program.
    <br><br>
    </details>
<hr>
<details>
    <br>
    <summary>Nested loops</summary>
        You can put loops inside of loops inside of loops inside of loops...
    <br><br>
    </details>

<br>
Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<span><a href="https://eamoses.github.io/blog/2019/06/18/oauth-react.html" style="float:left;">Previous: OAuth with ReactJS</a><a href="#" style="float:right;">Next: TBD</a></span>