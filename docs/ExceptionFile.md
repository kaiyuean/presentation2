### File I/O

Ruby provides a whole set of I/O-related methods implemented in the Kernel module. All the I/O methods are derived from the class IO.

The class IO provides all the basic methods, such as read, write, gets, puts, readline, getc, and printf.

This chapter will cover all the basic I/O functions available in Ruby. For more functions, please refer to Ruby Class IO.

**The puts Statement:**

In previous chapters, you assigned values to variables and then printed the output using puts statement.

The puts statement instructs the program to display the value stored in the variable. This will add a new line at the end of each line it writes.

**Example:**
````
val1 = "This is variable one"
val2 = "This is variable two"
puts val1
puts val2
```
This will produce the following result:
```
This is variable one
This is variable two
```

**The gets Statement:**

The gets statement can be used to take any input from the user from standard screen called STDIN.

**Example:**

The following code shows you how to use the gets statement. This code will prompt the user to enter a value, which will be stored in a variable val and finally will be printed on STDOUT.
```
puts "Enter a value :"
val = gets
puts val
```
This will produce the following result:
```
Enter a value :
This is entered value
This is entered value
```

**The putc Statement:**

Unlike the puts statement, which outputs the entire string onto the screen, the putc statement can be used to output one character at a time.

**Example:**

The output of the following code is just the character H:
```
str="Hello Ruby!"
putc str
```
This will produce the following result:

`H`

**The print Statement:**

The print statement is similar to the puts statement. The only difference is that the puts statement goes to the next line after printing the contents, whereas with the print statement the cursor is positioned on the same line.

Example:
```
print "Hello World"
print "Good Morning"
```
This will produce the following result:

`Hello WorldGood Morning`

**Opening and Closing Files:**

Until now, you have been reading and writing to the standard input and output. Now, we will see how to play with actual data files.

**The File.new Method:**

You can create a File object using File.new method for reading, writing, or both, according to the mode string. Finally, you can use File.close method to close that file.

**Syntax:**
```
aFile = File.new("filename", "mode")
   # ... process the file
aFile.close
```

**The File.open Method:**

You can use File.open method to create a new file object and assign that file object to a file. However, there is one difference in between File.open and File.new methods. The difference is that the File.open method can be associated with a block, whereas you cannot do the same using the File.new method.
```
File.open("filename", "mode") do |aFile|
   # ... process the file
end
```

**Reading and Writing Files:**

The same methods that we've been using for 'simple' I/O are available for all file objects. So, gets reads a line from standard input, and aFile.gets reads a line from the file object aFile.

However, I/O objects provides additional set of access methods to make our lives easier.

**The sysread Method:**

You can use the method sysread to read the contents of a file. You can open the file in any of the modes when using the method sysread. For example :

Following is the input text file:

`This is a simple text file for testing purpose.`

Now let's try to read thsi file:
```
aFile = File.new("input.txt", "r")
if aFile
   content = aFile.sysread(20)
   puts content
else
   puts "Unable to open file!"
end
```
This statement will output the first 20 characters of the file. The file pointer will now be placed at the 21st character in the file.

**The syswrite Method:**

You can use the method syswrite to write the contents into a file. You need to open the file in write mode when using the method syswrite. For example:
```
aFile = File.new("input.txt", "r+")
if aFile
   aFile.syswrite("ABCDEF")
else
   puts "Unable to open file!"
end
```
This statement will write "ABCDEF" into the file.

**The each_byte Method:**

This method belongs to the class File. The method each_byte is always associated with a block. Consider the following code sample:
```
aFile = File.new("input.txt", "r+")
if aFile
   aFile.syswrite("ABCDEF")
   aFile.each_byte {|ch| putc ch; putc ?. }
else
   puts "Unable to open file!"
