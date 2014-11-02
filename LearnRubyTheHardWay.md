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
