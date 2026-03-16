# Análisis de Texto (Estudio de Caso)

## ¿Qué es el análisis de texto?

El análisis de texto, también conocido como minería de texto o analítica de texto, se refiere al proceso de extraer información y conocimientos significativos de datos textuales.

## Objetivos

- Usar comandos de Python para realizar análisis de texto.
- Convertir el texto a minúsculas y luego encontrar y contar la frecuencia de todas las palabras únicas, así como una palabra especificada.

## Configuración

**Consideremos un escenario de la vida real donde estás analizando retroalimentación de clientes para un producto. Tienes un gran conjunto de datos de reseñas de clientes en forma de cadenas, y quieres extraer información útil de ellas usando las tres tareas identificadas:**

**Tarea 1. Cadena en minúsculas:** Quieres preprocesar la retroalimentación de clientes convirtiendo todo el texto a minúsculas. Este paso ayuda a estandarizar el texto. Poner el texto en minúsculas te permite enfocarte en el contenido en lugar del casing específico de las letras.

**Tarea 2. Frecuencia de todas las palabras en una cadena dada:** Después de convertir el texto a minúsculas, quieres determinar la frecuencia de cada palabra en la retroalimentación de clientes. Esta información te ayudará a identificar qué palabras se usan más frecuentemente, indicando los aspectos o temas clave que los clientes están mencionando en sus reseñas. Al analizar las frecuencias de palabras, puedes obtener conocimientos sobre los problemas más comunes planteados por los clientes.

**Tarea 3. Frecuencia de una palabra específica:** Además de analizar las frecuencias generales de palabras, quieres rastrear específicamente la frecuencia de una palabra particular que es relevante para tu análisis. Por ejemplo, podrías estar interesado en monitorear qué tan a menudo aparece la palabra "confiable" en las reseñas de clientes para medir el sentimiento de los clientes sobre la confiabilidad del producto. Al enfocarte en la frecuencia de una palabra específica, puedes obtener una comprensión más profunda de las opiniones o preferencias de los clientes relacionadas con ese aspecto particular.

Al realizar estas tareas en el conjunto de datos de retroalimentación de clientes, puedes obtener conocimientos valiosos sobre el sentimiento de los clientes

## Pasos

### 1. Definir una cadena

```python
givenstring="Lorem ipsum dolor! diam amet, consetetur Lorem magna. sed diam nonumy eirmod tempor. diam et labore? et diam magna. et diam amet."
```

### 2.  **Definir la clase y sus atributos**

```python
# Vamos a crear una clase llamada TextAnalyzer para analizar texto.
class TextAnalyzer(object):
    # El método __init__ inicializa la clase con un parámetro 'text'.
    # Almacenarás el 'text' proporcionado como una variable de instancia.
    def __init__(self, text):
```

### 3. **Implementar un código para formatear el texto**

```python
class TextAnalzer(object):
    
    def __init__ (self, text):
        # remover puntuación
        formattedText = text.replace('.','').replace('!','').replace('?','').replace(',','')
        
        # hacer texto minúsculas
        formattedText = formattedText.lower()
        
        self.fmtText = formattedText
```

### **4. Implementar un código para contar la frecuencia de todas las palabras únicas**

```python
class TextAnalyzer(object):
    
    def __init__ (self, text):
        # remover puntuación
        formattedText = text.replace('.','').replace('!','').replace('?','').replace(',','')
        
        # hacer texto minúsculas
        formattedText = formattedText.lower()
        
        self.fmtText = formattedText
        
    def freqAll(self):        
        # dividir texto en palabras
        wordList = self.fmtText.split(' ')
        
        # Crear diccionario
        freqMap = {}
        for word in set(wordList): # usar set para remover duplicados en lista
            freqMap[word] = wordList.count(word)
        
        return freqMap
```

### 5. Implementar un código para contar la frecuencia de una palabra específica

```python
class TextAnalyzer(object):
    
    def __init__ (self, text):
        # remover puntuación
        formattedText = text.replace('.','').replace('!','').replace('?','').replace(',','')
        
        # hacer texto minúsculas
        formattedText = formattedText.lower()
        
        self.fmtText = formattedText
        
    def freqAll(self):        
        # dividir texto en palabras
        wordList = self.fmtText.split(' ')
        
        # Crear diccionario
        freqMap = {}
        for word in set(wordList): # usar set para remover duplicados en lista
            freqMap[word] = wordList.count(word)
        
        return freqMap
    
    def freqOf(self,word):
        # obtener mapa de frecuencia
        freqDict = self.freqAll()
        
        if word in freqDict:
            return freqDict[word]
        else:
            return 0
```