# d3-map-workshop
Crea tu primer mapa con D3 en las [#jpd15](http://periodismodatos.okfn.es).

## Cómo empezar
Puedes ver los slides de la presentación (una introducción a D3 y desarrollo frontend), aunque sin una persona explicando no tendrán mucho sentido. El objetivo de este taller (al sólo tener una hora) es introducir D3, los formatos de mapas, y dar un ejemplo sencillo para que puedas replicarlo con los datos que prefieras.

Luego, instala un editor de código como [atom](https://atom.io) y sigue las instrucciones de acuerdo a tu sistema operativo.

### Mac
Si no tienes [brew](http://brew.sh), ¿a qué esperas? Así podrás instalar paquetes más fácilmente.

Luego instala [GDAL](http://www.gdal.org/) con brew (`brew install gdal`), GDAL es una suite de programas que nos ayudan a transformar datos geográficos en nuestro ordenador. También deberías instalar `node` (`brew install node`), y topojson (`npm install -g topojson`). El `http-server` que puedes instalar con `npm` es mejor que el que viene con python, en mi experiencia.

Si quieres ser un ninja del GIS, bájate [QGIS](http://www.kyngchaos.com/software/qgis). Al principio asusta pero es muy, muy útil.

### Linux
Lo mismo que en mac pero con `apt-get`, `pacman` o lo que sea que uses. Ya sabes usar un gestor de paquetes y podrías dar este taller si quisieras.

### Windows
Lo siento, [Windows es complicado](https://www.youtube.com/watch?v=dQw4w9WgXcQ).

Broma, puedes instalar QGIS [desde la web oficial](qgis.org/en/site/). Tienes que [instalar node](http://blog.teamtreehouse.com/install-node-js-npm-windows) e ir a la línea de comandos (`cmd`) para instalar de la misma manera que en mac (`npm`) `topojson` y `http-server`(aunque puedes usar el servidor python igualmente).

## Shapefiles
Los datos geográficos suelen venir en formato shapefile (SHP), que no es nada más que unos cuantos archivos con extensión rara y un encoding del siglo pasado. Busca por portales de institutos cartográficos (si eres periodista debes usar siempre fuentes oficiales).

- [Barcelona](https://github.com/martgnz/bcn-geodata) (ya convertidos)
- [Catalunya](http://www.icc.cat/vissir3/) (base municipal 1:50 000)
- [España](http://centrodedescargas.cnig.es/CentroDescargas/equipamiento.do?method=descargarEquipamiento&codEquip=3) (líneas límite municipales)
- [Mundo](http://www.naturalearthdata.com/downloads/)

## Conversión
Tener los shapefiles sólo es el primer paso. Una vez los tengas debes convertirlos a topoJSON, un formato similar a GeoJSON pero mucho más optimizado (~80% de compresión).

Con la utilidad `topojson` que ya has instalado es muy fácil convertir archivos. Abre una terminal en la carpeta donde estén tus archivos y ejecuta lo siguiente:

```bash
topojson input.shp -o output.json -p
```

Hay opciones adicionales (`-p` preserva las propiedades del shapefile, por ejemplo), que puedes leer en la [referencia](https://github.com/mbostock/topojson/wiki/Command-Line-Reference). Con `topojson` es posible hacer virguerías como juntar muchos shapefiles en diferentes capas, todo en el mismo archivo, o unir un csv con el mapa.

Un paso más, cuando tu mapa sigue ocupando mucho espacio es usar [mapshaper](http://mapshaper.org), una herramienta genial para simplificar nuestros mapas.

## Visualiza
Mira la carpeta `map` de este repo, allí está el código boilerplate para que puedas empezar a hacer tus mapas.

[Uno de los mejores ejemplos](https://github.com/alignedleft/d3-book/blob/master/chapter_12/05_choropleth.html) si quieres ir más allá está en el libro de Scott Murray, donde aprenderás a hacer coropletas de una manera muy sencilla. Allí está el verdadero poder de los datos.

Puedes ver el resultado en mi [bl.ocks](http://bl.ocks.org/martgnz/9602b285e51a6100521a). Aquí otro mapa de [coropletas](http://bl.ocks.org/martgnz/1b7ba8ebd60a1567e855). Aquí otro de [burbujas](http://bl.ocks.org/martgnz/75c7e4f9f7ad15532e18).

## Recursos
- [D3 Wiki](https://github.com/mbostock/d3/wiki) y la [galería](https://github.com/mbostock/d3/wiki/Gallery)
- [Interactive Data Visualization for the web](http://chimera.labs.oreilly.com/books/1230000000345)
- [Let's make a map](http://bost.ocks.org/mike/map/)
- BONUS: si trabajas con un mapa de España, Francia o Portugal, [d3-composite-projections](https://github.com/rveciana/d3-composite-projections) de rveciana es fantástico.
