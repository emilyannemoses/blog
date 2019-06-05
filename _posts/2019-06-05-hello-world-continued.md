---
layout: post
title:  "Hello world: C++ and Go"
---

In this installment of "Hello world" we'll be learning how to do this simple execution in both the C++ and Go programming languages.

The reason I split this up into two parts is because JavaScript, Ruby and Python can all be interpreted.  C++ and Go are compiled. This means we have more overhead to get started with coding in C++ and Go, even to just print a simple "Hello world"

C++ was created by Microsoft and is used on many enterprise software programs. Go (aka Golang) was created by Google and is very popular in the start-up world since it's open-source (free!)

<h1>C++</h1>

To compile and run our first C++ program, we have to make sure we have the compiler available. Type `gcc –version` or `gcc –v` into your terminal emulator. It should spit out what version your computer has.

If you don't have it, type the command `sudo apt-get install build-essential` for Windows and `xcode-select --install` for macOS.

To begin, we have to use a text editor. If you have a text editor already and know how to use it, continue with this tutorial. If you don't, read [this post about getting started with Visual Studio Code][vscode] first.

Before typing any code, we must create the file with the proper file extension. Create a file in VS Code called `hello.cpp` 

`.cpp` is the extension for all C++ program files.

Within the file, type the following code (do not include the line numbers!):

```cpp
1    // A hello world program in C++
2    // Compile the program using command: g++ -o hello hello.cpp
3    // Run it using this command: ./hello
4    #include<iostream>
5    using namespace std;
6
7    int main()
8    {
9        cout << "Hello world";
10       return 0;
11   }
```

Lines `1-3`: Comments. Comments are made by starting the line with double `//` characters. Comments are not read by the compiler, they're for human use only.

Line `4`: Lines beginning with an octothorpe (`#`) are used by the compiler's pre-processor. In this case the directive `#include` tells the pre-processor to include the `iostream` standard file. This file `iostream` includes the declarations of the basic standard input/output library in C++. 

Line `5`: All the elements of the standard C++ library are declared within what is called a namespace. In this case the namespace with the name `std` (standard). We put this line in to declare that we will make use of the functionality offered in the namespace `std`. This line of code is used very frequent in C++ programs that use the `standard` library.

Line `7`: `int` is what is called the "return value" - in our case of the type `integer`. Harkening back to Data Types: Integer is a whole number. It's necessary to explicitly declare it here at the creation of our function because it's what our function will eventually return.
Every program must have a `main()` function. The `main()` function is the point where all C++ programs start their execution. The word main is always followed by a pair of parentheses. In our case, we don't have anything inside the parentheses, but more complex programs will.

Line `8`: Curley braces. The two curly brackets (one in the beginning and one at the end) are used to indicate the beginning and the end of the function main. (Also called the body of a function). Everything contained within these curly brackets is what the function does when it is called and executed.

Line `9`: This line is a C++ statement. A statement is a simple expression that can produce an effect. In this case the statement will print something to our screen.

`cout` represents the standard output stream in C++. `"Hello World"` will be sent to the standard output stream - your terminal.
The words Hello World have to be between `” “`, but the `” ”` will not be printed on the screen. They indicate that the string (Data Type) begins and where it will end.

The statement ends with a semicolon `;`. The semicolon is used to mark the end of the statement. The semicolon must be placed behind all statements in C++ programs.

Line `10`: The return statement causes the main function to finish and it is dependent on how you start your function `main( )`. We said that `main ( )` will return an `int` (integer) - so we have to return something of that data type `int`. A zero normally indicates that everything went ok and a one normally indicates that something has gone wrong.

Now that you know what all of that code means, let's run it!

⭐️ MAKE SURE YOU ARE IN THE DIRECTORY IN YOUR TERMINAL EMULATOR WHERE YOUR hello.cpp FILE LIVES

To first compile the program, type `g++ -o hello hello.cpp` into your terminal emulater.

Then, to run the file, type `./hello`

Congratulations, you've just created your fist Hello world program in C++!

<h1>Go</h1>
<h4>(aka Golang)</h4>

We must use a text editor for compiling and running our `Hello world` Go program as well.  [Go here to get VS Code][vscode] if you don't already use a text editor.

First, we're going to make a file called `hello.go`. 

`.go` is the extension for all Go program files.

Within the file, type the following (without the line numbers!):

```go
1    package main
2
3    import "fmt"
4
5    func main() {
6        fmt.Println("Hello world")
7    }
```

Line `1`: The `main` package is always used in Go as the place where all of the code gets called or executed. Since we're only working with one line of code, we're just going to write that in the `main` package within the `main()` function.

If we had more functionality to our code, we may create other files and call the functions in those files from the `main` package as well. The rule of thumb: Always start with `package main` in your main code file.

Line `3`: This is an `import` statement. Import literally imports external packages that we get "for free" with the Go programming language. The `fmt` package stands for FORMATTING. This package formats strings. Since we're simply printing out "Hello world" we want to use this package to format our string to print it out to the console.

Line `5`: This is the syntax used to create all functions in Go. `func` is the keyword to start a function and `main()` is the name of the package, so we call the function main as well.  Always put open and closed curley braces after declaring a function `{}`, and put all of your code inside the curley braces.

Line `6`: This is the meat and potatoes of our Hello world program.  First, we call upon the `fmt` package that we've previously imported and use its built-in `.Println()` method.  A method is a function within a package that we can utilize in our own programs. Inside the parentheses for the method, we put the string `"Hello world"` because that's what we want `.Println()` to print out for us in our console.

⭐️ In Terminal, make sure you're in the same directory as your `hello.go` file.

To compile this program into binary, do `go build hello.go` in your terminal emulator.

To run your file type `./hello`

Congratulations! You've just written your first Hello world Go program!

[vscode]: https://eamoses.github.io/blog/2019/06/06/vs-code.html