# 3.3 Funciones

Una función es un bloque de código reutilizable que realiza operaciones especificadas en la función. Te permiten descomponer tareas y reutilizar tu código en diferentes programas.

Hay dos tipos de funciones:

- **Funciones predefinidas:**
- **Funciones definidas por el usuario**

## Funciones Predefinidas

Una **función incorporada** es una función que está disponible globalmente en Python sin requerir una importación o un contexto específico. Estas funciones están definidas en el nivel central de Python o proporcionadas por la biblioteca estándar. Algunos ejemplos que ya usamos son: `print()`, `len()`, `sum()`, `range()`, `slice()`, `sorted()`…

> No confundir con métodos, que están asociados con un objeto específico (o clase) y operan en el contexto del objeto al que pertenecen y pueden usar o modificar los datos internos del objeto. Ejemplos:
> 

| **Aspecto** | **Función Incorporada** | **Método** |
| --- | --- | --- |
| **Alcance** | Global | Específico a un objeto o clase |
| **Sintaxis de Llamada** | `function_name(args)` | `object.method(args)` |
| **Definido En** | Biblioteca incorporada de Python | La clase del objeto |
| **Comportamiento** | Puede trabajar en múltiples tipos de objeto | Específico al contexto del objeto |

## Funciones Definidas por el Usuario

Puedes definir funciones para proporcionar la funcionalidad requerida. Aquí hay reglas simples para definir una función en Python:

- Los bloques de funciones comienzan con `def` seguido del `nombre` de la función y paréntesis `()`.
- Hay parámetros de entrada o argumentos que deben colocarse dentro de estos paréntesis.
- También puedes definir parámetros dentro de estos paréntesis.
- Hay un cuerpo dentro de cada función que comienza con dos puntos (`:`) y está indentado.
- También puedes colocar documentación antes del cuerpo.
- La declaración `return` sale de una función, opcionalmente pasando de vuelta un valor.

```python
# Ejemplo de función simple

def add(a):
    """
    comentario dentro de la función: agregar 1 a a
    """
    b = a + 1
    print(a, "if you add one", b)
    return(b)
```

![Captura de pantalla 2024-12-12 a las 15.46.43.png](../../img/Captura_de_pantalla_2024-12-12_a_las_15.46.43.png)

```python
# Definir una función con múltiples parámetros

def Mult(a, b):
    c = a * b
    return(c)
    print('This is not printed') #la declaración return termina la función, por lo que este código nunca se ejecuta
    
result = Mult(12,2)
print(result)

Mult(10.0, 3.14) #Puedes multiplicar flotantes
Mult(2, "Michael Jackson ") #Puedes multiplicar entero y cadena. output: 'Michael Jackson Michael Jackson '
```

## Variables

- La entrada a una función se llama parámetro formal.
- El **alcance de una variable** es la parte de ese programa donde esa variable es accesible.
- Una variable que se declara dentro de una función se llama **variable local**. El parámetro solo existe dentro de la función (es decir, el punto donde la función comienza y termina).
- Una variable que se declara fuera de una definición de función es una **variable global**, y su valor es accesible y modificable a lo largo del programa.

```python
# Definición de Función
def squarePlusOne(a):
    # Variable local b
    b = 1
    c = a * a + b
    print(a, "if you square + 1", c) 
    return(c)
    
# Inicializa variable global  
x = 3
# Hace llamada a función y devuelve función a y
y = squarePlusOne(x)
y
```

- Si no hay declaración `return`, la función devuelve `None`.
    
    ```python
    # Definir funciones, una con valor de retorno None y otra sin valor de retorno
    
    def MJ():
        print('Michael Jackson')
        
    def MJ1():
        print('Michael Jackson')
        return(None)
        
    print(MJ())
    print(MJ1())
    #ambas imprimirán Michael Jackson 
    ```
    

## Usando Declaraciones `if`/`else` y Bucles en Funciones

