# 4.3 NumPy

## Introducción

NumPy es una biblioteca de Python utilizada para trabajar con arreglos, álgebra lineal, transformada de Fourier y matrices. NumPy significa Numerical Python y es un proyecto de código abierto.

## El objeto arreglo en NumPy

El objeto arreglo en NumPy se llama **ndarray**, proporciona muchas funciones de soporte que hacen que trabajar con ndarray sea muy fácil.

Los arreglos se usan muy frecuentemente en ciencia de datos, donde la velocidad y los recursos son muy importantes.

NumPy usualmente se importa bajo el alias `np`.

Usualmente es de tamaño fijo y cada elemento es del mismo tipo. Podemos convertir una lista a un arreglo numpy importando primero `numpy`:

```python
# importa la biblioteca numpy

import numpy as np 

# Crea un arreglo numpy

a = np.array([0, 1, 2, 3, 4])
a #output: array([0, 1, 2, 3, 4])
```

![Cada elemento es del mismo tipo (en este caso enteros)](../../img/Captura_de_pantalla_2024-12-17_a_las_16.14.09.png)

Cada elemento es del mismo tipo (en este caso enteros)

```python
# Como con las listas, puedes acceder a cada elemento vía corchetes:

print("a[0]:", a[0])
print("a[1]:", a[1])
print("a[2]:", a[2])
print("a[3]:", a[3])
print("a[4]:", a[4])
```

```python
# Verifica el tipo del arreglo: obtenemos numpy.ndarray
type(a)

# podemos usar el atributo "dtype" para obtener el tipo de datos de los elementos del arreglo
a.dtype #output: dtype('int32')
```

### Asignando valores y segmentación

```python
# Crea arreglo numpy
c = np.array([20, 1, 2, 3, 4])

# Asigna el primer elemento a 100
c[0] = 100
c #output: array([100,   1,   2,   3,   4])
```

```python
# Segmentando el arreglo numpy
d = c[1:4]
d #output: array([1, 2, 3])

# Establece el cuarto y quinto elemento a 300 y 400
c[3:5] = 300, 400
c #output array([100,   1,   2, 300, 400])
```

También podemos definir los pasos en la segmentación, como esto: `[start:end:step]`:

- **`start`**: El índice donde comienza el segmento (inclusivo). Si no pasamos start se considera 0
- **`end`**: El índice donde termina el segmento (exclusivo). Si no pasamos end se considera hasta la longitud del arreglo.
- **`step`**: El intervalo entre cada índice. Si no pasamos step se considera 1

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[1:5:2]) #output: [2 4]
print(arr[1:6:2]) #output: [2 4 6]
print(arr[:4]) #output: [1 2 3 4]
print(arr[4:]) #output: [5 6 7]
print(arr[1:5:]) #output: [2 3 4 5]
```

### Asignando valor con Lista

Similarmente, podemos usar una lista para seleccionar más de un índice específico.

```python
# Crea la lista de índices
select = [0, 2, 3, 4]
select #output: [0, 2, 3, 4]

# Usa Lista como argumento en corchetes
d = c[select]

```

### Otros atributos

```python
# Crea un arreglo numpy
a = np.array([0, 1, 2, 3, 4])

# Obtén el tamaño del arreglo numpy
a.size  #output: 5

# Obtén el número de dimensiones del arreglo numpy
a.ndim  #output: 1

# Obtén la forma/tamaño del arreglo numpy
a.shape #output: (5,)
```

### Funciones Estadísticas de NumPy

```python
# Crea un arreglo numpy
a = np.array([1, -1, 1, -1])

# Obtén la media del arreglo numpy
mean = a.mean()

# Obtén la desviación estándar del arreglo numpy
standard_deviation=a.std()

# Obtén el valor más grande en el arreglo numpy
max_a = a.max()

# Obtén el valor más pequeño en el arreglo numpy
min_a = a.min()
```

### Operaciones de Arreglos 1D de NumPy

```python
u = np.array([1, 0])
v = np.array([0, 1])

**# Adición de Arreglos Numpy**
z = np.add(u, v) #output: array([1, 1])
```

```python
**# Funciones de graficación**

import time 
import sys
import numpy as np 

import matplotlib.pyplot as plt

