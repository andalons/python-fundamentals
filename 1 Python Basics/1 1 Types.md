# 1.1 Types

## Strings, integers and floats

Python is an object-oriented language. There are many different types of objects in Python. Let's start with the most common object types: **strings**, **integers** and **floats**. 

Anytime you write words (text) in Python, you're using character strings (strings for short). The most common numbers, on the other hand, are integers (e.g. -1, 0, 100) and floats, which represent real numbers (e.g. 3.14, -42.0).

```python
# Integer
11

# Float
2.14

# String
"Hello, world"
```

## The function type()

You can get Python to tell you the type of an expression by using the built-in `type()` function. You'll notice that Python refers to integers as `int`, floats as `float`, and character strings as `str`.

## Typecasting

You can change the type of the object in Python; this is called **typecasting**. 

- You can convert an integer into a float (e.g. 2 to 2.0): `float(2)` → `2.0`
- When we convert an integer into a float, we don't really change the value (i.e., the significand) of the number. However, if we cast a float into an integer, we could potentially lose some information. For example, if we cast the float 1.6 to integer we will get 1 and lose the decimal information (i.e., 0.6): `int(1.6)` → `1`
- Sometimes, we can have a string that contains a number within it. If this is the case, we can cast that string that represents a number into an integer using int(): `int('2')` → `2`
- You can do the same with floats: `float('1.2')` → `1.2`
- If you try to do this with a string that is not a perfect match for an int or a float, you’ll get an error: `int('1 or 2')` → `error`

## Boolean data type

Boolean is another important type in Python. An object of type Boolean can take on one of two values: `True` or `False` (using the uppercase T and F)

- `int(True)` → 1
- `bool(1)` → `True`
- `bool(0)` → `False`
- `float(True)`→ `1.0`