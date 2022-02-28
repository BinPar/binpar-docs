# Aplicación de Hero para soporte al equipo

Con el objetivo de reducir la **pérdida de foco** de los perfiles de desarrollo en el día a día, **mejorar los tiempos de respuesta** y evitar las dudas sobre quién presta soporte a un compañero procedemos a implantar el modelo de atención **Hero**.

Para ello, crearemos un nuevo rol **Hero** en Discord, rotativo entre los perfiles con más experiencia de la empresa, en este caso, Miguel Rodríguez, Marcos González, Alberto Blanco y Kevin Muñoz.

El proceso de rotación será diario y el protocolo será a través del cambio manual del rol en Discord por parte de Isabel justo antes de la Daily de BinPar.

Si se produce una ausencia de la persona a la que le tocaría ser el Hero del día directamente pasará al siguiente en el orden pre-establecido.

En caso de que el Hero no pueda resolver una problemática determinada podría elevar la consulta al Director Técnico.

La atención se llevará a cabo todos los días en horario de trabajo.

Se podrá solicitar la atención del Hero en la Daily o directamente mencionando el rol (`@Hero`) en el hilo correspondiente de Discord.

## Requisitos necesarios para solicitar atención al Hero

Antes de pedir ayuda al **Hero**, debemos comprobar:

- Que estamos ejecutando el proyecto en la versión de Node.js correcta.
- Que no faltan variables de entorno y éstas son las correctas.
- Si el problema se da en un proyecto desplegado, se ha de comprobar si en local se reproduce. Tanto corriendo con `npm run dev` como compilando y corriendo con `npm start`. Si durante esta comprobación, el error se reproduce, gastemos un minuto para ver si esto nos da alguna pista adicional y encontramos el problema.
- Igualmente, si el proyecto se despliega a través de un CI/CD, sería bueno igualmente comprobar que la imagen de docker compila bien, normalmente ejecutando `docker build .` en la carpeta raíz del proyecto. De nuevo, si descubrimos un error en el proceso, debemos gastar un minuto para comprobar si nos ayuda a resolverlo por nuestra cuenta.
- La consola y el terminal no deben contener otros errores. Por el bien del Hero, debemos evitar que existan logs de cualquier otro problema para evitar cualquier confusión.

Si los puntos anteriores se cumplen y tras estas comprobaciones el problema persiste, llega el momento de preparar lo necesario para que el **Hero** nos ayude. La intención de esta metodología es que la ayuda que el Hero nos preste sirva no sólo para solucionar el problema, sino para aprender y formarnos. Para ello, lo ideal es que el Hero pueda trabajar directamente sobre nuestra máquina y nosotros podamos seguir su trabajo en directo.

Para ello, deberemos comprobar que tenemos las extensiones Live Share instaladas en nuestro VS Code (`Live Share` y `Live Share Extension Pack`). Y tendremos que tener una sesión iniciada a la que el Hero deberá unirse.

> Si el problema se da en entorno web, lo ideal sería compartir nuestro puerto `localhost:3000` (o el puerto que use la web en local) a través de Live Share.
>
> Si por el contrario el problema se da ejecutando código como un servicio, será bueno en ese caso compartir nuestra terminal a través de Live Share.

Una vez realizadas las comprobaciones y con el Live Share listo, procederemos a la creación de un task en ClickUp con la definición concisa del problema a resolver así como toda la información disponible para atacarlo.

Esta será la información que deberá contener la task:

- Enlace para unirse a la sesión de **Live Share**.
- **Repositorio de GitHub** en el que se encuentra el proyecto.
- **Branch** del proyecto en la que se da el problema.
- Si el error no corresponde a código nuevo y sabemos que es algo que funcionó en una versión anterior de nuestro código, un enlace a GitHub apuntando a la versión del código que funcionaba.
- **Versión de Node.js** en la que corre o debe correr el proyecto.
- **Dependencias externas**, si las hubiera (por ejemplo, imagemagick o ffmpeg). Si el problema se da en local, comprobar las versiones de estas librerías y añadirlas a la task. Idealmente, compararlas con las del entorno de test/release y añadir esta info también.
- Pasos para **reproducir el problema**.
- Listado resumido de pruebas que hayamos hecho y/o causas del problema que hayamos descartado.
- Cualquier otra información relevante o de interés para la resolución del problema.
