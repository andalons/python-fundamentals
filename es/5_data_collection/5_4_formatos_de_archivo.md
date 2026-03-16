# 5.4 Trabajando con diferentes formatos de archivo

# Ingeniería de Datos

**La ingeniería de datos** es una de las habilidades más críticas y fundamentales en el conjunto de herramientas de cualquier científico de datos. Hay varios pasos en el **proceso de Ingeniería de Datos**.

1. **Extraer** - La extracción de datos consiste en obtener datos de múltiples fuentes. Ej. Extracción de datos de un sitio web usando web scraping o recopilar información de los datos que están almacenados en diferentes formatos (JSON, CSV, XLSX, etc.).
2. **Transformar** - Transformar los datos significa remover los datos que no necesitamos para análisis posterior y convertir los datos en el formato que todos los datos de las múltiples fuentes estén en el mismo formato.
3. **Cargar** - Cargar los datos dentro de un almacén de datos. Un almacén de datos esencialmente contiene grandes volúmenes de datos que se acceden para recopilar insights.

# Diferentes formatos de archivo

En el mundo real, la gente rara vez obtiene datos tabulares ordenados. Por lo tanto, es obligatorio para cualquier científico de datos (o ingeniero de datos) estar al tanto de diferentes formatos de archivo, desafíos comunes en manejarlos y las mejores formas más eficientes de manejar estos datos en la vida real. Hemos revisado parte de este contenido en otros módulos.

Un formato de archivo es una forma estándar en la que la información se codifica para almacenamiento en un archivo. Primero, el formato de archivo especifica si el archivo es binario o ASCII. Segundo, muestra cómo se organiza la información. Por ejemplo, el formato de archivo de valores separados por comas (CSV) almacena datos tabulares en texto plano.

Para identificar un formato de archivo, usualmente puedes mirar la extensión del archivo para tener una idea. Por ejemplo, un archivo guardado con nombre "Data" en formato "CSV" aparecerá como **Data.csv**. Hay varios formatos para un conjunto de datos: .csv, .json, .xlsx, etc.

## Formato de archivo de valores separados por comas (CSV)

El **formato de archivo de valores separados por comas** cae bajo un formato de archivo de hoja de cálculo.

En un formato de archivo de hoja de cálculo, los datos se almacenan en celdas. Cada celda se organiza en filas y columnas. Una columna en el archivo de hoja de cálculo puede tener diferentes tipos. Por ejemplo, una columna puede ser de tipo cadena, tipo fecha, o tipo entero. Cada línea en el archivo CSV representa una observación, o comúnmente llamada registro. Cada registro puede contener uno o más campos que están separados por una coma.

La **Biblioteca Pandas** es una herramienta útil que nos permite leer varios conjuntos de datos en un marco de datos de Pandas. Usamos la función **pandas.read_csv()** para leer el archivo csv. En los paréntesis, ponemos la ruta del archivo junto con una marca de comillas como argumento, para que pandas lea el archivo en un marco de datos desde esa dirección. La ruta del archivo puede ser una URL o tu dirección de archivo local.

```python
import piplite
await piplite.install(['seaborn', 'lxml', 'openpyxl'])

import pandas as pd
from pyodide.http import pyfetch

filename = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/addresses.csv"

async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

await download(filename, "addresses.csv")

df = pd.read_csv("addresses.csv", header=None)

df # Output:
```

![Captura de pantalla 2024-12-20 a las 12.13.42.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.13.42.png)

```python
# Adding column name to the DataFrame
df.columns =['First Name', 'Last Name', 'Location ', 'City','State','Area Code']

df # Output:
```

![Captura de pantalla 2024-12-20 a las 12.15.03.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.15.03.png)

```python
# Selecting a single column
df["First Name"]

df # Output:
```

![Captura de pantalla 2024-12-20 a las 12.15.58.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.15.58.png)

```python
# Selecting multiple columns
df = df[['First Name', 'Last Name', 'Location ', 'City','State','Area Code']]

df # Output:
```

