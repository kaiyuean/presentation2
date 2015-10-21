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