```python
# Función con id

def type_of_album(artist, album, year_released):
    
    print(artist, album, year_released)
    if year_released > 1980:
        return "Modern"
    else:
        return "Oldie"
    
x = type_of_album("Michael Jackson", "Thriller", 1980)
print(x)
```

```python
# Función usando bucle for

def PrintList(the_list):
    for element in the_list:
        print(element)
```

## **Comparación de Cadenas en Funciones**

```python
#Ejemplo 1: Comparar Dos Cadenas Directamente usando operador in
string= "Michael Jackson is the best"

# Definir una función
def check_string(text):
    
# Usar declaración if else y operador 'in' para comparar la cadena
    if text in string:
        return 'String matched'
    else:
        return 'String not matched'

check_string("Michael Jackson is the best")
```

```python
#Ejemplo 2: Comparar dos cadenas usando operador == y función
def compareStrings(x, y):
# Usar declaración if else para comparar x e y
    if x==y:
        return 1
    
# Declarar dos variables diferentes como string1 y string2 y pasar cadena en ellas
string1 = "Michael Jackson is the best"
string2 = "Michael Jackson is the best"

# Declarar una variable para almacenar resultado después de comparar ambas cadenas
check = compareStrings(string1, string2)

#Usar declaración if else para comparar la cadena
if check==1:
    print("\nString Matched")
else:
    print("\nString not Matched")
```

```python
# Ejemplo 3: Programa Python para Contar palabras en una Cadena usando Diccionario
def freq(string):
    
    #paso1: Una variable de lista se declara e inicializa a una lista vacía.
    words = []
    
    #paso2: Romper la cadena en lista de palabras
    words = string.split() # o string.lower().split()
    
    #paso3: Declarar un diccionario
    Dict = {}
    
    #paso4: Usar bucle for para iterar palabras y valores al diccionario
    for key in words:
        Dict[key] = words.count(key)
        
    #paso5: Imprimir el diccionario
    print("The Frequency of words is:",Dict)
    
#paso6: Llamar función y pasar cadena en ella
freq("Mary had a little lamb Little lamb, little lamb Mary had a little lamb.Its fleece was white as snow And everywhere that Mary went Mary went, Mary went \
Everywhere that Mary went The lamb was sure to go")
```

## **Estableciendo valores de argumento predeterminados en tus funciones personalizadas**

```python
# Ejemplo para establecer param con valor predeterminado

def isGoodRating(rating=4): 
    if(rating < 7):
        print("this album sucks it's rating is",rating)
        
    else:
        print("this album is good its rating is",rating)

```

## Colecciones y funciones

Cuando el número de argumentos son desconocidos para una función, Todos pueden ser empaquetados en una tupla como se muestra:

```python
def printAll(*args): # Todos los argumentos son 'empaquetados' en args que pueden ser tratados como una tupla
    print("No of arguments:", len(args)) 
    for argument in args:
        print(argument)
#printAll con 3 argumentos
printAll('Horsefeather','Adonis','Bone')
#printAll con 4 argumentos
printAll('Sidecar','Long Island','Mudslide','Carriage')
```

Similarmente, Los argumentos también pueden ser empaquetados en un diccionario como se muestra:

```python
def printDictionary(**args):
    for key in args:
        print(key + " : " + args[key])

printDictionary(Country='Canada',Province='Ontario',City='Toronto')
```

Las funciones pueden ser increíblemente poderosas y versátiles. Pueden aceptar (y devolver) tipos de datos, objetos e incluso otras funciones como argumentos. Considera el ejemplo abajo. 

```python
def addItems(list):
    list.append("Three")
    list.append("Four")

myList = ["One","Two"]

addItems(myList)

myList
```

Nota cómo los cambios hechos a la lista no están limitados al alcance de la función. Esto ocurre ya que es la **referencia** de la lista la que se pasa a la función - Cualquier cambio hecho está en la instancia original de la lista. Por lo tanto, uno debería ser cauteloso cuando pasa objetos mutables a funciones.