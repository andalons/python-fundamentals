# 5.2 APIs REST y Solicitud HTTP

## Resumen de HTTP

Cuando tú, el **cliente**, usas una página web, tu navegador envía una solicitud **HTTP** al **servidor** donde la página está alojada. El servidor intenta encontrar el **recurso** deseado, típicamente el `index.html` por defecto. Si tu solicitud es exitosa, el servidor enviará el objeto al cliente en una **respuesta HTTP**. Esta respuesta incluye información como el tipo del **recurso**, la longitud del **recurso**, y otros detalles relevantes.

La figura abajo representa el proceso. El círculo a la izquierda representa el cliente, y el círculo a la derecha representa el servidor web. La tabla bajo el servidor web simboliza una lista de recursos almacenados en el servidor, como un archivo `HTML`, una imagen `png`, y un archivo `txt`.

El protocolo **HTTP** facilita el intercambio de información en la web, incluyendo páginas web, imágenes, y otros recursos. En este laboratorio, proporcionaremos una visión general de la biblioteca Requests para interactuar con el protocolo `HTTP`.

![Captura de pantalla 2024-12-19 a las 16.24.13.png](../../img/Captura_de_pantalla_2024-12-19_a_las_16.24.13.png)

### **Localizador Uniforme de Recursos: URL**

Un Localizador Uniforme de Recursos (URL) es la forma más popular de encontrar recursos en la web. Una URL puede dividirse en tres partes:

1. **Esquema**: Este es el protocolo. Para este laboratorio, siempre será `http://`.
2. **Dirección de Internet o URL Base**: Esta se usa para encontrar la ubicación. Ejemplos incluyen `www.ibm.com` y `www.gitlab.com`.
3. **Ruta**: Esta es la ubicación en el servidor web. Por ejemplo: `/images/IDSNlogo.png`.

> También puedes oír el término Identificador Uniforme de Recursos (URI), las URLs son en realidad un subconjunto de URIs. Otro término popular es endpoint, esta es la URL de una operación proporcionada por un Servidor Web.
> 

### Solicitud

El proceso puede dividirse en las fases de **Solicitud** y **Respuesta**. La solicitud usando el método GET se ilustra parcialmente abajo:

En la línea de inicio, tenemos el método `GET`, que es un **método HTTP**, junto con la ubicación del recurso (`/index.html`) y la **versión HTTP**. El Encabezado de Solicitud proporciona información adicional junto con la **solicitud HTTP**.

![Captura de pantalla 2024-12-19 a las 16.26.15.png](../../img/Captura_de_pantalla_2024-12-19_a_las_16.26.15.png)

![Captura de pantalla 2024-12-19 a las 16.27.38.png](../../img/fc22f1c1-5ac7-4f78-a3f6-6642c3720b38.png)

Cuando se hace una **solicitud HTTP**, se envía un **método HTTP**. Este método le dice al servidor qué acción realizar. La imagen a la derecha muestra una lista de varios **métodos HTTP**. 

### Respuesta

La figura representa la respuesta. La línea de inicio de respuesta incluye el número de versión (`HTTP/1.0`), un código de estado (`200`), que indica éxito, y una frase descriptiva (`OK`). El encabezado de respuesta proporciona información útil, y el cuerpo de respuesta contiene el archivo solicitado, como un documento `HTML`. También debe notarse que algunas solicitudes incluyen encabezados.

![Captura de pantalla 2024-12-19 a las 16.28.26.png](../../img/Captura_de_pantalla_2024-12-19_a_las_16.28.26.png)

Algunos ejemplos de códigos de estado se muestran en la tabla. El prefijo indica la clase (resaltado en amarillo), mientras que los códigos de estado reales se muestran en blanco. 

Para descripciones más detalladas, revisa el siguiente [enlace](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01).

![Captura de pantalla 2024-12-19 a las 16.31.17.png](../../img/Captura_de_pantalla_2024-12-19_a_las_16.31.17.png)

## Solicitudes en Python

Requests es una biblioteca de Python que te permite enviar solicitudes `HTTP/1.1` fácilmente. Puedes importar la biblioteca como se muestra abajo:

```python
import requests

# una solicitud GET a ibm
url='https://www.ibm.com/'
r=requests.get(url)

# Para ver el código de estado:
r.status_code

# Para ver los encabezados de solicitud:
print(r.request.headers)

# Para ver el cuerpo de solicitud (como no hay cuerpo para una solicitud get obtenemos None)
print("request body:", r.request.body)

# Para ver el encabezado de respuesta HTTP:
header=r.headers
print(r.headers)

# Podemos obtener la fecha en que se envió la solicitud usando la clave 'Date'
header['date']

# Y 'Content-Type' indicará el tipo de datos:
header['Content-Type']

# Para verificar la codificación: 
r.encoding

# Como el tipo de contenido es text/html, podemos usar el 
# atributo text para mostrar el HTML en el cuerpo.
# Aquí el código para mostrar los primeros 100 caracteres:
r.text[0:100]

```

