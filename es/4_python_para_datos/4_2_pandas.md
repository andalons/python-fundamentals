# 4.2 Pandas

## Introducción

Pandas es una popular biblioteca de código abierto para manipulación y análisis de datos para el lenguaje de programación Python. Proporciona un conjunto poderoso y flexible de herramientas para trabajar con datos estructurados, haciéndolo una herramienta fundamental para científicos de datos, analistas e ingenieros.

### Características y funcionalidades clave

### Estructuras de datos

Pandas ofrece dos estructuras de datos primarias: **DataFrames y Series**.

- Un **DataFrame** es una estructura de datos tabular bidimensional, de tamaño mutable y potencialmente heterogénea con ejes etiquetados (filas y columnas).
    - Un Pandas DataFrame será creado cargando los datasets desde almacenamiento existente.
    - El almacenamiento puede ser Base de Datos SQL, archivo CSV, archivo Excel, etc.
    - También puede ser creado desde listas, diccionarios, y desde una lista de diccionarios.
- Una **Series** es un arreglo etiquetado unidimensional, esencialmente una sola columna o fila de datos. Tiene dos componentes principales:
    - Un arreglo de datos reales.
    - Un arreglo asociado de índices o etiquetas de datos.
    
    El índice se usa para acceder a valores de datos individuales. También puedes obtener una columna de un dataframe como una **Series**. Puedes pensar en una Pandas series como un dataframe 1-D.
    

### **Importación y Exportación de Datos**

Pandas facilita leer datos desde varias fuentes, incluyendo archivos CSV, hojas de cálculo Excel, bases de datos SQL, y más. También puede exportar datos a estos formatos, habilitando intercambio de datos sin problemas.

### **Fusión y Unión de Datos**

Puedes combinar múltiples DataFrames usando métodos como merge y join, similar a operaciones SQL, para crear datasets más complejos desde diferentes fuentes.

### Indexación Eficiente

Pandas proporciona métodos eficientes de indexación y selección, permitiéndote acceder a filas y columnas específicas de datos rápidamente.

### **Estructuras de Datos Personalizadas**:

Puedes crear estructuras de datos personalizadas y manipular datos de maneras que se ajusten a tus necesidades específicas, extendiendo las capacidades de Pandas.

## Importando Pandas y Cargando datos

```python
import pandas
# Después de importar la biblioteca, tienes acceso a un gran  
# número de clases y funciones pre-construidas, como read_csv(), 
# DataFrame...
```

![Captura de pantalla 2024-12-16 a las 11.40.22.png](../../img/Captura_de_pantalla_2024-12-16_a_las_11.40.22.png)

```python
import pandas as pd
# Usa la declaración as para acortar el nombre de la biblioteca
# pd es la abreviatura estándar
```

### `read_csv()`

Es una **función a nivel de módulo de pandas** usada para cargar un archivo CSV en un pandas DataFrame. Lee el archivo, infiere la estructura, y permite opciones adicionales como especificar nombres de columna, manejar valores faltantes, o personalizar el delimitador.

```python
import pandas as pd
csv_path='file1.csv'
df = pd.read_csv(csv_path)
```

## **Seleccionando datos con Pandas: DataFrame y Series**

### Pandas Series

Una Series es una estructura similar a arreglo unidimensional que contiene datos junto con un índice asociado.

**Características**:

- Es esencialmente una columna de datos.
- Tiene solo un eje: una sola lista de valores con un índice.
- Puede contener datos de cualquier tipo (enteros, cadenas, flotantes, etc.).
- Piensa en ella como similar a una lista de Python o un diccionario donde las claves son el índice.

```python
import pandas as pd

# Creando una Series
s = pd.Series([10, 20, 30, 40], index=["a", "b", "c", "d"])
print(s)
```

```markdown
Output: 

a    10
b    20
c    30
d    40
dtype: int64
```

### Pandas DataFrame

Un DataFrame es una estructura de datos tabular bidimensional que puede contener múltiples Series como columnas.

**Características**:

- Tiene dos ejes: filas y columnas.
- Cada columna en un DataFrame es una Series, pero un DataFrame puede contener múltiples Series de diferentes tipos de datos.
- A menudo usado para representar datos estructurados, como una tabla en una base de datos o una hoja de cálculo.

```python
# Creando un DataFrame
df = pd.DataFrame({
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35],
    "Salary": [50000, 60000, 70000]
})
print(df)
```

```markdown
Output:

     Name  Age  Salary
0   Alice   25   50000
1     Bob   30   60000
2  Charlie   35   70000

```

### Creando un DataFrame desde un diccionario:

```python
# importa la Biblioteca Pandas
import pandas as pd

#Define un diccionario 'x'
x = {'Name': ['Rose','John', 'Jane', 'Mary'], 'ID': [1, 2, 3, 4], 'Department': ['Architect Group', 'Software Group', 'Design Team', 'Infrastructure'], 
      'Salary':[100000, 80000, 50000, 60000]}

#convirtiendo el diccionario a un DataFrame
df = pd.DataFrame(x)
```

