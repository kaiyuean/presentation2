# Syntax

### Whitespace in Ruby Program

Whitespace characters such as spaces and tabs are generally ignored in Ruby code, except when they appear in strings. Sometimes, however, they are used to interpret ambiguous statements. Interpretations of this sort produce warnings when the -w option is enabled.

Example:
```
a + b is interpreted as a+b ( Here a is a local variable)
a  +b is interpreted as a(+b) ( Here a is a method call)
```

### Line Endings in Ruby Program

Ruby interprets semicolons and newline characters as the ending of a statement. However, if Ruby encounters operators, such as +, -, or backslash at the end of a line, they indicate the continuation of a statement.

### Ruby Identifier

Identifiers are names of variables, constants, and methods. Ruby identifiers are case sensitive. It mean Ram and RAM are two different idendifiers in Ruby.

Ruby identifier names may consist of alphanumeric characters and the underscore character ( _ ).

### Ruby Comments

A comment hides a line, part of a line, or several lines from the Ruby interpreter. You can use the hash character (#) at the beginning of a line:

`# I am a comment. Just ignore me.`

Or, a comment may be on the same line after a statement or expression:

`name = "Madisetti" # This is again comment`

You can comment multiple lines as follows:
```
# This is a comment.
# This is a comment, too.
# This is a comment, too.
# I said that already.
```

Here is another form. This block comment conceals several lines from the interpreter with =begin/=end:
```
=begin
This is a comment.
This is a comment, too.
This is a comment, too.
I said that already.
=end
```

### Ruby Operators

Ruby Arithmetic Operators: +, -, *, /, %, **

Ruby Comparison Operators: ==, >, <, >=, etc.

Ruby Assignment Operators: =, +=, -=, *=, etc.

Ruby Parallel Assignment: a, b, c = 10, 20, 30

Ruby Bitwise Operators: &, |, ^, ~, <<, >>

Ruby Logical Operators: &&, ||, !

Ruby Ternary operator: ? :

Ruby Range operators: .., ...

Ruby defined? operators

Ruby dot "." and double Colon "::" Operators

### If...else

**Syntax**
```
if conditional [then]
	  code...
[elsif conditional [then]
	  code...]
[else
	  code...]
end
```
if expressions are used for conditional execution. The values false and nil are false, and everything else are true. Notice Ruby uses elsif, not else if nor elif.

Executes code if the conditional is true. If the conditional is not true, code specified in the else clause is executed.

An if expression's conditional is separated from code by the reserved word then, a newline, or a semicolon.

**Example**
```
x=1
if x > 2
    puts "x is greater than 2"
elsif x <= 2 and x!=0
    puts "x is 1"
else
    puts "I can't guess the number"
end
```
**If modifier**

Syntax: `code if condition`

example:
```
$debug=1
print "debug\n" if $debug
```

### Unless

**Syntax**
```
unless conditional [then]
    code
[else
    code ]
end
```
Executes code if conditional is false. If the conditional is true, code specified in the else clause is executed.

**Example**
```
x=1
unless x>2
   puts "x is less than 2"
 else
  puts "x is greater than 2"
end
```
**Unless modifier**

Syntax:
`code unless conditional`

Example:
```
$var =  1
print "1 -- Value is set\n" if $var
print "2 -- Value is set\n" unless $var

$var = false
print "3 -- Value is set\n" unless $var
```

### Case

**Syntax**
```
case expression
[when expression [, expression ...] [then]
    code ]...
[else
    code ]
end
```
Compares the expression specified by case and that specified by when using the === operator and executes the code of the when clause that matches.

The expression specified by the when clause is evaluated as the left operand. If no when clauses match, case executes the code of the else clause.

A when statement's expression is separated from code by the reserved word then, a newline, or a semicolon.

Thus:
```
case expr0
when expr1, expr2
    stmt1
when expr3, expr4
    stmt2
else
    stmt3
end
```
is basically similar to the following:
```
_tmp = expr0
if expr1 === _tmp || expr2 === _tmp
    stmt1
elsif expr3 === _tmp || expr4 === _tmp
    stmt2
else
    stmt3
end
```
**Example**
```
$age =  5
case $age
when 0 .. 2
    puts "baby"
when 3 .. 6
    puts "little child"
when 7 .. 12
    puts "child"
when 13 .. 18
    puts "youth"
else
    puts "adult"
end
```



### Loops

### Methods

### Blocks

### Modules

### Strings

### Arrays

### Hashes

### Data & Time

### Ranges

### Iterators

### File I/O

### Exception















