# Learn Ruby the Hard Way

## Basics
### Printing
Printing a string with to the console:
```ruby
# with new line at the end (like println)
puts 'string with a new line at the end'
# without new line at the end
print 'string without a new line at the end'
```
The `puts` (short for "put string") and `print` commands are both used to display the results of evaluating Ruby code. The primary difference between them is that `puts` adds a newline after executing, and `print` does not.
### The Truth Terms

- `&&` - and
- `||` - or
- `!=` - not equal
- `==` - equal
- `>=` - greater-than-equal
- `<=` - less-than-equal
- `true`
- `false`


### Other
Comments:
```ruby
# sample comment

=begin
Sample
multiline
comment
=end
```
Using variables:
```ruby
cars = 100
puts "There are #{cars} cars available."
```

Connecting (requiring) another ruby file:
```ruby
require "./ex25.rb"
```

## Strings
String interpolation:
```ruby
puts "What is 3 + 2? #{3 + 2}"
puts "If I add #{age}, #{height}, and #{weight} I get #{age + height + weight}."
```
In Ruby the `"` (double-quote) tell Ruby to replace variables it finds with `#{}`, but the `'` (single-quote) tells Ruby to leave the string alone and ignore any vraibles inside it.

Prints "." 10 times:
```ruby
puts "." * 10
```
String concatenation:
```ruby
print end1 + end2 + end3 + end4 + end5 + end6
puts end7 + end8 + end9 + end10 + end11 + end12
```
### String formating
```ruby
# Formatter
formatter = "%{first} %{second} %{third} %{fourth}"
puts formatter % {first: "one", second: "two", third: "three", fourth: "four"}
```
Returns "one two three fourth".

To print multiple lines, use `puts """..."""`:
```ruby
puts """
There's something going on here.
With the three double-quotes.
We'll be able to type as much as we like.
Even 4 lines if we want, or 5, or 6.
"""
```

Escape Sequences:

