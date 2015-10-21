# Introduction

<hr>

## Overview

Ruby is a pure object-oriented programming language. It was created in 1993 by Yukihiro Matsumoto of Japan.

Ruby is "A Programmer's Best Friend". Ruby has features that are similar to those of Smalltalk, Perl, and Python. Perl, Python, and Smalltalk are scripting languages. Smalltalk is a true object-oriented language. Ruby, like Smalltalk, is a perfect object-oriented language. Using Ruby syntax is much easier than using Smalltalk syntax.

Ruby is an interpreted scripting language for quick and easy object-oriented programming.

* interpreted scripting language:
    * ability to make operating system calls directly
	* powerful string operations and regular expressions
	* immediate feedback during development
* quick and easy:
	* variable declarations are unnecessary
	* variables are not typed
	* syntax is simple and consistent
	* memory management is automatic
* object oriented programming:
	* everything is an object
	* classes, methods, inheritance, etc.
	* singleton methods
	* "mixin" functionality by module
	* iterators and closures
* also:
	* multiple precision integers
	* convenient exception processing
	* dynamic loading
	* threading support

<hr>

## Getting started

First, you'll want to check whether ruby is installed. From the terminal, type

`$ ruby -v`

(-v tells the interpreter to print the version of ruby), then press the Enter key. If ruby is installed, you will see a message something like the following:

`ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]`

If ruby is not installed, you can install it easily, since ruby is free software with no restrictions on its installation or use.

Now, let's play with ruby. You can place a ruby program directly on the command line using the -e option:
```
$ ruby -e 'puts "hello world"'
hello world
```
More conventionally, a ruby program can be stored in a file.
```
$ echo "puts 'hello world'" > hello.rb
$ ruby hello.rb
hello world
```

<hr>

## Simple example

Let's write a function to compute factorials. The mathematical definition of n factorial is:
```
n!  = 1                   (when n==0)
    = n * (n-1)!          (otherwise)
```
In ruby, this can be written as:
```
def fact(n)
    if n == 0
        1
    else
        n * fact(n-1)   
    end
end
```
You may notice the repeated occurrence of end. Ruby has been called "Algol-like" because of this. (Actually, the syntax of ruby more closely mimics that of a langage named Eiffel.) You may also notice the lack of a return statement. It is unneeded because a ruby function returns the last thing that was evaluated in it. Use of a return statement here is permissible but unnecessary.

Let's try out our factorial function. Adding one line of code gives us a working program:
```
# Program to find the factorial of a number
# Save this as fact.rb

def fact(n)
    if n == 0
        1
    else
        n * fact(n-1)
    end
end
puts fact(ARGV[0].to_i)
```
Here, ARGV is an array which contains the command line arguments, and to_i converts a character string to an integer.
```
$ ruby fact.rb 1
1
$ ruby fact.rb 5
120
```







