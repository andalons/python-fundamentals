# 1.3 String Operations

![Captura de pantalla 2024-12-10 a las 16.16.45.png](Captura_de_pantalla_2024-12-10_a_las_16.16.45.png)

![Captura de pantalla 2024-12-10 a las 16.17.59.png](Captura_de_pantalla_2024-12-10_a_las_16.17.59.png)

It is helpful to think of a string as an ordered sequence of characters. Each element of the sequence can be accessed by the index represented by the array of numbers. Negative indexing can also be used (picture 2).

## **Basic Operations: concatenation, repetition, length**

- **Concatenation:** Combine strings using the `+` operator.
    
    ```python
    python
    Copiar código
    str1 = "Hello"
    str2 = "World"
    result = str1 + " " + str2  # Output: "Hello World"
    ```
    
- **Repetition:** Repeat strings using the `*` operator.
    
    ```python
    result = "Python" * 3  # Output: "PythonPythonPython
    ```
    
- **Length:** Use `len()` to find the number of characters.
    
    ```python
    length = len("Python")  # Output: 6
    ```
    

## **String Indexing and Slicing**

- **Indexing:** Access individual characters using their index (starts at 0).
    
    ```python
    word = "Python"
    first = word[0]  # Output: 'P'
    last = word[-1]  # Output: 'n'
    ```
    
- **Slicing:** Extract parts of a string using `start:end` (end is excluded).
    
    ```python
    substring = word[1:4]  # Output: 'yth'
    ```
    
    ![We can input a stride value as follows: The 2 indicates we'd select every second variable. ](Captura_de_pantalla_2024-12-10_a_las_16.26.51.png)
    
    We can input a stride value as follows: The 2 indicates we'd select every second variable. 
    
    ![Here an example which also incorporates slicing](Captura_de_pantalla_2024-12-10_a_las_16.27.13.png)
    
    Here an example which also incorporates slicing
    

## String methods

- **Transformations:**
    
    ```python
    word = "hello"
    print(word.upper())  # Output: "HELLO"
    print(word.lower())  # Output: "hello"
    print(word.capitalize())  # Output: "Hello"
    print(word.title())  # Output: "Hello"
    ```
    
- **Find and replace:**
    
    ```python
    text = "Python is fun"
    print(text.find("is"))  
    # Output: 7. If the sub-string is not in the string then the output is -1.
    print(text.replace("fun", "awesome"))  
    # Output: "Python is awesome"
    ```
    
- **Stripping and Padding:**
    
    ```python
    word = "  hello  "
    print(word.strip())  # Output: "hello"
    print(word.lstrip())  # Output: "hello  "
    print(word.rstrip())  # Output: "  hello"
    print(word.center(10, "-"))  # Output: "--hello---"
    ```
    

## **Checking Conditions**

- **Starts and Ends:**
    
    ```python
    text = "Python programming"
    print(text.startswith("Python"))  # Output: True
    print(text.endswith("ing"))  # Output: Tru
    ```
    
- **Content Check:**
    
    ```python
    print("123".isdigit())  # Output: True
    print("abc".isalpha())  # Output: True
    print("Python3".isalnum())  # Output: True
    ```
    

## **Advanced String Techniques**

- **Splitting and Joining:**
Syntax for `split`: `string.split(separator, maxsplit)`
    - separator (optional): if not provided, the default separator is any whitespace)
    - maxsplit (optional): it specifies the maximum number of splits to perform. If not provided, there is no limit.
    
    ```python
    sentence = "Python is fun"
    words = sentence.split()  # Output: ['Python', 'is', 'fun']
    joined = " ".join(words)  # Output: "Python is fun"
    ```
    
- **Raw Strings:**
    
    ```python
    raw = r"C:\new_folder\file.txt"
    print(raw)  # Output: "C:\new_folder\file.txt"
    ```
    

## **Escape Characters**

Use backslashes for special characters:

```python
print("This is a line\nAnd this is a new line.")  # Output includes a line break
print("This is a tab\tHere")  # Output includes a tab
print("This is a backslash \\")  # Output includes 1 backslash
```

## Format strings

**Format strings** are a way to inject variables into a string in Python. They produce more human-readable outputs. There are several ways to format strings in Python:

### **String Interpolation (f-strings)**

