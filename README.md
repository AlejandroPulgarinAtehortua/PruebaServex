#Prueba Servex S.A.C
Este repositorio contiene el proyecto que desarrolla el segundo punto de la prueba técnica de Servex S.A.C para los aprendices de desarrollo de software. Esta prueba evalua las habilidades técnicas frente a diferentes problemas que se pueden aplicar al mundo real del software. Esta prueba está diseñada de acuerdo a un perfil previamente analizado por parte de la organización.

El proyecto consume una API de los personajes de Rick & morty. Este API contiene personajes listados con ID del 1 al 671 API Rick & Morty, Se filtrar y presentan los primeros 20 IDs de la base de datos proporcionados por la API.

##Algunas condiciones para los estados de los personajes son:

Cada personaje tiene una tarjeta unica con una imagen, su nombre, status(Alived o Dead) y la especia a la que pertenece el personaje.
- Si el status del personaje es "Dead", la imagen debe estar en escala de grises.
- Si el status del peronaje es "Unknown" no se debe mostrar el personaje.
- Si el status es "Alived" se muesta además un marcador verde en el costado derecho del estado del personje.
- Si el status del personaje es "Dead" (además de mostrar al personaje en escala de grises) se muestra un marcador rojo en el costado derecho del estado del personaje
- El personaje pierde la escala de grises cuando se realiza un hover para darle mas información visual de este mismo al usuario.
- En el header hay un enlace para ir a la pagina oficial de la serie distribuida por adultswim rick & Motty
- Algunas especificaciones
-
Este proyecto se construyó utilizando:

[GitHub]()
Node Js para npm v14.17.0 [NodeJS](https://nodejs.org/es/)
@vue/cli 4.5.13 [VueJs](https://vuejs.org/)
El archivo index.html integra los componentes desarrollados al interior del framework, para este caso será App.vue por tanto este será en archivo que se documentará ya que esté contiende los scripts y los componentes que conforman la solucion.

Project setup
```
npm install
```
Compiles and hot-reloads for development
```
npm run serve
```
Compiles and minifies for production
```
npm run build
```
Lints and fixes files
```
npm run lint
```
Customize configuration
[See Configuration Reference](https://vuejs.org/).