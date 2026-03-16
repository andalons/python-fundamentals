# 1.1 Tipos

## Cadenas, enteros y flotantes

Python es un lenguaje orientado a objetos. Hay muchos tipos diferentes de objetos en Python. Empecemos con los tipos de objetos más comunes: **cadenas**, **enteros** y **flotantes**. 

Cada vez que escribes palabras (texto) en Python, estás usando cadenas de caracteres (cadenas para abreviar). Los números más comunes, por otro lado, son enteros (ej. -1, 0, 100) y flotantes, que representan números reales (ej. 3.14, -42.0).

```python
# Entero
11

# Flotante
2.14

# Cadena
"Hello, world"
```

## La función type()

Puedes hacer que Python te diga el tipo de una expresión usando la función incorporada `type()`. Notarás que Python se refiere a los enteros como `int`, a los flotantes como `float`, y a las cadenas de caracteres como `str`.

## Conversión de tipos

Puedes cambiar el tipo del objeto en Python; esto se llama **conversión de tipos**. 

- Puedes convertir un entero en un flotante (ej. 2 a 2.0): `float(2)` → `2.0`
- Cuando convertimos un entero en un flotante, no cambiamos realmente el valor (es decir, el significando) del número. Sin embargo, si convertimos un flotante en un entero, podríamos perder información. Por ejemplo, si convertimos el flotante 1.6 a entero obtendremos 1 y perderemos la información decimal (es decir, 0.6): `int(1.6)` → `1`
- A veces, podemos tener una cadena que contiene un número dentro de ella. Si este es el caso, podemos convertir esa cadena que representa un número en un entero usando int(): `int('2')` → `2`
- Puedes hacer lo mismo con flotantes: `float('1.2')` → `1.2`
- Si intentas hacer esto con una cadena que no es una coincidencia perfecta para un int o un float, obtendrás un error: `int('1 or 2')` → `error`

## Tipo de dato booleano

Booleano es otro tipo importante en Python. Un objeto de tipo Booleano puede tomar uno de dos valores: `True` o `False` (usando la T y F mayúsculas)

- `int(True)` → 1
- `bool(1)` → `True`
- `bool(0)` → `False`
- `float(True)`→ `1.0`