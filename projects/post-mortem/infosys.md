# PostMorten Infosys

## Descripción del Proyecto
En el año 2020 trabajamos por primera vez con el [IE](https://www.ie.edu/es/) en la realización de un caso multimedia denominado **LaLaLand**, tras un largo proceso comercial previo para convertirnos en proveedor oficial del IE.

Gracias al **éxito** de aquel primer proyecto surge esta segunda oportunidad, que a diferencia del caso anterior comienza con una **alta confianza** por parte del cliente desde el primer momento que facilita la comunicación y el desarrollo de este segundo proyecto.

El objetivo principal del cliente es formar a sus alumnos en temáticas concretas, en este caso concreto acerca del concepto “**Six Pilar Model**”, a través de casos multimedia entretenidos y con gran componente técnica apoyados en información práctica con empresas reales, en este caso Infosys.

La idea creativa detrás del multimedia era la creación de una **animación 360**, con las instalaciones principales del campus de Infosys. 

Cada sección correspondería a una sala con una foto 360, donde si el alumno gira, le irán apareciendo elementos clickables para consumir la información del caso.

Este cliente se caracteriza por una elevada exigencia en cuanto a requisitos técnicos, algunos de los más relevantes eran:

* El material debe cumplir las normas de **accesibilidad** WCAG 2.1 nivel AA
* La aplicación funcionará en **cliente**. No pudiendo ejecutar ningún tipo de lógica o configuración en el servidor. [Sin ficheros .htaccess ni web.config]
* El material debe ser **multilangague**, que vendrá marcado por la url
* Los paquetes con las dependencias se descargarán por **npm**
* Cualquier empaquetador que se use deberá poder ser llamado de manera **local** dentro del material a la hora de desplegar.
* El material debe estar adaptado para funcionar correctamente bajo los distintos protocolos HTTP y HTTPS
* Los lenguajes de programación deben ser HTML5, JS o CSS3, (preferiblemente minificados y optimizados).
* En ningún caso se debe usar recursos del servidor para ejecutar el material
* Es requisito un vídeo en loop del campus en la portada del caso

A continuación se muestran alguna imágenes del resultado:

![Screenshot 2022-04-28 at 12 50 38](https://user-images.githubusercontent.com/17255550/165736727-33a2fdf9-50ce-45ce-ba35-092423ae1f34.png)

![Screenshot 2022-04-28 at 12 53 24](https://user-images.githubusercontent.com/17255550/165737148-8df50220-294d-4859-af91-86b80cc3717e.png)

## Resultados
El material multimedia se empleará dentro de las **clases teóricas** en los Programas del IE. 

Una vez presentado en las clases el alumno debe llevar a cabo la parte práctica en su casa, imprimir el resultado y tras ello, habrá una nueva clase de debate sobre las preguntas teóricas del caso.

De forma adicional, se presentará a concurso en la **Universidad de Harvard**.

A futuro recibiremos los resultados estadísticos de su uso en las clases del IE.

## Aprendizaje
El modelo de trabajo para este proyecto fue la construcción de diversos [labs](https://visual-math-labs-test.binpar.cloud/) que aislaban los componentes y funcionalidades clave del proyecto.

Este paradigma de trabajo ha resultado ser muy útil en el proyecto para consolidar con el cliente la funcionalidad básica del caso, por ejemplo, el sistema de navegación o el desarrollo de los ejercicios prácticos.

Durante esta fase inicial del proyecto cargamos todos los contenidos que tuvieron que localizarse en el proyecto definitivo, por lo que habría sido suficiente la cargar parcial de contenido para evitar ese trabajo adicional.

En la fase inicial también se negoció con el cliente la posibilidad de no incluir Internet Explorer como navegador objetivo del caso.

También cabe destacar que ha sido unos de los primeros proyectos donde hemos empleado [Tailwind](https://tailwindcss.com/).

## Problemas Detectados
En este proyecto hemos aprovechado el aprendizaje que obtuvimos en la ejecución del caso multimedia de LaLaLand, ya que compartían los principales requisitos técnicos.

Por ejemplo, en LaLaLand nos había exigido la utilización de vídeojs como reproductor de vídeos, y la experiencia no fue la mejor posible por lo que en este proyecto propusimos emplear directamente el tag de HTML5.

## Posibles Mejoras

Deberíamos haber anticipado el momento en que damos por finalizada la fase de experimentación y avance en el modelo de Labs, ya que debería haber sido más corta.
