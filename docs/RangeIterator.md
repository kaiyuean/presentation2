### Ranges

Ranges occur everywhere: January to December, 0 to 9, lines 50 through 67, and so on. Ruby supports ranges and allows us to use ranges in a variety of ways:
* Ranges as Sequences
* Ranges as Conditions
* Ranges as Intervals

**Ranges as Sequences:**

The first and perhaps most natural use of ranges is to express a sequence. Sequences have a start point, an end point, and a way to produce successive values in the sequence.

Ruby creates these sequences using the ''..'' and ''...'' range operators. The two-dot form creates an inclusive range, while the three-dot form creates a range that excludes the specified high value.
```
(1..5)        #==> 1, 2, 3, 4, 5
(1...5)       #==> 1, 2, 3, 4
('a'..'d')    #==> 'a', 'b', 'c', 'd'
```
The sequence 1..100 is held as a Range object containing references to two Fixnum objects. If you need to, you can convert a range to a list using the to_a method. Try the following example:
```
$, =", "   # Array value separator
range1 = (1..10).to_a
range2 = ('bar'..'bat').to_a

puts "#{range1}"
puts "#{range2}"
```
This will produce the following result:
```
1, 2, 3, 4, 5, 6, 7, 8, 9, 10
bar, bas, bat
```
Ranges implement methods that let you iterate over them and test their contents in a variety of ways:
```
# Assume a range
digits = 0..9

puts digits.include?(5)
ret = digits.min
puts "Min value is #{ret}"

ret = digits.max
puts "Max value is #{ret}"

ret = digits.reject {|i| i < 5 }
puts "Rejected values are #{ret}"

digits.each do |digit|
   puts "In Loop #{digit}"
end
```
This will produce the following result:
```
true
Min value is 0
Max value is 9
Rejected values are 5, 6, 7, 8, 9
In Loop 0
In Loop 1
In Loop 2
In Loop 3
In Loop 4
In Loop 5
In Loop 6
In Loop 7
In Loop 8
In Loop 9
```

**Ranges as Conditions:**

Ranges may also be used as conditional expressions. For example, the following code fragment prints sets of lines from standard input, where the first line in each set contains the word start and the last line the word end.:
```
while gets
   print if /start/../end/
end
```
Ranges can be used in case statements:
```
score = 70

result = case score
   when 0..40 then "Fail"
   when 41..60 then "Pass"
   when 61..70 then "Pass with Merit"
   when 71..100 then "Pass with Distinction"
   else "Invalid Score"
end

puts result
```
This will produce the following result:
```
Pass with Merit
```

**Ranges as Intervals:**

A final use of the versatile range is as an interval test: seeing if some value falls within the interval represented by the range. This is done using ===, the case equality operator.
```
if ((1..10) === 5)
  puts "5 lies in (1..10)"
end

if (('a'..'j') === 'c')
  puts "c lies in ('a'..'j')"
end

if (('a'..'j') === 'z')
  puts "z lies in ('a'..'j')"
end
```
This will produce the following result:
```
5 lies in (1..10)
c lies in ('a'..'j')
```

<hr>

### Iterators

Iterators are nothing but methods supported by collections. Objects that store a group of data members are called collections. In Ruby, arrays and hashes can be termed collections.

Iterators return all the elements of a collection, one after the other. We will be discussing two iterators here, each and collect. Let's look at these in detail.

**Ruby each Iterator:**

The each iterator returns all the elements of an array or a hash.

**Syntax:**
```
collection.each do |variable|
   code
end
```
Executes code for each element in collection. Here, collection could be an array or a ruby hash.

**Example:**
```
ary = [1,2,3,4,5]
ary.each do |i|
   puts i
end
```
This will produce the following result:
```
1
2
3
4
5
```
You always associate the each iterator with a block. It returns each value of the array, one by one, to the block. The value is stored in the variable i and then displayed on the screen.

**Ruby collect Iterator:**

The collect iterator returns all the elements of a collection.

**Syntax:**

`collection = collection.collect`

The collect method need not always be associated with a block. The collect method returns the entire collection, regardless of whether it is an array or a hash.

Example:
```
a = [1,2,3,4,5]
b = Array.new
b = a.collect
puts b
```
This will produce the following result:
```
1
2
3
4
5
```
NOTE: The collect method is not the right way to do copying between arrays. There is another method called a clone, which should be used to copy one array into another array.

You normally use the collect method when you want to do something with each of the values to get the new array. For example, this code produces an array b containing 10 times each value in a.
```
a = [1,2,3,4,5]
b = a.collect{|x| 10*x}
puts b
```
This will produce the following result:
```
10
20
30
40
50
```





