# Actividad Dirigida 2

Aquí pondremos el código bruto para comprender lo que hemos hecho en el notebook de "Jupyter". Contrastar con el otro ejercicio cómo es el código en bruto y saber realizar una **narrativa de programación.**

## Librerías
Aquí el primer paso es importar la **librería requests.**
Esto nos permite obtener la página web a la que queremos hacer scrapping.

**Extraemos información de contenido en formato HTML o XML**  con la librería Beautiful Soup para luego poder analizar la información.

## Variables
En este paso se **define la URL** de donde se sacan los datos, en este caso (https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/) Es a este enlace al que se le hará el `request.get`, para obtener los datos.
Si el status code no nos permite hacer scrapping, nos tiene que informar a través del código `req.status_code !=200`

Para que podamos leer los datos en HTML o XML tenemos que pasarlos por `BeautifulSoup`

## Datos
Una vez sepamos con seguridad qué **variables queremos obtener**, en nuestro caso `oros`,`platas`,`bronces` y `total de medallas` que tienen los países que aparecen en la tabla de datos escogida. Por ello, hay que identificarlas en el HTML y en la URL aplicar **la función `find_all()`** para que las busque y las seleccione para, más tarde, mostrárnoslas.

Mediante un bucle a través del código `print`, el código mostrará los datos o número que hemos pedido y nos facilitará una visualización de datos rápida y sencilla.

## Pregunta
La función principal de la pregunta es para fomentar la interacción con el usuario. En este caso se pregunta `¿Quieres conocer los 20 países que han obtenido más medallas en 2020?`. Si el usuario pulsa `s` significará que si quiere conocerlo y se continuará con el scrapping. En cambio, **si el usuario no pulsa la tecla, no continuará**

## Código bruto
```
from bs4 import BeautifulSoup
import requests
#Datos sobre los Juegos Olímpicos en 2020

respuesta=input('¿QUIERES CONOCER LOS 20 PAÍSES QUE HAN OBTENIDO MÁS MEDALLAS EN 2020?\n \n Si tu respuesta es Sí, presiona "s" \n')
if(respuesta == 's'):
  print('\nRESULTADOS DE LOS DATOS DE LOS JUEGOS OLÍMPICOS 2020\n')
  print ('PAÍSES')
  URL = "https://resultados.elpais.com/deportivos/juegos-olimpicos/medallero/"
  # Realizamos la petición a la web
  req = requests.get(URL)
  # Si el estatus code no es 200 no se puede leer la página
  if (req.status_code != 200):
    raise Exception("No se puede hacer Web Scraping en"+ URL)
  # Pasamos el contenido HTML de la web a un objeto BeautifulSoup()
  html = BeautifulSoup(req.text, "html.parser")
  # Obtenemos todos los divs donde están las entradas
  paises = html.find_all("th",{"class":"pais"})
  oros = html.find_all("td",{"class":"m_oro"})
  platas = html.find_all("td",{"class":"m_plata"})
  bronces = html.find_all("td",{"class":"m_bronce"})
  totales = html.find_all("td",{"class":"m_total"})
  for i in range (20):
    # Con el método "getText()" no nos devuelve el HTML
    print("%d. %s \nOro: %s Plata: %s Bronce: %s \n Total: %s \n " % (i+1, paises[i+1].text.strip(),oros[i].text.strip(),platas[i].text.strip(),bronces[i].text.strip(), totales[i].text.strip()))

else:
  print('Qué lástima, y...')

```
