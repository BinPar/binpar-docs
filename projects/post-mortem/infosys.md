# PostMorten Infosys
#BinPar/Presupuestos/IE

## Descripción del Proyecto
Desde nuestro cliente [IE](https://www.ie.edu/es/) nos contactan para la realización de un nuevo **caso multimedia** tras el éxito del entregado en 2020, **LaLaLand**.

El objetivo principal del cliente es formar a sus alumnos en temáticas concretas, en este caso acerca del concepto “Six Pilar Model”, a través de casos multimedia con casos prácticos reales.

La idea creativa detrás del multimedia era la creación de una **animación 360** (o una imagen con elementos en movimiento para hacerlo más atractivo visualmente) , con las instalaciones principales del campus de Infosys. 

Cada sección corresponderá a una sala con una foto 360, donde si el alumno gira, le irán apareciendo elementos clickables para consumir la información del caso.

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

## Problemas Detectados
En este proyecto hemos aprovechado el aprendizaje que obtuvimos en la ejecución del caso multimedia de LaLaLand, ya que compartían los principales requisitos técnicos.



## Posibles Mejoras