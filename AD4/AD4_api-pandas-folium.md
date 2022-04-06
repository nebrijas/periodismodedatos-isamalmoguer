# API Pandas Folium

- API
- Pandas
- Folium,mapas

## Instalar librerías

Lo primero que tenemos que hacer es instalar la librería Panda. Esta libreria nos da herramientas para poder leer y escribir los datos en los diferentes formatos que necesitamos: CSV, Microsoft Excel, bases SQL y formato HDF5. Esta herramienta, además de esto, nos permite seleccionar y filtrar de forma sencillatablas de datos en función de la posición, el valor o las propias etiquetas, así como fusionar y unir datos que requiramos.


```python
!pip install pandas folium
```

    Requirement already satisfied: pandas in c:\programdata\anaconda3\lib\site-packages (1.2.4)
    Requirement already satisfied: folium in c:\programdata\anaconda3\lib\site-packages (0.12.1.post1)
    Requirement already satisfied: jinja2>=2.9 in c:\programdata\anaconda3\lib\site-packages (from folium) (2.11.3)
    Requirement already satisfied: requests in c:\programdata\anaconda3\lib\site-packages (from folium) (2.25.1)
    Requirement already satisfied: numpy in c:\programdata\anaconda3\lib\site-packages (from folium) (1.20.1)
    Requirement already satisfied: branca>=0.3.0 in c:\programdata\anaconda3\lib\site-packages (from folium) (0.4.2)
    Requirement already satisfied: MarkupSafe>=0.23 in c:\programdata\anaconda3\lib\site-packages (from jinja2>=2.9->folium) (1.1.1)
    Requirement already satisfied: pytz>=2017.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2021.1)
    Requirement already satisfied: python-dateutil>=2.7.3 in c:\programdata\anaconda3\lib\site-packages (from pandas) (2.8.1)
    Requirement already satisfied: six>=1.5 in c:\programdata\anaconda3\lib\site-packages (from python-dateutil>=2.7.3->pandas) (1.15.0)
    Requirement already satisfied: idna<3,>=2.5 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2.10)
    Requirement already satisfied: urllib3<1.27,>=1.21.1 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (1.26.4)
    Requirement already satisfied: certifi>=2017.4.17 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (2020.12.5)
    Requirement already satisfied: chardet<5,>=3.0.2 in c:\programdata\anaconda3\lib\site-packages (from requests->folium) (4.0.0)
    

## Configurar librerías

La configuración de las librerías se basa en importarlas para usarlas en este cuaderno, lo hacemos con las siguientes funciones:


```python
import pandas as pd
import folium
```

## Variables

Vamos a usar:
- La URL
- Y las coordenadas de Zaragoza, que llamaremos `coords_zrgz` y cuyas coordenadas exactas son `[41.649693, -0.887712]`
- Mapa, aunque más que una variable es un objeto. Lo haremos haciendo una llamada a `folium`

La primera variable que vamos a usar es la URL de donde queremos sacar los datos, en este caso la accidentalidad en el tráfico en la ciudad de Zaragoza. 

Para hacer el mapa llamaremos a la libreria folium, a la que le pediremos la localización y su valor serán las coordenadas de Zaragoza. Aquí las llamaremos `coords_zrgz`


```python
url = 'https://www.zaragoza.es/sede/servicio/transporte/accidentalidad-trafico/accidente.csv?rows=20'
coords_zrgz = [41.649693,-0.887712]
mapa = folium.Map(location=coords_zrgz)
```

Para empezar a ver algo visual tenemos que crear el mapa. Para ello, llamermos a la librería `folium` y a su función `map`. Esta función tiene una propiedad, que es location y ahí le pedimos que use las coordenadas de Zaragoza.
Escribimos la palabra `mapa`, ya que es la palabra a la que le hemos dado el valor de las coordenadas de Zaragoza.


```python
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_390764f4f1d54709a1c5b5f8813155a3%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_390764f4f1d54709a1c5b5f8813155a3%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_390764f4f1d54709a1c5b5f8813155a3%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_390764f4f1d54709a1c5b5f8813155a3%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_f87633031d69491c8f585177f5d302e7%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_390764f4f1d54709a1c5b5f8813155a3%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



El siguiente paso es crear un data frame `df`, que es como se llaman las tablas en el lenguaje de Phyton. Pero en esta ocasión tenemos que limpiar la url con el código `delimiter`, que en este caso es el punto y coma `;`. De esta forma la librería lee la función de Panda `read csv`, pero como no esta delimitado por comas `,`, sino por puntos y comas `;`, tenemos que ponerlo para que el programa nos muestre los datos que buscamos.


```python
df = pd.read_csv(url,delimiter=';')
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>year</th>
      <th>type</th>
      <th>accidentType</th>
      <th>firstAddress</th>
      <th>secondAddress</th>
      <th>geometry</th>
      <th>reason</th>
      <th>area</th>
      <th>creationDate</th>
      <th>daniosMateriales</th>
      <th>falloMecanico</th>
      <th>estadoPavimento</th>
      <th>tipoEstadoPavimento</th>
      <th>estadoAtmosfera</th>
      <th>tipoEstadoAtmosfera</th>
      <th>afectado</th>
      <th>vehiculo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>COSTA, JOAQUIN</td>
      <td>PERAL, ISAAC</td>
      <td>-0.8818527060979306,41.649027473051156</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2014-10-09T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CADENA(MARQUES DE LA)</td>
      <td>NaN</td>
      <td>-0.8645810716721081,41.661585829868585</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>2560.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>GOMEZ AVELLANEDA, G.</td>
      <td>CASTRO, R. (POETA)</td>
      <td>-0.887776415002892,41.666992622958105</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2598.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS FRONTOLATERAL</td>
      <td>NaN</td>
      <td>MONZON</td>
      <td>GARCIA CONDOY, H.</td>
      <td>-0.8825260453930127,41.62957498750602</td>
      <td>CEDA EL PASO, no respetar prioridad de paso</td>
      <td>2555.0</td>
      <td>2014-10-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.908314757720389,41.6562121210704</td>
      <td>PERDIDA del control por VELOCIDAD INADECUADA</td>
      <td>2554.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>MUEL</td>
      <td>NaN</td>
      <td>-0.8691088511672924,41.65949772773082</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>2578.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>PIGNATELLI, RAMON VIA</td>
      <td>NaN</td>
      <td>-0.8880337913721866,41.633353667694024</td>
      <td>PEATÓN cruza calz SIN PREFER. fuera de paso</td>
      <td>2606.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>CAIDA SOBRE CALZADA</td>
      <td>NaN</td>
      <td>ALIERTA, AV. CESAREO</td>
      <td>AULA, LUIS</td>
      <td>-0.8708838775078237,41.6390382112928</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>2583.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2014</td>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>NaN</td>
      <td>CERBUNA, PEDRO</td>
      <td>NaN</td>
      <td>-0.8970649943808023,41.64083344974765</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>2556.0</td>
      <td>2014-10-24T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN LATERAL</td>
      <td>NaN</td>
      <td>ASALTO</td>
      <td>COCCI, JORGE</td>
      <td>-0.8718525605769747,41.64904657717317</td>
      <td>INVADIR otro carril en el mismo sentido de cir...</td>
      <td>4657.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>10</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>OTRAS</td>
      <td>NaN</td>
      <td>ARAGON (CORONA DE)</td>
      <td>SAN ANTONIO M CLARET</td>
      <td>-0.8964627561577849,41.64322365075108</td>
      <td>Caída de ocupante en Transporte Público</td>
      <td>63.0</td>
      <td>2013-12-21T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>FRAGUA, LA</td>
      <td>GASSIER, PIERRE</td>
      <td>-0.8778095796207178,41.68753087470739</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4780.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>12</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>SALIDA CALZADA</td>
      <td>NaN</td>
      <td>PIRINEOS, AV. DE LOS</td>
      <td>NaN</td>
      <td>-0.8812157329722801,41.661646612715046</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4661.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>TORRES, CAMINO DE LAS</td>
      <td>NaN</td>
      <td>-0.8762000299022707,41.6454384961757</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4667.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>14</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>ATROPELLO</td>
      <td>NaN</td>
      <td>RIOJA</td>
      <td>NAVARRA, AVENIDA DE</td>
      <td>-0.9089013552408617,41.65543768899759</td>
      <td>PEATÓN cruza calz SIN PREFER. en PASO CON semá...</td>
      <td>4664.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>15</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>ITALIA</td>
      <td>NaN</td>
      <td>-0.9004729973337304,41.65180346604993</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4671.0</td>
      <td>2013-12-22T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>16</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>MAYANDIA (GENERAL)</td>
      <td>-0.8917562993466011,41.65233828238132</td>
      <td>DISTANCIA DE SEGURIDAD, no mantener</td>
      <td>18.0</td>
      <td>2013-12-20T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>17</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>AGUSTIN, PASEO MARIA</td>
      <td>SANTA ANA</td>
      <td>-0.888856043735591,41.65040494617356</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4718.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>18</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>CASPE, AV.COMPROMISO</td>
      <td>NaN</td>
      <td>-0.8629911318784169,41.645335650478316</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>4723.0</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>False</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
    <tr>
      <th>19</th>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
      <td>2013</td>
      <td>COLISIÓN ALCANCE</td>
      <td>NaN</td>
      <td>MURANO, ISLA DE AV.</td>
      <td>NaN</td>
      <td>-0.8870207060655807,41.609992514227066</td>
      <td>PERDIDA del control por FALTA de ATENCIÓN</td>
      <td>NaN</td>
      <td>2013-12-23T00:00:00Z</td>
      <td>True</td>
      <td>False</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>BUEN ESTADO</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>https://www.zaragoza.es/sede/servicio/transpor...</td>
    </tr>
  </tbody>
</table>
</div>



## Exploración de la tabla

Ahora identificamos las columnas que nos aparecen en la tabla. Esto lo hacemos pidiéndoselo al programa con el siguiente código:


```python
df.columns
```




    Index(['id', 'year', 'type', 'accidentType', 'firstAddress', 'secondAddress',
           'geometry', 'reason', 'area', 'creationDate', 'daniosMateriales',
           'falloMecanico', 'estadoPavimento', 'tipoEstadoPavimento',
           'estadoAtmosfera', 'tipoEstadoAtmosfera', 'afectado', 'vehiculo'],
          dtype='object')



Queremos que nos muestre la geometría, lo hacemos con la siguiente función ya que hemos visto arriba cuáles son las categorías a las que podemos acceder. También podemos acceder a otras como `year`, `creationDate` o `tipoEstadoAtmosfera`, entre otros.


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    Name: geometry, dtype: object



