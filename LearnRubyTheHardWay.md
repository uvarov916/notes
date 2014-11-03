# Learn Ruby the Hard Way

## Basics
### Printing
Printing a string with a new line at the end:
```ruby
puts 'string with a new line at the end'
print 'string without a new line at the end'
```
The `puts` (short for "put string") and `print` commands are both used to display the results of evaluating Ruby code. The primary difference between them is that `puts` adds a newline after executing, and `print` does not.
### Other
Comments:
```ruby
# sample comment
```
Using variables:
```ruby
cars = 100
puts "There are #{cars} cars available."
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