![Captura de pantalla 2024-12-20 a las 12.16.41.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.16.41.png)

### **Seleccionando filas usando .iloc y .loc**

- **`loc()`:** es un método de selección de datos basado en etiquetas lo que significa que tenemos que pasar el nombre de la fila o columna que queremos seleccionar.
    
    ```python
    # To select the first row
    df.loc[0]
    
    # To select the 0th,1st and 2nd row of "First Name" column only
    df.loc[[0,1,2], "First Name" ]
    ```
    
- **`iloc()`:** es un método de selección indexado lo que significa que tenemos que pasar el índice entero en el método para seleccionar fila/columna específica.
    
    ```python
    # To select the 0th,1st and 2nd row of "First Name" column only
    df.iloc[[0,1,2], 0]
    ```
    

### Función Transform en Pandas

La función Transform de Python devuelve un marco de datos auto-producido con valores transformados después de aplicar la función especificada en su parámetro.

```python
#import library
import pandas as pd
import numpy as np

#creating a dataframe
df=pd.DataFrame(np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]]), columns=['a', 'b', 'c'])
df

#applying the transform function to add 10 to each element in the dataframe
df = df.transform(func = lambda x : x + 10)
df

#use transform function to find the square root to each element of the dataframe
result = df.transform(func = ['sqrt'])
```

![Captura de pantalla 2024-12-20 a las 12.27.21.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.27.21.png)

![Captura de pantalla 2024-12-20 a las 12.27.28.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.27.28.png)

![Captura de pantalla 2024-12-20 a las 12.27.42.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.27.42.png)

## Formato de archivo JSON

**JSON (JavaScript Object Notation)** es un formato de intercambio de datos ligero. Es fácil para humanos leer y escribir.

JSON está construido en dos estructuras:

1. Una colección de pares nombre/valor. En varios lenguajes, esto se realiza como un objeto, registro, struct, diccionario, tabla hash, lista claveada, o arreglo asociativo.
2. Una lista ordenada de valores. En la mayoría de lenguajes, esto se realiza como un arreglo, vector, lista, o secuencia.

JSON es un formato de datos independiente del lenguaje. Fue derivado de JavaScript, pero muchos lenguajes de programación modernos incluyen código para generar y analizar datos en formato JSON. Es un formato de datos muy común con una diversa gama de aplicaciones.

Python soporta JSON a través de un paquete incorporado llamado **json**. Para usar esta característica, importamos el paquete json en el script de Python.

Escribir JSON a un archivo usualmente se llama **serialización**. Es el proceso de convertir un objeto en un formato especial que es adecuado para transmitir sobre la red o almacenar en archivo o base de datos.

Para manejar el flujo de datos en un archivo, la biblioteca JSON en Python usa la función **dump()** o **dumps()** para convertir los objetos de Python en sus respectivos objetos JSON. Esto hace fácil escribir datos a archivos.

```python
import json
import json

person = {
    'first_name' : 'Mark',
    'last_name' : 'abc',
    'age' : 27,
    'address': {
        "streetAddress": "21 2nd Street",
        "city": "New York",
        "state": "NY",
        "postalCode": "10021-3100"
    }
}
```

### Serialización usando función dump()

El método **json.dump()** puede ser usado para escribir a archivo JSON.

Sintaxis: json.dump(dict, file_pointer)

Parámetros:

1. **dictionary** – nombre del diccionario que debería ser convertido a objeto JSON.
2. **file pointer** – puntero del archivo abierto en modo escritura o append.

```python
with open('person.json', 'w') as f:  # writing JSON object
    json.dump(person, f)
```

### Serialización usando función dumps()

**json.dumps()** que ayuda en convertir un diccionario a un objeto JSON.

Toma dos parámetros:

1. **dictionary** – nombre del diccionario que debería ser convertido a objeto JSON.
2. **indent** – define el número de unidades para indentación

