# Manejo de Excepciones

## **¿Qué son las excepciones?**

**Las excepciones** son alertas cuando algo inesperado sucede mientras se ejecuta un programa. Podría ser un error en el código o una situación que no fue planeada. Python puede levantar estas alertas automáticamente, pero también podemos activarlas a propósito usando el comando raise. Lo genial es que podemos prevenir que nuestro programa se bloquee manejando excepciones.

## **Errores vs. Excepciones**

Espera, ¿cuál es la diferencia entre errores y excepciones? Bueno, los `errores` son usualmente problemas grandes que vienen de la computadora o el sistema. A menudo hacen que el programa deje de funcionar completamente. Por otro lado, las `excepciones` son más como problemas que podemos controlar. Suceden porque de algo que hicimos en nuestro código y usualmente pueden ser arreglados, así que el programa sigue funcionando.

## **Excepciones Comunes en Python**

Aquí hay algunos ejemplos de **excepciones incorporadas** que a menudo encontramos y podemos manejar usando esta herramienta:

- **ZeroDivisionError:**
    
    Este error surge cuando se intenta dividir un número por cero. La división por cero es indefinida en matemáticas, causando un error aritmético.
    
    **Ejemplo:**
    
    ```python
    try:
        result = 10 / 0
    except ZeroDivisionError as e:
        print("Error:", e)
    ```
    
- **ValueError:**
    
    Este error ocurre cuando se usa un valor inapropiado dentro del código. Por ejemplo, tratando de convertir una cadena no numérica a un entero.
    
    **Ejemplo:**
    
    ```python
    try:
        number = int("abc")
    except ValueError as e:
        print("Error:", e)
    ```
    
- **FileNotFoundError:**
    
    Esta excepción se encuentra cuando se intenta acceder a un archivo que no existe.
    
    **Ejemplo:**
    
    ```python
    try:
        with open("nonexistent_file.txt", "r") as file:
            content = file.read()
    except FileNotFoundError as e:
        print("Error:", e)
    ```
    
- **IndexError:**
    
    Un IndexError ocurre cuando se usa un índice para acceder a un elemento en una lista que está fuera del rango de índice válido.
    
    **Ejemplo:**
    
    ```python
    try:
        my_list = [1, 2, 3]
        print(my_list[5])
    except IndexError as e:
        print("Error:", e)
    ```
    
- **KeyError:**
    
    El KeyError surge cuando se intenta acceder a una clave no existente en un diccionario.
    
    **Ejemplo:**
    
    ```python
    try:
        my_dict = {"a": 1, "b": 2}
        print(my_dict["c"])
    except KeyError as e:
        print("Error:", e)
    ```
    
- **TypeError:**
    
    El TypeError ocurre cuando un objeto se usa de manera incompatible. Un ejemplo incluye tratando de concatenar una cadena y un entero.
    
    **Ejemplo:**
    
    ```python
    try:
        result = "Age: " + 25
    except TypeError as e:
        print("Error:", e)
    ```
    
- **AttributeError:**
    
    Un AttributeError ocurre cuando se accede a un atributo o método en un objeto que no posee ese atributo o método específico.
    
    **Ejemplo:**
    
    ```python
    try:
        number = 10
        number.append(5)
    except AttributeError as e:
        print("Error:", e)
    ```
    
- **ImportError:**
    
    Este error se encuentra cuando se intenta importar un módulo que no está disponible.
    
    **Ejemplo:**
    
    ```python
    try:
        import nonexistent_module
    except ImportError as e:
        print("Error:", e)
    ```
    

---

> Nota: Las excepciones que encontrarás no se limitan solo a estas. Hay muchas más en Python. Sin embargo, no hay necesidad de preocuparse. Usando la técnica proporcionada arriba y siguiendo la sintaxis correcta, podrás manejar cualquier excepción que venga en tu camino.
> 

## **Manejando Excepciones:**

### Try y except

Python tiene una herramienta útil llamada `try y except` que nos ayuda a manejar excepciones.

Aquí cómo funcionan:

1. El código que puede resultar en una excepción se contiene en el bloque `try`.
2. Si ocurre una excepción, el código salta directamente al bloque `except`.
3. En el bloque except, puedes definir cómo manejar la excepción graciosamente, como mostrar un mensaje de error o tomar acciones alternativas.
4. Después del bloque except, el programa continúa ejecutando el código restante.

```python
# código potencial antes de try catch

try:
    # código a intentar ejecutar
except ZeroDivisionError:
    # código a ejecutar si hay un ZeroDivisionError
except NameError:
    # código a ejecutar si hay un NameError
except:
    # código a ejecutar si hay cualquier excepción
    
# código que se ejecutará si no hay excepción o una que estamos manejando
```

**Ejemplo: Intentando dividir por cero**

```python
# usando Try - except 
try:
    # Intentando dividir 10 por 0
    result = 10 / 0
except ZeroDivisionError:
    # Manejando el ZeroDivisionError e imprimiendo un mensaje de error
    print("Error: Cannot divide by zero")
# Esta línea se ejecutará independientemente de si ocurrió una excepción
print("outside of try and except block")
```

### **Try Except Else y Finally**

- `else` permite verificar si no hubo excepción al ejecutar el bloque try. Esto es útil cuando queremos ejecutar algo solo si no hubo errores.
- `finally` nos permite siempre ejecutar algo incluso si hay una excepción o no. Esto usualmente se usa para significar el fin del try except.

```python
# código potencial antes de try catch

try:
    # código a intentar ejecutar
except ZeroDivisionError:
    # código a ejecutar si hay un ZeroDivisionError
except NameError:
    # código a ejecutar si hay un NameError
except:
    # código a ejecutar si hay cualquier excepción
else:
    # código a ejecutar si no hay excepción
finally:
    # código a ejecutar al final del try except sin importar qué
    
# código que se ejecutará si no hay excepción o una que estamos manejando
```