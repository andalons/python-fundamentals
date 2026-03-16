# 5.1 Introducción: APIs Simples

## ¿Qué es una API?

Una API permite que dos piezas de software se comuniquen entre sí. Al igual que una función, no tienes que saber cómo funciona la API, solo sus entradas y salidas. Un tipo esencial de API es una REST API que te permite acceder a recursos a través de internet.

### Ejemplo: Pandas es una API

Pandas es en realidad un conjunto de componentes de software, muchos de los cuales ni siquiera están escritos en Python.

![Captura de pantalla 2024-12-18 a las 14.25.56.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.25.56.png)

Cuando creas un objeto Pandas con el constructor DataFrame, en jerga de API esto es una "instancia". Los datos en el diccionario se pasan a la API de pandas. Luego usas el dataframe para comunicarte con la API.

```python
import pandas as pd
import matplotlib.pyplot as plt

dict_={'a':[11,21,31],'b':[12,22,32]}
df=pd.DataFrame(dict_)
type(df) #Output: pandas.core.frame.DataFrame
```

Cuando llamas al método `head` el dataframe se comunica con la API mostrando las primeras filas del dataframe.

```python
df.head()
```

![Captura de pantalla 2024-12-18 a las 14.27.22.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.27.22.png)

Cuando llamas al método `mean`, la API calculará la media y devolverá el valor.

```python
df.mean()
```

![Captura de pantalla 2024-12-18 a las 14.27.33.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.27.33.png)

## APIs REST

Las APIs REST funcionan enviando una **solicitud** que se comunica vía mensaje HTTP. El mensaje HTTP usualmente contiene un archivo JSON. Esto contiene instrucciones para qué operación nos gustaría que el servicio o **recurso** realice. De manera similar, la API devuelve una **respuesta**, vía un mensaje HTTP, también usualmente contenida dentro de un JSON.

En este laboratorio, usaremos la [NBA API](https://pypi.org/project/nba-api/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01) para determinar qué tan bien los Golden State Warriors se desempeñaron contra los Toronto Raptors. Usaremos la API para determinar el número de puntos por los que los Golden State Warriors ganaron o perdieron en cada juego. Así que si el valor es tres, los Golden State Warriors ganaron por tres puntos. Similarmente si los Golden State Warriors perdieron por dos puntos el resultado será negativo dos. La API manejará muchos de los detalles, como Endpoints y Autenticación.

### Ejemplo: NBA API

`!pip install nba_api`

Usaremos la [NBA API](https://pypi.org/project/nba-api/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0101ENSkillsNetwork19487395-2021-01-01) para determinar qué tan bien los Golden State Warriors se desempeñaron contra los Toronto Raptors. La API manejará muchos de los detalles, como Endpoints y Autenticación.

Es bastante simple usar la nba api para hacer una solicitud para un equipo específico. No requerimos un JSON, todo lo que requerimos es un id. Esta información se almacena localmente en la API. Importamos el módulo `teams`.

```python
from nba_api.stats.static import teams
import matplotlib.pyplot as plt

def one_dict(list_dict):
    keys=list_dict[0].keys()
    out_dict={key:[] for key in keys}
    for dict_ in list_dict:
        for key, value in dict_.items():
            out_dict[key].append(value)
    return out_dict

# El método get_teams() devuelve una lista de diccionarios.    
nba_teams = teams.get_teams()

#La clave del diccionario id tiene un identificador único para cada equipo como valor. 
#Veamos los primeros tres elementos de la lista:
nba_teams[0:3] #Output in the side image
```

![Captura de pantalla 2024-12-18 a las 14.33.23.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.33.23.png)

Para hacer las cosas más fáciles, podemos convertir el diccionario a una tabla. Primero, usamos la función `one dict`, para crear un diccionario. Usamos las claves comunes para cada equipo como las claves, el valor es una lista; cada elemento de la lista corresponde a los valores para cada equipo. Luego convertimos el diccionario a un dataframe, cada fila contiene la información para un equipo diferente:

```python
dict_nba_team=one_dict(nba_teams)
df_teams=pd.DataFrame(dict_nba_team)
df_teams.head()
```

![Captura de pantalla 2024-12-18 a las 14.38.58.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.38.58.png)

Usaremos el apodo del equipo para encontrar el id único, podemos ver la fila que contiene a los warriors usando la columna nickname como sigue:

```python
df_warriors=df_teams[df_teams['nickname']=='Warriors']
df_warriors
```

![Captura de pantalla 2024-12-18 a las 14.39.42.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.39.42.png)

Podemos usar la siguiente línea de código para acceder a la primera columna del DataFrame:

```python
id_warriors=df_warriors[['id']].values[0][0]
# ahora tenemos un entero que puede ser usado para solicitar la información de los Warriors 
id_warriors #output: 1610612744
```

La función "League Game Finder " hará una llamada a la API, está en el módulo `stats.endpoints`. 

El parámetro `team_id_nullable` es el ID único para los warriors. Bajo el capó, la NBA API está haciendo una solicitud HTTP. La información solicitada es proporcionada y se transmite vía una respuesta HTTP esto se asigna al objeto `game finder`. El objeto game finder tiene un método `get_data_frames()`, que devuelve un dataframe. Si vemos el dataframe, podemos ver que contiene información sobre todos los juegos que los Warriors jugaron. 

```python
from nba_api.stats.endpoints import leaguegamefinder

gamefinder = leaguegamefinder.LeagueGameFinder(team_id_nullable=id_warriors)
gamefinder.get_json()
games = gamefinder.get_data_frames()[0]
games.head()
```

Puedes descargar el dataframe desde la llamada a la API para Golden State :

```python
import requests

filename = "https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%205/Labs/Golden_State.pkl"

def download(url, filename):
    response = requests.get(url)
    if response.status_code == 200:
        with open(filename, "wb") as f:
            f.write(response.content)

download(filename, "Golden_State.pkl")

file_name = "Golden_State.pkl"
games = pd.read_pickle(file_name)
games.head()
```

![Captura de pantalla 2024-12-18 a las 14.49.23.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.49.23.png)

Podemos crear dos dataframes, uno para los juegos que los Warriors enfrentaron a los raptors en casa, y el segundo para juegos de visitante.

```python
games_home=games[games['MATCHUP']=='GSW vs. TOR']
games_away=games[games['MATCHUP']=='GSW @ TOR']
```

Podemos calcular la media para la columna `PLUS_MINUS` para los dataframes `games_home` y `games_away`:

```python
games_home['PLUS_MINUS'].mean() #3.730769230769231
games_away['PLUS_MINUS'].mean() #-0.6071428571428571
```

Podemos graficar la columna `PLUS MINUS` para los dataframes `games_home` y `games_away`. Vemos que los warriors jugaron mejor en casa:

```python
fig, ax = plt.subplots()

games_away.plot(x='GAME_DATE',y='PLUS_MINUS', ax=ax)
games_home.plot(x='GAME_DATE',y='PLUS_MINUS', ax=ax)
ax.legend(["away", "home"])
plt.show()
```

![Captura de pantalla 2024-12-18 a las 14.51.16.png](../../img/Captura_de_pantalla_2024-12-18_a_las_14.51.16.png)