end
```
Characters are passed one by one to the variable ch and then displayed on the screen as follows:
```
s. .a. .s.i.m.p.l.e. .t.e.x.t. .f.i.l.e. .f.o.r. .t.e.s.t.i.n.g. .p.u.r.p.o.s.e...
.
.
```

**The IO.readlines Method:**

The class File is a subclass of the class IO. The class IO also has some methods, which can be used to manipulate files.

One of the IO class methods is IO.readlines. This method returns the contents of the file line by line. The following code displays the use of the method IO.readlines:
```
arr = IO.readlines("input.txt")
puts arr[0]
puts arr[1]
```
In this code, the variable arr is an array. Each line of the file input.txt will be an element in the array arr. Therefore, arr[0] will contain the first line, whereas arr[1] will contain the second line of the file.

**The IO.foreach Method:**

This method also returns output line by line. The difference between the method foreach and the method readlines is that the method foreach is associated with a block. However, unlike the method readlines, the method foreach does not return an array. For example:

`IO.foreach("input.txt"){|block| puts block}`

This code will pass the contents of the file test line by line to the variable block, and then the output will be displayed on the screen.

**Renaming and Deleting Files:**

You can rename and delete files programmatically with Ruby with the rename and delete methods.

Following is the example to rename an existing file test1.txt:
```
# Rename a file from test1.txt to test2.txt
File.rename( "test1.txt", "test2.txt" )
```
Following is the example to delete an existing file test2.txt:
```
# Delete file test2.txt
File.delete("test2.txt")
```

**File Modes and Ownership:**

Use the chmod method with a mask to change the mode or permissions/access list of a file:

Following is the example to change mode of an existing file test.txt to a mask value:
```
file = File.new( "test.txt", "w" )
file.chmod( 0755 )
```

**File Inquiries:**

The following command tests whether a file exists before opening it:

`File.open("file.rb") if File::exists?( "file.rb" )`

The following command inquire whether the file is really a file:
```
# This returns either true or false
File.file?( "text.txt" ) 
```
The following command finds out if it given file name is a directory:
```
# a directory
File::directory?( "/usr/local/bin" ) # => true

# a file
File::directory?( "file.rb" ) # => false
```
The following command finds whether the file is readable, writable or executable:
```
File.readable?( "test.txt" )   # => true
File.writable?( "test.txt" )   # => true
File.executable?( "test.txt" ) # => false
```
The following command finds whether the file has zero size or not:
```
File.zero?( "test.txt" )      # => true
```
The following command returns size of the file :
```
File.size?( "text.txt" )     # => 1002
```
The following command can be used to find out a type of file :
```
File::ftype( "test.txt" )     # => file
```
The ftype method identifies the type of the file by returning one of the following: file, directory, characterSpecial, blockSpecial, fifo, link, socket, or unknown.

The following command can be used to find when a file was created, modified, or last accessed :
```
File::ctime( "test.txt" ) # => Fri May 09 10:06:37 -0700 2008
File::mtime( "text.txt" ) # => Fri May 09 10:44:44 -0700 2008
File::atime( "text.txt" ) # => Fri May 09 10:45:01 -0700 2008
```

<hr>

### Directories

All files are contained within various directories, and Ruby has no problem handling these too. Whereas the File class handles files, directories are handled with the Dir class.

**Navigating Through Directories:**

To change directory within a Ruby program, use Dir.chdir as follows. This example changes the current directory to /usr/bin.

`Dir.chdir("/usr/bin")`

You can find out what the current directory is with Dir.pwd:

`puts Dir.pwd # This will return something like /usr/bin`

You can get a list of the files and directories within a specific directory using Dir.entries:

`puts Dir.entries("/usr/bin").join(' ')`

Dir.entries returns an array with all the entries within the specified directory. Dir.foreach provides the same feature:
```
Dir.foreach("/usr/bin") do |entry|
   puts entry
end
```
An even more concise way of getting directory listings is by using Dir's class array method:

`Dir["/usr/bin/*"]`

**Creating a Directory:**

The Dir.mkdir can be used to create directories:

`Dir.mkdir("mynewdir")`

You can also set permissions on a new directory (not one that already exists) with mkdir:

NOTE: The mask 755 sets permissions owner, group, world [anyone] to rwxr-xr-x where r = read, w = write, and x = execute.

`Dir.mkdir( "mynewdir", 755 )`

**Deleting a Directory:**

The Dir.delete can be used to delete a directory. The Dir.unlink and Dir.rmdir perform exactly the same function and are provided for convenience.

`Dir.delete("testdir")`

**Creating Files & Temporary Directories:**