![Captura de pantalla 2024-12-16 a las 8.10.24.png](../../img/Captura_de_pantalla_2024-12-16_a_las_8.10.24.png)

### Selección de columna

```python
# Recuperando la columna "ID" y asignándola a una variable x
x = df[['ID']]
x

# verificar el tipo de x
type(x) #output: pandas.core.frame.DataFrame

# Acceso a múltiples columnas
z = df[['Department','Salary','ID']]
z

# Para ver la columna como una series, solo usa un bracket:
x = df['Name']
x
```

![Captura de pantalla 2024-12-16 a las 8.13.28.png](../../img/Captura_de_pantalla_2024-12-16_a_las_8.13.28.png)

![Captura de pantalla 2024-12-16 a las 8.15.25.png](../../img/Captura_de_pantalla_2024-12-16_a_las_8.15.25.png)

![Captura de pantalla 2024-12-16 a las 8.25.47.png](../../img/Captura_de_pantalla_2024-12-16_a_las_8.25.47.png)

### **Atributos de DataFrame**

Los atributos son propiedades de un DataFrame que pueden ser accedidas sin paréntesis (`()`).

- **Información General**
    - **`shape`**: Tupla representando las dimensiones del DataFrame `(filas, columnas)`.
    - **`size`**: Número total de elementos en el DataFrame (`filas × columnas`).
    - **`ndim`**: Número de dimensiones (siempre `2` para DataFrames).
    - **`empty`**: Booleano indicando si el DataFrame está vacío.
- **Etiquetas y ejes**
    - **`index`**: Las etiquetas de fila (objeto Index) del DataFrame.
    - **`columns`**: Las etiquetas de columna (objeto Index) del DataFrame.
    - **`axes`**: Una lista de las etiquetas de fila y columna: `[index, columns]`.
- **Tipos de datos y memoria**
    - **`dtypes`**: Tipos de datos de cada columna como una pandas Series.
    - **`memory_usage`**: Uso de memoria de cada columna, opcionalmente incluyendo el índice.
- **Valores de datos**
    - **`values`**: Los datos subyacentes del DataFrame como un arreglo NumPy.
- **Metadatos**
    - **`attrs`**: Diccionario para almacenar metadatos personalizados sobre el DataFrame (ej. `df.attrs = {"source": "dataset"}`).
- **Columnas Categóricas** (Estos son aplicables si una columna es de tipo `category`.)
    - **`categories`**: Las categorías en una columna categórica.
    - **`ordered`**: Booleano indicando si los datos categóricos están ordenados.

### **Métodos de DataFrame**

Los métodos son acciones que puedes realizar en un DataFrame y requieren paréntesis (`()`). Algunos de ellos son:

- **Información General**
    - **`info()`**: Muestra un resumen del DataFrame, incluyendo tipos de datos y conteos no nulos.
    - **`describe()`**: Genera estadísticas resumen para columnas numéricas.
    - **`head(n)`**: Devuelve las primeras `n` filas del DataFrame (por defecto `n=5`).
    - **`tail(n)`**: Devuelve las últimas `n` filas del DataFrame (por defecto `n=5`).
- **Índice y Columnas**
    - **`set_index()`**: Establece una columna como el índice.
    - **`reset_index()`**: Resetea el índice al índice entero por defecto.
    - **`rename()`**: Renombra columnas o etiquetas de índice.
    - **`sort_index()`**: Ordena el DataFrame por su índice.
    - **`sort_values()`**: Ordena el DataFrame por los valores de una o más columnas.
- **Selección y Filtrado**
    - **`loc[]`**: Accede filas y columnas por etiqueta o condición (atributo, no método).
    - **`iloc[]`**: Accede filas y columnas por posición entera (atributo, no método).
    - **`query()`**: Consulta el DataFrame usando una expresión de cadena.
    - **`filter()`**: Filtra columnas basado en etiquetas o condiciones.
- **Manipulación de Datos**
    - **`apply()`**: Aplica una función a lo largo de un eje (filas o columnas).
    - **`applymap()`**: Aplica una función elemento por elemento.
    - **`agg()` / `aggregate()`**: Realiza operaciones de agregación en columnas o filas.
    - **`groupby()`**: Agrupa datos para agregación o transformación.
    - **`pivot()`**: Pivotea un DataFrame reorganizando sus filas y columnas.
    - **`pivot_table()`**: Crea una tabla pivote con agregación.
    - **`melt()`**: Despivotea un DataFrame de formato ancho a largo.
    - **`stack()`**: Apila columnas en una sola columna (multi-índice).
    - **`unstack()`**: Desapila filas en columnas (multi-índice).
    - **`join()`**: Une columnas de otro DataFrame basado en el índice.
    - **`merge()`**: Fusiona dos DataFrames basado en claves o índices.
    - **`concat()`**: Concatena múltiples DataFrames a lo largo de filas o columnas.
