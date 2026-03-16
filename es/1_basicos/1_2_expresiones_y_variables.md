# 1.2 Expresiones y Variables

## **Expresiones**

Las expresiones en Python pueden incluir operaciones entre tipos compatibles (ej. enteros y flotantes).

Por ejemplo, operaciones aritméticas básicas:

- Suma: `43 + 60 + 16 + 41`
- Resta: `50 - 60`
- División: `6 / 2`
- División entera: `6 // 2`

## Variables

Al igual que con la mayoría de los lenguajes de programación, podemos almacenar valores en *variables*, para usarlos más tarde.

Por ejemplo:

```python
# Almacenar valor en variable
x = 43 + 60 + 16 + 41

# Imprimir el valor en la variable
x

# Usar otra variable para almacenar el resultado de la operación entre variable y valor
y = x / 60
y

# Sobrescribir variable con nuevo valor
x = x / 60
x
```

Es importante nombrar las variables de manera significativa:

```python
total_min = 43 + 42 + 57 # Longitud total de álbumes en minutos
total_min

total_hours = total_min / 60 # Longitud total de álbumes en horas 
total_hours
```

En las celdas anteriores, sumamos la longitud de tres álbumes en minutos y la almacenamos en `total_min`. Luego la dividimos por 60 para calcular la longitud total (`total_hours`) en horas.

También puedes hacerlo todo de una vez en una sola expresión, siempre y cuando uses paréntesis para sumar las longitudes de los álbumes antes de dividir, como se muestra a continuación:

```python
total_hours = (43 + 42 + 57) / 60  # Horas totales en una sola expresión
total_hours
```