Temporary files are those that might be created briefly during a program's execution but aren't a permanent store of information.

Dir.tmpdir provides the path to the temporary directory on the current system, although the method is not available by default. To make Dir.tmpdir available it's necessary to use require 'tmpdir'.

You can use Dir.tmpdir with File.join to create a platform-independent temporary file:
```
require 'tmpdir'
   tempfilename = File.join(Dir.tmpdir, "tingtong")
   tempfile = File.new(tempfilename, "w")
   tempfile.puts "This is a temporary file"
   tempfile.close
   File.delete(tempfilename)
```
This code creates a temporary file, writes data to it, and deletes it. Ruby's standard library also includes a library called Tempfile that can create temporary files for you:
```
require 'tempfile'
   f = Tempfile.new('tingtong')
   f.puts "Hello"
   puts f.path
   f.close
```

<hr>

### Exceptions

The execution and the exception always go together. If you are opening a file, which does not exist, then if you did not handle this situation properly, then your program is considered to be of bad quality.

The program stops if an exception occurs. So exceptions are used to handle various type of errors, which may occur during a program execution and take appropriate action instead of halting program completely.

Ruby provide a nice mechanism to handle exceptions. We enclose the code that could raise an exception in a begin/end block and use rescue clauses to tell Ruby the types of exceptions we want to handle.

**Syntax:**
```
begin  
# -  
rescue OneTypeOfException  
# -  
rescue AnotherTypeOfException  
# -  
else  
# Other exceptions
ensure
# Always will be executed
end
```
Everything from begin to rescue is protected. If an exception occurs during the execution of this block of code, control is passed to the block between rescue and end.

For each rescue clause in the begin block, Ruby compares the raised Exception against each of the parameters in turn. The match will succeed if the exception named in the rescue clause is the same as the type of the currently thrown exception, or is a superclass of that exception.

In an event that an exception does not match any of the error types specified, we are allowed to use an else clause after all the rescue clauses.

**Example:**
```
begin
   file = open("/unexistant_file")
   if file
      puts "File opened successfully"
   end
rescue
      file = STDIN
end
print file, "==", STDIN, "\n"
```
This will produce the following result. You can see that STDIN is substituted to file because open failed.

`#<IO:0xb7d16f84>==#<IO:0xb7d16f84>`

**Using retry Statement:**

You can capture an exception using rescue block and then use retry statement to execute begin block from the beginning.

**Syntax:**
```
begin
    # Exceptions raised by this code will 
	# be caught by the following rescue clause
rescue
    # This block will capture all types of exceptions
    retry  # This will move control to the beginning of begin
end
```
**Example:**
```
begin
   file = open("/unexistant_file")
   if file
      puts "File opened successfully"
   end
rescue
   fname = "existant_file"
   retry
end
```
The following is the flow of the process:
* an exception occurred at open
* went to rescue. fname was re-assigned
* by retry went to the beginning of the begin
* this time file opens successfully
* continued the essential process.

NOTE: Notice that if the file of re-substituted name does not exist this example code retries infinitely. Be careful if you use retry for an exception process.

**Using raise Statement:**

You can use raise statement to raise an exception. The following method raises an exception whenever it's called. It's second message will be printed. Program

**Syntax:**
```
raise 

OR

raise "Error Message" 

OR

raise ExceptionType, "Error Message"

OR

raise ExceptionType, "Error Message" condition
```
The first form simply reraises the current exception (or a RuntimeError if there is no current exception). This is used in exception handlers that need to intercept an exception before passing it on.

The second form creates a new RuntimeError exception, setting its message to the given string. This exception is then raised up the call stack.

The third form uses the first argument to create an exception and then sets the associated message to the second argument.

The fourth form is similar to third form but you can add any conditional statement like unless to raise an exception.

Example:
```
begin  
    puts 'I am before the raise.'  
    raise 'An error has occurred.'  
    puts 'I am after the raise.'  
rescue  
    puts 'I am rescued.'  
end  
puts 'I am after the begin block.'  
```
This will produce the following result:
```
I am before the raise.  
I am rescued.  
I am after the begin block. 
```
One more example showing usage of raise:
```
begin  
  raise 'A test exception.'  
rescue Exception => e  
  puts e.message  
  puts e.backtrace.inspect  
end  
```
This will produce the following result:
```
A test exception.
["main.rb:4"]
```

