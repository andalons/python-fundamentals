# 1.2 Expressions and Variables

## **Expressions**

Expressions in Python can include operations among compatible types (e.g., integers and floats).

For example, basic arithmetic operations:

- Addition:`43 + 60 + 16 + 41`
- Subtraction: `50 - 60`
- Division: `6 / 2`
- Integer division: `6 // 2`

## Variables

Just like with most programming languages, we can store values in *variables*, so we can use them later on.

For example:

```python
# Store value into variable
x = 43 + 60 + 16 + 41

# Print out the value in variable
x

# Use another variable to store the result of the operation between variable and value
y = x / 60
y

# Overwrite variable with new value
x = x / 60
x
```

It is important to name variables meaningfully:

```python
total_min = 43 + 42 + 57 # Total length of albums in minutes
total_min

total_hours = total_min / 60 # Total length of albums in hours 
total_hours
```

In the cells above, we added the length of three albums in minutes and stored it in `total_min`. We then divided it by 60 to calculate the total length (`total_hours`) in hours.

You can also do it all at once in a single expression, as long as you use parentheses to add the albums' lengths before you divide, as shown below:

```python
total_hours = (43 + 42 + 57) / 60  # Total hours in a single expression
total_hours
```