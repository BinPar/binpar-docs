# IV Megasimulacro

## Descripción del Proyecto

El Megasimulacro es un proyecto anual (este año ha sido la IV edición) de EMP (Editorial Médica Panamericana) para preparar a los opositores del MIR proponiéndoles un simulacro online con preguntas similares a las que van a encontrarse en el examen real. Aunque está enfocado para las personas que se presentan este año al MIR, se puede presentar cualquiera que quiera probar sus conocimientos de cara al MIR, realizando luego desde EMP la comprobación de quiénes están admitidos al MIR de este año para dividir los resultados entre los MIR y no MIR.

<img src="https://user-images.githubusercontent.com/5817146/150366695-1d1d3ef2-8bb3-42d9-bf38-aa26b0819665.png" height="275"> <img src="https://user-images.githubusercontent.com/5817146/150365848-c9f3e8eb-a8df-4bbc-9f38-330fb2bf726f.png" height="275"> <img src="https://user-images.githubusercontent.com/5817146/150365941-3d29a29e-e98d-42e1-ba6f-7d07c6dc0636.png" height="275"> <img src="https://user-images.githubusercontent.com/5817146/150365397-b1da4b5e-3ce2-4a4b-9f34-dc905ffc273d.png" height="275"> <img src="https://user-images.githubusercontent.com/5817146/150364635-69dead84-3ba2-43cc-932a-b7132810b8aa.png" height="275">

Es el mismo proyecto que en años anteriores. Principalmente los trabajos consisten en cambiar los emails, las imágenes de la landing, los parámetros variables (fechas, edición, duración del examen, número de preguntas, notas del último MIR...) e incorporar los cambios pedidos desde EMP o detectados por BinPar el año anterior para que los usuarios puedan realizar el test sin problemas. Los dos principales cambios este año han sido añadir el campo Curso y marcar el campo Móvil como opcional en la landing de inscripción y cambiar todas las fechas a formato UTC para evitar problemas con la hora de fin en otras zonas horarias.

Este proyecto dispone de una beta para testing: https://megasimulacro.binpar.cloud

Si se quiere ver una demo del mismo, hay que cambiar en las settings de la instancia de beta los parámetros *startExamDate* y *limitDate* a fechas futuras e inscribirse en https://megasimulacro.binpar.cloud/inscripcion para recibir el mail de registro. Si se quiere probar el examen, hay que volver a cambiar *startExamDate* para que sea una fecha anterior y deje realizar el examen.

## Resultados

Se han extraído los siguientes datos de los registros guardados en la base de datos:
- Se registraron 1.209 usuarios, siendo 4 de ellos pruebas de BinPar y 3 de EMP.
- Comenzaron el examen 604 usuarios, siendo 4 de ellos pruebas de BinPar y 1 de EMP.
- Finalizaron el examen 601 usuarios, siendo 1 de ellos pruebas de BinPar y 1 de EMP.

## Aprendizaje

Al no haber apenas documentación sobre el proyecto en ClickUp y no encontrarse ya en la empresa la persona encargada del III Megasimulacro, había una laguna de conocimientos sobre el funcionamiento general del proyecto y de los procesos manuales del mismo de los que se encarga BinPar. Esto se solventó revisando funcionamientos en el código, revisando tasks del año pasado y consultando procedimientos con EMP.

Por circunstancias ajenas, nadie del Departamento de Diseño se pudo encargar de la maquetación de los mails ni de los últimos ajustes de la landing, como el responsive de la sección de premios, así que tuve que maquetarlos yo, aprendiendo algunos conceptos de diseño en el proceso, como a insertar links en imágenes usando Image Map.

## Problemas Detectados

Una vez desplegado en producción, se detectaron los siguientes problemas:

