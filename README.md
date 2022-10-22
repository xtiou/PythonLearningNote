# This is a repository for Basic Python learning Note || Coursera course
### week 1
### week 2

### Arithmetic operators

Python can operate with numbers using the usual mathematical operators, and some special operators, too. These are all of them (we'll explore the last two in later videos).

- a + b = Adds a and b
- a - b = Subtracts b from a
- a * b = Multiplies a and b
- a / b = Divides a by b
- a ** b = Elevates a to the power of b. For non integer values of b, this becomes a root (i.e. a**(1/2) is the square root of a)
- a // b = The integer part of the integer division of a by b
- a % b = The remainder part of the integer division of a by b


### Comparison operators

- a == b: a is equal to b
- a != b: a is different than b
- a < b: a is smaller than b
- a <= b: a is smaller or equal to b
- a > b: a is bigger than b
- a >= b: a is bigger or equal to b

### Logical operators

- a and b: True if both a and b are True. False otherwise.
- a or b: True if either a or b or both are True. False if both are False.
- not a: True if a is False, False if a is True.

#### Exercices
If a filesystem has a block size of 4096 bytes, this means that a file comprised of only one byte will still use 4096 bytes of storage. A file made up of 4097 bytes will use 4096*2=8192 bytes of storage. Knowing this, can you fill in the gaps in the calculate_storage function below, which calculates the total number of bytes needed to store a file of a given size?
```python
def calculate_storage(filesize):
    block_size = 4096
    # Use floor division to calculate how many blocks are fully occupied
    full_blocks = filesize//4096
    # Use the modulo operator to check whether there's any remainder
    partial_block_remainder = filesize%4096
    # Depending on whether there's a remainder or not, return
    # the total number of bytes required to allocate enough blocks
    # to store your data.
    if partial_block_remainder > 0:
        return 4096*(full_blocks+1)
    return full_blocks*4096

print(calculate_storage(1))    # Should be 4096
print(calculate_storage(4096)) # Should be 4096
print(calculate_storage(4097)) # Should be 8192
print(calculate_storage(6000)) # Should be 8192
```
The fractional_part function divides the numerator by the denominator, and returns just the fractional part (a number between 0 and 1). Complete the body of the function so that it returns the right number.
Note: Since division by 0 produces an error, if the denominator is 0, the function should return 0 instead of attempting the division.
```python
def fractional_part(numerator, denominator):
    if denominator == 0:
        return 0
    else:
        return (numerator/denominator) %1

print(fractional_part(5, 5)) # Should be 0
print(fractional_part(5, 4)) # Should be 0.25
print(fractional_part(5, 3)) # Should be 0.66...
print(fractional_part(5, 2)) # Should be 0.5
print(fractional_part(5, 0)) # Should be 0
print(fractional_part(0, 5)) # Should be 0
```

### week 3
#### While Loop
#### Exercices
Fill in the blanks to make the print_prime_factors function print all the prime factors of a number. A prime factor is a number that is prime and divides another without a remainder
```python
def print_prime_factors(number):
  # Start with two, which is the first prime
  factor = 2
  # Keep going until the factor is larger than the number
  while factor <= number:
    # Check if factor is a divisor of number
    if number % factor == 0:
      # If it is, print it and divide the original number
      print(factor)
      number = number / factor
    else:
      # If it's not, increment the factor by one
      factor += 1
  return "Done"

print_prime_factors(100)
# Should print 2,2,5,5
# DO NOT DELETE THIS COMMENT
```
The following code can lead to an infinite loop. Fix the code so that it can finish successfully for all numbers.
Note: Try running your function with the number 0 as the input, and see what you get!
```python
def is_power_of_two(n):
  # Check if the number can be divided by two without a remainder
  while n % 2 == 0:
    if n<=0:
      return False
    else:
      n = n / 2
      return True
    break
  # If after dividing by two the number is 1, it's a power of two
  if n == 1:
    return True
    
  return False
  

print(is_power_of_two(0)) # Should be False
print(is_power_of_two(1)) # Should be True
print(is_power_of_two(8)) # Should be True
print(is_power_of_two(9)) # Should be False
```
Fill in the empty function so that it returns the sum of all the divisors of a number, without including it. A divisor is a number that divides into another without a remainder.
```python
def sum_divisors(n):
  # Return the sum of all divisors of n, not including n
  return sum([i for i in range(1, n)if n % i == 0])

print(sum_divisors(0))
# 0
print(sum_divisors(3)) # Should sum of 1
# 1
print(sum_divisors(36)) # Should sum of 1+2+3+4+6+9+12+18
# 55
print(sum_divisors(102)) # Should be sum of 2+3+6+17+34+51
# 114
```
The multiplication_table function prints the results of a number passed to it multiplied by 1 through 5. An additional requirement is that the result is not to exceed 25, which is done with the break statement. Fill in the blanks to complete the function to satisfy these conditions.

```python
def multiplication_table(number):
	# Initialize the starting point of the multiplication table
	multiplier = 1
	# Only want to loop through 5
	while multiplier <= 5:
		result = number * multiplier
		# What is the additional condition to exit out of the loop?
		if result > 25 :
			break
		print(str(number) + "x" + str(multiplier) + "=" + str(result))
		# Increment the variable for the loop
		multiplier += 1

multiplication_table(3) 
# Should print: 3x1=3 3x2=6 3x3=9 3x4=12 3x5=15

multiplication_table(5) 
# Should print: 5x1=5 5x2=10 5x3=15 5x4=20 5x5=25

multiplication_table(8)	
# Should print: 8x1=8 8x2=16 8x3=24
```
#### for Loop
For loops allow you to iterate over a sequence of values
##### range() function

While loops iterate while a condition is true, for loops iterate through a sequence of elements.
##### Exercices 
Fill in the blanks to make the factorial function return the factorial of n. Then, print the first 10 factorials (from 0 to 9) with the corresponding number. Remember that the factorial of a number is defined as the product of an integer and all integers before it. For example, the factorial of five (5!) is equal to 1*2*3*4*5=120. Also recall that the factorial of zero (0!) is equal to 1.
```python
def factorial(n):
    result = 1
    for x in range(1,n+1):
        result = result * x
    return result

for n in range(0,10):
    print(n, factorial(n+0))
```

Write a script that prints the first 10 cube numbers (x**3), starting with x=1 and ending with x=10.
```python
for x in range(1,11):
  print(x**3)
```

Write a script that prints the multiples of 7 between 0 and 100. Print one multiple per line and avoid printing any numbers that aren't multiples of 7. Remember that 0 is also a multiple of 7.
```python
for x in range(0, 100, 7):
    print(x)
```

The retry function tries to execute an operation that might fail, it retries the operation for a number of attempts.  Currently the code will keep executing the function even if it succeeds. Fill in the blank so the code stops trying after the operation succeeded.
```python
def retry(operation, attempts):
  for n in range(attempts):
    if operation():
      print("Attempt " + str(n) + " succeeded")
      break
    else:
      print("Attempt " + str(n) + " failed")

retry(create_user, 3)
retry(stop_service, 5)
```



#### recursion
A recursive function must include a recursive case and base case. The recursive case calls the function again, with a different value. The base case returns a value without calling the same function.

A recursive function will usually have this structure:
```python
def recursive_function(parameters):
    if base_case_condition(parameters):
        return base_case_value
    recursive_function(modified_parameters)

```
Recursion lets us tackle complex problems by reducing the problem to a simpler one.

Good use cases for recursive programs : 
* Going through a file system collecting information related to directories and files.
* Managing permissions assigned to groups inside a company, when each group can contain both subgroups and users.

##### Exercices
Question 3
Fill in the blanks to make the is_power_of function return whether the number is a power of the given base. Note: base is assumed to be a positive number. Tip: for functions that return a boolean value, you can return the result of a comparison.
```python
def is_power_of(number, base):
  # Base case: when number is smaller than base.
  if number < base:
    # If number is equal to 1, it's a power (base**0).
    return number == 1

  # Recursive case: keep dividing number by base.
  return is_power_of(number//base, base)

print(is_power_of(8,2)) # Should be True
print(is_power_of(64,4)) # Should be True
print(is_power_of(70,10)) # Should be False
```

The count_users function recursively counts the amount of users that belong to a group in the company system, by going through each of the members of a group and if one of them is a group, recursively calling the function and counting the members. But it has a bug! Can you spot the problem and fix it?
```python
def count_users(group):
  count = 0
  for member in get_members(group):
    if is_group(member):
      count += count_users(member)
    else:
      count += 1
  return count

print(count_users("sales")) # Should be 3
print(count_users("engineering")) # Should be 8
print(count_users("everyone")) # Should be 18
```

Implement the sum_positive_numbers function, as a recursive function that returns the sum of all positive numbers between the number n received and 1. For example, when n is 3 it should return 1+2+3=6, and when n is 5 it should return 1+2+3+4+5=15.
```python
def sum_positive_numbers(n):
  if n == 0:
    return n
  return n + sum_positive_numbers(n-1)

print(sum_positive_numbers(3)) # Should be 6
print(sum_positive_numbers(5)) # Should be 15
```

Fill in the blanks of this code to print out the numbers 1 through 7 :
```python
number = 1
while number <= 7:
	print(number, end=" ")
	number += 1
```

The show_letters function should print out each letter of a word on a separate line. Fill in the blanks to make that happen.
```python
def show_letters(word):
	for letter in word:
		print(letter)

show_letters("Hello")
# Should print one line per letter
```
Complete the function digits(n) that returns how many digits the number has. For example: 25 has 2 digits and 144 has 3 digits. Tip: you can figure out the digits of a number by dividing it by 10 once per digit until there are no digits left.
```python
def digits(n):
	count = 0
	if n == 0:
	  return 1
	while (n >= 1):
		count += 1
		n = n / 10
	return count
	
print(digits(25))   # Should print 2
print(digits(144))  # Should print 3
print(digits(1000)) # Should print 4
print(digits(0))    # Should print 1
```

This function prints out a multiplication table (where each number is the result of multiplying the first number of its row by the number at the top of its column). Fill in the blanks so that calling multiplication_table(1, 3) will print out:
```python
def multiplication_table(start, stop):
	for x in range(start, stop+1):
		for y in range(start, stop+1):
			print(str(x*y), end=" ")
		print()

multiplication_table(1, 3)
# Should print the multiplication table shown above
```

The counter function counts down from start to stop when start is bigger than stop, and counts up from start to stop otherwise. Fill in the blanks to make this work correctly.
```python
def counter(start, stop):
	x = start
	if start > stop:
		return_string = "Counting down: "
		while x >= stop:
			return_string += str(x)
			if x > stop:
				return_string += ","
			x -= 1
	else:
		return_string = "Counting up: "
		while x <= stop:
			return_string += str(x)
			if x < stop:
				return_string += ","
			x += 1
	return return_string

print(counter(1, 10)) # Should be "Counting up: 1,2,3,4,5,6,7,8,9,10"
print(counter(2, 1)) # Should be "Counting down: 2,1"
print(counter(5, 5)) # Should be "Counting up: 5"
```

The even_numbers function returns a space-separated string of all positive numbers that are divisible by 2, up to and including the maximum that's passed into the function. For example, even_numbers(6) returns “2 4 6”. Fill in the blank to make this work.
```python
def even_numbers(maximum):
	return_string = ""
	for x in [num for num in range(1, maximum+1) if num % 2 == 0]:
		return_string += str(x) + " "
	return return_string.strip()

print(even_numbers(6))  # Should be 2 4 6
print(even_numbers(10)) # Should be 2 4 6 8 10
print(even_numbers(1))  # No numbers displayed
print(even_numbers(3))  # Should be 2
print(even_numbers(0))  # No numbers displayed
```



### week 4
#### Strings
String Indexing and Slicing
String indexing allows you to access individual characters in a string. You can do this by using square brackets and the location, or index, of the character you want to access. It's important to remember that Python starts indexes at 0. So to access the first character in a string, you would use the index [0]. If you try to access an index that’s larger than the length of your string, you’ll get an IndexError. This is because you’re trying to access something that doesn't exist! You can also access indexes from the end of the string going towards the start of the string by using negative values. The index [-1] would access the last character of the string, and the index [-2] would access the second-to-last character.

You can also access a portion of a string, called a slice or a substring. This allows you to access multiple characters of a string. You can do this by creating a range, using a colon as a separator between the start and end of the range, like [2:5]. 

This range is similar to the range() function we saw previously. It includes the first number, but goes to one less than the last number. For example:
```console
>>> fruit = "Mangosteen"
>>> fruit[1:4]
'ang'
```

The slice includes the character at index 1, and excludes the character at index 4. You can also easily reference a substring at the start or end of the string by only specifying one end of the range. For example, only giving the end of the range:
```console
>>> fruit[:5]
'Mango'
```

This gave us the characters from the start of the string through index 4, excluding index 5. On the other hand this example gives is the characters including index 5, through the end of the string:
```console
>>> fruit[5:]
'steen'
```
You might have noticed that if you put both of those results together, you get the original string back!
```console
>>> fruit[:5] + fruit[5:]
'Mangosteen'
```

##### String Reference Cheat Sheet
In Python, there are a lot of things you can do with strings. In this cheat sheet, you’ll find the most common string operations and string methods.

###### String operations
* **len(string)** - Returns the length of the string
* **for character in string** - Iterates over each character in the string
* **if substring in string** - Checks whether the substring is part of the string
* **string[i]** - Accesses the character at index i of the string, starting at zero
* **string[i:j]** - Accesses the substring starting at index i, ending at index j minus 1. If i is omitted, its value defaults to 0. If j is omitted, the value will default to len(string).

###### String methods
* **string.lower()** - Returns a copy of the string with all lowercase characters
* **string.upper()** - Returns a copy of the string with all uppercase characters
* **string.lstrip()** - Returns a copy of the string with the left-side whitespace removed
* **string.rstrip()** - Returns a copy of the string with the right-side whitespace removed
* **string.strip()** - Returns a copy of the string with both the left and right-side whitespace removed
* **string.count(substring)** - Returns the number of times substring is present in the string
* **string.isnumeric()** - Returns True if there are only numeric characters in the string. If not, returns False.
* **string.isalpha()** - Returns True if there are only alphabetic characters in the string. If not, returns False.
* **string.split()** - Returns a list of substrings that were separated by whitespace (whitespace can be a space, tab, or new line)
* **string.split(delimiter)** - Returns a list of substrings that were separated by whitespace or a delimiter
* **string.replace(old, new)** - Returns a new string where all occurrences of old have been replaced by new.
* **delimiter.join(list of strings)** - Returns a new string with all the strings joined by the delimiter 

###### Formatting Strings Cheat Sheet
####### format() method
```python
# "base string with {} placeholders".format(variables)

example = "format() method"

formatted_string = "this is an example of using the {} on a string".format(example)

print(formatted_string)

"""Outputs:
this is an example of using the format() method on a string
"""
```
If the placeholders indicate a number, they’re replaced by the variable corresponding to that order (starting at zero)
```python
# "{0} {1}".format(first, second)

first = "apple"
second = "banana"
third = "carrot"

formatted_string = "{0} {2} {1}".format(first, second, third)

print(formatted_string)

"""Outputs:
apple carrot banana
"""
```
If the placeholders indicate a field name, they’re replaced by the variable corresponding to that field name. This means that parameters to format need to be passed indicating the field name.
```python
# "{var1} {var2}".format(var1=value1, var2=value2)
"{:exp1} {:exp2}".format(value1, value2)
```
If the placeholders include a colon, what comes after the colon is a formatting expression. See below for the expression reference.
```python
# {:d} integer value
'{:d}'.format(10.5) → '10'
```
###### Formatting expressions
![image](https://user-images.githubusercontent.com/18415884/197331516-33f9cf8c-2262-4dbc-a93a-0cf154c9b60e.png)

###### Formatted string literals
This feature was added in Python 3.6 and isn’t used a lot yet<br/>
###### Examples:
```python
>>> name = "Micah"
>>> print(f'Hello {name}')
Hello Micah
```
```python
>>> item = "Purple Cup"
>>> amount = 5
>>> price = amount * 3.25
>>> print(f'Item: {item} - Amount: {amount} - Price: {price:.2f}')
Item: Purple Cup - Amount: 5 - Price: 16.25
```


#### Lists
#### Dictionaries
### week 5
### week 6