```python
# Serializing json  
json_object = json.dumps(person, indent = 4) 
  
# Writing to sample.json 
with open("sample.json", "w") as outfile: 
    outfile.write(json_object) 

print(json_object)
```

![Captura de pantalla 2024-12-20 a las 12.47.29.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.47.29.png)

### Deserialización: Leyendo JSON a un Archivo

es el reverso de la serialización. Convierte el formato especial retornado por la serialización de vuelta a un objeto usable.

### Usando json.load()

El paquete JSON tiene función json.load() que carga el contenido json de un archivo json en un diccionario.

Toma un parámetro: Un puntero de archivo que apunta a un archivo JSON.

```python
import json 
  
# Opening JSON file 
with open('sample.json', 'r') as openfile: 
  
    # Reading from json file 
    json_object = json.load(openfile) 
  
print(json_object) #output: {'first_name': 'Mark', 'last_name': 'abc', 'age': 27, 'address': {'streetAddress': '21 2nd Street', 'city': 'New York', 'state': 'NY', 'postalCode': '10021-3100'}}

print(type(json_object)) #output: <class 'dict'>
```

## Formato de archivo XLSX

**XLSX** es un formato de archivo Microsoft Excel Open XML. Es otro tipo de formato de archivo de hoja de cálculo.

En XLSX los datos se organizan bajo las celdas y columnas en una hoja. Para cargar los datos puedes usar la biblioteca Pandas en python.

```python
import pandas as pd

# Not needed unless you're running locally
# import urllib.request
# urllib.request.urlretrieve("https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/file_example_XLSX_10.xlsx", "sample.xlsx")

filename = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/file_example_XLSX_10.xlsx"

async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

await download(filename, "file_example_XLSX_10.xlsx")

df = pd.read_excel("file_example_XLSX_10.xlsx")

df #output:
```

![Captura de pantalla 2024-12-20 a las 12.54.47.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.54.47.png)

## Formato de archivo XML

**XML también se conoce como Extensible Markup Language**. Como el nombre sugiere, es un lenguaje de marcado. Tiene ciertas reglas para codificar datos. El formato de archivo XML es un formato de archivo legible por humanos y máquinas.

Pandas no incluye ningún método para leer y escribir archivos XML. Aquí, echaremos un vistazo a cómo podemos usar otros módulos para leer datos de un archivo XML, y cargarlo en un DataFrame de Pandas.

### **Escribiendo con xml.etree.ElementTree**

El módulo **xml.etree.ElementTree** viene incorporado con Python. Proporciona funcionalidad para analizar y crear documentos XML. **ElementTree** representa el documento XML como un árbol. Podemos movernos a través del documento usando nodos que son elementos y sub-elementos del archivo XML.