**Using ensure Statement:**

Sometimes, you need to guarantee that some processing is done at the end of a block of code, regardless of whether an exception was raised. For example, you may have a file open on entry to the block and you need to make sure it gets closed as the block exits.

The ensure clause does just this. ensure goes after the last rescue clause and contains a chunk of code that will always be executed as the block terminates. It doesn't matter if the block exits normally, if it raises and rescues an exception, or if it is terminated by an uncaught exception, the ensure block will get run.

**Syntax:**
```
begin 
   #.. process 
   #..raise exception
rescue 
   #.. handle error 
ensure 
   #.. finally ensure execution
   #.. This will always execute.
end
```
**Example:**
```
begin
  raise 'A test exception.'
rescue Exception => e
  puts e.message
  puts e.backtrace.inspect
ensure
  puts "Ensuring execution"
end
```
This will produce the following result:
```
A test exception.
["main.rb:4"]
Ensuring execution
```
**Using else Statement:**

If the else clause is present, it goes after the rescue clauses and before any ensure.

The body of an else clause is executed only if no exceptions are raised by the main body of code.

**Syntax:**
```
begin 
   #.. process 
   #..raise exception
rescue 
   # .. handle error
else
   #.. executes if there is no exception
ensure 
   #.. finally ensure execution
   #.. This will always execute.
end
```
Example:
```
begin
 # raise 'A test exception.'
 puts "I'm not raising exception"
rescue Exception => e
  puts e.message
  puts e.backtrace.inspect
else
   puts "Congratulations-- no errors!"
ensure
  puts "Ensuring execution"
end
```
This will produce the following result:
```
I'm not raising exception
Congratulations-- no errors!
Ensuring execution
```
Raised error message can be captured using $! variable.

**Catch and Throw:**

While the exception mechanism of raise and rescue is great for abandoning execution when things go wrong, it's sometimes nice to be able to jump out of some deeply nested construct during normal processing. This is where catch and throw come in handy.

The catch defines a block that is labeled with the given name (which may be a Symbol or a String). The block is executed normally until a throw is encountered.

**Syntax:**
```
throw :lablename
#.. this will not be executed
catch :lablename do
#.. matching catch will be executed after a throw is encountered.
end

OR

throw :lablename condition
#.. this will not be executed
catch :lablename do
#.. matching catch will be executed after a throw is encountered.
end
```
**Example:**

The following example uses a throw to terminate interaction with the user if '!' is typed in response to any prompt.
```
def promptAndGet(prompt)
   print prompt
   res = readline.chomp
   throw :quitRequested if res == "!"
   return res
end

catch :quitRequested do
   name = promptAndGet("Name: ")
   age = promptAndGet("Age: ")
   sex = promptAndGet("Sex: ")
   # ..
   # process information
end
promptAndGet("Name:")
```
You should try above program on your machine because it needs manual interaction. This will produce the following result:
```
Name: Ruby on Rails
Age: 3
Sex: !
Name:Just Ruby
```

**Class Exception:**

Ruby's standard classes and modules raise exceptions. All the exception classes form a hierarchy, with the class Exception at the top. The next level contains seven different types:
* Interrupt
* NoMemoryError
* SignalException
* ScriptError
* StandardError
* SystemExit

There is one other exception at this level, Fatal, but the Ruby interpreter only uses this internally.

Both ScriptError and StandardError have a number of subclasses, but we do not need to go into the details here. The important thing is that if we create our own exception classes, they need to be subclasses of either class Exception or one of its descendants.

Let's look at an example:
```
class FileSaveError < StandardError
   attr_reader :reason
   def initialize(reason)
      @reason = reason
   end
end
```
Now, look at the following example, which will use this exception:
```
File.open(path, "w") do |file|
begin
    # Write out the data ...
rescue
    # Something went wrong!
    raise FileSaveError.new($!)
end
end
```
The important line here is raise FileSaveError.new($!). We call raise to signal that an exception has occurred, passing it a new instance of FileSaveError, with the reason being that specific exception caused the writing of the data to fail.