def Plotvec1(u, z, v):
    
    ax = plt.axes() # para generar los ejes de la ventana completa
    ax.arrow(0, 0, *u, head_width=0.05, color='r', head_length=0.1)# Agrega una flecha a los Ejes U con ancho de cabeza de flecha 0.05, color rojo y longitud de cabeza de flecha 0.1
    plt.text(*(u + 0.1), 'u')#Agrega el texto u a los Ejes 
    
    ax.arrow(0, 0, *v, head_width=0.05, color='b', head_length=0.1)# Agrega una flecha a los Ejes v con ancho de cabeza de flecha 0.05, color rojo y longitud de cabeza de flecha 0.1
    plt.text(*(v + 0.1), 'v')#Agrega el texto v a los Ejes 
    
    ax.arrow(0, 0, *z, head_width=0.05, head_length=0.1)
    plt.text(*(z + 0.1), 'z')#Agrega el texto z a los Ejes 
    plt.ylim(-2, 2)#establece el ylim a inferior(-2), superior(2)
    plt.xlim(-2, 2)#establece el xlim a izquierda(-2), derecha(2)

# Grafica arreglos numpy

Plotvec1(u, z, v)
```

![Captura de pantalla 2024-12-17 a las 16.47.21.png](../../img/Captura_de_pantalla_2024-12-17_a_las_16.47.21.png)

```python
**# Sustracción de Arreglos**

a = np.array([10, 20, 30])
b = np.array([5, 10, 15])

c = np.subtract(a, b)
print(c) #output: [ 5 10 15]
```

```python
**# Multiplicación de Arreglos** 

x = np.array([1, 2])
y = np.array([2, 1])

z = np.multiply(x, y)
```

```python
**# División de Arreglos**

z = np.divide(x, y)
```

```python
**# Producto punto de Arreglos**

X = np.array([1, 2])
Y = np.array([3, 2])

np.dot(X,Y) #output: 7
```

El **producto punto** es una operación matemática que toma dos vectores del mismo tamaño y devuelve un solo escalar (número):

![Captura de pantalla 2024-12-17 a las 16.57.43.png](../../img/Captura_de_pantalla_2024-12-17_a_las_16.57.43.png)

```python
# **Agregando una constante**: 

u = np.array([1, 2, 3, -1]) 
u + 1 #output: array([2, 3, 4, 0]) agrega 1 a cada elemento en el arreglo

```

### Funciones matemáticas

```python
**# El valor de pi**
np.pi

**# El arreglo numpy en radianes**
x = np.array([0, np.pi/2 , np.pi])
```

Podemos aplicar la función `sin` al arreglo `x` y asignar los valores al arreglo `y`; esto aplica la función seno a cada elemento en el arreglo:

```python
**# El seno de cada elemento**
y = np.sin(x)
```

![Captura de pantalla 2024-12-17 a las 17.08.17.png](../../img/Captura_de_pantalla_2024-12-17_a_las_17.08.17.png)

La función seno es una función trigonométrica que funciona en ángulos (en radianes) y produce valores entre -1 y 1.

```python
**# Función Linespace**

# Una función útil para graficar funciones matemáticas
# Linspace devuelve números espaciados uniformemente sobre un intervalo especificado

**# Sintaxis:**
# numpy.linspace(start, stop, num = int value)
# start  :  inicio del rango de intervalo
# stop   :  fin del rango de intervalo
# num    :  Número de muestras a generar.

# Crea un arreglo numpy dentro de [-2, 2] y 5 elementos
np.linspace(-2, 2, num=5)
# array([-2., -1.,  0.,  1.,  2.])

# Crea un arreglo numpy dentro de [-2, 2] y 9 elementos
np.linspace(-2, 2, num=9)
# array([-2. , -1.5, -1. , -0.5,  0. ,  0.5,  1. ,  1.5,  2. ])

# Crea un arreglo numpy dentro de [0, 2π] y 100 elementos 
x = np.linspace(0, 2*np.pi, num=100)
# Calcula el seno de la lista x
y = np.sin(x)
# Grafica el resultado
plt.plot(x, y)
```

![Captura de pantalla 2024-12-17 a las 17.16.18.png](../../img/Captura_de_pantalla_2024-12-17_a_las_17.16.18.png)

### Iterando arreglos 1D

```python
arr1 = np.array([1, 2, 3])
for x in arr1:
  print(x)