Para más información por favor lee la documentación [xml.etree.ElementTree](https://docs.python.org/3/library/xml.etree.elementtree.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01).

```python
import xml.etree.ElementTree as ET

# create the file structure
employee = ET.Element('employee')
details = ET.SubElement(employee, 'details')
first = ET.SubElement(details, 'firstname')
second = ET.SubElement(details, 'lastname')
third = ET.SubElement(details, 'age')
first.text = 'Shiv'
second.text = 'Mishra'
third.text = '23'

# create a new XML file with the results
mydata1 = ET.ElementTree(employee)
# myfile = open("items2.xml", "wb")
# myfile.write(mydata)
with open("new_sample.xml", "wb") as files:
    mydata1.write(files)
```

### **Leyendo con xml.etree.ElementTree**

Echemos un vistazo a una forma de leer datos XML y ponerlos en un DataFrame de Pandas. Puedes ver el archivo XML en el Bloc de notas de tu máquina local.

```python
# Not needed unless running locally
# !wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/Sample-employee-XML-file.xml

import xml.etree.ElementTree as etree

filename = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/Sample-employee-XML-file.xml"

async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

await download(filename, "Sample-employee-XML-file.xml")
```

Necesitarías analizar primero un archivo XML y crear una lista de columnas para el marco de datos, luego extraer información útil del archivo XML y agregar a un marco de datos de pandas.

Aquí hay un código de muestra que puedes usar.:

```python
# Parse the XML file
tree = etree.parse("Sample-employee-XML-file.xml")

# Get the root of the XML tree
root = tree.getroot()

# Define the columns for the DataFrame
columns = ["firstname", "lastname", "title", "division", "building", "room"]

# Initialize an empty DataFrame
datatframe = pd.DataFrame(columns=columns)

# Iterate through each node in the XML root
for node in root:
    # Extract text from each element
    firstname = node.find("firstname").text
    lastname = node.find("lastname").text
    title = node.find("title").text
    division = node.find("division").text
    building = node.find("building").text
    room = node.find("room").text
    
    # Create a DataFrame for the current row
    row_df = pd.DataFrame([[firstname, lastname, title, division, building, room]], columns=columns)
    
    # Concatenate with the existing DataFrame
    datatframe = pd.concat([datatframe, row_df], ignore_index=True)

datatframe #output:
```

![Captura de pantalla 2024-12-20 a las 12.56.57.png](../../img/Captura_de_pantalla_2024-12-20_a_las_12.56.57.png)

### Leyendo archivo xml usando función pandas.read_xml

También podemos leer el archivo xml descargado usando la función read_xml presente en la biblioteca pandas que retorna un objeto Dataframe.

Para más información lee la documentación [pandas.read_xml](https://pandas.pydata.org/pandas-docs/dev/reference/api/pandas.read_xml.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01#pandas-read-xml).

```python
# Herein xpath we mention the set of xml nodes to be considered for migrating  to the dataframe which in this case is details node under employees.
df=pd.read_xml("Sample-employee-XML-file.xml", xpath="/employees/details") 
```

**Guardar Datos**

Correspondientemente, Pandas nos permite guardar el conjunto de datos a csv usando el método **dataframe.to_csv()**, puedes agregar la ruta del archivo y nombre junto con marcas de comillas en los paréntesis.

Por ejemplo, si guardarías el marco de datos df como **employee.csv** a tu máquina local, puedes usar la sintaxis abajo:

```python
datatframe.to_csv("employee.csv", index=False)
```

También podemos leer y guardar otros formatos de archivo, podemos usar funciones similares a **`pd.read_csv()`** y **`df.to_csv()`** para otros formatos de datos. Las funciones están listadas en la siguiente tabla:

![Captura de pantalla 2024-12-20 a las 12.58.37.png](../../img/63a9750e-72bb-4cf7-9983-fa22457f3a16.png)

## Formato de archivo binario

Los archivos "Binarios" son cualquier archivo donde el formato no está hecho de caracteres legibles. Contienen información de formato que solo ciertas aplicaciones o procesadores pueden entender. Mientras humanos pueden leer archivos de texto, los archivos binarios deben ser ejecutados en el software o procesador apropiado antes de que humanos puedan leerlos.

Los archivos binarios pueden variar desde archivos de imagen como JPEGs o GIFs, archivos de audio como MP3s o formatos de documento binario como Word o PDF.

Veamos cómo leer un archivo de **Imagen**.

### Leyendo el archivo de Imagen

Python soporta herramientas muy poderosas cuando se trata de procesamiento de imágenes. Veamos cómo procesar las imágenes usando la biblioteca **PIL**.

**PIL** es la Python Imaging Library que proporciona al intérprete de python capacidades de edición de imágenes.

```python
# importing PIL 
from PIL import Image 

# Uncomment if running locally
# import urllib.request
# urllib.request.urlretrieve("https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/dog-puppy-on-garden-royalty-free-image-1586966191.jpg", "dog.jpg")

filename = "https://hips.hearstapps.com/hmg-prod.s3.amazonaws.com/images/dog-puppy-on-garden-royalty-free-image-1586966191.jpg"

async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

await download(filename, "./dog.jpg")

# Read image 
img = Image.open('./dog.jpg','r') 
  
# Output Images 
img.show()
```

# Data Analysis

In this section, you will learn how to approach data acquisition in various ways and obtain necessary insights from a dataset. 

## Case study: the Diabetes Dataset

The **Diabetes Dataset** is an online source and it is in CSV (comma separated value) format. 

- **Context:** This dataset is originally from the **National Institute of Diabetes and Digestive and Kidney Diseases**. The objective of the dataset is to diagnostically predict whether or not a patient has diabetes, based on certain diagnostic measurements included in the dataset. Several constraints were placed on the selection of these instances from a larger database. In particular, all patients here are females at least 21 years of age of Pima Indian heritage.
- **Content:** The datasets consists of several medical predictor variables and one target variable, Outcome. Predictor variables includes the number of pregnancies the patient has had, their BMI, insulin level, age, and so on. We have 768 rows and 9 columns. The first 8 columns represent the features and the last column represent the target/label.

```python
# Import pandas library
import pandas as pd

filename = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/diabetes.csv"

async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

await download(filename, "diabetes.csv")
df = pd.read_csv("diabetes.csv")

# show the first 5 rows using dataframe.head() method
print("The first 5 rows of the dataframe") 
df.head(5)
```

![Captura de pantalla 2024-12-20 a las 13.04.18.png](../../img/Captura_de_pantalla_2024-12-20_a_las_13.04.18.png)

```python
#To view the dimensions of the dataframe:
df.shape #outcome: (768, 9)
```

## Statistical Overview of the dataset:

```python
df.info()
# This method prints information about a DataFrame including the index dtype 
# and columns, non-null values and memory usage.

df.describe()
# Pandas describe() is used to view some basic statistical details like percentile,
# mean, standard deviation, etc. of a data frame or a series of numeric values. 
# When this method is applied to a series of strings, it returns a different output
```

![Captura de pantalla 2024-12-20 a las 13.08.41.png](../../img/Captura_de_pantalla_2024-12-20_a_las_13.08.41.png)

![Captura de pantalla 2024-12-20 a las 13.08.56.png](../../img/Captura_de_pantalla_2024-12-20_a_las_13.08.56.png)

### **Identify and handle missing values**

We use Python's built-in functions to identify these missing values. There are two methods to detect missing data:

- **`.isnull()`**
- **`.notnull()`**

The output is a boolean value indicating whether the value that is passed into the argument is in fact missing data.

```python
missing_data = df.isnull()
missing_data.head(5)

# "True" standos for missing value, "False" fornot missing value
```

![Captura de pantalla 2024-12-20 a las 13.08.20.png](../../img/Captura_de_pantalla_2024-12-20_a_las_13.08.20.png)

### Count missing values in each column

Using a for loop in Python, we can quickly figure out the number of missing values in each column. As mentioned above, "True" represents a missing value, "False" means the value is present in the dataset. In the body of the for loop the method ".value_counts()" counts the number of "True" values.

```python
for column in missing_data.columns.values.tolist():
    print(column)
    print (missing_data[column].value_counts())
    print("")    
```

### Correct data format

Check all data is in the correct format (int, float, text or other).

In Pandas, we use

**.dtype()** to check the data type

**.astype()** to change the data type

Numerical variables should have type **'float'** or **'int'**.

```python
df.dtypes
```

![Captura de pantalla 2024-12-20 a las 13.10.31.png](../../img/Captura_de_pantalla_2024-12-20_a_las_13.10.31.png)

## Visualization

**Visualization** is one of the best way to get insights from the dataset. **Seaborn** and **Matplotlib** are two of Python's most powerful visualization libraries.

```python
# import libraries
import matplotlib.pyplot as plt
import seaborn as sns

labels= 'Not Diabetic','Diabetic'
plt.pie(df['Outcome'].value_counts(),labels=labels,autopct='%0.02f%%')
plt.legend()
plt.show()
```

![Captura de pantalla 2024-12-20 a las 13.11.42.png](../../img/Captura_de_pantalla_2024-12-20_a_las_13.11.42.png)