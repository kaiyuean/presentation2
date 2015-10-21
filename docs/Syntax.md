# Syntax

<hr>

### Whitespace in Ruby Program

Whitespace characters such as spaces and tabs are generally ignored in Ruby code, except when they appear in strings. Sometimes, however, they are used to interpret ambiguous statements. Interpretations of this sort produce warnings when the -w option is enabled.

Example:
```
a + b is interpreted as a+b ( Here a is a local variable)
a  +b is interpreted as a(+b) ( Here a is a method call)
```

<hr>

### Line Endings in Ruby Program

Ruby interprets semicolons and newline characters as the ending of a statement. However, if Ruby encounters operators, such as +, -, or backslash at the end of a line, they indicate the continuation of a statement.

<hr>

### Ruby Identifier

Identifiers are names of variables, constants, and methods. Ruby identifiers are case sensitive. It mean Ram and RAM are two different idendifiers in Ruby.

Ruby identifier names may consist of alphanumeric characters and the underscore character ( _ ).

<hr>

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

<hr>

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

<hr>

### If...Else

**Syntax:**
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

**Example:**
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
`x is 1`

**If modifier**

Syntax: 

`code if condition`

Example:
```
$debug=1
print "debug\n" if $debug
```
`debug`

<hr>

### Unless

**Syntax:**
```
unless conditional [then]
    code
[else
    code ]
end
```
Executes code if conditional is false. If the conditional is true, code specified in the else clause is executed.

**Example:**
```
x=1
unless x>2
   puts "x is less than 2"
 else
  puts "x is greater than 2"
end
```
`x is less than 2`

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
```
1 -- Value is set
3 -- Value is set
```

<hr>

### Case

**Syntax:**
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
**Example:**
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
`little child`

<hr>

### Loops

#### While

**Syntax:**
```
while conditional [do]
   code
end
```
Executes code while conditional is true. A while loop's conditional is separated from code by the reserved word do, a newline, backslash \, or a semicolon ;.

**Example:**
```
$i = 0
$num = 5

while $i < $num  do
   puts("Inside the loop i = #$i" )
   $i +=1
end
```
```
Inside the loop i = 0
Inside the loop i = 1
Inside the loop i = 2
Inside the loop i = 3
Inside the loop i = 4
```
**While modifier:**

Syntax:

`code while condition`

or
```
begin 
  code 
end while conditional
```
Executes code while conditional is true.

If a while modifier follows a begin statement with no rescue or ensure clauses, code is executed once before conditional is evaluated.

Example:
```
$i = 0
$num = 5
begin
   puts("Inside the loop i = #$i" )
   $i +=1
end while $i < $num
```
```
Inside the loop i = 0
Inside the loop i = 1
Inside the loop i = 2
Inside the loop i = 3
Inside the loop i = 4
```


#### Until 

**Syntax:**
```
until conditional [do]
   code
end
```
Executes code while conditional is false. An until statement's conditional is separated from code by the reserved word do, a newline, or a semicolon.

**Example:**
```
$i = 0
$num = 5

until $i > $num  do
   puts("Inside the loop i = #$i" )
   $i +=1;
end
```
```
Inside the loop i = 0
Inside the loop i = 1
Inside the loop i = 2
Inside the loop i = 3
Inside the loop i = 4
Inside the loop i = 5
```
**Until modifier:**

Syntax:

`code until conditional`

or
```
begin
   code
end until conditional
```
Executes code while conditional is false.

If an until modifier follows a begin statement with no rescue or ensure clauses, code is executed once before conditional is evaluated.

Example:
```
$i = 0
$num = 5
begin
   puts("Inside the loop i = #$i" )
   $i +=1;
end until $i > $num
```
```
Inside the loop i = 0
Inside the loop i = 1
Inside the loop i = 2
Inside the loop i = 3
Inside the loop i = 4
Inside the loop i = 5
```
##### For

**Syntax:**
```
for variable [, variable ...] in expression [do]
   code
end
```
Executes code once for each element in expression.

**Example:**
```
for i in 0..5
   puts "Value of local variable is #{i}"
end
```
Here, we have defined the range 0..5. The statement for i in 0..5 will allow i to take values in the range from 0 to 5 (including 5). This will produce the following result:
```
Value of local variable is 0
Value of local variable is 1
Value of local variable is 2
Value of local variable is 3
Value of local variable is 4
Value of local variable is 5
```
A for...in loop is almost exactly equivalent to:

`(expression).each do |variable[, variable...]| code end`

except that a for loop doesn't create a new scope for local variables. A for loop's expression is separated from code by the reserved word do, a newline, or a semicolon.

**Example:**
```
(0..5).each do |i|
   puts "Value of local variable is #{i}"
end
```
```
Value of local variable is 0
Value of local variable is 1
Value of local variable is 2
Value of local variable is 3
Value of local variable is 4
Value of local variable is 5
```

#### Break

**Syntax:**

`break`

Terminates the most internal loop. Terminates a method with an associated block if called within the block (with the method returning nil).

**Example:**
```
for i in 0..5
   if i > 2 then
      break
   end
   puts "Value of local variable is #{i}"
end
```
```
Value of local variable is 0
Value of local variable is 1
Value of local variable is 2
```

#### Next

**Syntax:**

`next`

Jumps to next iteration of the most internal loop. Terminates execution of a block if called within a block (with yield or call returning nil).

**Example:**
```
for i in 0..5
   if i < 2 then
      next
   end
   puts "Value of local variable is #{i}"
end
```
```
Value of local variable is 2
Value of local variable is 3
Value of local variable is 4
Value of local variable is 5
```

#### Redo

**Syntax:**

`redo`

Restarts this iteration of the most internal loop, without checking loop condition. Restarts yield or call if called within a block.

Example:
```
for i in 0..5
   if i < 2 then
      puts "Value of local variable is #{i}"
      redo
   end
end
```
```
Value of local variable is 0
Value of local variable is 0
............................
```

#### Retry

**Syntax:**

`retry`

If retry appears in rescue clause of begin expression, restart from the beginning of the 1begin body.
```
begin
   do_something # exception raised
rescue
   # handles error
   retry  # restart from beginning
end
```
If retry appears in the iterator, the block, or the body of the for expression, restarts the invocation of the iterator call. Arguments to the iterator is re-evaluated.
```
for i in 1..5
   retry if some_condition # restart from i == 1
end
```

**Example:**
```
for i in 1..5
   retry if  i > 2
   puts "Value of local variable is #{i}"
end
```
```
Value of local variable is 1
Value of local variable is 2
Value of local variable is 1
Value of local variable is 2
Value of local variable is 1
Value of local variable is 2
............................
```