# Exception Handling

## **What are exceptions?**

**Exceptions** are alerts when something unexpected happens while running a program. It could be a mistake in the code or a situation that was not planned for. Python can raise these alerts automatically, but we can also trigger them on purpose using the raise command. The cool part is that we can prevent our program from crashing by handling exceptions.

## **Errors vs. Exceptions**

Hold on, what is the difference between errors and exceptions? Well, `errors` are usually big problems that come from the computer or the system. They often make the program stop working completely. On the other hand, `exceptions` are more like issues we can control. They happen because of something we did in our code and can usually be fixed, so the program keeps going.

## **Common Exceptions in Python**

Here are a few examples of **built-in exceptions** we often run into and can handle using this tool:

- **ZeroDivisionError:**
    
    This error arises when an attempt is made to divide a number by zero. Division by zero is undefined in mathematics, causing an arithmetic error.
    
    **Example:**
    
    ```python
    try:
        result = 10 / 0
    except ZeroDivisionError as e:
        print("Error:", e)
    ```
    
- **ValueError:**
    
    This error occurs when an inappropriate value is used within the code. For example, trying to convert a non-numeric string to an integer.
    
    **Example:**
    
    ```python
    try:
        number = int("abc")
    except ValueError as e:
        print("Error:", e)
    ```
    
- **FileNotFoundError:**
    
    This exception is encountered when an attempt is made to access a file that does not exist.
    
    **Example:**
    
    ```python
    try:
        with open("nonexistent_file.txt", "r") as file:
            content = file.read()
    except FileNotFoundError as e:
        print("Error:", e)
    ```
    
- **IndexError:**
    
    An IndexError occurs when an index is used to access an element in a list that is outside the valid index range.
    
    **Example:**
    
    ```python
    try:
        my_list = [1, 2, 3]
        print(my_list[5])
    except IndexError as e:
        print("Error:", e
    ```
    
- **KeyError:**
    
    The KeyError arises when an attempt is made to access a non-existent key in a dictionary.
    
    **Example:**
    
    ```python
    try:
        my_dict = {"a": 1, "b": 2}
        print(my_dict["c"])
    except KeyError as e:
        print("Error:", e)
    ```
    
- **TypeError:**
    
    The TypeError occurs when an object is used in an incompatible manner. An example includes trying to concatenate a string and an integer.
    
    **Example:**
    
    ```python
    try:
        result = "Age: " + 25
    except TypeError as e:
        print("Error:", e)
    ```
    
- **AttributeError:**
    
    An AttributeError occurs when an attribute or method is accessed on an object that doesn't possess that specific attribute or method.
    
    **Example:**
    
    ```python
    try:
        number = 10
        number.append(5)
    except AttributeError as e:
        print("Error:", e)
    ```
    
- **ImportError:**
    
    This error is encountered when an attempt is made to import a module that is unavailable.
    
    **Example:**
    
    ```python
    try:
        import nonexistent_module
    except ImportError as e:
        print("Error:", e)
    ```
    

---

> Note: The exceptions you will encounter are not limited to just these. There are many more in Python. However, there is no need to worry. By using the technique provided above and following the correct syntax, you will be able to handle any exceptions that come your way.
> 

## **Handling Exceptions:**

### Try and except

Python has a handy tool called `try and except` that helps us manage exceptions.

Here's how they work:

1. The code that may result in an exception is contained in the `try` block.
2. If an exception occurs, the code directly jumps to `except` block.
3. In the except block, you can define how to handle the exception gracefully, like displaying an error message or taking alternative actions.
4. After the except block, the program continues executing the remaining code.

```python
# potential code before try catch

try:
    # code to try to execute
except ZeroDivisionError:
    # code to execute if there is a ZeroDivisionError
except NameError:
    # code to execute if there is a NameError
except:
    # code to execute if there is any exception
    
# code that will execute if there is no exception or a one that we are handling
```

**Example: Attempting to divide by zero**

```python
# using Try - except 
try:
    # Attempting to divide 10 by 0
    result = 10 / 0
except ZeroDivisionError:
    # Handling the ZeroDivisionError and printing an error message
    print("Error: Cannot divide by zero")
# This line will be executed regardless of whether an exception occurred
print("outside of try and except block")
```

### **Try Except Else and Finally**

- `else` allows one to check if there was no exception when executing the try block. This is useful when we want to execute something only if there were no errors.
- `finally` allows us to always execute something even if there is an exception or not. This is usually used to signify the end of the try except.

```python
# potential code before try catch

try:
    # code to try to execute
except ZeroDivisionError:
    # code to execute if there is a ZeroDivisionError
except NameError:
    # code to execute if there is a NameError
except:
    # code to execute if ther is any exception
else:
    # code to execute if there is no exception
finally:
    # code to execute at the end of the try except no matter what
    
# code that will execute if there is no exception or a one that we are handling
```