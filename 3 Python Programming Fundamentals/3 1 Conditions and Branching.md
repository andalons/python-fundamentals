# 3.1 Conditions and Branching

## Comparison operators

Comparison operations compare some value or operand and based on a condition, produce a Boolean. When comparing two values you can use these operators:

- equal: **==**
- not equal: **!=**
- greater than: **>**
- less than: **<**
- greater than or equal to: **>=**
- less than or equal to: **<=**

```python
#Examples

# Greater than Sign
i = 2
i > 5 #output: False

# Inequality Sign
i = 2
i != 6 #output: True

# Comparing the strings
"ACDC" != "Michael Jackson" #output: True
```

<aside>

The inequality operation is also used to compare the letters/words/symbols according to the ASCII value of letters. The decimal value shown in the following table represents the order of the character:

![Captura de pantalla 2024-12-12 a las 10.57.46.png](../img/Captura_de_pantalla_2024-12-12_a_las_10.57.46.png)

For example, the ASCII code for **!** is 33, while the ASCII code for **+** is 43. Therefore **+** is larger than **!** as 43 is greater than 33.

`'B' > 'A’` → True

When there are multiple letters, the first letter takes precedence in ordering:

`'BA' > 'AB’` → True 

**Note**: Upper Case Letters have different ASCII code than Lower Case Letters, which means the comparison between the letters in Python is case-sensitive.

</aside>

## Branching

Branching allows us to run different statements for different inputs. It is helpful to think of an **if statement** as a locked room, if the statement is **True** we can enter the room and your program will run some predefined tasks, but if the statement is **False** the program will ignore the task. 

- We can use the condition statements learned before as the conditions that need to be checked in the **if statement**. The syntax is as simple as  `if *condition statement* :`, which contains a word `if`, any condition statement, and a colon at the end. Start your tasks which need to be executed under this condition in a new line with an indent. The lines of code after the colon and with an indent will only be executed when the **if statement** is **True**. The tasks will end when the line of code does not contain the indent.
    
    ```python
    # If statement example
    age = 18
    #age = 19 
    
    #expression that can be true or false
    if age > 18:
        
        #within an indent, we have the expression that is run if the condition is true
        print("you can enter" )
    
    #The statements after the if statement will run regardless if the condition is true or false 
    print("move on")
    ```
    
- The `else` statement runs a block of code if none of the conditions are **True** before this `else` statement. The syntax of the `else` statement is similar as the syntax of the `if` statement, as `else :`. Notice that, there is no condition statement for `else`.
    
    ```python
    # Else statement example
    age = 18
    #age = 19 
    
    if age > 18:
        print("you can enter" )
    else:
        print("go see Meat Loaf" )
        
    print("move on")
    ```
    
- The `elif` statement, short for else if, allows us to check additional conditions if the condition statements before it are **False**. If the condition for the `elif` statement is **True**, the alternate expressions will be run. The syntax of the `elif` statement is similar in that we merely change the `if` in the `if` statement to `elif`.
    
    ```python
    # Elif statment example
    
    age = 18
    
    if age > 18:
        print("you can enter" )
    elif age == 18:
        print("go see Pink Floyd")
    else:
        print("go see Meat Loaf" )
        
    print("move on")
    ```
    

## Logic operators

Sometimes you want to check more than one condition at once. For example, you might want to check if one condition and another condition are both **True**. Logical operators allow you to combine or modify conditions.

- `and`
- `or`
- `not`

```python
# Condition statement example

album_year = 1980

if(album_year > 1979) **and** (album_year < 1990):
    print ("Album year was in between 1980 and 1989")
    
print("")
print("Do Stuff..")

#output: 
#Album year was in between 1980 and 1989

#Do Stuff.
```

```python
# Condition statement example

album_year = 1990

if(album_year < 1980) **or** (album_year > 1989):
    print ("Album was not made in the 1980's")
else:
    print("The Album was made in the 1980's ")
    
#output:
#Album was not made in the 1980's
```

```python
# Condition statement example

album_year = 1983

if **not** (album_year == 1984):
    print ("Album year is not 1984")
    
#output:
#Album year is not 1984
```