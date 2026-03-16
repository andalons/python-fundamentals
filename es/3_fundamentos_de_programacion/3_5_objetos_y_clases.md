# 3.5 Objetos y clases

## **Introducción: Clases y Objetos**

Python es un lenguaje de **programación orientada a objetos (OOP)** que usa un paradigma centrado en objetos y clases.

Una ***clase*** es un plano o plantilla para crear objetos. Define la estructura y comportamiento que sus objetos tendrán. Piensa en una clase como un cortador de galletas y objetos como las galletas cortadas de esa plantilla. En Python, puedes crear clases usando la palabra clave `class`.

Cuando creas una clase, especificas los `atributos` (datos) y `métodos`(funciones) que los objetos de esa clase tendrán. Los `atributos` se definen como variables dentro de la clase, y los `métodos` se definen como funciones.

Un ***objeto*** es una unidad fundamental en Python que representa una entidad o concepto del mundo real.

Los objetos pueden ser tangibles (como un coche) o abstractos (como la calificación de un estudiante).

*Cada objeto tiene dos características principales:*

- **Estado**: Los `atributos` *o datos* que describen el objeto. Para tu objeto "Coche", esto podría incluir atributos como "color", "velocidad" y "nivel de combustible".
- **Comportamiento**: Las acciones *o* `métodos` que el objeto puede realizar. En Python, los métodos son funciones que pertenecen a objetos y pueden cambiar el estado del objeto o realizar operaciones específicas.

Una vez que has definido una clase, puedes crear objetos individuales (instancias) basados en esa clase. Cada objeto es independiente y tiene su propio conjunto de atributos y métodos. Para crear un objeto, usas el nombre de la clase seguido de paréntesis, así: "my_car = Car()"

Interactúas con objetos llamando a sus métodos o accediendo a sus atributos usando notación de punto. Por ejemplo, si tienes un objeto Coche llamado **my_car**, puedes establecer su color con **my_car.color = "blue"** y acelerarlo con **my_car.accelerate()** si hay un método accelerate definido en la clase.

## Creando clases

El primer paso en crear una clase es darle un nombre. Crearemos dos clases: Circle y Rectangle. Cada una tiene sus atributos, que son variables. La clase Circle tiene el atributo radius y color, mientras que la clase Rectangle tiene el atributo height y width.

![](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%203/images/ClassesClass.png)

El primer paso en crear tu propia clase es usar la palabra clave `class`, luego el nombre de la clase. En este curso la clase padre siempre será object:

![Captura de pantalla 2024-12-14 a las 10.31.31.png](../../img/Captura_de_pantalla_2024-12-14_a_las_10.31.31.png)

El siguiente paso es un método especial llamado constructor `__init__`, que se usa para inicializar el objeto. Las entradas son atributos de datos. El término `self` contiene todos los atributos en el conjunto. Por ejemplo, `self.color` da el valor del atributo color y `self.radius` te dará el radio del objeto. También tenemos el método `add_radius()` con el parámetro `r`, el método agrega el valor de `r` al atributo radius. Para acceder al radio usamos la sintaxis `self.radius`. La sintaxis etiquetada se resume en la Figura 5:

![Captura de pantalla 2024-12-14 a las 10.32.48.png](../../img/Captura_de_pantalla_2024-12-14_a_las_10.32.48.png)

```python
# Importar biblioteca para dibujar círculo
import matplotlib.pyplot as plt
%matplotlib inline 

class Circle(object):
    
    # Constructor
    def __init__(self, radius=3, color='blue'):
        self.radius = radius
        self.color = color 
    
    # Método
    def add_radius(self, r):
        self.radius = self.radius + r
        return(self.radius)
    
    # Método
    def drawCircle(self):
        plt.gca().add_patch(plt.Circle((0, 0), radius=self.radius, fc=self.color))
        plt.axis('scaled')
        plt.show() 
```

## **Creando instancias de una Clase: Objetos y Atributos**

Una instancia de un objeto es la realización de una clase.

![*Tres instancias de la clase Circle, o tres objetos de tipo Circle. El atributo de color para el Circle rojo es el color rojo, para el objeto Circle verde el atributo de color es verde, y para el Circle amarillo el atributo de color es amarillo.*](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%203/images/ClassesObj.png)

*Three instances of the class Circle, or three objects of type Circle. The colour attribute for the red Circle is the colour red, for the green Circle object the colour attribute is green, and for the yellow Circle the colour attribute is yellow.*

```python
# Crear un objeto RedCircle
RedCircle = Circle(10, 'red')

#Podemos usar el comando dir para obtener una lista de los métodos del objeto. Muchos de ellos son métodos predeterminados de Python.
dir(RedCircle)

#output: 
['__class__',
 '__delattr__',
 '__dict__',
 '__dir__',
 '__doc__',
 '__eq__',
 '__format__',
 '__ge__',
 '__getattribute__',
 '__getstate__',
 '__gt__',
 '__hash__',
 '__init__',
 '__init_subclass__',
 '__le__',
 '__lt__',
 '__module__',
 '__ne__',
 '__new__',
 '__reduce__',
 '__reduce_ex__',
 '__repr__',
 '__setattr__',
 '__sizeof__',
 '__str__',
 '__subclasshook__',
 '__weakref__',
 **'add_radius',**
 '**color**',
 '**drawCircle**',
 '**radius**']
 
# Podemos interactuar con los atributos y métodos del objeto:
 
# Imprimir el atributo radius del objeto
RedCircle.radius 

# Imprimir el atributo color del objeto
RedCircle.color

# Establecer el atributo radius del objeto
RedCircle.radius = 1
RedCircle.radius

# Llamar al método drawCircle
RedCircle.drawCircle()

# Usar método para cambiar el atributo radius del objeto
print('Radius of object:',RedCircle.radius)
RedCircle.add_radius(2)
print('Radius of object of after applying the method add_radius(2):',RedCircle.radius)
RedCircle.add_radius(5)
print('Radius of object of after applying the method add_radius(5):',RedCircle.radius)

# Crear un círculo azul con un radio dado (el valor predeterminado para color en el constructor es azul)
BlueCircle = Circle(radius=100)
```