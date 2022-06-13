# PostMorten Read Garden en GrupoA

## Descripción del Proyecto

Read Garden para Grupo A es el primer proyecto Read Garden custom que se ha desarrollado en Binpar desde que la plataforma goza de un nivel de madurez elevado.

Antes de este, cabe mencionar Mi Eureka o Duana, pero estos son proyectos que se desarrollaron a la vez que Read Garden, y que sirvieron para construir la plataforma, pero en los que no se pudo llevar a cabo la reutilización que se plantea en RG.

### Proyectos satélites RG

El concepto de un proyecto satélite de Read Garden es el de un proyecto que comparte código con RG, pero que tiene suficentes necesidades especiales como para que el cliente no se pueda dar de alta directamente en la plataforma SaaS. Estas peculiaridades suelen ser las siguientes:

- Una base de datos independiente.
- El cliente tiene su propio S3.
- El catálogo, o la bbdd de usuarios requieren una importación a medida.

En el caso de Grupo A, lo más importante era sincronizar el catálogo, los usuarios y las licencias, además de realizar un pequeño proxy de agrupación de licencias para que los usuarios que tuviesen acceso a colecciones accediesen usando el modelo de licencias del nuevo DRM de RG.

## Resultados

Podemos considerar el desarrollo de Read Garden para Grupo A la primera integración exitosa de RG en un cliente histórico.

Algunas capturas del visor de RG para grupo A:

![Bookshelf](https://raw.githubusercontent.com/BinPar/binpar-docs/develop/img/grupo-a/bookshelf.png)
![Book](https://raw.githubusercontent.com/BinPar/binpar-docs/develop/img/grupo-a/book.png)


## Aprendizaje

Quizá el punto de aprendizaje más importante de este proyecto fue la fase inicial de análisis y toma de requisitos.

Se realizaron varias reuniones internas para limitar el alcance, estimar y detallar todos los desarrollos necesarios bastante al detalle.

En una primera instancia, el alcance del proyecto (y por tanto su coste) era bastante superior, ya que incluia una serie de módulos de gestión integrados, que reemplazaban al gestor actual de Grupo A. El cliente no aceptó este presupuesto por ser demasiado elevado. Gracias a la toma de requisitos, se pudo modificar el alcance, y sustituir los módulos de gestión por una serie de microservicios de sincronización, reduciendo el presupuesto casi hasta la mitad y manteniendo el gestor actual.

Como segundo punto de aprendizaje es importante destacar, que en el caso de Grupo A, el bucket de S3 se encuentra en Brasil, ya que la mayoría de los usuarios accdederán desde allí. Como colateral de esto, hemos comprobado, que el acceso desde Europa es considerablemente más lento que en el resto de proyectos.

## Problemas Detectados

El problema que más desviación ha causado en este proyecto, ha sido claramente la comunicación con el cliente. En el caso de Grupo A, y en concreto Vinicius (el responsable de este proyecto por su parte) la barrera idiomática es bastante grande. Esto, en varios puntos del desarrollo ha causado que no entendiesen bien ciertas facetas del producto o que solicitasen funcionalidades que no son necesarias y que se encontraban fuera del alcance.

Por otro lado, aunque al inicio del proyecto se definió el alcance detalladamente, durante el transcurso del mismo, se han introducido funcionalidades fuera del alcance del mismo, agotando las horas disponibles antes de lo esperado, y retrasando los tiempos. Aunque en el caso de Grupo A, tenemos la suerte de poder contar con el mantenimiento mensual desde el inicio del proyecto, que nos aporta un colchón de horas adicional, estos desarrollos pueden causar una desviación que provoque que el proyecto deje de ser rentable.

## Posibles Mejoras

Después de haber dado un paso adelante en el análisis de los proyectos y la toma de requisitos mencionada anteriormente, debemos centrarnos en comunicar este alcance al cliente de forma más clara, y diferenciar las funcionalidades que quedan fuera del mismo, de cara a desarrollarlas en sprints futuros posteriores a la entrega, y con presupuestos independientes, o bien incluirlos en el desarrollo base, pero modificando los tiempos de entrega y el presupuesto.