Introduced in Python 3.6, f-strings are prefixed with `f` and use curly braces `{}` to enclose variables.

Example:

```python
name = "John"
age = 30
print(f"My name is {name} and I am {age} years old."

#output:
My name is John and I am 30 years old.
```

### **`str.format()`**

Uses curly braces `{}` as placeholders and the `format()` method to inject variables.

Example:

```python
name = "John"
age = 50
print("My name is {} and I am {} years old.".format(name, age))

#output: My name is John and I am 50 years old.
```

### **`% Operator`**

One of the oldest ways to format strings, using `%` for replacement.

Example:

```python
name = "Johnathan"
age = 30
print("My name is %s and I am %d years old." % (name, age))

#output: My name is Johnathan and I am 30 years old.
```

**Explanation:**

- `%s`: Placeholder for a string.
- `%d`: Placeholder for an integer.
- `% (name, age)`: Tuple containing variables that replace placeholders.

### **Additional Capabilities of f-strings**

F-strings can evaluate expressions inside curly braces.

Example:

```python
x = 10
y = 20
print(f"The sum of x and y is {x + y}.")

#output:The sum of x and y is 30.
```

### **Raw Strings (`r''`)**

Raw strings handle escape characters by treating backslashes (`\`) as literal characters.

**Regular String Example:**

```python
regular_string = "C:\new_folder\file.txt"
print("Regular String:", regular_string)

#output:
Regular String: C:
ew_folderile.txt
```

**Raw String Example:**

```python
raw_string = r"C:\new_folder\file.txt"
print("Raw String:", raw_string)

#output:
Raw String: C:\new_folder\file.txt

```

Raw strings ensure backslashes are not interpreted as escape sequences.

<aside>

**Summary:**

- **f-strings:** Modern, preferred for readability and performance.
- **`str.format()`:** Flexible for older Python versions.
- **`% operator`:** Useful but considered outdated.
- **Raw strings:** Essential for handling file paths and escape characters.
</aside>

## RegEx

In Python, RegEx (short for Regular Expression) is a tool for matching and handling strings.

This RegEx module provides several functions for working with regular expressions, including `search`, `split`, `findall` and `sub`.

Python provides a built-in module called `re`, which allows you to work with regular expressions. First, import the `re` module.

```python
import re

s1 = "Michael Jackson is the best"

# Define the pattern to search for
pattern = r"Jackson"

# Use the search() function to search for the pattern in the string
result = re.search(pattern, s1)

# Check if a match was found
if result:
    print("Match found!")
else:
    print("Match not found.")
```

The search() function searches for specified patterns within a string. Here is an example that explains how to use the search() function to search for the word "Jackson" in the string "Michael Jackson is the best".

Regular expressions (RegEx) are patterns used to match and manipulate strings of text. There are several special sequences in RegEx that can be used to match specific characters or patterns.

![Captura de pantalla 2024-12-10 a las 16.58.56.png](Captura_de_pantalla_2024-12-10_a_las_16.58.56.png)

Examples of regular expressions and RegEx functions

```python
# The \d special sequence in a regular expression pattern using **search** function:

pattern = r"\d\d\d\d\d\d\d\d\d\d"  # Matches any ten consecutive digits
text = "My Phone number is 1234567890"
match = re.search(pattern, text)

if match:
    print("Phone number found:", match.group())
else:
    print("No match")
    
#output: 
Phone number found: 1234567890
```

```python
# The \W special sequence in a regular expression pattern using **findall** function:

pattern = r"\W"  # Matches any non-word character
text = "Hello, world!"
matches = re.findall(pattern, text)

print("Matches:", matches)

#output:
Matches: [',', ' ', '!']
```

```python
# Use the **split** function to split the string by the "\s" (regular expression pattern that matches any whitespace character)
split_array = re.split(r"\s", s2)

# The split_array contains all the substrings, split by whitespace characters
print(split_array)
```

```python
#The **sub** function of a regular expression is used to replace all occurrences of a pattern in a string.

# Define the regular expression pattern to search for
pattern = r"King of Pop"

# Define the replacement string
replacement = "legend"

# Use the sub function to replace the pattern with the replacement string
new_string = re.sub(pattern, replacement, s2, flags=re.IGNORECASE)

# The new_string contains the original string with the pattern replaced by the replacement string
print(new_string) 
```