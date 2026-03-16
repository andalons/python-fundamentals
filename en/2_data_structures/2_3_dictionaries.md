# 2.3 Dictionaries {”key”: value}

- A dictionary consists of **keys** and **values**. It is helpful to compare a dictionary to a list:
    
    ![Captura de pantalla 2024-12-12 a las 7.42.13.png](../../img/Captura_de_pantalla_2024-12-12_a_las_7.42.13.png)
    
- Instead of being indexed numerically like a list, dictionaries have keys. These keys are the keys that are used to access values within a dictionary.
- Each key is separated from its value by a colon "`:`". Commas separate the items, and the whole dictionary is enclosed in curly braces. An empty dictionary without any items is written with just two curly braces, like this `{}`.
- For every key, there can only be one single value, however, multiple keys can hold the same value. Keys can only be strings, numbers, or tuples, but values can be any data type.

```python
#The keys can be strings, but they can also be any inmmutable object, such as a tuple:
Dict = {"key1": 1, "key2": "2", (0, 1): 6} 
Dict["key1"] #output: 1
Dict[(0, 1)] #output: 6    

# Dictionary example:
release_year_dict = {"Thriller": "1982", "Back in Black": "1980", \
                    "The Dark Side of the Moon": "1973", "The Bodyguard": "1992", \
                    "Bat Out of Hell": "1977", "Their Greatest Hits (1971-1975)": "1976", \
                    "Saturday Night Fever": "1977", "Rumours": "1977"}

# Get value by key
release_year_dict['The Bodyguard']     

# Get all the keys in dictionary
release_year_dict.**keys**()  

# Get all the values in dictionary
release_year_dict.**values**()                        

# Append value with key into dictionary
release_year_dict['Graduation'] = '2007'

# Delete entries by key
**del**(release_year_dict['Thriller'])

# Verify the key is in the dictionary
'The Bodyguard' **in** release_year_dict #output: True
```