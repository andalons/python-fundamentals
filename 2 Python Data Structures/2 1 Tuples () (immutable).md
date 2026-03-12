# 2.1 Tuples () (immutable)

- Tuples are an ordered sequence, expressed as comma separated elements within parentheses.
- In Python, there are different types: strings, integer, float. They can all be contained in a tuple but the type of the variable is tuple.
- Each element of a tuple can be accessed via an index.
- We can concatenate or combine tuples by adding them. We can also slice them.

```python
tuple1=(1, 2.2, “hello”)
type(tuple1)= tuple
tuple1[0]= 1
tuple1[-1]="hello"

**#Concatenating**
tuple2 = tuple1 + ("andrea", 10) #output: (1, 2.2, "hello", "andrea", 10)

**#Slicing**
tupple2[3:5] #output: ("andrea", 10)
**len**(tupple2) #output: 5

#**Sorting**
Ratings = (0, 9, 6, 5, 10, 8, 9, 6, 2)
RatingsSorted = **sorted**(Ratings)
```

- Tupes are **immutable:**
    
    ![Each variable does not contain a tuple, but references the same immutable tuple object. ](Captura_de_pantalla_2024-12-11_a_las_8.19.34.png)
    
    Each variable does not contain a tuple, but references the same immutable tuple object. 
    
    As a consequence of immutability, if we would like to manipulate a tuple we must create a new tuple instead. For example, if we would like to sort a tuple we use the function `sorted` : 
    
    ```python
    Ratings = (10, 9, 6, 7)
    RatingsSorted = **sorted**(Ratings)
    ```
    
- A tuple can contain other tuples as well as other complex data types. This is called nesting:
    
    ```python
    NT = (1, 2, ("pop", "rock"), (3, 4,), ("disco, (1, 2)))
    ```
    
    We can access these elements using the standard indexing methods
    
    ![Captura de pantalla 2024-12-11 a las 8.31.14.png](Captura_de_pantalla_2024-12-11_a_las_8.31.14.png)
    
- **Usage**: Often used to represent fixed collections of items (e.g., coordinates, records).