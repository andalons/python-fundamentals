# 2.2 Listas []

- Una lista es también una colección secuenciada de objetos.
- Las listas pueden contener cadenas, flotantes e enteros. Podemos anidar otras listas, y también podemos anidar tuplas y otras estructuras de datos, como enteros, cadenas e incluso otras listas. La dirección de cada elemento dentro de una lista se llama **índice**. Un índice se usa para acceder y referirse a elementos dentro de una lista.
    
    ```python
    # Lista de ejemplo
    ["Michael Jackson", 10.1, 1982, [1, 2], ("A", 1)]
    ```
    

- Diferencia clave con las tuplas: las listas son **mutables**.
- Las mismas convenciones de indexación aplican para anidamiento.

```python
List1=[1, 2.2, "hello"]
type(List1)= list

**# Segmentación de listas**
L[3:5]

**#Las listas son mutables**
A=["disco", 10]
A[0]="hard rock" #output A: ["hard rock", 10]
**del**(A[1]) #eliminará 10 de la lista

# **Dividir** la cadena, por defecto por espacio
'hard rock'.**split**() #output: ['hard', 'rock']
# **Dividir** la cadena por coma
'A,B,C,D'.**split**(',')#output: ['A', 'B', 'C', 'D']

**#Métodos de lista:**
L=["Andrea", 7.2, 1992]
#**extend**: agregar varios nuevos elementos a la lista
L.**extend**(["music", 10]) #output L: ["Andrea", 7.2, 1992, "music", 10]
#**append** (agrega solo un elemento: agregar solo un elemento 
L.**append**(["pop", 7]) #output L: ["Andrea", 7.2, 1992, "music", 10, ["pop", 7]]
```

- **Alias**: múltiples nombres refiriéndose al mismo objeto se conoce como aliasing. Cuando establecemos una variable **B** igual a **A**, tanto **A** como **B** están referenciando la misma lista en memoria:
    
    ![A y B están referenciando la misma lista, por lo tanto si cambiamos A, la lista B también cambia.](../../img/Captura_de_pantalla_2024-12-11_a_las_9.12.46.png)
    
    A y B están referenciando la misma lista, por lo tanto si cambiamos A, la lista B también cambia.
    
- **Clonación**: Sintaxis `B = A[:]`
    
    ![La variable A referencia una lista. La variable B referencia una nueva copia o clon de la lista original. Ahora si cambias A, B no cambiará. ](../../img/Captura_de_pantalla_2024-12-11_a_las_9.14.28.png)
    
    La variable A referencia una lista. La variable B referencia una nueva copia o clon de la lista original. Ahora si cambias A, B no cambiará. 
    
- **Uso**: Típicamente se usan cuando necesitas una colección que cambia con el tiempo (ej. una lista de tareas).