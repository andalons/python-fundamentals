# 3.2 Bucles

## La función range

La función range en Python 3 devuelve un objeto range que puede usarse en bucles. Toma uno o dos argumentos:

- Si se le da un argumento (ej. range(3)), genera una secuencia comenzando desde 0 hasta (pero no incluyendo) el número dado.
- Si se le dan dos argumentos (ej. range(1, 3)), genera una secuencia comenzando desde el primer argumento hasta (pero no incluyendo) el segundo argumento.

```python
range(3): #output range(0,3)
range(1, 3):
```

## Bucles `for`

El bucle `for` te permite ejecutar un bloque de código múltiples veces. 

```python
#Ejemplo usando range
dates = [1982,1980,1973]
N = len(dates)

for i in range(N):
    print(dates[i])     
```

El código en la indentación se ejecuta `N` veces, cada vez el valor de `i` se incrementa en 1 por cada ejecución. La declaración ejecutada es imprimir el valor en la lista en el índice `i`.

También podemos acceder directamente a los elementos en la lista de la siguiente manera:

```python
# Ejemplo iterando a través de la lista
for year in dates:  
    print(year) 
```

Otros usos de bucles for:

```python
# Usar bucle for para cambiar los elementos en la lista
squares = ['red', 'yellow', 'green', 'purple', 'blue']

for i in range(0, 5):
    print("Before square ", i, 'is',  squares[i])
    squares[i] = 'white'
    print("After square ", i, 'is',  squares[i])
    
    
# Iterar a través de la lista e iterar en ambos índice y valor del elemento 
# La función enumerate()
squares=['red', 'yellow', 'green', 'purple', 'blue']

for i, square in enumerate(squares):
    print(i, square)
```

## Bucles `while`

Como puedes ver, el bucle `for` se usa para un flujo controlado de repetición. Sin embargo, ¿qué pasa si no sabemos cuándo queremos detener el bucle? ¿Qué pasa si queremos seguir ejecutando un bloque de código hasta que se cumpla una cierta condición? El bucle `while` existe como una herramienta para ejecución repetida basada en una condición. El bloque de código seguirá siendo ejecutado hasta que la condición lógica dada devuelva un valor booleano **False**.

```python
#Ejemplo
dates = [1982, 1980, 1973, 2000]

i = 0
year = dates[0]

while(year != 1973):    
    print(year)
    i = i + 1 # lo mismo que i += 1
    year = dates[i]
    

print("It took ", i ,"repetitions to get out of loop.")
#Output: 
#1982
#1980
#It took  2 repetitions to get out of loop.
```

Un bucle while itera simplemente hasta que la condición en el argumento no se cumple

```python
#Este bucle while copia las cadenas 'orange' de la lista squares a la lista new_squares. 
#El bucle se detiene y sale si el valor en la lista no es 'orange' 

squares = ['orange', 'orange', 'purple', 'blue ', 'orange']
new_squares = []
i = 0
while(i < len(squares) and squares[i] == 'orange'):
    new_squares.append(squares[i])
    i += 1
print (new_squares)

#output: ['orange', 'orange']
```