- No dejaba registrarse a usuarios que participaron el año pasado.

  - Problema:

    Al comprobar si el email o el D.N.I. existían devolvía que sí y no dejaba registrarse.
    
  - Usuarios afectados de los que tenemos constancia:
  
    2
 
  - Revisión:

    Al comprobar en la base de datos, se observa que todos los registros que no aceptaba por existir ya eran del año pasado. Se observa que la colección no tiene ningún campo que establezca que el usuario es de otro año ni hay ninguna comprobación de ese tipo en el código. También se observa que todos los usuarios guardados son del último Megasimulacro, por lo que se deduce que todos los años se borran los registros anteriores, pero este requisito no estaba anotado en ninguna parte.
    
  - Solución:
    
    Se borraron de la base de datos todos los registros anteriores al día del lanzamiento para eliminar los usuarios del año pasado. Previamente, se le pidió a Nico que guardase un backup de la base de datos por si desde EMP necesitaban algún dato.
    
- Fallo en la landing de inscripción.

  - Problema:
  
    Puntualmente, al registrarse en la landing, no llegaba a finalizar el registro, dejando permanentemente el mensaje: *Su peticion está siendo procesada, por favor, espere.*
  
  - Usuarios afectados de los que tenemos constancia: 
    
    4, aunque desde EMP dicen tener varios reportes con el mismo problema.
  
  - Revisión:
  
    No se logró replicar en ninguna prueba realizada por el equipo. Se revisaron los logs y no se encontró ningún error específico. Lo único que se detectó fue un error con el fichero *common.js*. Se consultó con el equipo si podía ser el problema y se consideró que era poco probable ya que ese error ya estaba en años anteriores.
    
  - Solución:
  
    No se llegó a realizar una solución sobre el código. Al ser fallos puntuales, si los usuarios lo intentaban al rato ya podían registrarse.

- Cierre del examen antes de tiempo.

  - Problema:
  
    Algunos usuarios notifican que se les cerró el examen antes de tiempo, en concreto a las 4 horas en vez de a las 4.5 horas definidas en las settings.
    
  - Usuarios afectados de los que tenemos constancia:
    
    13
    
  - Revisión:
  
    Al revisar la creación de la constante a partir del valor de la setting, se observa que la duración se parsea a integer en vez de a float, por lo que establecía la duración del examen a 4.
    
  - Solución:
  
    Se cambió el parseo del valor a float. Para dar una solución a los usuarios, se les reabrió el examen con 40 minutos disponibles para que terminasen. Para ello, se creó un nuevo campo para la colección users: *custonExamHours*. Si un usuario tiene un valor en ese campo y no ha finalizado el examen, lo utiliza para establecer la duración del examen, en vez te tener en cuenta las horas definidas por la instancia.
    
- No se han guardado algunas respuestas.

  - Problema:

    Algunos usuarios notificaron que no les estaba guardando algunas respuestas que habían marcado.
  
  - Usuarios afectados de los que tenemos constancia:
  
    2
    
  - Revisión:
  
    No se consiguió replicar. Al revisar logs, se vio un error del fichero *common.js* sobre la hora que el primer usuario notificó el problema. Al ser el único error que se mostraba se revisaron horas a las que se guardaron las respuestas y la última guardada fue justo un minuto antes del error. Podría estar relacionado, pero no se llegó a nada concluyente.
  
  - Solución:

    No se hizo ningún cambio sobre el código. Al primer usuario se le reabrió el test con 10 minutos para que las completase. Con el segundo usuario no se realizó nada.

- No recibieron el mail de inicio.

  - Problema:
  
    A algunos usuarios no les llegó el mail de inicio del Megasimulacro, que contiene el link para acceder al mismo.
  
  - Usuarios afectados de los que tenemos constancia:
  
    6
    
  - Revisión:
    
    No se encontró ningún error relacionado, probablemente es un problema externo a BinPar relacionado con el servidor de correo.
    
  - Solución:
   
    Se reenviaron los mails. Además se buscó el código de acceso de cada usuario para dárselo a EMP y que les mandasen el link en caso de seguir sin recibir los correos.

## Posibles Mejoras

Posibles desarrollos futuros que podrían mejorar el producto

Posibles mejoras en los procesos

##

**Informe realizado por Beatriz Ortega de Pedro, desarrolladora y responsable del proyecto en el momento de redactar el informe (20/01/2022).**
