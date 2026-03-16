# 2.4 Conjuntos {} (sin duplicados)

- Un conjunto es una colección única de objetos en Python. Puedes denotar un conjunto con un par de llaves **{}**. Python automáticamente eliminará elementos duplicados:
    
    ![Esta figura ilustra el proceso de mapeo.](../../img/Captura_de_pantalla_2024-12-12_a_las_8.48.23.png)
    
    Esta figura ilustra el proceso de mapeo.
    

```python
# Convertir lista a conjunto (**typecasting**)
album_list = [ "Michael Jackson", "Thriller", 1982, "00:42:19", \
              "Pop, Rock, R&B", 46.0, 65, "30-Nov-82", None, 10.0]
album_set = set(album_list)             
album_set

**# Operaciones de Conjunto**
A = set(["Thriller", "Back in Black", "AC/DC"])
A #output: {'AC/DC', 'Back in Black', 'Thriller'}

# Agregar elemento al conjunto usando el método **add()**:
A.**add**("NSYNC") #output: {'AC/DC', 'Back in Black', 'NSYNC', 'Thriller'}

# Remover el elemento del conjunto con el método **remove()**:
A.**remove**("NSYNC") #output: {'AC/DC', 'Back in Black', 'Thriller'}

# **Verificar** si el elemento está en el conjunto
"AC/DC" **in** A #output: True
```

- Con los conjuntos puedes verificar la diferencia entre conjuntos, así como la **diferencia simétrica**, **intersección**, y **unión**:
    
    
    ![Diferencia](../../img/Captura_de_pantalla_2024-12-12_a_las_9.04.23.png)
    
    Diferencia
    
    ![Intersección](../../img/Captura_de_pantalla_2024-12-12_a_las_9.08.55.png)
    
    Intersección
    
    ![Diferencia](../../img/Captura_de_pantalla_2024-12-12_a_las_9.04.36.png)
    
    Diferencia
    
    ![Unión](../../img/Captura_de_pantalla_2024-12-12_a_las_9.09.55.png)
    
    Unión
    

```python
# **Operaciones Lógicas de Conjuntos**
album_set1 = set(["Thriller", 'AC/DC', 'Back in Black'])
album_set2 = set([ "AC/DC", "Back in Black", "The Dark Side of the Moon"])

# Encontrar las **intersecciones**
intersection = album_set1 **&** album_set2
intersection #output: {'AC/DC', 'Back in Black'}

# También puedes usar el método **intersection** 
album_set1.intersection(album_set2) #output: {'AC/DC', 'Back in Black'}

# Encontrar los elementos que están contenidos solo en un conjunto **usando el método difference**
album_set1.**difference**(album_set2) #output: {'Thriller'}
album_set2.**difference**(album_set1) #output: {'The Dark Side of the Moon'}

# Encontrar la unión de dos conjuntos usando el método **union**
album_set1.**union**(album_set2) #output:{'AC/DC', 'Back in Black', 'The Dark Side of the Moon', 'Thriller'}

****# Verificar si es superconjunto
album_set1.**issuperset**(album_set2) #output: False
album_set1.**issuperset**({"Back in Black", "AC/DC"}) #output: True

# Verificar si es subconjunto
album_set2.**issubset**(album_set1) #output: False
set({"Back in Black", "AC/DC"}).**issubset**(album_set1) #output: True 

****
```