### Ejemplos:

- **Accediendo a una imagen:** 
Una imagen es un objeto de respuesta que contiene la imagen como un [objeto similar a bytes](https://docs.python.org/3/glossary.html?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01#term-bytes-like-object). Por lo tanto, debe guardarse usando un objeto de archivo. Para hacer esto, primero especificamos la **ruta del archivo y nombre**.
    
    ```python
    path=os.path.join(os.getcwd(),'image.png')
    ```
    
    Guardamos el archivo. Para acceder al cuerpo de la respuesta, usamos el atributo `content`. Luego, lo guardamos usando la función `open` y el método `write`.
    
    ```python
    from PIL import Image
    
    with open(path,'wb') as f:
        f.write(r.content)
        
    # Para ver la imagen:
    Image.open(path)
    ```
    
- **Accediendo a un archivo:**
Dada la URL: [`https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module 5/data/Example1.txt](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/Example1.txt)`
Estos serían los comandos para descargar el archivo txt:
    
    ```python
    url='https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0101EN-SkillsNetwork/labs/Module%205/data/Example1.txt'
    path=os.path.join(os.getcwd(),'example1.txt')
    r=requests.get(url)
    with open(path,'wb') as f:
        f.write(r.content)
    ```
    

## **Solicitud GET con Parámetros URL**

Puedes usar el método **GET** para modificar los resultados de tu consulta, como recuperar datos de una API. Enviamos una solicitud **GET** al servidor. Como antes, tenemos la **URL Base**, y en la **Ruta**, agregamos `/get`, lo que indica que nos gustaría realizar una solicitud **GET**.

```python
url_get='http://httpbin.org/get'
```

Una [cadena de consulta](https://en.wikipedia.org/wiki/Query_string?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01) es una parte de un Localizador Uniforme de Recursos (URL) que envía información adicional al servidor web. La consulta comienza con un `?`, seguida de una serie de pares parámetro-valor, como se muestra en la tabla abajo. El primer nombre de parámetro es `name`, con el valor `Joseph`. El segundo nombre de parámetro es `ID`, con el valor `123`. Cada par parámetro-valor está separado por un signo igual (`=`), y los pares están separados por un ampersand (`&`).

![Captura de pantalla 2024-12-19 a las 16.56.08.png](../../img/Captura_de_pantalla_2024-12-19_a_las_16.56.08.png)

```python
# Para crear una Cadena de consulta, agrega un diccionario. 
# Las claves son los nombres de parámetros y los valores son el valor de la Cadena de consulta.

payload={"name":"Joseph","ID":"123"}

# Luego pasa el diccionario payload al parámetro params de la función get():
r=requests.get(url_get,params=payload)
r.url #podemos imprimir la url y ver el nombre y valores
print("request body:", r.request.body) #No hay cuerpo de solicitud
print(r.status_code) #Para imprimir el código de estado
print(r.text) #Para imprimir la respuesta como texto
r.headers['Content-Type'] #Para ver tipo de contenido

# Como el tipo de contenido está en formato JSON, podemos convertirlo a un dict de python por:
r.json()

# La clave args tiene el nombre y valores
r.json()['args']
```

## Solicitud POST

Como una solicitud `GET`, una `POST` se usa para enviar datos a un servidor, pero la solicitud `POST` envía los datos en el cuerpo de la solicitud. Para enviar la solicitud `POST` en Python, cambiamos la ruta a `POST` en la **URL**.

```python
url_post='http://httpbin.org/post'
```

Este endpoint esperará datos como un archivo o como un formulario. Un formulario es una forma conveniente de configurar una solicitud HTTP para enviar datos a un servidor.

Para hacer una solicitud `POST` usamos la función `post()`, la variable `payload` se pasa al parámetro `data`:

```python
r_post=requests.post(url_post,data=payload)

# Comparando la URL del objeto de respuesta de las solicitudes GET y POST 
# vemos que la solicitud POST no tiene pares nombre o valor en la URL 
# pero, a diferencia de la solicitud GET, sí tiene información en el cuerpo.

print("POST request URL:",r_post.url )
print("GET request URL:",r.url)

print("POST request body:",r_post.request.body)
print("GET request body:",r.request.body)

#Podemos ver el formulario también:
r_post.json()['form']
```