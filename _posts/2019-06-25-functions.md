---
layout: post
title:  "Functions"
---

A function groups together statements that perform the same task. Instead of repeating the same statement multiple times, we can wrap it up nicely in function syntax and control when the program executes.

### Why use functions?

Using functions to modularize programs is essential to both ease and readability of programs. Once code is broken down into several different small functions that all perform their own task, not only is it easier to add to the program, it's also easier to debug and know where problems are arising.

Programming is all about working on a team of other developers. We want our code to be as readable as possible for our friends!

Consider a burrito making shop with only one employee. As you request various toppings for your burrito, the individual plops that ingredient on, and moves to the next section. This is similar to the programs we've been writing up to this point.

But what if there were 5 workers behind the counter, each one responsible for a different ingredient: Tortilla, beans, meat, vegetables, and sauce. Now you know exactly who to go to (or who to skip) depending on what ingredients you want in your burrito!

### Anatomy of a function

Getting to the meat of the burrito: There are two types of functions. Void functions executes the statements within it and termiates. Value-returning functions executes the statements within it and then returns a value back to whichever statement that called upon it.

What if the individual whom we ask to put black beans on our burrito ploped a ladle full on, and then just stopped? In some function cases, this would work, but as the person who wants to eat the burrito, I want something returned!  Both functions are useful and I'll show you why.

Similar to the rules around declaring variables in any programming language, there are rules to what we can and can't name functions. You can't use a reserved keyword as a function name. It can't contain spaces. The first character must be a letter, `a-z` or `_` underscore character. Case matters.

```python
1 def choose_tortilla():
2    print("Wheat")
3
4 choose_tortilla()
```

Line 4 is important. Lines 1 and 2 won't do anything until we call the function on line 4. This is what tells our program to actually print the string "Wheat" - until then, our program can't see anything inside the `choose_tortilla()` function.

Let's bring it together with two functions:

```python
1 def build_burrito():
2    print("Welcome to the buritto shop, I am here to build your burrito!")
3    choose_tortilla()
4
5 def choose_tortilla():
6    print("Wheat")
7
8 build_burrito()
```

We're building a burrito program!  First, line 8 is executed. The program ignores all functions until they are called. Once the program is prompted to execute `build_burrito()`, it reads line 2 and prints the welcome message.

Then, it reads line 3 and is told to execute the `choose_tortilla()` function, and we can choose the type of tortilla we want, which prints "Wheat"

### Flowcharting is important!

As you can see, a program can get very complicated. If we want each burrito ingredient to be a separate function we'll first want to map out visually how we want our program to "flow"  We wouldn't want the salsa to be put on before the rice and beans, for example!

A chart should go top to bottom as follows:

```python
build_burrito()
↓
prints out a statement and calls a function
↓
choose_tortilla()
↓
print out a statement and calls a function
↓
choose_beans()
↓
prints out a statement and calls a function
↓
...keeps going until our burrito is built
↓
Return burrito to customer
```

#### Hierarchy chart

While flowcharts graphically depicts the flow of the logic inside a function, hierarchy charts give a visual representation of the relationship between functions. [Hierarchy charts explained](http://elearning.algonquincollege.com/coursemat/mcintyb/dat2219d/lectures/33-Implementation-of-Hierarchy.htm)

### Scope

Scope is to a function as black beans are to our burrito. When we need to add black beans to our burrito, we have to do so with in the `choose_beans()` function. If we try to add our beans within the `choose_tortilla()` function we'll get an error, because of the scope of our programs functions.

#### What is a local variable?

Let's build out our program a bit more to showcase some local, or scoped, variables:

```python
1 def build_burrito():
2    print("Welcome to the buritto shop, I am here to build your burrito!")
3    choose_tortilla()
4
5 def choose_tortilla():
6    if (wheat):
7       print(wheat)
8    elif (white):
9       print(white)
10   elif(spinach):
11      print(spinach)
12
13 build_burrito()
```

We've added a few local variables: `wheat`, `white`, and `spinach` as tortilla options.  We can only choose these options within the `choose_tortilla()` function! That's because they're scoped locally to that function, they don't exist anywhere else in the program.

Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<span><a href="https://eamoses.github.io/blog/2019/06/21/repetition-structures.html" style="float:left;">Previous: Repetition structures</a><a href="https://eamoses.github.io/blog/2019/06/26/functions-cont.html" style="float:right;">Next: Functions continued</a></span>