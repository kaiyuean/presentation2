### String

A String object in Ruby holds and manipulates an arbitrary sequence of one or more bytes, typically representing characters that represent human language.

The simplest string literals are enclosed in single quotes (the apostrophe character). The text within the quote marks is the value of the string:

`'This is a simple Ruby string literal'`

If you need to place an apostrophe within a single-quoted string literal, precede it with a backslash so that the Ruby interpreter does not think that it terminates the string:

`'Won\'t you read O\'Reilly\'s book?'`

The backslash also works to escape another backslash, so that the second backslash is not itself interpreted as an escape character.

Following are string-related features Ruby.

**Expression Substitution:**

Expression substitution is a means of embedding the value of any Ruby expression into a string using #{ and }:
```
x, y, z = 12, 36, 72
puts "The value of x is #{ x }."
puts "The sum of x and y is #{ x + y }."
puts "The average was #{ (x + y + z)/3 }."
```
This will produce the following result:
```
The value of x is 12.
The sum of x and y is 48.
The average was 40.
```

**General Delimited Strings:**

With general delimited strings, you can create strings inside a pair of matching though arbitrary delimiter characters, e.g., !, (, {, <, etc., preceded by a percent character (%). Q, q, and x have special meanings. General delimited strings can be
```
%{Ruby is fun.}  equivalent to "Ruby is fun."
%Q{ Ruby is fun. } equivalent to " Ruby is fun. "
%q[Ruby is fun.]  equivalent to a single-quoted string
%x!ls! equivalent to back tick command output `ls`
```

**Character Encoding:**

The default character set for Ruby is ASCII, whose characters may be represented by single bytes. If you use UTF-8, or another modern character set, characters may be represented in one to four bytes.

You can change your character set using $KCODE at the beginning of your program, like this:

`$KCODE = 'u'`

Following are the possible values for $KCODE.
```
Code	Description
a	    ASCII (same as none). This is the default.
e	    EUC.
n   	None (same as ASCII).
u	    UTF-8.
```

**String Built-in Methods:**

We need to have an instance of String object to call a String method. Following is the way to create an instance of String object:

`new [String.new(str="")]`

This will return a new string object containing a copy of str. Now, using str object, we can call any available instance methods. For example:
```
myStr = String.new("THIS IS TEST")
foo = myStr.downcase

puts "#{foo}"
````
This will produce the following result:

`this is test`

<hr>

### Arrays

Ruby arrays are ordered, integer-indexed collections of any object. Each element in an array is associated with and referred to by an index.

Array indexing starts at 0, as in C or Java. A negative index is assumed relative to the end of the array --- that is, an index of -1 indicates the last element of the array, -2 is the next to last element in the array, and so on.

Ruby arrays can hold objects such as String, Integer, Fixnum, Hash, Symbol, even other Array objects. Ruby arrays are not as rigid as arrays in other languages. Ruby arrays grow automatically while adding elements to them.

**Creating Arrays:**

There are many ways to create or initialize an array. One way is with the new class method:

`names = Array.new`

You can set the size of an array at the time of creating array:

`names = Array.new(20)`

The array names now has a size or length of 20 elements. You can return the size of an array with either the size or length methods:
```
names = Array.new(20)
puts names.size  # This returns 20
puts names.length # This also returns 20
```
This will produce the following result:
```
20
20
```
You can assign a value to each element in the array as follows:
```
names = Array.new(4, "mac")
puts "#{names}"
```
This will produce the following result:

`macmacmacmac`
You can also use a block with new, populating each element with what the block evaluates to:
```
nums = Array.new(10) { |e| e = e * 2 }
puts "#{nums}"
```
This will produce the following result:
```
024681012141618
```

There is another method of Array, []. It works like this:

`nums = Array.[](1, 2, 3, 4,5)`

One more form of array creation is as follows :

`nums = Array[1, 2, 3, 4,5]`

The Kernel module available in core Ruby has an Array method, which only accepts a single argument. Here, the method takes a range as an argument to create an array of digits:
```
digits = Array(0..9)
puts "#{digits}"
```
This will produce the following result:

`0123456789`

**Array Built-in Methods:**

We need to have an instance of Array object to call a Array method. As we have seen, following is the way to create an instance of Array object:

`Array.[](...) [or] Array[...] [or] [...]`

This will return a new array populated with the given objects. Now, using created object, we can call any available instance methods. For example:
```
digits = Array(0..9)
num = digits.at(6)
puts "#{num}"
```
This will produce the following result:

`6`


### Hashes

A Hash is a collection of key-value pairs like this: "employee" => "salary". It is similar to an Array, except that indexing is done via arbitrary keys of any object type, not an integer index.

The order in which you traverse a hash by either key or value may seem arbitrary and will generally not be in the insertion order. If you attempt to access a hash with a key that does not exist, the method will return nil.

**Creating Hashes:**

As with arrays, there is a variety of ways to create hashes. You can create an empty hash with the new class method:

`months = Hash.new`

You can also use new to create a hash with a default value, which is otherwise just nil:
```
months = Hash.new( "month" )

or

months = Hash.new "month"
```
When you access any key in a hash that has a default value, if the key or value doesn't exist, accessing the hash will return the default value:
```
months = Hash.new( "month" )

puts "#{months[0]}"
puts "#{months[72]}"
```
This will produce the following result:
```
month
month
```
```
H = Hash["a" => 100, "b" => 200]

puts "#{H['a']}"
puts "#{H['b']}"
```
This will produce the following result:
```
100
200
```
You can use any Ruby object as a key or value, even an array, so following example is a valid one:

`[1,"jan"] => "January"`

**Hash Built-in Methods:**

We need to have an instance of Hash object to call a Hash method. As we have seen, following is the way to create an instance of Hash object:
```
Hash[[key =>|, value]* ] or

Hash.new [or] Hash.new(obj) [or]

Hash.new { |hash, key| block }
```
This will return a new hash populated with the given objects. Now using created object we can call any available instance methods. For example:
```
$, = ", "
months = Hash.new( "month" )

months = {"1" => "January", "2" => "February"}

keys = months.keys

puts "#{keys}"
```
This will produce the following result:

`["1", "2"]`

### Date & Time

The Time class represents dates and times in Ruby. It is a thin layer over the system date and time functionality provided by the operating system. This class may be unable on your system to represent dates before 1970 or after 2038.

**Getting Current Date and Time:**
Following is the simple example to get current date and time:
```
time1 = Time.new

puts "Current Time : " + time1.inspect

# Time.now is a synonym:
time2 = Time.now
puts "Current Time : " + time2.inspect
```
This will produce the following result:
```
Current Time : Mon Jun 02 12:02:39 -0700 2008
Current Time : Mon Jun 02 12:02:39 -0700 2008
```

**Getting components of a Date & Time:**

We can use Time object to get various components of date and time. Following is the example showing the same:
```
time = Time.new

# Components of a Time
puts "Current Time : " + time.inspect
puts time.year    # => Year of the date 
puts time.month   # => Month of the date (1 to 12)
puts time.day     # => Day of the date (1 to 31 )
puts time.wday    # => 0: Day of week: 0 is Sunday
puts time.yday    # => 365: Day of year
puts time.hour    # => 23: 24-hour clock
puts time.min     # => 59
puts time.sec     # => 59
puts time.usec    # => 999999: microseconds
puts time.zone    # => "UTC": timezone name
```
This will produce the following result:
```
Current Time : Mon Jun 02 12:03:08 -0700 2008
2008
6
2
1
154
12
3
8
247476
UTC
```

**Time.utc, Time.gm and Time.local Functions:**

These two functions can be used to format date in standard format as follows:
```
# July 8, 2008
Time.local(2008, 7, 8)  
# July 8, 2008, 09:10am, local time
Time.local(2008, 7, 8, 9, 10)   
# July 8, 2008, 09:10 UTC
Time.utc(2008, 7, 8, 9, 10)  
# July 8, 2008, 09:10:11 GMT (same as UTC)
Time.gm(2008, 7, 8, 9, 10, 11)  
```
Following is the example to get all components in an array in the following format:

`[sec,min,hour,day,month,year,wday,yday,isdst,zone]`

Try the following:
```
time = Time.new

values = time.to_a
p values
```
This will generate the following result:

`[26, 10, 12, 2, 6, 2008, 1, 154, false, "MST"]`

This array could be passed to Time.utc or Time.local functions to get different format of dates as follows:
```
time = Time.new

values = time.to_a
puts Time.utc(*values)
```
This will generate following result:

`Mon Jun 02 12:15:36 UTC 2008`

Following is the way to get time represented internally as seconds since the (platform-dependent) epoch:
```
# Returns number of seconds since epoch
time = Time.now.to_i  

# Convert number of seconds into Time object.
Time.at(time)

# Returns second since epoch which includes microseconds
time = Time.now.to_f
```

**Timezones and daylight savings time:**

You can use a Time object to get all the information related to Timezones and daylight savings as follows:
```
time = Time.new

# Here is the interpretation
time.zone       # => "UTC": return the timezone
time.utc_offset # => 0: UTC is 0 seconds offset from UTC
time.zone       # => "PST" (or whatever your timezone is)
time.isdst      # => false: If UTC does not have DST.
time.utc?       # => true: if t is in UTC time zone
time.localtime  # Convert to local timezone.
time.gmtime     # Convert back to UTC.
time.getlocal   # Return a new Time object in local zone
time.getutc     # Return a new Time object in UTC
```

**Formatting Times and Dates:**

There are various ways to format date and time. Here is one example showing few:
```
time = Time.new

puts time.to_s
puts time.ctime
puts time.localtime
puts time.strftime("%Y-%m-%d %H:%M:%S")
```
This will produce the following result:
```
Mon Jun 02 12:35:19 -0700 2008
Mon Jun  2 12:35:19 2008
Mon Jun 02 12:35:19 -0700 2008
2008-06-02 12:35:19
```

**Time arithmetic:**

You can do simple arithmetic with time as follows:
```
now = Time.now           # Current time
puts now

past = now - 10          # 10 seconds ago. Time - number => Time
puts past

future = now + 10        # 10 seconds from now Time + number => Time
puts future

diff = future - now      # => 10  Time - Time => number of seconds
puts diff
```
This will produce the following result:
```
Thu Aug 01 20:57:05 -0700 2013
Thu Aug 01 20:56:55 -0700 2013
Thu Aug 01 20:57:15 -0700 2013
10.0
```