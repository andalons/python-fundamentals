# 3.2 Loops

## The range function

The range function in Python 3 returns a range object that can be used in loops. It takes one or two arguments:

- If given one argument (e.g., range(3)), it generates a sequence starting from 0 up to (but not including) the given number.
- If given two arguments (e.g., range(1, 3)), it generates a sequence starting from the first argument up to (but not including) the second argument.

```python
range(3): #output range(0,3)
range(1, 3):
```

## `for` loops

The `for` loop enables you to execute a code block multiple times. 

```python
#Example using range
dates = [1982,1980,1973]
N = len(dates)

for i in range(N):
    print(dates[i])     
```

The code in the indent is executed `N` times, each time the value of `i` is increased by 1 for every execution. The statement executed is to `print` out the value in the list at index `i`.

We can also directly access the elements in the list as follows:

```python
# Exmaple looping through list
for year in dates:  
    print(year) 
```

Other uses of for loops:

```python
# Use for loop to change the elements in list
squares = ['red', 'yellow', 'green', 'purple', 'blue']

for i in range(0, 5):
    print("Before square ", i, 'is',  squares[i])
    squares[i] = 'white'
    print("After square ", i, 'is',  squares[i])
    
    
# Loop through the list and iterate on both index and element value 
# The function enumerate()
squares=['red', 'yellow', 'green', 'purple', 'blue']

for i, square in enumerate(squares):
    print(i, square)
```

## `while` loops

As you can see, the `for` loop is used for a controlled flow of repetition. However, what if we don't know when we want to stop the loop? What if we want to keep executing a code block until a certain condition is met? The `while` loop exists as a tool for repeated execution based on a condition. The code block will keep being executed until the given logical condition returns a **False** boolean value.

```python
#Example
dates = [1982, 1980, 1973, 2000]

i = 0
year = dates[0]

while(year != 1973):    
    print(year)
    i = i + 1 # the same as i += 1
    year = dates[i]
    

print("It took ", i ,"repetitions to get out of loop.")
#Output: 
#1982
#1980
#It took  2 repetitions to get out of loop.
```

A while loop iterates merely until the condition in the argument is not  met

```python
#This while loop copies the strings 'orange' of the list squares to the list new_squares. 
#The loop is stopped and exited if the value on the list is not 'orange' 

squares = ['orange', 'orange', 'purple', 'blue ', 'orange']
new_squares = []
i = 0
while(i < len(squares) and squares[i] == 'orange'):
    new_squares.append(squares[i])
    i += 1
print (new_squares)

#output: ['orange', 'orange']
```