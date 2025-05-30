---
id: web-service-set-option
title: WEB SERVICE SET OPTION
slug: /commands/web-service-set-option
displayed_sidebar: docs
---

<!--REF #_command_.WEB SERVICE SET OPTION.Syntax-->**WEB SERVICE SET OPTION** ( *opción* ; *valor* )<!-- END REF-->
<!--REF #_command_.WEB SERVICE SET OPTION.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| opción | Integer | &#8594;  | Código de la opción a definir |
| valor | Integer, Text | &#8594;  | Valor de la opción |

<!-- END REF-->

## Nota preliminar 

<!--REF #_command_.WEB SERVICE SET OPTION.Summary-->Este comando está diseñado para los usuarios de servicios web.<!-- END REF--> Su uso es opcional. 

## Descripción 

El comando **WEB SERVICE SET OPTION** permite definir diferentes opciones que se utilizarán durante la próxima petición SOAP provocada por el comando [WEB SERVICE CALL](web-service-call.md).  

Puede llamar este comando tantas veces como opciones a definir.

En el parámetro *opcion*, pase el número de la opción a definir y en el parámetro *valor*, pase el nuevo valor de la opción. Para estos parámetros, puede utilizar una de las siguientes constantes predefinidas del tema *Servicios Web (Cliente)*:

| Constante                       | Tipo         | Valor | Comentario                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------- | ------------ | ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Web Service display auth dialog | Entero largo | 4     | *valor* \= 0 (no mostrar la caja de diálogo) ó 1 (mostrar caja de diálogo)<br/>Esta opción administra la visualización de la caja de diálogo de actualización durante la ejecución del comando *CALL WEB SERVICE*. Por defecto, este comando nunca muestra la caja de diálogo; por lo general, para hacerlo debe utilizar el comando *AUTHENTICATE WEB SERVICE*. Sin embargo, si quiere que aparezca la caja de diálogo de autenticación para que el usuario introduzca sus identificadores, deberá utilizar esta opción: pase 1 en *valor* para mostrar la caja de diálogo, de lo contrario pase 0\. La caja de diálogo sólo aparece si el servicio web necesita autenticación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Web Service HTTP compression    | Entero largo | 6     | *valor* \= Web Service Compression <br/> Esta opción permite activar un mecanismo interno de compresión de las peticiones SOAP con el fin de acelerar los intercambios entre aplicaciones 4D. Cuando ejecuta la instrucción [WEB SERVICE SET OPTION](web-service-set-option.md)(Web Service HTTP Compression; Web Service Compression) en el cliente 4D del servicio web, los datos de la próxima petición SOAP enviados por el cliente serán comprimidos utilizando un mecanismo estándar HTTP ("gzip" o "deflate" en función del contenido de la petición) antes de su envío al servidor SOAP 4D. El servidor descomprimirá y analizará la petición, luego responderá automáticamente utilizando el mismo mecanismo. Sólo se afecta la petición que sigue la llamada al comando [WEB SERVICE SET OPTION](web-service-set-option.md). Por lo tanto debe llamar este comando cada vez que quiera utilizar la compresión. Por defecto, 4D no comprime las peticiones HTTP de los servicios web.<br/>**Nota:** este mecanismo no puede utilizarse para las peticiones enviadas a un servidor SOAP 4D de una versión anterior a la 11.3\. Para que pueda optimizar más este funcionamiento, las opciones adicionales configuran el límite y la tasa de compresión de las peticiones. Estas opciones son accesibles vía el comando [SET DATABASE PARAMETER](set-database-parameter.md). |
| Web Service HTTP timeout        | Entero largo | 1     | *valor* \= "timeout" de la parte cliente expresado en segundos.<br/>El timeout de la parte clientes es el periodo de espera del cliente servicio web en caso de que no haya respuesta del servidor. Después de este período, el cliente cierra la sesión y se pierde la petición. <br/>Por defecto, este timeout es de 180 segundos. Puede modificarse por razones específicas (estado de la red, especificaciones del servicio web, etc.).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Web Service reset auth settings | Entero largo | 5     | *valor* \= 0 (no borrar la información) ó 1 (borra la información)<br/>Esta opción le permite indicar a 4D memorizar la información de autenticación del usuario (nombre de usuario, contraseña, método, etc.), para reutilizarla posteriormente. Por defecto, esta información se borra después de cada ejecución del comando  CALL WEB SERVICE. Pase 0 en valor para guardar la información y 1 para borrarla. Note que cuando pasa 0, la información se conserva durante la sesión pero no se almacena.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Web Service SOAP header         | Entero largo | 2     | *valor* \= referencia del elemento XML raíz a insertar como encabezado de la petición SOAP.<br/>Esta opción permite insertar un encabezado en la petición SOAP generada utilizando el comando  CALL WEB SERVICE. Por defecto, las peticiones SOAP no contienen un encabezado específico. Sin embargo, algunos servicios web requieren un encabezado, por ejemplo para la gestión de los parámetros de identificación.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Web Service SOAP version        | Entero largo | 3     | *valor* \= Web Service SOAP\_1\_1 o Web Service SOAP\_1\_2<br/>Esta opción permite precisar la versión del protocolo SOAP utilizado en la petición. Pase en valor la constante Web Service SOAP\_1\_1 para indicar la versión 1.1 y la constante Web Service SOAP\_1\_2 para indicar la versión 1.2.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

El orden de llamada de las opciones no es importante. Si la misma *opcion* está definida varias veces, sólo el valor de la primera llamada se tiene en cuenta. 

## Ejemplo 1 

Inserción de un encabezado personalizado en la petición SOAP: 

```4d
  // Creación de una referencia XML
 var vRootRef;vElemRef : Text
 vRootRef:=DOM Create XML Ref("RootElement")
 vxPath:="/RootElement/Elem1/Elem2/Elem3"
 vElemRef:=DOM Create XML element(vRootRef;vxPath)
  //Modificación del encabezado SOAP con la referencia
 WEB SERVICE SET OPTION(Web Service SOAP header;vElemRef)
```

## Ejemplo 2 

Utilización de la versión 1.2 del protocolo SOAP:  

```4d
 WEB SERVICE SET OPTION(Web Service SOAP version;Web Service SOAP_1_2)
```

## Ver también 

[WEB SERVICE CALL](web-service-call.md)  

## Propiedades

|  |  |
| --- | --- |
| Número de comando | 901 |
| Hilo seguro | &check; |