- **Datos Faltantes**
    - **`isna()` / `isnull()`**: Devuelve un DataFrame indicando valores faltantes (`True`).
    - **`notna()` / `notnull()`**: Devuelve un DataFrame indicando valores no faltantes.
    - **`fillna()`**: Reemplaza valores faltantes con un valor especificado.
    - **`dropna()`**: Remueve filas o columnas con valores faltantes.
    - **`interpolate()`**: Llena valores faltantes usando interpolación.
- **Estadísticas**
    - **`sum()`**: Calcula la suma de valores para cada columna o fila.
    - **`mean()`**: Calcula la media de valores.
    - **`median()`**: Calcula la mediana de valores.
    - **`std()`**: Calcula la desviación estándar de valores.
    - **`var()`**: Calcula la varianza de valores.
    - **`min()`**: Devuelve el valor mínimo para cada columna o fila.
    - **`max()`**: Devuelve el valor máximo.
    - **`count()`**: Cuenta valores no nulos.
    - **`cumsum()`**: Calcula la suma acumulativa.
    - **`cumprod()`**: Calcula el producto acumulativo.
- **Visualización**
    - **`plot()`**: Genera gráficos básicos (línea, barra, histograma, etc.) para columnas de DataFrame.
    - **`hist()`**: Crea un histograma para columnas numéricas.
- **Operaciones de Cadena**(Estos métodos están disponibles a través del accesor `.str` para columnas de cadena.)
    - **`str.contains()`**: Verifica si una cadena contiene una subcadena específica.
    - **`str.replace()`**: Reemplaza subcadenas con otra cadena.
    - **`str.split()`**: Divide cadenas en listas basado en un delimitador.
- **Exportando e Importando Datos**
    - **`to_csv()`**: Exporta el DataFrame a un archivo CSV.
    - **`to_excel()`**: Exporta el DataFrame a un archivo Excel.
    - **`to_json()`**: Exporta el DataFrame a un archivo JSON.
    - **`to_sql()`**: Exporta el DataFrame a una base de datos SQL.

### `loc()` y `iloc()`

- `loc()` es un método de selección de datos basado en etiquetas lo que significa que tenemos que pasar el nombre de la fila o columna que queremos seleccionar. Este método incluye el último elemento del rango pasado en él.
    
    **Sintaxis**: `loc[row_label, column_label]`
    
- `iloc()` es un método de selección indexado lo que significa que tenemos que pasar un índice entero en el método para seleccionar una fila/columna específica. Este método no incluye el último elemento del rango pasado en él.
    
    **Sintaxis**: `iloc[row_index, column_index]`
    

```python
# Acceder al valor en la primera fila y la primera columna
df.**iloc**[0, 0]

# Acceder al valor en la primera fila y la tercera columna
df.**iloc**[0,2]

# Acceder a la columna usando el nombre
df.**loc**[0, 'Salary']
```

### `set_index()` y `head()`

```python
df2=df
# establecer la columna "Name" como una columna índice usando el método set_index()
df2=df2.**set_index**("Name")

#Para mostrar las primeras 5 filas del nuevo dataframe
df2.**head**()
```

### Segmentación

La segmentación usa el operador [] para seleccionar un conjunto de filas y/o columnas de un DataFrame.

Para segmentar un conjunto de filas, usas esta sintaxis: `data[start:stop]` donde start representa el índice desde donde considerar, y stop representa el índice un paso más allá de la fila que quieres seleccionar. Puedes realizar segmentación usando tanto el índice como el nombre de la columna.

> **NOTA**: Cuando segmentas en pandas, el límite start está incluido en la salida. Así que si quieres seleccionar filas 0, 1, y 2 tu código se vería así: `df.iloc[0:3]`. Con `loc()`, tanto el límite start como el stop son inclusivos. Cuando usas `loc()`, enteros pueden ser usados, pero los enteros se refieren a la etiqueta del índice y no a la posición. Usando `loc()` y seleccionar 1:4 obtendrá un resultado diferente que usando `iloc()` para seleccionar filas 1:4.
> 

![Captura de pantalla 2024-12-16 a las 9.10.41.png](../../img/Captura_de_pantalla_2024-12-16_a_las_9.10.41.png)

```python
# 1. segmentación usando el viejo dataframe df
df.**iloc**[0:2, 0:3]

# 2. segmentación usando función loc() en el viejo dataframe df donde la columna índice tiene etiquetas como 0,1,2
df.**loc**[0:2,'ID':'Department']

# 3. segmentación usando función loc() en el nuevo dataframe df2 donde la columna índice es Name teniendo etiquetas: Rose, John y Jane
df2.**loc**['Rose':'Jane', 'ID':'Department']
```

![Output 1.](../../img/Captura_de_pantalla_2024-12-16_a_las_9.15.41.png)

Output 1.

![Output 2.](../../img/Captura_de_pantalla_2024-12-16_a_las_9.15.50.png)

Output 2.

![Output 3.](../../img/Captura_de_pantalla_2024-12-16_a_las_9.16.11.png)

Output 3.