Escape	| What it does
--- | ---
`\\` | Backslash (\\)
`\'` | Single-quote (')
`\"` | Double-quote (")
`\n` | ASCII linefeed (LF)
`\t ASCII` | Horizontal Tab (TAB)
`\uxxxx` | Character with 16-bit hex value xxxx (Unicode only)
`\v` | ASCII vertical tab (VT)
`\ooo` | Character with octal value `ooo`
`\xhh` | Character with hex value `hh`

`\n` and `\t` work only when inside double quotes: `"\n\t"`; don't work in this case: `'\n\t'`

### String methods

`.length` - returns length of a string
`.reverse` - returns reversed string
`.upcase` - transforms string to uppercase
`.downcase` - transform string to lowercase
`.capitalize` - capitalizes the first letter of a string and makes the rest of the letters lowercase

```ruby
first_name = "Ivan"

# returns upercase string, but doesn't change the value stored in a variable
first_name.upcase
# changes values stored in a variable
first_name.upcase!
```

## Taking input from a user

To get user input use `gets.chop`, where `chop` removes end of the line character (`\n`) from a string:
```ruby
print "How old are you? "
age = gets.chomp
puts "You're #{age} years old."
```

`gets` returns a string, to get an integer use `to_i`:  `gets.chomp.to_i`, use `to_f` to get a float.

### Taking command line arguments

`ARGV`, "argument variable" - holds the arguments you pass to your Ruby script when you run it.

To unpack `ARGV` do sometihng the following:
```ruby
first, second, third = ARGV
```
`first`, `second` and `third` will be assigned to the first 3 arguments respectively.

Example program:
```ruby
first, second, third = ARGV

puts "Your first variable is: #{first}."
puts "Your second variable is: #{second}."
puts "Your third variable is: #{third}."
```

Another way of taking input using `$stdin` and custom prompt:
```ruby
user_name = ARGV.first
prompt = '> '

puts "Hi #{user_name}."
puts "Do you like me #{user_name}? ", prompt
likes = $stdin.gets.chomp

puts "Alright, so you said #{likes} about liking me."
```

## Working with files (File I/O)

Printing content of a file:
```ruby
# Opens a file and stores file object into a variable
txt = open(filename)
# Gets contents of the file be calling read method on file object and prints it to the console
puts txt.read
# can be used without parentheses: txt.close
txt.close()
```

List of file object commands:
- `close` - closes the file, like `File->Save..` in the editor
- `read` - reads the contents of the file; result can be assigned to a variable
- `readline` - reads just one line of a text file
- `truncate` - empties the file (watch out if you care about the file)
- `write('stuff')` - writes "stuff" to the file

Writing to a file:
```ruby
filename = ARGV.first

# opens file for writing
target = open(filename, 'w')
# erases file (truncates, so it has at most 0 bytes)
target.truncate(0)

target.write("I am the first line.\n")
target.write("I am the second line.\n")

target.close
```

Some modes (not all) for opening a file:

Mode | Meadning
--- | ---
`r` | Read-only, starts at beginning of file (default mode)
`r+` | Read-write, starts at beginning of file
`w` | Write-only, truncates existing file to zerol length or creates a new file for writing
`w+` | Read-write, truncates existing file to zero length or creates a new file for reading and writing.
`a` | Write-only, starts at end of file if exists, otherwise creates a new file for writing
`a+` | Read-write, starts at end of file if file exists, otherwise xreates a new file for reading and writing.

Copying one file to another:
```ruby
from_file, to_file = ARGV

puts "Copying from #{from_file} to #{to_file}"

in_file = open(from_file)
# returns all contents of the file
indata = in_file.read

puts "Does the output file exist? #{File.exist?(to_file)}"
puts "Ready, hit RETURN to continue, CTRL-C to abort."
$stdin.gets

out_file = open(to_file, 'w')
out_file.write(indata)

puts "Alright, all done."

out_file.close
in_file.close
```

`File.exist?(to_file)` - checks if given file exists

`file.read` returns all contents of the file.

`file.seek()` can be used to move inside a file. For example, if you pass `0` to it, you'll move to the beginning of the file:
```ruby
current_file = open(input_file)

# moves to the beginning of the file
current_file.seek(0)
# saves the first line of the file
first_line = current_file.gets.chomp
# saves the second line of the file
second_line = current_file.gets.chomp
```



## Functions

Creating a function:
```ruby
def function_name(arg1, arg2)
	# do something here
	return arg1
end

# two ways to call a function
function_name "arg1", "arg2"
function_name("arg1", "arg2")
```

Creating simple function that add 2 numbers:
```ruby
def add_two(num1, num2)
	puts "Adding #{num1} and #{num2}..."
	return num1 + num2
end

result = add_two(5, 3)
```

It's possible to create arguments list using `*` (splat operator). In the following example all arguments passed to the funtion will be put into an array called args.
```ruby
def func(*args)
	# ...
end

# puts first 2 parameters into arg1 and arg2, and the rest to array other_arguments
def func2(arg1, arg2, *other_arguments)
	# ...
end
```

Functions can return multiple values; to access them you need to unpack returned value:
```ruby
def some_function()
	return 1, 2
end

# value1 will be 1; value2 will be 2
value1, value2 = some_function()
```

## Modules

A `Module` is a collection of methods and constants (similiar to Classes).
```ruby
module Ex

	# defining a method in a module
	def Ex.add_two(a, b)
		return a + b
	end
	
	def Ex.add_three(a, b, c)
		return a + b + c
	end
	
end

# using methods from a module
a = Ex.add_two(1,2)
b = Ex.add_three(1, 2, 3)
```

## Control flow

### If statements:
```ruby
if a > 5
	puts "a more than 5"
elsif a < 5
	puts "a less than 5"
else
	puts "a is equal to 5"
end
```

### Loops

3 ways to print elemtns of the array with for loops:
```ruby
the_count = [1, 2, 3, 4, 5]

for number in the_count
	puts "This is count #{number}"
end

# more Ruby-style loops, better use one of the next two than the first one
the_count.each do |number|
	puts "This is count #{number}"
end

the_count.each {|number| puts "This is count #{number}"}
```

While loops
```ruby
i = 0
while a < 5
	puts a
	a += 1
end
```

## Arrays

Basic operations on array:
```ruby
sample_array = ["abc", 5, true]

# adds 7 to the end of the array
sample_array.push(7)

# adds "str" to the end of the array
sample_array << "str"
```

## Miscellaneous

There's no `++` or `--` operators in Ruby; instead, you should use `var += 1` or `var -= 1` correspondingly.