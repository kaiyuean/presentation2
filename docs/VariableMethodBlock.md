### Variables

Variables are the memory locations which hold any data to be used by any program. There are five types of variables supported by Ruby. 

#### Global Variables

Global variables begin with $. Uninitialized global variables have the value nil and produce warnings with the -w option.

Assignment to global variables alters global status. It is not recommended to use global variables. They make programs cryptic.

Here is an example showing usage of global variable.
```
$global_variable = 10
class Class1
  def print_global
     puts "Global variable in Class1 is #$global_variable"
  end
end
class Class2
  def print_global
     puts "Global variable in Class2 is #$global_variable"
  end
end

class1obj = Class1.new
class1obj.print_global
class2obj = Class2.new
class2obj.print_global
```
Here $global_variable is a global variable. This will produce the following result:

NOTE: In Ruby you CAN access value of any variable or constant by putting a hash (#) character just before that variable or constant.
```
Global variable in Class1 is 10
Global variable in Class2 is 10
```

#### Instance Variables

Instance variables begin with @. Uninitialized instance variables have the value nil and produce warnings with the -w option.

Here is an example showing usage of Instance Variables.
```
class Customer
   def initialize(id, name, addr)
      @cust_id=id
      @cust_name=name
      @cust_addr=addr
   end
   def display_details()
      puts "Customer id #@cust_id"
      puts "Customer name #@cust_name"
      puts "Customer address #@cust_addr"
    end
end

# Create Objects
cust1=Customer.new("1", "John", "Wisdom Apartments, Ludhiya")
cust2=Customer.new("2", "Poul", "New Empire road, Khandala")

# Call Methods
cust1.display_details()
cust2.display_details()
```
Here, @cust_id, @cust_name and @cust_addr are instance variables. This will produce the following result:
```
Customer id 1
Customer name John
Customer address Wisdom Apartments, Ludhiya
Customer id 2
Customer name Poul
Customer address New Empire road, Khandala
```

#### Class Variables

Class variables begin with @@ and must be initialized before they can be used in method definitions.

Referencing an uninitialized class variable produces an error. Class variables are shared among descendants of the class or module in which the class variables are defined.

Overriding class variables produce warnings with the -w option.

Here is an example showing usage of class variable:
```
class Customer
   @@no_of_customers=0
   def initialize(id, name, addr)
      @cust_id=id
      @cust_name=name
      @cust_addr=addr
   end
   def display_details()
      puts "Customer id #@cust_id"
      puts "Customer name #@cust_name"
      puts "Customer address #@cust_addr"
    end
    def total_no_of_customers()
       @@no_of_customers += 1
       puts "Total number of customers: #@@no_of_customers"
    end
end

# Create Objects
cust1=Customer.new("1", "John", "Wisdom Apartments, Ludhiya")
cust2=Customer.new("2", "Poul", "New Empire road, Khandala")

# Call Methods
cust1.total_no_of_customers()
cust2.total_no_of_customers()
```
Here @@no_of_customers is a class variable. This will produce the following result:
```
Total number of customers: 1
Total number of customers: 2
```
#### Local Variables

Local variables begin with a lowercase letter or _. The scope of a local variable ranges from class, module, def, or do to the corresponding end or from a block's opening brace to its close brace {}.

When an uninitialized local variable is referenced, it is interpreted as a call to a method that has no arguments.

Assignment to uninitialized local variables also serves as variable declaration. The variables start to exist until the end of the current scope is reached. The lifetime of local variables is determined when Ruby parses the program.

In the above example local variables are id, name and addr.

#### Constants

Constants begin with an uppercase letter. Constants defined within a class or module can be accessed from within that class or module, and those defined outside a class or module can be accessed globally.

Constants may not be defined within methods. Referencing an uninitialized constant produces an error. Making an assignment to a constant that is already initialized produces a warning.
```
class Example
   VAR1 = 100
   VAR2 = 200
   def show
       puts "Value of first Constant is #{VAR1}"
       puts "Value of second Constant is #{VAR2}"
   end
end

# Create Objects
object=Example.new()
object.show
```
Here VAR1 and VAR2 are constant. This will produce the following result:
```
Value of first Constant is 100
Value of second Constant is 200
```
#### Pseudo-Variables

They are special variables that have the appearance of local variables but behave like constants. You can not assign any value to these variables.
* self: The receiver object of the current method.

* true: Value representing true.

* false: Value representing false.

* nil: Value representing undefined.

* __FILE__: The name of the current source file.

* __LINE__: The current line number in the source file.

<hr>

### Method

Ruby methods are very similar to functions in any other programming language. Ruby methods are used to bundle one or more repeatable statements into a single unit.

Method names should begin with a lowercase letter. If you begin a method name with an uppercase letter, Ruby might think that it is a constant and hence can parse the call incorrectly.

Methods should be defined before calling them, otherwise Ruby will raise an exception for undefined method invoking.

#### Syntax:
```
def method_name [( [arg [= default]]...[, * arg [, &expr ]])]
   expr..
end
```
So you can define a simple method as follows:
```
def method_name 
   expr..
end
```
You can represent a method that accepts parameters like this:
```
def method_name (var1, var2)
   expr..
end
```
You can set default values for the parameters which will be used if method is called without passing required parameters:
```
def method_name (var1=value1, var2=value2)
   expr..
end
```
Whenever you call the simple method, you write only the method name as follows:

`method_name`

However, when you call a method with parameters, you write the method name along with the parameters, such as:

`method_name 25, 30`

The most important drawback to using methods with parameters is that you need to remember the number of parameters whenever you call such methods. For example, if a method accepts three parameters and you pass only two, then Ruby displays an error.

**Example:**
```
def test(a1="Ruby", a2="Perl")
   puts "The programming language is #{a1}"
   puts "The programming language is #{a2}"
end
test "C", "C++"
test
```
This will produce the following result:
```
The programming language is C
The programming language is C++
The programming language is Ruby
The programming language is Perl
```

#### Return Values from Methods:

Every method in Ruby returns a value by default. This returned value will be the value of the last statement. For example:
```
def test
   i = 100
   j = 10
   k = 0
end
```
This method, when called, will return the last declared variable k.

#### Ruby return Statement:

The return statement in ruby is used to return one or more values from a Ruby Method.

**Syntax:**

`return [expr[',' expr...]]`

If more than two expressions are given, the array containing these values will be the return value. If no expression given, nil will be the return value.

**Example:**
```
return

OR

return 12

OR

return 1,2,3
```
Have a look at this example:
```
def test
   i = 100
   j = 200
   k = 300
return i, j, k
end
var = test
puts var
```
This will produce the following result:
```
100
200
300
```

#### Variable Number of Parameters:

Suppose you declare a method that takes two parameters, whenever you call this method, you need to pass two parameters along with it.

However, Ruby allows you to declare methods that work with a variable number of parameters. Let us examine a sample of this:
```
def sample (*test)
   puts "The number of parameters is #{test.length}"
   for i in 0...test.length
      puts "The parameters are #{test[i]}"
   end
end
sample "Zara", "6", "F"
sample "Mac", "36", "M", "MCA"
```
In this code, you have declared a method sample that accepts one parameter test. However, this parameter is a variable parameter. This means that this parameter can take in any number of variables. So above code will produce following result:
```
The number of parameters is 3
The parameters are Zara
The parameters are 6
The parameters are F
The number of parameters is 4
The parameters are Mac
The parameters are 36
The parameters are M
The parameters are MCA
```

#### Class Methods:

When a method is defined outside of the class definition, the method is marked as private by default. On the other hand, the methods defined in the class definition are marked as public by default. The default visibility and the private mark of the methods can be changed by public or private of the Module.

Whenever you want to access a method of a class, you first need to instantiate the class. Then, using the object, you can access any member of the class.

Ruby gives you a way to access a method without instantiating a class. Let us see how a class method is declared and accessed:
```
class Accounts
   def reading_charge
   end
   def Accounts.return_date
   end
end
```
See how the method return_date is declared. It is declared with the class name followed by a period, which is followed by the name of the method. You can access this class method directly as follows:

`Accounts.return_date`

To access this method, you need not create objects of the class Accounts.

<hr>

### Blocks
* A block consists of chunks of code.
* You assign a name to a block.
* The code in the block is always enclosed within braces ({}).
* A block is always invoked from a function with the same name as that of the block. This means that if you have a block with the name test, then you use the function test to invoke this block.
* You invoke a block by using the yield statement.

**Syntax:**
```
block_name{
   statement1
   statement2
   ..........
}
```
Here, you will learn to invoke a block by using a simple yield statement. You will also learn to use a yield statement with parameters for invoking a block. You will check the sample code with both types of yield statements.

**The yield Statement:**

Let's look at an example of the yield statement:
```
def test
   puts "You are in the method"
   yield
   puts "You are again back to the method"
   yield
end
test {puts "You are in the block"}
```
This will produce the following result:
```
You are in the method
You are in the block
You are again back to the method
You are in the block
```
You also can pass parameters with the yield statement. Here is an example:
```
def test
   yield 5
   puts "You are in the method test"
   yield 100
end
test {|i| puts "You are in the block #{i}"}
````
This will produce the following result:
```
You are in the block 5
You are in the method test
You are in the block 100
```
Here, the yield statement is written followed by parameters. You can even pass more than one parameter. In the block, you place a variable between two vertical lines (||) to accept the parameters. Therefore, in the preceding code, the yield 5 statement passes the value 5 as a parameter to the test block.

Now, look at the following statement:

`test {|i| puts "You are in the block #{i}"}`

Here, the value 5 is received in the variable i. Now, observe the following puts statement:

`puts "You are in the block #{i}"`

The output of this puts statement is:

`You are in the block 5`

If you want to pass more than one parameters, then the yield statement becomes:

`yield a, b`

and the block is:

`test {|a, b| statement}`

The parameters will be separated by commas.

**Blocks and Methods:**

You have seen how a block and a method can be associated with each other. You normally invoke a block by using the yield statement from a method that has the same name as that of the block. Therefore, you write:
```
def test
  yield
end
test{ puts "Hello world"}
```
This example is the simplest way to implement a block. You call the test block by using the yield statement.

But if the last argument of a method is preceded by &, then you can pass a block to this method and this block will be assigned to the last parameter. In case both * and & are present in the argument list, & should come later.
```
def test(&block)
   block.call
end
test { puts "Hello World!"}
```
This will produce the following result:

`Hello World!`

**BEGIN and END Blocks**

Every Ruby source file can declare blocks of code to be run as the file is being loaded (the BEGIN blocks) and after the program has finished executing (the END blocks).
```
BEGIN { 
  # BEGIN block code 
  puts "BEGIN code block"
} 

END { 
  # END block code 
  puts "END code block"
}
  # MAIN block code 
puts "MAIN code block"
```
A program may include multiple BEGIN and END blocks. BEGIN blocks are executed in the order they are encountered. END blocks are executed in reverse order. When executed, above program produces the following result:
```
BEGIN code block
MAIN code block
END code block
```