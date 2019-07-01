---
layout: post
title:  "Functions continued"
---

Let's continue building out our burrito-making function using the flow chart from the last blog post. We'll be using parameters, arguments, global variables, constants and returning values.

### Parameters and Arguments

These definitions are important! Parameters and Arguments have different functionality in a function. 

Agnostic of language, an argument is a piece of data that is passed into a function **when the function is called** and a parameter is passed into a function **when the function is declared**

```python
1 def choose_tortilla():
2    print('Which type of torilla would you like?')
3    print("-------------------------------------")
4    print("1. Wheat Tortilla")
5    print("2. Corn Tortilla")
6    tortilla_choice = int(input("Choose: "))
7    choose_beans(tortilla_choice)
```

We've defined the function `choose_tortilla()` on line 1, and on line 7 we've called the function `choose_beans()`.  The variable `tortilla_choice` is being passed in as an **argument** on line 7.

```python
1 def choose_beans(tortilla):
2   print('You have chosen a tortilla, now you can choose your beans')
```

On line 1 we're declaring the `choose_beans()` function and passing in `tortilla` as a **parameter**. This is because we want the `choose_beans()` function to be able to access the value that is held within the `tortilla_choice` variable in the previous function. That's how every step of our burrito building function will know about the customer's previous choice!

### Global variables and constants

A global variable is accessible to all the functions in a program file.

It is important to restrict the use of global variables, or not use them at all. They make debugging difficult because it is possible to change the value of a global variable anywhere else in the program!

Instead, if you must have a global value, create a **global constant**. There are a few examples of this in the code at the bottom of this post. A constant references a value that cannot be changed elsewhere in the program. Technically in the code below, they are unnecessary, but they highlight what a global constant would look like if you were to use them.

### Returning values

Using the `return` statement at the end of a function will return that value back to the part of the program that called it. 

In the code below, the last function `choose_meat()` returns a formatted string. We can scroll up and see that the `choose_beans()` function calls the `choose_meat()` function, so we know that it's being returned back to the `choose_beans()` function. 

In `choose_beans()` we're returning the function call to `choose_meat()` and since the `choose_tortilla()` function calls the `choose_beans()` function, that return value is being returned to the `choose_tortilla()` function.  

`choose_tortilla()` is returning the value of the `choose_beans()` function back to the `build_burrito()` function, because it is the `build_burrito()` function that originally calls `choose_tortilla()`

🌯🌯🌯🌯🌯

Using the concepts we've learned, take the following code, refactor and build on it to create your own burrito making program!

```python
# Examples of global constants:
# Constants for tortilla options
WHEAT = 1
CORN = 2
# Contants for bean options
BLACK = 3
REFRIED = 4
#Contants for meat options
CARNITAS = 5
ASADA = 6

def build_burrito():
    print('Welcome to my burrito shop')
    print('I am here to build your burrito!')
    burrito = choose_tortilla()
    print(burrito)

def choose_tortilla():
    print('Which type of torilla would you like?')
    print("-------------------------------------")
    print("1. Wheat Tortilla")
    print("2. Corn Tortilla")
    tortilla_choice = int(input("Choose: "))
    return choose_beans(tortilla_choice)

def choose_beans(tortilla_choice):
    if tortilla_choice == 1:
        print('You want a wheat tortilla')
        print('Which type of beans would you like?')
        print("-------------------------------------")
        print("3. Black beans")
        print("4. Refried beans")
        beans_choice = input("Choose: ")
        return choose_meat(tortilla_choice, beans_choice)
    elif tortilla_choice == 2:
        print('You want a corn tortilla')
        print('Which type of beans would you like?')
        print("-------------------------------------")
        print("3. Black beans")
        print("4. Refried beans")
        beans_choice = int(input("Choose: "))
        return choose_meat(tortilla_choice, beans_choice)

def choose_meat(tortilla_choice, beans_choice):
    if tortilla_choice == 1:
        if beans_choice == 3:
            print('You want a wheat tortilla and black beans')
            tortilla_choice = "wheat"
            beans_choice = "black"
        if beans_choice == 4:
            print('You want a wheat tortilla and refried beans')
            tortilla_choice = "wheat"
            beans_choice = "refried"
    elif tortilla_choice == 2:
        if beans_choice == 3:
            print('You want a corn tortilla and black beans')
            tortilla_choice = "corn"
            beans_choice = "black"
        if beans_choice == 4:
            print('You want a corn tortilla and refried beans')
            tortilla_choice = "corn"
            beans_choice = "refried"
    print('Which type of meat would you like?')
    print("-------------------------------------")
    print("5. Carnitas")
    print("6. Asada")
    meat_choice = int(input("Choose: "))
    if meat_choice == 5:
        meat_choice = "carnitas"
    if meat_choice == 6:
        meat_choice = "asada"
    return "Here is your {2} burrito with a {0} tortilla and {1} beans!!".format(tortilla_choice, beans_choice, meat_choice)

build_burrito()
```

Happy coding!

E
<hr>
<h4>Got Questions❓, Comments 🗣 or Edits ✍</h4>
<h5>Use the Twitter thread below and hashtag <a href="https://twitter.com/hashtag/e4everything?f=tweets&vertical=default&lang=en" target="_blank">#E4Everything</a> to get in touch with me regarding this blog post:</h5>

<span><a href="https://eamoses.github.io/blog/2019/06/25/functions.html" style="float:left;">Previous: Functions</a><a href="#" style="float:right;">Next: TBD</a></span>