```

## Arreglos NumPy Bidimensionales

```python

# Importa las bibliotecas
import numpy as np

# Crea una lista
a = [[11, 12, 13], [21, 22, 23], [31, 32, 33]]

# Convierte lista a Arreglo Numpy: cada elemento es del mismo tipo
A = np.array(a)

# Muestra las dimensiones del arreglo numpy
# Usa el atributo ndim para obtener el número de ejes o dimensiones, referido como el rango.
A.ndim  #output: 2

# Muestra la forma del arreglo numpy
# Devuelve una tupla correspondiente al tamaño o número de cada dimensión
A.shape  #output: (3, 3)

# Muestra el tamaño del arreglo numpy: el número total de elementos en el arreglo
A.size  #output: 9
```

### Accediendo a diferentes elementos de un arreglo numpy 2D:

![Captura de pantalla 2024-12-18 a las 7.42.19.png](../../img/Captura_de_pantalla_2024-12-18_a_las_7.42.19.png)

![Captura de pantalla 2024-12-18 a las 7.42.31.png](../../img/Captura_de_pantalla_2024-12-18_a_las_7.42.31.png)

```python
# Usamos los corchetes y los índices correspondientes al elemento que queremos:
A[1, 2]

# También podemos usar la siguiente notación 
A[1][2]

# Output: 23 para ambos
```

### Segmentación en un arreglo numpy 2D:

![Captura de pantalla 2024-12-18 a las 7.46.14.png](../../img/Captura_de_pantalla_2024-12-18_a_las_7.46.14.png)

![Captura de pantalla 2024-12-18 a las 7.46.26.png](../../img/Captura_de_pantalla_2024-12-18_a_las_7.46.26.png)

```python
# Accede al elemento en la primera fila y primera y segunda columnas
A[0][0:2] #output: array([11, 12])

A[0:2, 2] #output: array([13, 23])
```

### Operaciones básicas

![Sumando](../../img/Captura_de_pantalla_2024-12-18_a_las_7.48.02.png)

Sumando

![Multiplicando por un escalar](../../img/Captura_de_pantalla_2024-12-18_a_las_7.50.02.png)

Multiplicando por un escalar

![La multiplicación de dos arreglos corresponde a un producto elemento por elemento o ***Producto Hadamard***. Considera la matriz `X` y `Y`. El producto Hadamard corresponde a multiplicar cada uno de los elementos en la misma posición, es decir, multiplicando elementos contenidos en las mismas cajas de color juntas. El resultado es una nueva matriz que es del mismo tamaño que la matriz `Y` o `X`, como se muestra en la siguiente figura](../../img/Captura_de_pantalla_2024-12-18_a_las_7.50.33.png)

La multiplicación de dos arreglos corresponde a un producto elemento por elemento o ***Producto Hadamard***. Considera la matriz `X` y `Y`. El producto Hadamard corresponde a multiplicar cada uno de los elementos en la misma posición, es decir, multiplicando elementos contenidos en las mismas cajas de color juntas. El resultado es una nueva matriz que es del mismo tamaño que la matriz `Y` o `X`, como se muestra en la siguiente figura

También podemos realizar **multiplicación de matrices** con los arreglos numpy `A` y `B` como sigue:

![Captura de pantalla 2024-12-18 a las 7.56.32.png](../../img/Captura_de_pantalla_2024-12-18_a_las_7.56.32.png)

![Captura de pantalla 2024-12-18 a las 7.57.19.png](../../img/Captura_de_pantalla_2024-12-18_a_las_7.57.19.png)

```python
# Crea una matriz A
A = np.array([[0, 1, 1], [1, 0, 1]])

# Crea una matriz B
B = np.array([[1, 1], [1, 1], [-1, 1]])

# Calcula el producto punto
Z = np.dot(A,B)
Z # Output:
# array([[0, 2],
#       [0, 2]])

# Calcula el seno de Z
np.sin(Z)
```

```python
# # Obtén la transpuesta de C usando el atributo T

C = np.array([[1,1],[2,2],[3,3]])
C # Output:
# array([[1, 1],
#        [2, 2],
#        [3, 3]])

C.T # Output:
# array([[1, 2, 3],
#        [1, 2, 3]])
```