Para que nos muestre una información concreta añadimos a `df` el atributo `info` especificando qué tipo de información específica queremos entre los paréntesis, tanl y como se muestra en el código de abajo


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 20 entries, 0 to 19
    Data columns (total 18 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   id                   20 non-null     object 
     1   year                 20 non-null     int64  
     2   type                 20 non-null     object 
     3   accidentType         0 non-null      float64
     4   firstAddress         20 non-null     object 
     5   secondAddress        11 non-null     object 
     6   geometry             20 non-null     object 
     7   reason               20 non-null     object 
     8   area                 18 non-null     float64
     9   creationDate         20 non-null     object 
     10  daniosMateriales     20 non-null     bool   
     11  falloMecanico        20 non-null     bool   
     12  estadoPavimento      20 non-null     object 
     13  tipoEstadoPavimento  0 non-null      float64
     14  estadoAtmosfera      20 non-null     object 
     15  tipoEstadoAtmosfera  0 non-null      float64
     16  afectado             15 non-null     object 
     17  vehiculo             20 non-null     object 
    dtypes: bool(2), float64(4), int64(1), object(11)
    memory usage: 2.7+ KB
    

Si, en cambio, queremos información sobre las `columnas numéricas`, tendremos que utilizar la función `describe` de la siguiente forma


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>year</th>
      <th>accidentType</th>
      <th>area</th>
      <th>tipoEstadoPavimento</th>
      <th>tipoEstadoAtmosfera</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>20.000000</td>
      <td>0.0</td>
      <td>18.000000</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2013.450000</td>
      <td>NaN</td>
      <td>3234.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.510418</td>
      <td>NaN</td>
      <td>1551.515843</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>18.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2557.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2013.000000</td>
      <td>NaN</td>
      <td>2602.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4666.250000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2014.000000</td>
      <td>NaN</td>
      <td>4780.000000</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Para acceder a una columna en específico, debemos añadir la columna que nos interesa entre corchetes. En este caso, queremos la columna `Type`. Si también queremos que nos haga una descripción de los valores únicos, añadimos a la función el código `.unique()`. 


```python
df['type'].unique()
```




    array(['SALIDA CALZADA', 'COLISIÓN ALCANCE', 'COLIS FRONTOLATERAL',
           'OTRAS', 'ATROPELLO', 'CAIDA SOBRE CALZADA', 'COLIS. MARCHA ATRÁS',
           'COLISIÓN LATERAL'], dtype=object)



Para crear un mapa interactivo, empezamos por pedir que saltan todas las coordenadas del dataframe, pero al ser una línea única Phyton no lo entiende como coordenadas. Para solucionar esto, empezaremos por acceder a la fila `geometry`, donde tendría que haber coordenadas, y encapsularlo. Primero accedes a la fila 0, poniéndolo entre paréntesis, para asegurar los datos que nos han dado anteriormente. 


```python
df['geometry']
```




    0     -0.8818527060979306,41.649027473051156
    1     -0.8645810716721081,41.661585829868585
    2      -0.887776415002892,41.666992622958105
    3      -0.8825260453930127,41.62957498750602
    4        -0.908314757720389,41.6562121210704
    5      -0.8691088511672924,41.65949772773082
    6     -0.8880337913721866,41.633353667694024
    7       -0.8708838775078237,41.6390382112928
    8      -0.8970649943808023,41.64083344974765
    9      -0.8718525605769747,41.64904657717317
    10     -0.8964627561577849,41.64322365075108
    11     -0.8778095796207178,41.68753087470739
    12    -0.8812157329722801,41.661646612715046
    13      -0.8762000299022707,41.6454384961757
    14     -0.9089013552408617,41.65543768899759
    15     -0.9004729973337304,41.65180346604993
    16     -0.8917562993466011,41.65233828238132
    17      -0.888856043735591,41.65040494617356
    18    -0.8629911318784169,41.645335650478316
    19    -0.8870207060655807,41.609992514227066
    Name: geometry, dtype: object




```python
type(df['geometry'][0])
```




    str



En este caso nos sale `str`, que quiere decir string o cadena de carácteres o un texto. De esta forma, hemos comprobado lo que sospechábamos. A nosotros nos interesa separar en el espacio los carácteres que nos salen separados por comas. Esto se consigue utilizando la función split, mencionando las líneas que queremos separar e indicando que queremos que se separen a partir de las comas `,`. 


```python
df['geometry'][0].split(',')
```




    ['-0.8818527060979306', '41.649027473051156']



Una vez separados, y que ya podemos empezar a manipular, vamos a nombrarlo para saber diferenciar cada columna separando los valores, en este caso de `longitud` y `latitud`. Para ello, creamos un punto 'point' con los datos de la fila.


```python
point = df['geometry'][0].split(',')
point
```




    ['-0.8818527060979306', '41.649027473051156']



A continuación, podemos definir el tipo de dato que es 'point', en este caso, es una lista de dos elementos


```python
type(point)
```




    list



Ahora, vamos a crear una serie para guardar cada uno de los elementos de las filas. Una llamada `longitudes` y otra, `latitudes`, que estarán vacías


```python
longitudes = []
latitudes = []
```


```python
longitudes
```




    []




```python
type(longitudes)
```




    list



Ahora, vamos a llenar la lista con el bucle `for i` para las longitudes. Para cada uno de los elementos que tengamos en el data frame, en su columna geometry. Sobre cada elemento haremos un `split`, como hemos hecho anteriormente, para separar los datos a partir de las comas en todas las filas. 
Vamos a hacer un bucle para cada uno de los elementos de la columna geometry. Para ello, decimos que vamos a llamar punto_coord a la separación entre cada celda de la columna geometry. Añadimos el objeto longitudes el segundo valor de punto de coordenadas


```python
for i in df['geometry']:
    punto_coord = i.split (',')
    longitudes += [float (punto_coord[1])]
longitudes
```




    [41.649027473051156,
     41.661585829868585,
     41.666992622958105,
     41.62957498750602,
     41.6562121210704,
     41.65949772773082,
     41.633353667694024,
     41.6390382112928,
     41.64083344974765,
     41.64904657717317,
     41.64322365075108,
     41.68753087470739,
     41.661646612715046,
     41.6454384961757,
     41.65543768899759,
     41.65180346604993,
     41.65233828238132,
     41.65040494617356,
     41.645335650478316,
     41.609992514227066]



Ahora, haremos la misma operación, pero esta vez con las latitudes


```python
for i in df['geometry']:
    punto_coord = i.split (',')
    latitudes += [float(punto_coord[0])]
latitudes
```




    [-0.8818527060979306,
     -0.8645810716721081,
     -0.887776415002892,
     -0.8825260453930127,
     -0.908314757720389,
     -0.8691088511672924,
     -0.8880337913721866,
     -0.8708838775078237,
     -0.8970649943808023,
     -0.8718525605769747,
     -0.8964627561577849,
     -0.8778095796207178,
     -0.8812157329722801,
     -0.8762000299022707,
     -0.9089013552408617,
     -0.9004729973337304,
     -0.8917562993466011,
     -0.888856043735591,
     -0.8629911318784169,
     -0.8870207060655807]



Ahora vemos los datos en forma de lista, podría ser una columna. Pero, para poder verlo de forma más sencilla vamos a crear un data frame de las coordenadas para obtener los datos en una tabla -o diccionario- separados por `longitud` y `latitud`


```python
df_coord = pd.DataFrame({'long':longitudes,'lat':latitudes})
df_coord
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>5</th>
      <td>41.659498</td>
      <td>-0.869109</td>
    </tr>
    <tr>
      <th>6</th>
      <td>41.633354</td>
      <td>-0.888034</td>
    </tr>
    <tr>
      <th>7</th>
      <td>41.639038</td>
      <td>-0.870884</td>
    </tr>
    <tr>
      <th>8</th>
      <td>41.640833</td>
      <td>-0.897065</td>
    </tr>
    <tr>
      <th>9</th>
      <td>41.649047</td>
      <td>-0.871853</td>
    </tr>
    <tr>
      <th>10</th>
      <td>41.643224</td>
      <td>-0.896463</td>
    </tr>
    <tr>
      <th>11</th>
      <td>41.687531</td>
      <td>-0.877810</td>
    </tr>
    <tr>
      <th>12</th>
      <td>41.661647</td>
      <td>-0.881216</td>
    </tr>
    <tr>
      <th>13</th>
      <td>41.645438</td>
      <td>-0.876200</td>
    </tr>
    <tr>
      <th>14</th>
      <td>41.655438</td>
      <td>-0.908901</td>
    </tr>
    <tr>
      <th>15</th>
      <td>41.651803</td>
      <td>-0.900473</td>
    </tr>
    <tr>
      <th>16</th>
      <td>41.652338</td>
      <td>-0.891756</td>
    </tr>
    <tr>
      <th>17</th>
      <td>41.650405</td>
      <td>-0.888856</td>
    </tr>
    <tr>
      <th>18</th>
      <td>41.645336</td>
      <td>-0.862991</td>
    </tr>
    <tr>
      <th>19</th>
      <td>41.609993</td>
      <td>-0.887021</td>
    </tr>
  </tbody>
</table>
</div>



Ahora, vamos a crear otro data frame `accidentes`, y con una herramienta de Pandas, vamos a concatenar el data frame original con el que hemos creado nosotros. También, le pedimos que nos lo ponga en el eje 1 para que nos salga a la izquierda


```python
df_accidentes = pd.concat([df['type'],df_coord],axis=1)
df_accidentes
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>long</th>
      <th>lat</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>SALIDA CALZADA</td>
      <td>41.649027</td>
      <td>-0.881853</td>
    </tr>
    <tr>
      <th>1</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.661586</td>
      <td>-0.864581</td>
    </tr>
    <tr>
      <th>2</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.666993</td>
      <td>-0.887776</td>
    </tr>
    <tr>
      <th>3</th>
      <td>COLIS FRONTOLATERAL</td>
      <td>41.629575</td>
      <td>-0.882526</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SALIDA CALZADA</td>
      <td>41.656212</td>
      <td>-0.908315</td>
    </tr>
    <tr>
      <th>5</th>
      <td>OTRAS</td>
      <td>41.659498</td>
      <td>-0.869109</td>
    </tr>
    <tr>
      <th>6</th>
      <td>ATROPELLO</td>
      <td>41.633354</td>
      <td>-0.888034</td>
    </tr>
    <tr>
      <th>7</th>
      <td>CAIDA SOBRE CALZADA</td>
      <td>41.639038</td>
      <td>-0.870884</td>
    </tr>
    <tr>
      <th>8</th>
      <td>COLIS. MARCHA ATRÁS</td>
      <td>41.640833</td>
      <td>-0.897065</td>
    </tr>
    <tr>
      <th>9</th>
      <td>COLISIÓN LATERAL</td>
      <td>41.649047</td>
      <td>-0.871853</td>
    </tr>
    <tr>
      <th>10</th>
      <td>OTRAS</td>
      <td>41.643224</td>
      <td>-0.896463</td>
    </tr>
    <tr>
      <th>11</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.687531</td>
      <td>-0.877810</td>
    </tr>
    <tr>
      <th>12</th>
      <td>SALIDA CALZADA</td>
      <td>41.661647</td>
      <td>-0.881216</td>
    </tr>
    <tr>
      <th>13</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.645438</td>
      <td>-0.876200</td>
    </tr>
    <tr>
      <th>14</th>
      <td>ATROPELLO</td>
      <td>41.655438</td>
      <td>-0.908901</td>
    </tr>
    <tr>
      <th>15</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.651803</td>
      <td>-0.900473</td>
    </tr>
    <tr>
      <th>16</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.652338</td>
      <td>-0.891756</td>
    </tr>
    <tr>
      <th>17</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.650405</td>
      <td>-0.888856</td>
    </tr>
    <tr>
      <th>18</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.645336</td>
      <td>-0.862991</td>
    </tr>
    <tr>
      <th>19</th>
      <td>COLISIÓN ALCANCE</td>
      <td>41.609993</td>
      <td>-0.887021</td>
    </tr>
  </tbody>
</table>
</div>



Ahora vamos a crear un marcador para que nos salga un punto en el mapa. Creo el marcador con la función de folium, esta función va a tener las coordenadas de Zaragoza y añadiremos un popup con el texto que queremos que salga cuandos se pinche en las coordenadas nombradas al comienzo del código `[41.649693,-0.887712]`. Después, añadimos al objeto `mapa` el `marcador`


```python
marcador = folium.Marker(coords_zrgz, popup="Estás en Zaragoza")
mapa = mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_b1bb0f366cc64380a7465b988c3bdc99%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_b1bb0f366cc64380a7465b988c3bdc99%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_b1bb0f366cc64380a7465b988c3bdc99%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_b1bb0f366cc64380a7465b988c3bdc99%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_cfc2b741198e4ac790fcb9ce75d5aac7%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dce8a7e4ebb84eecbc66208ef27a876c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22popu%22%3A%20%22Est%5Cu00e1s%20en%20Zaragoza%22%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f8d81941ec7d44968e04854e0cb71556%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_19514db429694414bffb4550a89c8944%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_12c14883a2744fe791987997e4d6a0d0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_12c14883a2744fe791987997e4d6a0d0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_19514db429694414bffb4550a89c8944.setContent%28html_12c14883a2744fe791987997e4d6a0d0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f8d81941ec7d44968e04854e0cb71556.bindPopup%28popup_19514db429694414bffb4550a89c8944%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8e4c98a4115f472aa179077b0d805bad%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6eb53c842e254f9c8a85117e372940ea%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_bd7cfa70c8be4016bcce97743b46cf27%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_bd7cfa70c8be4016bcce97743b46cf27%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6eb53c842e254f9c8a85117e372940ea.setContent%28html_bd7cfa70c8be4016bcce97743b46cf27%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8e4c98a4115f472aa179077b0d805bad.bindPopup%28popup_6eb53c842e254f9c8a85117e372940ea%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e932c251b13f4c039f233e4f0af447a4%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2494d1351d8a4fd69c33e27c184b856e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d8f4c0c0a57f46b0993d0a7b4b7054e9%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d8f4c0c0a57f46b0993d0a7b4b7054e9%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2494d1351d8a4fd69c33e27c184b856e.setContent%28html_d8f4c0c0a57f46b0993d0a7b4b7054e9%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e932c251b13f4c039f233e4f0af447a4.bindPopup%28popup_2494d1351d8a4fd69c33e27c184b856e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1a01a22a477a45aeb4f1cb30022daac2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_fba40d60d1fa41708a233c088ff5e173%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3150bba1bc6a4804bfc337114e2f9556%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3150bba1bc6a4804bfc337114e2f9556%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_fba40d60d1fa41708a233c088ff5e173.setContent%28html_3150bba1bc6a4804bfc337114e2f9556%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1a01a22a477a45aeb4f1cb30022daac2.bindPopup%28popup_fba40d60d1fa41708a233c088ff5e173%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c20d1c7b45d34ac399b05c7894224194%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_17567a96b70a40eb8d2863d25b042df3%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a90fdac0261541699f9fb515bd1a757f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a90fdac0261541699f9fb515bd1a757f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_17567a96b70a40eb8d2863d25b042df3.setContent%28html_a90fdac0261541699f9fb515bd1a757f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c20d1c7b45d34ac399b05c7894224194.bindPopup%28popup_17567a96b70a40eb8d2863d25b042df3%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_86a6ed88a9114520a80c5c020a5f036b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_970627018b3a45d88d769e141f0a576a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_62e03e2ae42c43c78f0b1ea556da74e7%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_62e03e2ae42c43c78f0b1ea556da74e7%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_970627018b3a45d88d769e141f0a576a.setContent%28html_62e03e2ae42c43c78f0b1ea556da74e7%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_86a6ed88a9114520a80c5c020a5f036b.bindPopup%28popup_970627018b3a45d88d769e141f0a576a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d879727743e5432e90741372e580b315%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1c13709d0432487496c37eeabdcbe82f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6eabcd7038cf4cdbbaf39886827edb3b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6eabcd7038cf4cdbbaf39886827edb3b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1c13709d0432487496c37eeabdcbe82f.setContent%28html_6eabcd7038cf4cdbbaf39886827edb3b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d879727743e5432e90741372e580b315.bindPopup%28popup_1c13709d0432487496c37eeabdcbe82f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_fbd5ad49325f4c2d9acf6d0a28acb282%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0245d204a533464f87323fa8762709cb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_57d2278f190f407593c45e36db8f81f0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_57d2278f190f407593c45e36db8f81f0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0245d204a533464f87323fa8762709cb.setContent%28html_57d2278f190f407593c45e36db8f81f0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_fbd5ad49325f4c2d9acf6d0a28acb282.bindPopup%28popup_0245d204a533464f87323fa8762709cb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_20bab71bc9724c888bfb0a3d1ac7c3f2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_366391888b16458982a4327424bd89ab%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_983e01242e79403881e53a64aa59a984%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_983e01242e79403881e53a64aa59a984%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_366391888b16458982a4327424bd89ab.setContent%28html_983e01242e79403881e53a64aa59a984%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_20bab71bc9724c888bfb0a3d1ac7c3f2.bindPopup%28popup_366391888b16458982a4327424bd89ab%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f9d31572ed9a4a558fd292fa776e312e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_33cb3e0c5159419fa88cf20da08e9d08%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2c2d32f470c645c3903ae4140cdc0721%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2c2d32f470c645c3903ae4140cdc0721%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_33cb3e0c5159419fa88cf20da08e9d08.setContent%28html_2c2d32f470c645c3903ae4140cdc0721%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f9d31572ed9a4a558fd292fa776e312e.bindPopup%28popup_33cb3e0c5159419fa88cf20da08e9d08%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bc83d296362d464197144b01ae590313%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a7a9441a637b418f84ee09f0d5674e25%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_415409a47a494b2bb78ce7294ad0d70b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_415409a47a494b2bb78ce7294ad0d70b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a7a9441a637b418f84ee09f0d5674e25.setContent%28html_415409a47a494b2bb78ce7294ad0d70b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bc83d296362d464197144b01ae590313.bindPopup%28popup_a7a9441a637b418f84ee09f0d5674e25%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f766c82133b6498199d0dd6403e8ab62%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b9ad0ed5ff84470bb089b18a1586c2c1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3c080511a0654bdc88d0e6ab4db6ff37%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3c080511a0654bdc88d0e6ab4db6ff37%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b9ad0ed5ff84470bb089b18a1586c2c1.setContent%28html_3c080511a0654bdc88d0e6ab4db6ff37%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f766c82133b6498199d0dd6403e8ab62.bindPopup%28popup_b9ad0ed5ff84470bb089b18a1586c2c1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b9ad966a5186406bb86b92ad1b9aaa26%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3cf81ed9ba854fa19121d373d320b722%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_29a2dd52e9a447da88be8b4611b4dea6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_29a2dd52e9a447da88be8b4611b4dea6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3cf81ed9ba854fa19121d373d320b722.setContent%28html_29a2dd52e9a447da88be8b4611b4dea6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b9ad966a5186406bb86b92ad1b9aaa26.bindPopup%28popup_3cf81ed9ba854fa19121d373d320b722%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dbae2d0d9e7e436ba590729d268e555d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_684de62c4c9d4cdb8b40f91058157aed%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6cb4b4f5e33d416a9cea97b30a5e4144%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6cb4b4f5e33d416a9cea97b30a5e4144%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_684de62c4c9d4cdb8b40f91058157aed.setContent%28html_6cb4b4f5e33d416a9cea97b30a5e4144%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dbae2d0d9e7e436ba590729d268e555d.bindPopup%28popup_684de62c4c9d4cdb8b40f91058157aed%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f71f6a3acc124901b293211e4414b982%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6dc712a7c64545f7bef6c209627d56d8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6caf6ac8e75e452a8cc5d26682e39b4c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6caf6ac8e75e452a8cc5d26682e39b4c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6dc712a7c64545f7bef6c209627d56d8.setContent%28html_6caf6ac8e75e452a8cc5d26682e39b4c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f71f6a3acc124901b293211e4414b982.bindPopup%28popup_6dc712a7c64545f7bef6c209627d56d8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_737a249b0b1646189083ee0c99da8750%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_716597041c6444f2b77f13a73fb4a700%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e0a74bf6a11b45618dbf8e36715a25b8%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e0a74bf6a11b45618dbf8e36715a25b8%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_716597041c6444f2b77f13a73fb4a700.setContent%28html_e0a74bf6a11b45618dbf8e36715a25b8%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_737a249b0b1646189083ee0c99da8750.bindPopup%28popup_716597041c6444f2b77f13a73fb4a700%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b460fcb8315c4c50aa309640f2144daf%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b36f326f8d414f0489fc4a3a140641cb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c319ebc802ef439bba8bba8636d1f8aa%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c319ebc802ef439bba8bba8636d1f8aa%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b36f326f8d414f0489fc4a3a140641cb.setContent%28html_c319ebc802ef439bba8bba8636d1f8aa%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b460fcb8315c4c50aa309640f2144daf.bindPopup%28popup_b36f326f8d414f0489fc4a3a140641cb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_74f85d2cf4234a23a864e950578ceccb%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4199acaa11b84369bbd5a2a1f11a7946%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2fb4c57433574bb891944b7bebbd82d6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2fb4c57433574bb891944b7bebbd82d6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4199acaa11b84369bbd5a2a1f11a7946.setContent%28html_2fb4c57433574bb891944b7bebbd82d6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_74f85d2cf4234a23a864e950578ceccb.bindPopup%28popup_4199acaa11b84369bbd5a2a1f11a7946%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a9e47fd9bdb54b0e859880af56476d01%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_32e5979d05754174a37429d48bfb20b5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2f4008fb2c5546278fc48af01b4d21c4%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2f4008fb2c5546278fc48af01b4d21c4%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_32e5979d05754174a37429d48bfb20b5.setContent%28html_2f4008fb2c5546278fc48af01b4d21c4%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a9e47fd9bdb54b0e859880af56476d01.bindPopup%28popup_32e5979d05754174a37429d48bfb20b5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a5110bf1c3034bf39a517228f2ead4d9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9cee316d96144bf0938f93355e25b530%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0928584b16e04b86bbfed8b328c04207%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0928584b16e04b86bbfed8b328c04207%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9cee316d96144bf0938f93355e25b530.setContent%28html_0928584b16e04b86bbfed8b328c04207%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a5110bf1c3034bf39a517228f2ead4d9.bindPopup%28popup_9cee316d96144bf0938f93355e25b530%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_687536ab70db4d79a0e35afc28a9be09%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d12514db15b942edb7fb1aa9464eab92%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e721b6c8893f4034b8cdbb1c7f4f7b9a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e721b6c8893f4034b8cdbb1c7f4f7b9a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d12514db15b942edb7fb1aa9464eab92.setContent%28html_e721b6c8893f4034b8cdbb1c7f4f7b9a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_687536ab70db4d79a0e35afc28a9be09.bindPopup%28popup_d12514db15b942edb7fb1aa9464eab92%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0df462cbde654144b8ee0fe4695bd982%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e83e809c964a48d9ac8b046699fefc48%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e67e00057a214a4cb732d9d1ef714db6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e67e00057a214a4cb732d9d1ef714db6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e83e809c964a48d9ac8b046699fefc48.setContent%28html_e67e00057a214a4cb732d9d1ef714db6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0df462cbde654144b8ee0fe4695bd982.bindPopup%28popup_e83e809c964a48d9ac8b046699fefc48%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3f8e9de4f36a4d769d4e64453023cd9a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d22d620601cd4e56967cc11ee4854611%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5d62c007a8124d3883af7db9fc964aab%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5d62c007a8124d3883af7db9fc964aab%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d22d620601cd4e56967cc11ee4854611.setContent%28html_5d62c007a8124d3883af7db9fc964aab%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3f8e9de4f36a4d769d4e64453023cd9a.bindPopup%28popup_d22d620601cd4e56967cc11ee4854611%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d16b2990154c430cbf98ba1f5d5bb5e9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_11b7f21796ac43d4bd3c5f72f36ea7b8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ee25247bb3f246daa8b9fef17f9e5a58%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ee25247bb3f246daa8b9fef17f9e5a58%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_11b7f21796ac43d4bd3c5f72f36ea7b8.setContent%28html_ee25247bb3f246daa8b9fef17f9e5a58%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d16b2990154c430cbf98ba1f5d5bb5e9.bindPopup%28popup_11b7f21796ac43d4bd3c5f72f36ea7b8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_eef756cbc1814134a082b04992b7e1dc%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c8a55fed7c9d4602b2b860b5b1dca045%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_61497c21a2124606b818f276bf922aab%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_61497c21a2124606b818f276bf922aab%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c8a55fed7c9d4602b2b860b5b1dca045.setContent%28html_61497c21a2124606b818f276bf922aab%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_eef756cbc1814134a082b04992b7e1dc.bindPopup%28popup_c8a55fed7c9d4602b2b860b5b1dca045%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a67e55fb173d49eeb97aae65b6ff08b2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_085d67d43eda446bae99a39869961d7d%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_50a2f57135ec49d6b3a66f17d0fa425d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_50a2f57135ec49d6b3a66f17d0fa425d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_085d67d43eda446bae99a39869961d7d.setContent%28html_50a2f57135ec49d6b3a66f17d0fa425d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a67e55fb173d49eeb97aae65b6ff08b2.bindPopup%28popup_085d67d43eda446bae99a39869961d7d%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2b64bcadba3547cfa0f1039116dd1b32%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_72d60af9fa3740e48337ecff4ae82051%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_78bfbaf928b64c91a3860021bacc1368%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_78bfbaf928b64c91a3860021bacc1368%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_72d60af9fa3740e48337ecff4ae82051.setContent%28html_78bfbaf928b64c91a3860021bacc1368%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2b64bcadba3547cfa0f1039116dd1b32.bindPopup%28popup_72d60af9fa3740e48337ecff4ae82051%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8468649bf9b647ca97b2747dea1ea3d8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ffd1f4f3b3da4366826520dac818a453%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_eaa1392c9390416f892f021cca99097f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_eaa1392c9390416f892f021cca99097f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ffd1f4f3b3da4366826520dac818a453.setContent%28html_eaa1392c9390416f892f021cca99097f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8468649bf9b647ca97b2747dea1ea3d8.bindPopup%28popup_ffd1f4f3b3da4366826520dac818a453%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d834206ade81475daedd0f5a3dedbbe8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d0453b11d1474bd4b3b804cf9461d44a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b3107ad36fd64da8a07e562cdd768458%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b3107ad36fd64da8a07e562cdd768458%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d0453b11d1474bd4b3b804cf9461d44a.setContent%28html_b3107ad36fd64da8a07e562cdd768458%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d834206ade81475daedd0f5a3dedbbe8.bindPopup%28popup_d0453b11d1474bd4b3b804cf9461d44a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5ffe0212bc514d9d838986eefa097dd7%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7ee81bf7b72c4c06a6363cb474fb37ae%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b677ac6456a04952bba3c85bdc98031d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b677ac6456a04952bba3c85bdc98031d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7ee81bf7b72c4c06a6363cb474fb37ae.setContent%28html_b677ac6456a04952bba3c85bdc98031d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5ffe0212bc514d9d838986eefa097dd7.bindPopup%28popup_7ee81bf7b72c4c06a6363cb474fb37ae%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6f44946a40584482bd85892d7fe9bb8e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7f8ee865463c4f95871e9958552de38b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d582b2e6e61c47d9b9f4f7ddb05820fa%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d582b2e6e61c47d9b9f4f7ddb05820fa%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7f8ee865463c4f95871e9958552de38b.setContent%28html_d582b2e6e61c47d9b9f4f7ddb05820fa%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6f44946a40584482bd85892d7fe9bb8e.bindPopup%28popup_7f8ee865463c4f95871e9958552de38b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_60b535057c5d4d64a8d57245dd7c6c9b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_efa87eac60644838891fc0cd6ff08adb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9c06ffc3e1754fa89b35e2035c6216fc%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9c06ffc3e1754fa89b35e2035c6216fc%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_efa87eac60644838891fc0cd6ff08adb.setContent%28html_9c06ffc3e1754fa89b35e2035c6216fc%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_60b535057c5d4d64a8d57245dd7c6c9b.bindPopup%28popup_efa87eac60644838891fc0cd6ff08adb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5538062af5f9487a9555795d32fae8d2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_95371583459d42f298a686c7886ec8b8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_73ef654891c94a238c0136a9a5bedc0e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_73ef654891c94a238c0136a9a5bedc0e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_95371583459d42f298a686c7886ec8b8.setContent%28html_73ef654891c94a238c0136a9a5bedc0e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5538062af5f9487a9555795d32fae8d2.bindPopup%28popup_95371583459d42f298a686c7886ec8b8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_ae442f27f3c64215833f77d1768dce29%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_13b22c700f15422caf769abebfc97c81%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c304b803b8c1427e9047133490aaf2e7%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c304b803b8c1427e9047133490aaf2e7%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_13b22c700f15422caf769abebfc97c81.setContent%28html_c304b803b8c1427e9047133490aaf2e7%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_ae442f27f3c64215833f77d1768dce29.bindPopup%28popup_13b22c700f15422caf769abebfc97c81%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_92e5484074054c028447b5721f6c83d0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_406b59ea46014adbb2368dc29137346b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ee31bb1277d5400ca536363aa9b9d2f4%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ee31bb1277d5400ca536363aa9b9d2f4%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_406b59ea46014adbb2368dc29137346b.setContent%28html_ee31bb1277d5400ca536363aa9b9d2f4%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_92e5484074054c028447b5721f6c83d0.bindPopup%28popup_406b59ea46014adbb2368dc29137346b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9559dc01c9ca4aecbd2a7c2a6150a1bc%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_eba3336c06fc456ea8b1d47f1e40aa03%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a9dab2b359364893b8ceaee4e0c8e3b0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a9dab2b359364893b8ceaee4e0c8e3b0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_eba3336c06fc456ea8b1d47f1e40aa03.setContent%28html_a9dab2b359364893b8ceaee4e0c8e3b0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9559dc01c9ca4aecbd2a7c2a6150a1bc.bindPopup%28popup_eba3336c06fc456ea8b1d47f1e40aa03%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_65c321283f44459daca2d6db0a42baea%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2839a4f07995475eb3d63ab4a290e29e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8a269123ae954ec8bd859828f3ef4c95%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8a269123ae954ec8bd859828f3ef4c95%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2839a4f07995475eb3d63ab4a290e29e.setContent%28html_8a269123ae954ec8bd859828f3ef4c95%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_65c321283f44459daca2d6db0a42baea.bindPopup%28popup_2839a4f07995475eb3d63ab4a290e29e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3186f97869944011bb7c2738a97a4bef%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_03c8886f6c794bfd8a3c9fe268117184%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0a284af0f2f4451b91fffacdcd32ee98%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0a284af0f2f4451b91fffacdcd32ee98%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_03c8886f6c794bfd8a3c9fe268117184.setContent%28html_0a284af0f2f4451b91fffacdcd32ee98%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3186f97869944011bb7c2738a97a4bef.bindPopup%28popup_03c8886f6c794bfd8a3c9fe268117184%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a7ebe5259755460d8cc19f4e8bd7212f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_639741fdaabe4464a506e57b322eefec%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2e9f022fe600446c896fddd655f91d3b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2e9f022fe600446c896fddd655f91d3b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_639741fdaabe4464a506e57b322eefec.setContent%28html_2e9f022fe600446c896fddd655f91d3b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a7ebe5259755460d8cc19f4e8bd7212f.bindPopup%28popup_639741fdaabe4464a506e57b322eefec%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_241d1d03b6a14b798cde82deb6681c81%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9bc5023fe5624ea18a09cc55709bc96a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_304826831fd24948bb033688e5b86429%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_304826831fd24948bb033688e5b86429%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9bc5023fe5624ea18a09cc55709bc96a.setContent%28html_304826831fd24948bb033688e5b86429%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_241d1d03b6a14b798cde82deb6681c81.bindPopup%28popup_9bc5023fe5624ea18a09cc55709bc96a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e2f04132fe8744c4b052f5b73f473609%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22popu%22%3A%20%22Est%5Cu00e1s%20en%20Zaragoza%22%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



Ahora, vamos a añadir un marcador a cada una de las coordenadas de nuestra tabla. Para ello, utilizaremos la función `iterrows` que sirve para marcar todos los elementos de la fila


```python
longitudes = []
for i in df['geometry']:
    longlat = i.split(',')
    longitudes += [float(longlat[0])]
latitudes = []
for i in df['geometry']:
    longlat = i.split(',')
    latitudes += [float(longlat[1])]
df_coord = pd.DataFrame({'long':longitudes, 'lat': latitudes})
df_tipo = pd.concat([df['type'],df_coord], axis=1)
for index, fila in df_tipo.iterrows():
    marcador = folium.Marker([fila['lat'],fila['long']],popup=fila['type'])
    mapa.add_child(marcador)
mapa
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><span style="color:#565656">Make this Notebook Trusted to load map: File -> Trust Notebook</span><iframe src="about:blank" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" data-html=%3C%21DOCTYPE%20html%3E%0A%3Chead%3E%20%20%20%20%0A%20%20%20%20%3Cmeta%20http-equiv%3D%22content-type%22%20content%3D%22text/html%3B%20charset%3DUTF-8%22%20/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%3Cscript%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20L_NO_TOUCH%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20L_DISABLE_3D%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%3C/script%3E%0A%20%20%20%20%0A%20%20%20%20%3Cstyle%3Ehtml%2C%20body%20%7Bwidth%3A%20100%25%3Bheight%3A%20100%25%3Bmargin%3A%200%3Bpadding%3A%200%3B%7D%3C/style%3E%0A%20%20%20%20%3Cstyle%3E%23map%20%7Bposition%3Aabsolute%3Btop%3A0%3Bbottom%3A0%3Bright%3A0%3Bleft%3A0%3B%7D%3C/style%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//code.jquery.com/jquery-1.12.4.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/js/bootstrap.min.js%22%3E%3C/script%3E%0A%20%20%20%20%3Cscript%20src%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.js%22%3E%3C/script%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/npm/leaflet%401.6.0/dist/leaflet.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/bootstrap/3.2.0/css/bootstrap-theme.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdnjs.cloudflare.com/ajax/libs/Leaflet.awesome-markers/2.0.2/leaflet.awesome-markers.css%22/%3E%0A%20%20%20%20%3Clink%20rel%3D%22stylesheet%22%20href%3D%22https%3A//cdn.jsdelivr.net/gh/python-visualization/folium/folium/templates/leaflet.awesome.rotate.min.css%22/%3E%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cmeta%20name%3D%22viewport%22%20content%3D%22width%3Ddevice-width%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20initial-scale%3D1.0%2C%20maximum-scale%3D1.0%2C%20user-scalable%3Dno%22%20/%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cstyle%3E%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%23map_b1bb0f366cc64380a7465b988c3bdc99%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20position%3A%20relative%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20width%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20height%3A%20100.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20left%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20top%3A%200.0%25%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%3C/style%3E%0A%20%20%20%20%20%20%20%20%0A%3C/head%3E%0A%3Cbody%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%3Cdiv%20class%3D%22folium-map%22%20id%3D%22map_b1bb0f366cc64380a7465b988c3bdc99%22%20%3E%3C/div%3E%0A%20%20%20%20%20%20%20%20%0A%3C/body%3E%0A%3Cscript%3E%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20map_b1bb0f366cc64380a7465b988c3bdc99%20%3D%20L.map%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22map_b1bb0f366cc64380a7465b988c3bdc99%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20center%3A%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20crs%3A%20L.CRS.EPSG3857%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoom%3A%2010%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20zoomControl%3A%20true%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20preferCanvas%3A%20false%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29%3B%0A%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20tile_layer_cfc2b741198e4ac790fcb9ce75d5aac7%20%3D%20L.tileLayer%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%22https%3A//%7Bs%7D.tile.openstreetmap.org/%7Bz%7D/%7Bx%7D/%7By%7D.png%22%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22attribution%22%3A%20%22Data%20by%20%5Cu0026copy%3B%20%5Cu003ca%20href%3D%5C%22http%3A//openstreetmap.org%5C%22%5Cu003eOpenStreetMap%5Cu003c/a%5Cu003e%2C%20under%20%5Cu003ca%20href%3D%5C%22http%3A//www.openstreetmap.org/copyright%5C%22%5Cu003eODbL%5Cu003c/a%5Cu003e.%22%2C%20%22detectRetina%22%3A%20false%2C%20%22maxNativeZoom%22%3A%2018%2C%20%22maxZoom%22%3A%2018%2C%20%22minZoom%22%3A%200%2C%20%22noWrap%22%3A%20false%2C%20%22opacity%22%3A%201%2C%20%22subdomains%22%3A%20%22abc%22%2C%20%22tms%22%3A%20false%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dce8a7e4ebb84eecbc66208ef27a876c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22popu%22%3A%20%22Est%5Cu00e1s%20en%20Zaragoza%22%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f8d81941ec7d44968e04854e0cb71556%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_19514db429694414bffb4550a89c8944%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_12c14883a2744fe791987997e4d6a0d0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_12c14883a2744fe791987997e4d6a0d0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_19514db429694414bffb4550a89c8944.setContent%28html_12c14883a2744fe791987997e4d6a0d0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f8d81941ec7d44968e04854e0cb71556.bindPopup%28popup_19514db429694414bffb4550a89c8944%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8e4c98a4115f472aa179077b0d805bad%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6eb53c842e254f9c8a85117e372940ea%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_bd7cfa70c8be4016bcce97743b46cf27%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_bd7cfa70c8be4016bcce97743b46cf27%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6eb53c842e254f9c8a85117e372940ea.setContent%28html_bd7cfa70c8be4016bcce97743b46cf27%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8e4c98a4115f472aa179077b0d805bad.bindPopup%28popup_6eb53c842e254f9c8a85117e372940ea%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e932c251b13f4c039f233e4f0af447a4%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2494d1351d8a4fd69c33e27c184b856e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d8f4c0c0a57f46b0993d0a7b4b7054e9%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d8f4c0c0a57f46b0993d0a7b4b7054e9%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2494d1351d8a4fd69c33e27c184b856e.setContent%28html_d8f4c0c0a57f46b0993d0a7b4b7054e9%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e932c251b13f4c039f233e4f0af447a4.bindPopup%28popup_2494d1351d8a4fd69c33e27c184b856e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1a01a22a477a45aeb4f1cb30022daac2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_fba40d60d1fa41708a233c088ff5e173%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3150bba1bc6a4804bfc337114e2f9556%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3150bba1bc6a4804bfc337114e2f9556%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_fba40d60d1fa41708a233c088ff5e173.setContent%28html_3150bba1bc6a4804bfc337114e2f9556%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1a01a22a477a45aeb4f1cb30022daac2.bindPopup%28popup_fba40d60d1fa41708a233c088ff5e173%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c20d1c7b45d34ac399b05c7894224194%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_17567a96b70a40eb8d2863d25b042df3%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a90fdac0261541699f9fb515bd1a757f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a90fdac0261541699f9fb515bd1a757f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_17567a96b70a40eb8d2863d25b042df3.setContent%28html_a90fdac0261541699f9fb515bd1a757f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c20d1c7b45d34ac399b05c7894224194.bindPopup%28popup_17567a96b70a40eb8d2863d25b042df3%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_86a6ed88a9114520a80c5c020a5f036b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_970627018b3a45d88d769e141f0a576a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_62e03e2ae42c43c78f0b1ea556da74e7%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_62e03e2ae42c43c78f0b1ea556da74e7%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_970627018b3a45d88d769e141f0a576a.setContent%28html_62e03e2ae42c43c78f0b1ea556da74e7%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_86a6ed88a9114520a80c5c020a5f036b.bindPopup%28popup_970627018b3a45d88d769e141f0a576a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d879727743e5432e90741372e580b315%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1c13709d0432487496c37eeabdcbe82f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6eabcd7038cf4cdbbaf39886827edb3b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6eabcd7038cf4cdbbaf39886827edb3b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1c13709d0432487496c37eeabdcbe82f.setContent%28html_6eabcd7038cf4cdbbaf39886827edb3b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d879727743e5432e90741372e580b315.bindPopup%28popup_1c13709d0432487496c37eeabdcbe82f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_fbd5ad49325f4c2d9acf6d0a28acb282%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0245d204a533464f87323fa8762709cb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_57d2278f190f407593c45e36db8f81f0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_57d2278f190f407593c45e36db8f81f0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0245d204a533464f87323fa8762709cb.setContent%28html_57d2278f190f407593c45e36db8f81f0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_fbd5ad49325f4c2d9acf6d0a28acb282.bindPopup%28popup_0245d204a533464f87323fa8762709cb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_20bab71bc9724c888bfb0a3d1ac7c3f2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_366391888b16458982a4327424bd89ab%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_983e01242e79403881e53a64aa59a984%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_983e01242e79403881e53a64aa59a984%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_366391888b16458982a4327424bd89ab.setContent%28html_983e01242e79403881e53a64aa59a984%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_20bab71bc9724c888bfb0a3d1ac7c3f2.bindPopup%28popup_366391888b16458982a4327424bd89ab%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f9d31572ed9a4a558fd292fa776e312e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_33cb3e0c5159419fa88cf20da08e9d08%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2c2d32f470c645c3903ae4140cdc0721%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2c2d32f470c645c3903ae4140cdc0721%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_33cb3e0c5159419fa88cf20da08e9d08.setContent%28html_2c2d32f470c645c3903ae4140cdc0721%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f9d31572ed9a4a558fd292fa776e312e.bindPopup%28popup_33cb3e0c5159419fa88cf20da08e9d08%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bc83d296362d464197144b01ae590313%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a7a9441a637b418f84ee09f0d5674e25%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_415409a47a494b2bb78ce7294ad0d70b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_415409a47a494b2bb78ce7294ad0d70b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a7a9441a637b418f84ee09f0d5674e25.setContent%28html_415409a47a494b2bb78ce7294ad0d70b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bc83d296362d464197144b01ae590313.bindPopup%28popup_a7a9441a637b418f84ee09f0d5674e25%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f766c82133b6498199d0dd6403e8ab62%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b9ad0ed5ff84470bb089b18a1586c2c1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_3c080511a0654bdc88d0e6ab4db6ff37%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_3c080511a0654bdc88d0e6ab4db6ff37%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b9ad0ed5ff84470bb089b18a1586c2c1.setContent%28html_3c080511a0654bdc88d0e6ab4db6ff37%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f766c82133b6498199d0dd6403e8ab62.bindPopup%28popup_b9ad0ed5ff84470bb089b18a1586c2c1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b9ad966a5186406bb86b92ad1b9aaa26%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3cf81ed9ba854fa19121d373d320b722%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_29a2dd52e9a447da88be8b4611b4dea6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_29a2dd52e9a447da88be8b4611b4dea6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3cf81ed9ba854fa19121d373d320b722.setContent%28html_29a2dd52e9a447da88be8b4611b4dea6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b9ad966a5186406bb86b92ad1b9aaa26.bindPopup%28popup_3cf81ed9ba854fa19121d373d320b722%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dbae2d0d9e7e436ba590729d268e555d%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_684de62c4c9d4cdb8b40f91058157aed%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6cb4b4f5e33d416a9cea97b30a5e4144%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6cb4b4f5e33d416a9cea97b30a5e4144%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_684de62c4c9d4cdb8b40f91058157aed.setContent%28html_6cb4b4f5e33d416a9cea97b30a5e4144%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dbae2d0d9e7e436ba590729d268e555d.bindPopup%28popup_684de62c4c9d4cdb8b40f91058157aed%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_f71f6a3acc124901b293211e4414b982%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6dc712a7c64545f7bef6c209627d56d8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_6caf6ac8e75e452a8cc5d26682e39b4c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_6caf6ac8e75e452a8cc5d26682e39b4c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6dc712a7c64545f7bef6c209627d56d8.setContent%28html_6caf6ac8e75e452a8cc5d26682e39b4c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_f71f6a3acc124901b293211e4414b982.bindPopup%28popup_6dc712a7c64545f7bef6c209627d56d8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_737a249b0b1646189083ee0c99da8750%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_716597041c6444f2b77f13a73fb4a700%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e0a74bf6a11b45618dbf8e36715a25b8%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e0a74bf6a11b45618dbf8e36715a25b8%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_716597041c6444f2b77f13a73fb4a700.setContent%28html_e0a74bf6a11b45618dbf8e36715a25b8%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_737a249b0b1646189083ee0c99da8750.bindPopup%28popup_716597041c6444f2b77f13a73fb4a700%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b460fcb8315c4c50aa309640f2144daf%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b36f326f8d414f0489fc4a3a140641cb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c319ebc802ef439bba8bba8636d1f8aa%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c319ebc802ef439bba8bba8636d1f8aa%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b36f326f8d414f0489fc4a3a140641cb.setContent%28html_c319ebc802ef439bba8bba8636d1f8aa%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b460fcb8315c4c50aa309640f2144daf.bindPopup%28popup_b36f326f8d414f0489fc4a3a140641cb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_74f85d2cf4234a23a864e950578ceccb%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4199acaa11b84369bbd5a2a1f11a7946%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2fb4c57433574bb891944b7bebbd82d6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2fb4c57433574bb891944b7bebbd82d6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4199acaa11b84369bbd5a2a1f11a7946.setContent%28html_2fb4c57433574bb891944b7bebbd82d6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_74f85d2cf4234a23a864e950578ceccb.bindPopup%28popup_4199acaa11b84369bbd5a2a1f11a7946%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a9e47fd9bdb54b0e859880af56476d01%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_32e5979d05754174a37429d48bfb20b5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2f4008fb2c5546278fc48af01b4d21c4%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2f4008fb2c5546278fc48af01b4d21c4%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_32e5979d05754174a37429d48bfb20b5.setContent%28html_2f4008fb2c5546278fc48af01b4d21c4%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a9e47fd9bdb54b0e859880af56476d01.bindPopup%28popup_32e5979d05754174a37429d48bfb20b5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a5110bf1c3034bf39a517228f2ead4d9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9cee316d96144bf0938f93355e25b530%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0928584b16e04b86bbfed8b328c04207%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0928584b16e04b86bbfed8b328c04207%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9cee316d96144bf0938f93355e25b530.setContent%28html_0928584b16e04b86bbfed8b328c04207%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a5110bf1c3034bf39a517228f2ead4d9.bindPopup%28popup_9cee316d96144bf0938f93355e25b530%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_687536ab70db4d79a0e35afc28a9be09%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d12514db15b942edb7fb1aa9464eab92%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e721b6c8893f4034b8cdbb1c7f4f7b9a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e721b6c8893f4034b8cdbb1c7f4f7b9a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d12514db15b942edb7fb1aa9464eab92.setContent%28html_e721b6c8893f4034b8cdbb1c7f4f7b9a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_687536ab70db4d79a0e35afc28a9be09.bindPopup%28popup_d12514db15b942edb7fb1aa9464eab92%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0df462cbde654144b8ee0fe4695bd982%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_e83e809c964a48d9ac8b046699fefc48%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e67e00057a214a4cb732d9d1ef714db6%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e67e00057a214a4cb732d9d1ef714db6%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_e83e809c964a48d9ac8b046699fefc48.setContent%28html_e67e00057a214a4cb732d9d1ef714db6%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0df462cbde654144b8ee0fe4695bd982.bindPopup%28popup_e83e809c964a48d9ac8b046699fefc48%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3f8e9de4f36a4d769d4e64453023cd9a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d22d620601cd4e56967cc11ee4854611%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5d62c007a8124d3883af7db9fc964aab%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5d62c007a8124d3883af7db9fc964aab%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d22d620601cd4e56967cc11ee4854611.setContent%28html_5d62c007a8124d3883af7db9fc964aab%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3f8e9de4f36a4d769d4e64453023cd9a.bindPopup%28popup_d22d620601cd4e56967cc11ee4854611%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d16b2990154c430cbf98ba1f5d5bb5e9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_11b7f21796ac43d4bd3c5f72f36ea7b8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ee25247bb3f246daa8b9fef17f9e5a58%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ee25247bb3f246daa8b9fef17f9e5a58%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_11b7f21796ac43d4bd3c5f72f36ea7b8.setContent%28html_ee25247bb3f246daa8b9fef17f9e5a58%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d16b2990154c430cbf98ba1f5d5bb5e9.bindPopup%28popup_11b7f21796ac43d4bd3c5f72f36ea7b8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_eef756cbc1814134a082b04992b7e1dc%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c8a55fed7c9d4602b2b860b5b1dca045%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_61497c21a2124606b818f276bf922aab%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_61497c21a2124606b818f276bf922aab%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c8a55fed7c9d4602b2b860b5b1dca045.setContent%28html_61497c21a2124606b818f276bf922aab%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_eef756cbc1814134a082b04992b7e1dc.bindPopup%28popup_c8a55fed7c9d4602b2b860b5b1dca045%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a67e55fb173d49eeb97aae65b6ff08b2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_085d67d43eda446bae99a39869961d7d%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_50a2f57135ec49d6b3a66f17d0fa425d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_50a2f57135ec49d6b3a66f17d0fa425d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_085d67d43eda446bae99a39869961d7d.setContent%28html_50a2f57135ec49d6b3a66f17d0fa425d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a67e55fb173d49eeb97aae65b6ff08b2.bindPopup%28popup_085d67d43eda446bae99a39869961d7d%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2b64bcadba3547cfa0f1039116dd1b32%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_72d60af9fa3740e48337ecff4ae82051%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_78bfbaf928b64c91a3860021bacc1368%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_78bfbaf928b64c91a3860021bacc1368%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_72d60af9fa3740e48337ecff4ae82051.setContent%28html_78bfbaf928b64c91a3860021bacc1368%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2b64bcadba3547cfa0f1039116dd1b32.bindPopup%28popup_72d60af9fa3740e48337ecff4ae82051%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8468649bf9b647ca97b2747dea1ea3d8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_ffd1f4f3b3da4366826520dac818a453%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_eaa1392c9390416f892f021cca99097f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_eaa1392c9390416f892f021cca99097f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_ffd1f4f3b3da4366826520dac818a453.setContent%28html_eaa1392c9390416f892f021cca99097f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8468649bf9b647ca97b2747dea1ea3d8.bindPopup%28popup_ffd1f4f3b3da4366826520dac818a453%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d834206ade81475daedd0f5a3dedbbe8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_d0453b11d1474bd4b3b804cf9461d44a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b3107ad36fd64da8a07e562cdd768458%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b3107ad36fd64da8a07e562cdd768458%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_d0453b11d1474bd4b3b804cf9461d44a.setContent%28html_b3107ad36fd64da8a07e562cdd768458%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d834206ade81475daedd0f5a3dedbbe8.bindPopup%28popup_d0453b11d1474bd4b3b804cf9461d44a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5ffe0212bc514d9d838986eefa097dd7%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7ee81bf7b72c4c06a6363cb474fb37ae%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b677ac6456a04952bba3c85bdc98031d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b677ac6456a04952bba3c85bdc98031d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7ee81bf7b72c4c06a6363cb474fb37ae.setContent%28html_b677ac6456a04952bba3c85bdc98031d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5ffe0212bc514d9d838986eefa097dd7.bindPopup%28popup_7ee81bf7b72c4c06a6363cb474fb37ae%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6f44946a40584482bd85892d7fe9bb8e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_7f8ee865463c4f95871e9958552de38b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d582b2e6e61c47d9b9f4f7ddb05820fa%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d582b2e6e61c47d9b9f4f7ddb05820fa%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_7f8ee865463c4f95871e9958552de38b.setContent%28html_d582b2e6e61c47d9b9f4f7ddb05820fa%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6f44946a40584482bd85892d7fe9bb8e.bindPopup%28popup_7f8ee865463c4f95871e9958552de38b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_60b535057c5d4d64a8d57245dd7c6c9b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_efa87eac60644838891fc0cd6ff08adb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_9c06ffc3e1754fa89b35e2035c6216fc%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_9c06ffc3e1754fa89b35e2035c6216fc%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_efa87eac60644838891fc0cd6ff08adb.setContent%28html_9c06ffc3e1754fa89b35e2035c6216fc%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_60b535057c5d4d64a8d57245dd7c6c9b.bindPopup%28popup_efa87eac60644838891fc0cd6ff08adb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_5538062af5f9487a9555795d32fae8d2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_95371583459d42f298a686c7886ec8b8%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_73ef654891c94a238c0136a9a5bedc0e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_73ef654891c94a238c0136a9a5bedc0e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_95371583459d42f298a686c7886ec8b8.setContent%28html_73ef654891c94a238c0136a9a5bedc0e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_5538062af5f9487a9555795d32fae8d2.bindPopup%28popup_95371583459d42f298a686c7886ec8b8%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_ae442f27f3c64215833f77d1768dce29%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_13b22c700f15422caf769abebfc97c81%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c304b803b8c1427e9047133490aaf2e7%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c304b803b8c1427e9047133490aaf2e7%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_13b22c700f15422caf769abebfc97c81.setContent%28html_c304b803b8c1427e9047133490aaf2e7%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_ae442f27f3c64215833f77d1768dce29.bindPopup%28popup_13b22c700f15422caf769abebfc97c81%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_92e5484074054c028447b5721f6c83d0%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_406b59ea46014adbb2368dc29137346b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ee31bb1277d5400ca536363aa9b9d2f4%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ee31bb1277d5400ca536363aa9b9d2f4%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_406b59ea46014adbb2368dc29137346b.setContent%28html_ee31bb1277d5400ca536363aa9b9d2f4%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_92e5484074054c028447b5721f6c83d0.bindPopup%28popup_406b59ea46014adbb2368dc29137346b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9559dc01c9ca4aecbd2a7c2a6150a1bc%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_eba3336c06fc456ea8b1d47f1e40aa03%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a9dab2b359364893b8ceaee4e0c8e3b0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a9dab2b359364893b8ceaee4e0c8e3b0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_eba3336c06fc456ea8b1d47f1e40aa03.setContent%28html_a9dab2b359364893b8ceaee4e0c8e3b0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9559dc01c9ca4aecbd2a7c2a6150a1bc.bindPopup%28popup_eba3336c06fc456ea8b1d47f1e40aa03%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_65c321283f44459daca2d6db0a42baea%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2839a4f07995475eb3d63ab4a290e29e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_8a269123ae954ec8bd859828f3ef4c95%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_8a269123ae954ec8bd859828f3ef4c95%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2839a4f07995475eb3d63ab4a290e29e.setContent%28html_8a269123ae954ec8bd859828f3ef4c95%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_65c321283f44459daca2d6db0a42baea.bindPopup%28popup_2839a4f07995475eb3d63ab4a290e29e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_3186f97869944011bb7c2738a97a4bef%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_03c8886f6c794bfd8a3c9fe268117184%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0a284af0f2f4451b91fffacdcd32ee98%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0a284af0f2f4451b91fffacdcd32ee98%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_03c8886f6c794bfd8a3c9fe268117184.setContent%28html_0a284af0f2f4451b91fffacdcd32ee98%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_3186f97869944011bb7c2738a97a4bef.bindPopup%28popup_03c8886f6c794bfd8a3c9fe268117184%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a7ebe5259755460d8cc19f4e8bd7212f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_639741fdaabe4464a506e57b322eefec%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2e9f022fe600446c896fddd655f91d3b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2e9f022fe600446c896fddd655f91d3b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_639741fdaabe4464a506e57b322eefec.setContent%28html_2e9f022fe600446c896fddd655f91d3b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a7ebe5259755460d8cc19f4e8bd7212f.bindPopup%28popup_639741fdaabe4464a506e57b322eefec%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_241d1d03b6a14b798cde82deb6681c81%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9bc5023fe5624ea18a09cc55709bc96a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_304826831fd24948bb033688e5b86429%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_304826831fd24948bb033688e5b86429%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9bc5023fe5624ea18a09cc55709bc96a.setContent%28html_304826831fd24948bb033688e5b86429%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_241d1d03b6a14b798cde82deb6681c81.bindPopup%28popup_9bc5023fe5624ea18a09cc55709bc96a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e2f04132fe8744c4b052f5b73f473609%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649693%2C%20-0.887712%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%22popu%22%3A%20%22Est%5Cu00e1s%20en%20Zaragoza%22%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_a87ab22a7422485fad3974185f4ef87e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8818527060979306%2C%2041.649027473051156%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_047c2205600e4eb986110b9b9bc6cbfb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_76e5f085be9c470a9e92adfdcc29e2ce%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_76e5f085be9c470a9e92adfdcc29e2ce%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_047c2205600e4eb986110b9b9bc6cbfb.setContent%28html_76e5f085be9c470a9e92adfdcc29e2ce%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_a87ab22a7422485fad3974185f4ef87e.bindPopup%28popup_047c2205600e4eb986110b9b9bc6cbfb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e6849a0abd20453cb830607ec8dc2f7e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8645810716721081%2C%2041.661585829868585%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_14a2ceff4f4441cc9a560f7caa8a275d%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a94c914e8dee47d28529b8f4b3e117cb%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a94c914e8dee47d28529b8f4b3e117cb%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_14a2ceff4f4441cc9a560f7caa8a275d.setContent%28html_a94c914e8dee47d28529b8f4b3e117cb%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e6849a0abd20453cb830607ec8dc2f7e.bindPopup%28popup_14a2ceff4f4441cc9a560f7caa8a275d%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_66067a3993d541de89127cd4d6d8e151%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.887776415002892%2C%2041.666992622958105%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_cff5302594a24720915e4fe214eb1966%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1118c8b0fa044521ab0d3a1bac5d2f7e%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1118c8b0fa044521ab0d3a1bac5d2f7e%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_cff5302594a24720915e4fe214eb1966.setContent%28html_1118c8b0fa044521ab0d3a1bac5d2f7e%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_66067a3993d541de89127cd4d6d8e151.bindPopup%28popup_cff5302594a24720915e4fe214eb1966%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0b9763ad1ed542da8829e3be04f806ee%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8825260453930127%2C%2041.62957498750602%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4d9a0d40bad2498e833eb119a9d5dcd3%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_5e315334ad5643188a8543e2c48855a9%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_5e315334ad5643188a8543e2c48855a9%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4d9a0d40bad2498e833eb119a9d5dcd3.setContent%28html_5e315334ad5643188a8543e2c48855a9%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0b9763ad1ed542da8829e3be04f806ee.bindPopup%28popup_4d9a0d40bad2498e833eb119a9d5dcd3%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1ff7d8ee99044d79acb3939f8f84927b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.908314757720389%2C%2041.6562121210704%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_43221e03d28042b988748d591cccb29a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_87da215aa56e4ae591ba2d4a65693a78%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_87da215aa56e4ae591ba2d4a65693a78%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_43221e03d28042b988748d591cccb29a.setContent%28html_87da215aa56e4ae591ba2d4a65693a78%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1ff7d8ee99044d79acb3939f8f84927b.bindPopup%28popup_43221e03d28042b988748d591cccb29a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_1648ca3a4a9342e5b02399dc6e29a575%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8691088511672924%2C%2041.65949772773082%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f5f77f2cccd14329907dc3d772e4399e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_7ecfd04f1d184a878e16a3c2d2f3e7ad%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_7ecfd04f1d184a878e16a3c2d2f3e7ad%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f5f77f2cccd14329907dc3d772e4399e.setContent%28html_7ecfd04f1d184a878e16a3c2d2f3e7ad%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_1648ca3a4a9342e5b02399dc6e29a575.bindPopup%28popup_f5f77f2cccd14329907dc3d772e4399e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_47a91c611a7a491b95e67c3ba1471774%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8880337913721866%2C%2041.633353667694024%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4cd4fdbb3912441998dd9532ea3087b5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_4236990abce04c16b6653d2652b6ec8c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_4236990abce04c16b6653d2652b6ec8c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4cd4fdbb3912441998dd9532ea3087b5.setContent%28html_4236990abce04c16b6653d2652b6ec8c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_47a91c611a7a491b95e67c3ba1471774.bindPopup%28popup_4cd4fdbb3912441998dd9532ea3087b5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e680a04ad68a4b08b3d31a7f68aa5226%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8708838775078237%2C%2041.6390382112928%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c484edb328804fe1a5c699014a62e22a%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a02015bea8d64ae7b159949b2f76c3ee%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a02015bea8d64ae7b159949b2f76c3ee%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c484edb328804fe1a5c699014a62e22a.setContent%28html_a02015bea8d64ae7b159949b2f76c3ee%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e680a04ad68a4b08b3d31a7f68aa5226.bindPopup%28popup_c484edb328804fe1a5c699014a62e22a%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c0a1fa3a6d5f4ad4b4d5846e8518f0df%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8970649943808023%2C%2041.64083344974765%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_fa036d746fe04236a2f9408acabe1eb1%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d80ee02e2f07474da638a6089272ab1f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d80ee02e2f07474da638a6089272ab1f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_fa036d746fe04236a2f9408acabe1eb1.setContent%28html_d80ee02e2f07474da638a6089272ab1f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c0a1fa3a6d5f4ad4b4d5846e8518f0df.bindPopup%28popup_fa036d746fe04236a2f9408acabe1eb1%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_ca1ffef484954e4ea39cfbb53c77135a%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8718525605769747%2C%2041.64904657717317%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_556fe441a6f84ae6b6b8f782850df946%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_729b029aad4040f6ba06bb12c546679d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_729b029aad4040f6ba06bb12c546679d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_556fe441a6f84ae6b6b8f782850df946.setContent%28html_729b029aad4040f6ba06bb12c546679d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_ca1ffef484954e4ea39cfbb53c77135a.bindPopup%28popup_556fe441a6f84ae6b6b8f782850df946%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_02eb68509fe44a8c9e93573810cc52f8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8964627561577849%2C%2041.64322365075108%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_060d4b6807c74a948733e3497dc12ad7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b5a7ac8dbf88448499cf58bb977cfe09%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b5a7ac8dbf88448499cf58bb977cfe09%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_060d4b6807c74a948733e3497dc12ad7.setContent%28html_b5a7ac8dbf88448499cf58bb977cfe09%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_02eb68509fe44a8c9e93573810cc52f8.bindPopup%28popup_060d4b6807c74a948733e3497dc12ad7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7165114cdfb745338c39470183bcc8bd%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8778095796207178%2C%2041.68753087470739%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_56fd6c99e0ff4832b84a30a5db109943%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_da945dc4501f417883d03f30ce8f6faf%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_da945dc4501f417883d03f30ce8f6faf%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_56fd6c99e0ff4832b84a30a5db109943.setContent%28html_da945dc4501f417883d03f30ce8f6faf%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7165114cdfb745338c39470183bcc8bd.bindPopup%28popup_56fd6c99e0ff4832b84a30a5db109943%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_86cdaf7c78c142b4879e895cb5022c17%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8812157329722801%2C%2041.661646612715046%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_1c79728be1e34f6d87fc2268781b132f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_4156485c27384f17a773998ffeb12f81%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_4156485c27384f17a773998ffeb12f81%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_1c79728be1e34f6d87fc2268781b132f.setContent%28html_4156485c27384f17a773998ffeb12f81%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_86cdaf7c78c142b4879e895cb5022c17.bindPopup%28popup_1c79728be1e34f6d87fc2268781b132f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_377311ac668b4310bbbc1f4ce059e690%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8762000299022707%2C%2041.6454384961757%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a83317e65ce44e50b40ead48d9b0fd60%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1c69728c5f5a4192b7abfc63d085550f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1c69728c5f5a4192b7abfc63d085550f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a83317e65ce44e50b40ead48d9b0fd60.setContent%28html_1c69728c5f5a4192b7abfc63d085550f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_377311ac668b4310bbbc1f4ce059e690.bindPopup%28popup_a83317e65ce44e50b40ead48d9b0fd60%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e4aa5dab02914e93b4bfb09d4472d4d1%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9089013552408617%2C%2041.65543768899759%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_b4f421cd400b4829bdfe88453ca44826%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_2a2b281d8ace46cebc7109431faa4fec%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_2a2b281d8ace46cebc7109431faa4fec%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_b4f421cd400b4829bdfe88453ca44826.setContent%28html_2a2b281d8ace46cebc7109431faa4fec%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e4aa5dab02914e93b4bfb09d4472d4d1.bindPopup%28popup_b4f421cd400b4829bdfe88453ca44826%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0a73f38695d84bae8051612806ddf1b9%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.9004729973337304%2C%2041.65180346604993%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4d538a9c358b4e4a86a90e327973de2e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_c73bbb294a844f23b67669d0b4907057%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_c73bbb294a844f23b67669d0b4907057%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4d538a9c358b4e4a86a90e327973de2e.setContent%28html_c73bbb294a844f23b67669d0b4907057%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0a73f38695d84bae8051612806ddf1b9.bindPopup%28popup_4d538a9c358b4e4a86a90e327973de2e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_0f00b575f30946b2aa5241553aa1e009%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8917562993466011%2C%2041.65233828238132%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_0efdad0532ad426282b155147bc5215f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e175c122063b455aa3feb4c4da3ede9b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e175c122063b455aa3feb4c4da3ede9b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_0efdad0532ad426282b155147bc5215f.setContent%28html_e175c122063b455aa3feb4c4da3ede9b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_0f00b575f30946b2aa5241553aa1e009.bindPopup%28popup_0efdad0532ad426282b155147bc5215f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bb7ffddf0d174b428290ab718aca30fa%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.888856043735591%2C%2041.65040494617356%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_3ade97c7193a4f558313c8492260064c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_0af3334089244cf6968a5d528fe6895b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_0af3334089244cf6968a5d528fe6895b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_3ade97c7193a4f558313c8492260064c.setContent%28html_0af3334089244cf6968a5d528fe6895b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bb7ffddf0d174b428290ab718aca30fa.bindPopup%28popup_3ade97c7193a4f558313c8492260064c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7857f28e5b2147928b80b7ee924a49a6%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8629911318784169%2C%2041.645335650478316%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_701fe7f46a164243be1531654ee4f8a9%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b98f8937f481480e876670a60d3d7695%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b98f8937f481480e876670a60d3d7695%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_701fe7f46a164243be1531654ee4f8a9.setContent%28html_b98f8937f481480e876670a60d3d7695%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7857f28e5b2147928b80b7ee924a49a6.bindPopup%28popup_701fe7f46a164243be1531654ee4f8a9%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_765077f8eec6477aa072bef0d0766c9c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B-0.8870207060655807%2C%2041.609992514227066%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_702da67ee09f40d299c8843e700b421c%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_4b31b48fb2c74d3590bca00687567584%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_4b31b48fb2c74d3590bca00687567584%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_702da67ee09f40d299c8843e700b421c.setContent%28html_4b31b48fb2c74d3590bca00687567584%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_765077f8eec6477aa072bef0d0766c9c.bindPopup%28popup_702da67ee09f40d299c8843e700b421c%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_2acf4af059014983a414fafbf269bca8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.649027473051156%2C%20-0.8818527060979306%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_c5606d749f814b2ca6800d8a4409ce93%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_b40632d3dee2475e802609d8c46f4551%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_b40632d3dee2475e802609d8c46f4551%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_c5606d749f814b2ca6800d8a4409ce93.setContent%28html_b40632d3dee2475e802609d8c46f4551%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_2acf4af059014983a414fafbf269bca8.bindPopup%28popup_c5606d749f814b2ca6800d8a4409ce93%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_d78dfe3703c94db9acc1d42662dc6802%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.661585829868585%2C%20-0.8645810716721081%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_9571775c0c9d4b6ea9a388201131cd26%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_a07fdddfb9794463969d9984bf7c288c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_a07fdddfb9794463969d9984bf7c288c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_9571775c0c9d4b6ea9a388201131cd26.setContent%28html_a07fdddfb9794463969d9984bf7c288c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_d78dfe3703c94db9acc1d42662dc6802.bindPopup%28popup_9571775c0c9d4b6ea9a388201131cd26%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bc9b0b3e22cb4528980fcb1ba011163c%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.666992622958105%2C%20-0.887776415002892%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_348b6294c20a468fa551b028cd6bf774%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_ea949f960bc9406bb4804e8e832e10b0%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_ea949f960bc9406bb4804e8e832e10b0%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_348b6294c20a468fa551b028cd6bf774.setContent%28html_ea949f960bc9406bb4804e8e832e10b0%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bc9b0b3e22cb4528980fcb1ba011163c.bindPopup%28popup_348b6294c20a468fa551b028cd6bf774%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7a16df78a2c44763a123edd72c2b3d3f%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.62957498750602%2C%20-0.8825260453930127%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f49379f335e04289bb227d3c864db29f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_46667324dfc54975af19b918b6126f0f%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_46667324dfc54975af19b918b6126f0f%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS%20FRONTOLATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f49379f335e04289bb227d3c864db29f.setContent%28html_46667324dfc54975af19b918b6126f0f%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7a16df78a2c44763a123edd72c2b3d3f.bindPopup%28popup_f49379f335e04289bb227d3c864db29f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_e8318a745b014e6d945754374cf67152%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6562121210704%2C%20-0.908314757720389%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_32625faf988f460fa299143abcf7243d%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1fe32c9ddd114cb5a2a80b2d699c1c48%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1fe32c9ddd114cb5a2a80b2d699c1c48%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_32625faf988f460fa299143abcf7243d.setContent%28html_1fe32c9ddd114cb5a2a80b2d699c1c48%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_e8318a745b014e6d945754374cf67152.bindPopup%28popup_32625faf988f460fa299143abcf7243d%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6d90bf5835b840f78790c79365150013%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65949772773082%2C%20-0.8691088511672924%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_496d9ac8212d4fd9acb0bb5ca13f3b6e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_eaad6efdc59a48b6a20122946a2ec142%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_eaad6efdc59a48b6a20122946a2ec142%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_496d9ac8212d4fd9acb0bb5ca13f3b6e.setContent%28html_eaad6efdc59a48b6a20122946a2ec142%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6d90bf5835b840f78790c79365150013.bindPopup%28popup_496d9ac8212d4fd9acb0bb5ca13f3b6e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6966a541d1004d07839c0810cca6d79e%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.633353667694024%2C%20-0.8880337913721866%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4f6a1b8bcfd1427d94ad9408c223ead6%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d4e128cdf8774ce184cdded1a511c721%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d4e128cdf8774ce184cdded1a511c721%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4f6a1b8bcfd1427d94ad9408c223ead6.setContent%28html_d4e128cdf8774ce184cdded1a511c721%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6966a541d1004d07839c0810cca6d79e.bindPopup%28popup_4f6a1b8bcfd1427d94ad9408c223ead6%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_c2e2785f0bda46ee91b2e3499b9e9e95%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6390382112928%2C%20-0.8708838775078237%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_f3366e17fe7044a48121f01cec6960dc%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_377888803ccc484b86ce97f813ca6e1c%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_377888803ccc484b86ce97f813ca6e1c%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECAIDA%20SOBRE%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_f3366e17fe7044a48121f01cec6960dc.setContent%28html_377888803ccc484b86ce97f813ca6e1c%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_c2e2785f0bda46ee91b2e3499b9e9e95.bindPopup%28popup_f3366e17fe7044a48121f01cec6960dc%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_dbb310c6742949859ce8f64a890d48c8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64083344974765%2C%20-0.8970649943808023%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_93c4ee16aec64e5fb7939283f51db8c5%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_4ae1696084604b5abcaf0bcac44cf642%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_4ae1696084604b5abcaf0bcac44cf642%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLIS.%20MARCHA%20ATR%C3%81S%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_93c4ee16aec64e5fb7939283f51db8c5.setContent%28html_4ae1696084604b5abcaf0bcac44cf642%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_dbb310c6742949859ce8f64a890d48c8.bindPopup%28popup_93c4ee16aec64e5fb7939283f51db8c5%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_abd2474fe2c040a4bdb46c6e1b7758b4%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64904657717317%2C%20-0.8718525605769747%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2dd6cb316fcf4bd1a69dde2df709a30e%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_e9fd5985633e4015aeeee8579c792bac%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_e9fd5985633e4015aeeee8579c792bac%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20LATERAL%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2dd6cb316fcf4bd1a69dde2df709a30e.setContent%28html_e9fd5985633e4015aeeee8579c792bac%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_abd2474fe2c040a4bdb46c6e1b7758b4.bindPopup%28popup_2dd6cb316fcf4bd1a69dde2df709a30e%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_512f88ed6e58454e912f645135ddde46%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.64322365075108%2C%20-0.8964627561577849%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_a57b667b58fa493189b7b8794bb46799%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_df9f5681a25e4939a9dcac82b691511d%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_df9f5681a25e4939a9dcac82b691511d%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EOTRAS%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_a57b667b58fa493189b7b8794bb46799.setContent%28html_df9f5681a25e4939a9dcac82b691511d%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_512f88ed6e58454e912f645135ddde46.bindPopup%28popup_a57b667b58fa493189b7b8794bb46799%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_9521920c336e463db56b69888a730759%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.68753087470739%2C%20-0.8778095796207178%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_2b915ac682b042d1937d519f47ac1b22%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_54add75b66b14ac790132c0acbbd4c7b%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_54add75b66b14ac790132c0acbbd4c7b%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_2b915ac682b042d1937d519f47ac1b22.setContent%28html_54add75b66b14ac790132c0acbbd4c7b%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_9521920c336e463db56b69888a730759.bindPopup%28popup_2b915ac682b042d1937d519f47ac1b22%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_776761edc31e455eb1f5d12ceafcb9db%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.661646612715046%2C%20-0.8812157329722801%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_bc2790a1542b4a88a754d3af9a85ccdb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_d63229cbd65c4deb8ff300c7a2930490%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_d63229cbd65c4deb8ff300c7a2930490%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ESALIDA%20CALZADA%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_bc2790a1542b4a88a754d3af9a85ccdb.setContent%28html_d63229cbd65c4deb8ff300c7a2930490%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_776761edc31e455eb1f5d12ceafcb9db.bindPopup%28popup_bc2790a1542b4a88a754d3af9a85ccdb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_7dee1b1c9b7046f6b9bc4363a90fb016%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.6454384961757%2C%20-0.8762000299022707%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_6786a18021d34d238c85b81747aa28bb%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_df1ac8e4a3204ec9b06fb4aeaee12ec1%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_df1ac8e4a3204ec9b06fb4aeaee12ec1%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_6786a18021d34d238c85b81747aa28bb.setContent%28html_df1ac8e4a3204ec9b06fb4aeaee12ec1%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_7dee1b1c9b7046f6b9bc4363a90fb016.bindPopup%28popup_6786a18021d34d238c85b81747aa28bb%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_111741ddd1174cc48cea80b5c2a164e7%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65543768899759%2C%20-0.9089013552408617%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_13b06ee658f04ff79228c528780f07a7%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_601182cb9dd44de89603d6a2a47573df%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_601182cb9dd44de89603d6a2a47573df%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3EATROPELLO%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_13b06ee658f04ff79228c528780f07a7.setContent%28html_601182cb9dd44de89603d6a2a47573df%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_111741ddd1174cc48cea80b5c2a164e7.bindPopup%28popup_13b06ee658f04ff79228c528780f07a7%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_b54d7be56ade4ccf9d984901f655019b%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65180346604993%2C%20-0.9004729973337304%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_4cfd22d0afcd4a7db52e5757803adc4b%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1f4fcd5020ff46179dc07fd05658e777%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1f4fcd5020ff46179dc07fd05658e777%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_4cfd22d0afcd4a7db52e5757803adc4b.setContent%28html_1f4fcd5020ff46179dc07fd05658e777%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_b54d7be56ade4ccf9d984901f655019b.bindPopup%28popup_4cfd22d0afcd4a7db52e5757803adc4b%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_036738d542704bbe89ac19c35b4082f2%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65233828238132%2C%20-0.8917562993466011%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_bc053a6250c64e7495241f993fde2b95%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_03d9ae1cb2374cd18cb4f4d6c098a704%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_03d9ae1cb2374cd18cb4f4d6c098a704%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_bc053a6250c64e7495241f993fde2b95.setContent%28html_03d9ae1cb2374cd18cb4f4d6c098a704%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_036738d542704bbe89ac19c35b4082f2.bindPopup%28popup_bc053a6250c64e7495241f993fde2b95%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_6894e6caa2124459a3821862eea5dca8%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.65040494617356%2C%20-0.888856043735591%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_8379e24fa0da49a28d41923a563425d9%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_08ae2e9eae09418ba59cb27331d57290%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_08ae2e9eae09418ba59cb27331d57290%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_8379e24fa0da49a28d41923a563425d9.setContent%28html_08ae2e9eae09418ba59cb27331d57290%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_6894e6caa2124459a3821862eea5dca8.bindPopup%28popup_8379e24fa0da49a28d41923a563425d9%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_bc88cc9332c14363917e0248af19ef85%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.645335650478316%2C%20-0.8629911318784169%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_cc9664f95ae8400a97ad1223f362ad00%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_1b8ad1e14cff4638b9836f8c84ae8f56%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_1b8ad1e14cff4638b9836f8c84ae8f56%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_cc9664f95ae8400a97ad1223f362ad00.setContent%28html_1b8ad1e14cff4638b9836f8c84ae8f56%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_bc88cc9332c14363917e0248af19ef85.bindPopup%28popup_cc9664f95ae8400a97ad1223f362ad00%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20marker_8de2573ed5f348a98f0fedaa21e2f6da%20%3D%20L.marker%28%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5B41.609992514227066%2C%20-0.8870207060655807%5D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7B%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%29.addTo%28map_b1bb0f366cc64380a7465b988c3bdc99%29%3B%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%20%20%20%20%20%20%20%20var%20popup_37e44526b48e49259dac4e6335186e4f%20%3D%20L.popup%28%7B%22maxWidth%22%3A%20%22100%25%22%7D%29%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20var%20html_577a69499f0845e6b7cc519e6aa77f3a%20%3D%20%24%28%60%3Cdiv%20id%3D%22html_577a69499f0845e6b7cc519e6aa77f3a%22%20style%3D%22width%3A%20100.0%25%3B%20height%3A%20100.0%25%3B%22%3ECOLISI%C3%93N%20ALCANCE%3C/div%3E%60%29%5B0%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20popup_37e44526b48e49259dac4e6335186e4f.setContent%28html_577a69499f0845e6b7cc519e6aa77f3a%29%3B%0A%20%20%20%20%20%20%20%20%0A%0A%20%20%20%20%20%20%20%20marker_8de2573ed5f348a98f0fedaa21e2f6da.bindPopup%28popup_37e44526b48e49259dac4e6335186e4f%29%0A%20%20%20%20%20%20%20%20%3B%0A%0A%20%20%20%20%20%20%20%20%0A%20%20%20%20%0A%3C/script%3E onload="this.contentDocument.open();this.contentDocument.write(    decodeURIComponent(this.getAttribute('data-html')));this.contentDocument.close();" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>




```python

```


```python

```
