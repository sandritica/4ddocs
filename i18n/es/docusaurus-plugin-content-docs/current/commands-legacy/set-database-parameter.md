---
id: set-database-parameter
title: SET DATABASE PARAMETER
slug: /commands/set-database-parameter
displayed_sidebar: docs
---

<!--REF #_command_.SET DATABASE PARAMETER.Syntax-->**SET DATABASE PARAMETER** ( {*tabla* ;} *selector* ; *valor* )<!-- END REF-->
<!--REF #_command_.SET DATABASE PARAMETER.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| tabla | Table | &#8594;  | Tabla para la cual definir el parámetro o Tabla por defecto si se omite este parámetro |
| selector | Integer | &#8594;  | Código del parámetro de la base a modificar |
| valor | Real, Text | &#8594;  | Valor del parámetro |

<!-- END REF-->

#### Descripción 

<!--REF #_command_.SET DATABASE PARAMETER.Summary-->El comando **SET DATABASE PARAMETER** permite modificar varios parámetros internos de la base de datos 4D.<!-- END REF-->  
  
El *selector* designa el parámetro a modificar. 4D ofrece constantes predefinidas, las cuales se ubican en el tema *Parámetros de la base*. La siguiente tabla lista cada constante, describe su alcance e indica si los cambios realizados se conservan entre dos sesiones:

### 4D Server timeout (13)

**Alcance**: aplicación 4D si *valor* positivo

Se conserva entre dos **sesiones**: sí si *valor* positivo

**Valores posibles**: 0 -> 32 767

**Descripción**: valor del tiempo de espera antes de desconexión (timeout) de 4D Server a los equipos clientes. Por defecto, este valor se define en la página "Cliente-Servidor/Configuración" de la caja de diálogo Preferencias en el equipo servidor. 

El timeout del servidor define el periodo máximo de no respuesta del cliente "autorizado", por ejemplo si realiza una operación de bloqueo. Al terminar esta periodo, 4D Server desconecta al cliente. El selector 4D Server Timeout le permite asignar en el parámetro *valor*un nuevo timeout, expresado en minutos. Esta funcionalidad es particularmente útil para aumentar el valor del timeout antes de la ejecución en el equipo cliente de una operación de larga duración, tal como la impresión de un gran número de páginas, la cual puede causar un timeout inesperado.



Tiene dos opciones:

Si pasa un valor **positivo** en el parámetro *valor*, define un timeout global y permanente: el nuevo valor se aplica a todos los procesos y se almacena en las Preferencias de la aplicación 4D (equivalente a cambiar en el diálogo Preferencias).Si pasa un valor **negativo** en el parámetro *valor*, define un timeout lobal y temporal: el nuevo valor se aplica únicamente a los procesos llamantes (los otros procesos conservan los valores por defecto) y se restaura al valor por defecto tan pronto como el servidor recibe una señal de actividad del cliente, por ejemplo, cuando la operación termina. Esta opción es muy útil para administrar operaciones largas iniciadas por plug-ins 4D. Para definir una conexión "Sin timeout", pase 0 en *valor*. Ver el ejemplo 1.



### 4D Remote mode timeout (14)

**Alcance** (antigua capa de red únicamente): aplicación 4D si valor positivo

**Se conserva entre dos sesiones**: sí si *valor* positivo

**Descripción**: a utilizar en casos muy específicos. Valor del timeout otorgado por el equipo 4D remoto a la máquina 4D Server. Por defecto, este valor se define en la página "Cliente-Servidor/Configuración" de la caja de diálogo de Preferencias en el equipo remoto.

El selector Timeout 4D mode distant no se tiene en cuenta si utiliza la antigua capa de red. Con la capa 4D *ServerNet* activada, se ignora: esta configuración es administrada por el selector Timeout 4D Server (13).



### Port ID (15)

**Alcance**: 4D local, 4D Server

Se conserva entre dos **sesiones**: no

**Descripción**: Command SET DATABASE Número de puerto TCP utilizado por el servidor web 4D con 4D en modo local y 4D Server. Por defecto, el valor es 80.

El número de puerto TCP está definido en la página "Web/Configuración" de la caja de diálogo de las Propiedades de la base. Puede utilizar las constantes del tema  para el parámetro *valor*. 

El selector Port ID se utiliza en el marco de servidores web 4D compilados y fusionados con 4D Desktop (sin acceso al modo Diseño). Para mayor información sobre el número de puerto TCP, consulte la sección *Parámetros del servidor web*





### Character set (17)

**Alcance:** 4D local, 4D Server**

Se conserva entre dos sesiones:** sí**

Descripción:** constante obsoleta (se conserva por compatibilidad únicamente). Ahora recomendamos utilizar los comandos [WEB SET OPTION](web-set-option.md) y [WEB GET OPTION](web-get-option.md) para la configuración del servidor HTTP.





### Max concurrent Web processes (18)

**Alcance**: 4D local, 4D Server

Se conserva entre dos **sesiones**: sí

**Valores**: todo valor entre 10 y 32 000\. El valor por defecto es 100.

**Descripción**: Constante obsoleta (se conserva por compatibilidad únicamente). Se recomienda utilizar los comandos [WEB SET OPTION](web-set-option.md) y [WEB GET OPTION](web-get-option.md) para la configuración del servidor HTTP.



### Client port ID (22)

**Alcance**: todos los equipos 4D remotos

 Se conserva entre dos **sesiones**: sí

 **Valores posibles**: ver selector 15

**Descripción**: permite especificar este parámetro para todos los equipos 4D remotos utilizados como servidores web. Los valores definidos utilizando estos selectores se aplican a todos los equipos remotos utilizados como servidores web. Si quiere definir valores sólo para ciertos equipos remotos, utilice la caja de diálogo de Preferencias de 4D en modo remoto.



### Client character set (24)

**Alcance**: todos los equipos 4D remotos

 Se conserva entre dos **sesiones**: sí

 **Valores posibles**: ver selector 17

**Descripción**: permite especificar este parámetro para todos los equipos 4D remotos utilizados como servidores web. Los valores definidos utilizando estos selectores se aplican a todos los equipos remotos utilizados como servidores web. Si quiere definir los valores sólo para algunos equipos remotos, utilice la caja de diálogo de Preferencias de 4D en modo remoto.



### Client max concurrent Web proc (25)

**Alcance**: todos los equipos 4D remotos

Se conserva entre dos **sesiones**: sí

Valores posibles: ver selector 18

**Descripción**: permite especificar esta parámetro para las máquinas 4D remotas utilizadas como servidores web. Los valores definidos utilizando estos selectores se aplican a todos los equipos remotos utilizados como servidores web. Si quiere definir este valor sólo para ciertos equipos remotos, utilice la caja de diálogo de Preferencias de 4D en modo remoto.





### Maximum Web requests size (27)

**Alcance**: 4D local, 4D Server

Se conserva entre dos **sesiones**: sí

**Valores posibles**: 500 000 a 2 147 483 648.

**Descripción**: Constante obsoleta (se conserva por compatibilidad únicamente). Se recomienda utilizar los comandos [WEB SET OPTION](web-set-option.md) y [WEB GET OPTION](web-get-option.md) para la configuración del servidor HTTP.



### 4D Server log recording (28)

**Thread-safe** : Yes

**Alcance**: 4D Server, 4D remoto*

* Se conserva entre dos **sesiones**: no

 **Valores** **posibles**: 0 ó de 1 a X (0 = no grabar, 1 a X = número secuencial, añadido al nombre del archivo).

**Descripción**: inicia o detiene la grabación de las peticiones estándar recibidas por 4D Server (excluyendo las peticiones web). Por defecto, el valor es 0 (no se graban las peticiones).

4D Server le permite grabar cada petición recibida por el equipo servidor en un archivo de historial. Cuando este mecanismo está activo, el archivo de historial se crea junto al archivo de estructura de la base. Su nombre es "4DRequestsLog\_X," donde X es el número secuencial del historial. Una vez el archivo alcanza un tamaño de 10 MB, se cierra y se genera un nuevo archivo, con un número secuencial incrementado. Si existe un archivo con el mismo nombre, se reemplaza directamente. Puede definir el número de inicio de la secuencia utilizando el parámetro *valor*.

Este archivo texto almacena en formato tabulado simple diferente información sobre cada petición: hora, número de proceso, usuario, tamaño de la petición, duración del proceso, etc. Esta información puede ser útil particularmente durante la fase de afinamiento de la aplicación o con fines estadísticos. Por ejemplo puede importarse, en un software de hoja de cálculo para procesarse.



### Client Web log recording (30)

**Alcance**: todos los equipos 4D remotos

 Se conserva entre dos **sesiones**: sí

 **Valores posibles**: 0 = No grabar (por defecto), 1 = Registrar en formato CLF, 2 = Registrar en formato DLF, 3 = Registrar en formato ELF, 4 = Registrar en formato WLF.

**Descripción**: inicia o detiene la grabación de las peticiones web recibidas por los servidores web de todos los equipos cliente. Por defecto, el valor es 0 (no se graban las peticiones).

El funcionamiento de este selector es idéntico al del selector 29; sin embargo, aplica a todos los equipos 4D remotos utilizados como servidores web. El archivo "logweb.txt", en este caso, automáticamente ubicado en la subcarpeta Logs de la base 4D remota (carpeta de caché). Si quiere definir los valores únicamente para ciertos equipos cliente, utilice la caja de diálogo de Preferencias de 4D en modo remoto.



### Table sequence number (31)

**Alcance**: *a*plicación 4D

 Se conserva entre dos **sesiones**: sí

 **Valores posibles**: todo valor de tipo entero largo.

**Descripción**: este selector se utiliza para modificar o modificar u obtener el número único actual de los registros de la tabla pasada en parámetro. "Número actual" significa "último número utilizado": si modifica este valor utilizando SET DATABASE PARAMETER, el siguiente registro será el valor pasado + 1\. Este nuevo número es el número devuelto por el comando Sequence number [](http://doc.tmp.4d.fr/Database-Parameters/4Dv11.4/ConstantTheme/4870/CMU00244.HTM) como también en todo campo de la tabla a la cual se asigna la propiedad "Autoincrementar" en el editor de estructura o vía SQL.

Por defecto, este número único es definido por 4D y corresponde al orden de creación de los registros. Para información adicional, por favor consulte la documentación del comando [Sequence number](sequence-number.md "Sequence number").







### Debug log recording (34)

**Thread-safe** : Yes

**Alcance**: Aplicación 4D

**Se conserva entre dos sesiones**: No

**Descripción**: inicia o detiene la grabación secuencial de los eventos a nivel de programación de 4D en el archivo 4DDebugLog, que se ubica automáticamente en la subcarpeta Logs de la base de datos, junto al archivo de estructura. Un nuevo formato texto tabulado, más compacto se utiliza en el archivo de registro de eventos "4DDebugLog \[\_n\].txt" a partir de 4D v14 (donde \_n es el número de segmento del archivo).

**Valores posibles**: Entero largo contiene un campo de bits: valor = bit1(1)+bit2(2)+bit3(4)+bit4(8)+…). 

- Bit 0 (valor 1) permite activar el archivo (note que cualquier otro valor no nulo también lo activará)

- Bit 1 (valor 2) permite solicitar los parámetros de llamada a los métodos y comandos.

- Bit 2 (valor 4) permite activar el nuevo formato tabulado.

- Bit 3 (valor 8) permite desactivar la escritura inmediata de cada operación en el disco (activado por defecto). La escritura inmediata es menor rápida y más eficaz por ejemplo para buscar las causas de un fallo.Si desactiva este modo, el contenido del archivo será generado más rápidamente.

- Bit 4 (valor 16) desactiva el registro de llamadas de plug-ins (activado por defecto).

- Bit 5 (valor 32) desactiva el registro de las funciones miembros.

Ejemplos:

SET DATABASE PARAMETER (34;1) // activa el modo estándar sin los parámetros, con las duraciones

SET DATABASE PARAMETER (34;2) // activa el modo estándar con los parámetros y las duraciones

SET DATABASE PARAMETER (34;2+4) // activa el modo tabulado con los parámetros y las duraciones

SET DATABASE PARAMETER (34;0) // desactiva el archivo Para todo tipo de aplicación 4D interpretada o compilada (4D todos los modos, 4D Server, 4D Volume Desktop), puede evitar que un archivo registre demasiada información:

- restringiendo los comandos 4D que se examinan utilizando Log command list (selector 80), o

- restringiéndolo sólo al proceso actual con Current process debug log recording (selector 111). Esto añadirá la letra "p" y el número de proceso al nombre del archivo: *4DDebugLog\[\_pn\_n\].txt* o *4DDebugLogServer\[\_pn\_n\].txt*

Para más información sobre este formato y sobre el uso del archivo *4DDebugLog*, consulte la sección *Descripción de archivos de historial*. **Nota:** este selector se ofrece únicamente con fines de depuración y debe utilizarse con cuidado, ya que puede afectar al rendimiento de la aplicación.



### Client Server port ID (35)

**Alcance**: base de datos 

Se conserva entre dos **sesiones**: sí**

Valores posibles**: 0 a 65535

**Descripción**: número de puerto TCP donde el servidor 4D publica la base de datos (para conexión remota 4D). Por defecto, el valor es 19813\. 

La personalización de este valor permite utilizar varias aplicaciones 4D cliente-servidor en la misma máquina con el protocolo TCP; en este caso, debe indicar un número de puerto diferente para cada aplicación.

El valor se guarda en el archivo de estructura de la base. Puede definirse con 4D en modo local pero sólo se tiene en cuenta en configuración cliente servidor.

Cuando modifica este valor, es necesario reiniciar el equipo servidor para que el nuevo valor sea tenido en cuenta.



### HTTPS Port ID (39)

**Alcance**: 4D local, 4D Server

Se conserva entre dos **sesiones**: sí

**Descripción**: Constante obsoleta (se conserva por compatibilidad únicamente). Se recomienda utilizar los comandos [WEB SET OPTION](web-set-option.md) y [WEB GET OPTION](web-get-option.md) para la configuración del servidor HTTP.



### Client HTTPS port ID (40)

**Alcance**:todos los equipos 4D remotos

 Se conserva entre dos **sesiones**: sí

 **Valores posibles**: 0 a 65535

**Descripción**: número de puerto TCP utilizado por los servidores web de los equipos clientes para conexiones seguras vía SSL (protocolo HTTPS). Por defecto, el valor es 443 (valor estándar).

Este selector puede utilizarse para modificar por programación el puerto TCP utilizado por los servidores web de los equipos clientes para las conexiones seguras vía SSL (protocolo HTTPS). Por defecto, el valor es 443 (valor estándar).

Este selector funciona exactamente igual que el selector 39; sin embargo, aplica a todos los equipos 4D remotos utilizados como servidores web. Si quiere modificar el valor de ciertos equipos clientes únicamente, utilice la caja de diálogo de Preferencias de 4D remoto.





### SQL Autocommit (43)

**Alcance**:base de datos

 Se conserva entre dos **sesiones**: sí

 **Posibles valores**: 0 (desactivación) o 1 (activación)

**Descripción**: activación o desactivación del modo SQL auto-commit. Por defecto, el valor es 0 (modo desactivado)

 El modo auto-commit permite reforzar la integridad referencial de la base. Cuando este modo está activo, las peticiones *SELECT*, INSERT, UPDATE y *DELETE* (SIUD) se incluyen automáticamente en las transacciones cuando no se han ejecutado dentro de una transacción. Este modo igualmente puede definirse en las Preferencias de la base.



### SQL Engine case sensitivity (44)

**Alcance**:base de datos

 Se conserva entre dos sesiones: sí

 **Valores posibles**: 0 (no se tienen en cuenta las mayúsculas y minúsculas) ó 1 (sensible a las mayúsculas y minúsculas)

**Descripción**: activación o desactivación de la sensibilidad a mayúsculas y minúsculas para comparaciones de cadenas efectuadas por el motor SQL. 

Por defecto, el valor es 1 (sensible a las mayúsculas y minúsculas): el motor SQL diferencia entre mayúsculas y minúsculas y entre caracteres acentuados al comparar cadenas (ordenaciones y búsquedas). Por ejemplo “ABC”= “ABC” pero “ABC” # “Abc.” En algunos casos, por ejemplo para alinear el funcionamiento del motor SQL con el del motor 4D, podría querer que las comparaciones de cadenas no tengan en cuenta las mayúsculas y minúsculas (“ABC”=“Abc”). 

Esta opción también puede definirse en la [CALL SUBFORM CONTAINER](call-subform-container.md) de las Preferencias de la base.



### Client log recording (45)

**Alcance**:equipo 4D remoto 

 Se conserva entre dos **sesiones**: no

 **Valores posibles**: 0 ó de 1 a X (0 = no grabar, 1 a X = número secuencial, asociado al nombre del archivo). 

**Descripción**: inicia o detiene la grabación de peticiones estándar efectuadas por el equipo cliente 4D que ejecutó el comando (excluyendo las peticiones web). Por defecto, el valor es 0 (no se graban las peticiones). 

4D le permite registrar el historial de peticiones realizadas por el equipo cliente. Cuando este mecanismo se activa, se crean dos archivos en el equipo cliente, en la subcarpeta Logs de la carpeta local de la base. Son llamados 4DRequestsLog\_X y 4DRequestsLog\_ProcessInfo\_X, donde X es el número secuencial del historial. Una vez el archivo 4DRequestsLog alcanza un tamaño de 10 MB, se cierra y se genera uno nuevo, con un número secuencial incrementado. Si ya existe un archivo con el mismo nombre, se reemplaza directamente. Puede definir el número de inicio para la secuencia utilizando el parámetro *valor*.

Estos archivos texto almacenan en formato tabulado simple diferente información relacionada con cada petición: hora, número de proceso, tamaño de la petición, duración del proceso, etc. Esta información es particularmente útil durante la fase de desarrollo de la aplicación o con fines estadísticos.



### Query by formula on server (46)

**Alcance**: tabla y procesos actuales

 Se conserva entre dos **sesiones**: no

 **Valores posibles**: 0 (utilizar la configuración de la base), 1 (ejecutar en cliente) o 2 (ejecutar en servidor)

**Descripción**: ubicación de la ejecución de los comandos [QUERY BY FORMULA](query-by-formula.md "QUERY BY FORMULA") y [QUERY SELECTION BY FORMULA](query-selection-by-formula.md "QUERY SELECTION BY FORMULA") para la *tabla* pasada en parámetro. 

Cuando se utiliza una base en modo cliente-servidor, los comandos de búsqueda "por fórmula" pueden ejecutarse en el servidor o en el equipo cliente:

en bases creadas con 4D v11 SQL, estos comandos se ejecutan en el servidor.en bases convertidas, estos comandos se ejecutan en el equipo cliente, como en las versiones anteriores de 4D.en las bases convertidas, una preferencia específica permite modificar globalmente la ubicación de ejecución de estos comandos.Esta diferencia en ubicación de ejecución influye no sólo en el rendimiento de la aplicación (la ejecución en el servidor es generalmente más rápida) sino también en la programación. En efecto, el valor de los componentes de la fórmula (en particular las variables llamadas vía un método) varía de acuerdo al contexto de ejecución. Puede utilizar este selector para adaptar puntualmente el funcionamiento de su aplicación. 

Si pasa 0 en el parámetro *valor*, la ubicación de ejecución de los comandos de búsqueda "por fórmula" dependerá de la configuración de la base: en bases creadas con 4D v11 SQL, estos comandos se ejecutarán en el servidor. En bases convertidas, se ejecutarán en el equipo cliente o en el servidor en función de las preferencias de la base. Pase 1 ó 2 en *valor* para "forzar" la ejecución de estos comandos respectivamente en el equipo cliente o en el servidor. Consulte el ejemplo 2. 

 si quiere activar las uniones "tipo SQL" (consulte el selector QUERY BY FORMULA Joins selector), siempre debe ejecutar las fórmulas en el servidor de manera que tengan acceso a los registros. Atención, en este contexto, la fórmula no debe contener llamadas a un método, de lo contrario pasará automáticamente al equipo remoto.



### Order by formula on server (47)

**Alcance**: tabla y procesos actuales

 Se conserva entre dos **sesiones**: no

 **Valores posibles**: 0 (utilizar la configuración de la base), 1 (ejecutar en el cliente) o 2 (ejecutar en el servidor)

**Descripción**: ubicación de la ejecución del comando [ORDER BY FORMULA](order-by-formula.md "ORDER BY FORMULA") para la tabla pasada en parámetro. 

Al utilizar una base en modo cliente-servidor, el comando [ORDER BY FORMULA](order-by-formula.md "ORDER BY FORMULA") puede ejecutarse bien sea en el equipo servidor o en el cliente. Este selector puede utilizarse para especificar la ubicación de la ejecución de este comando (servidor o cliente). Este modo también puede definirse en las preferencias de la base. Para mayor información, consulte la descripción del selector 46, Query By Formula On Server.

 

 si quiere activar las uniones "tipo SQL" (consulte el selector QUERY BY FORMULA Joins selector), siempre debe ejecutar las fórmulas en el servidor de manera que tengan acceso a los registros. Atención, en este contexto, la fórmula no debe contener llamadas a un método, de lo contrario pasará automáticamente al equipo remoto.



### Auto synchro resources folder (48)

**Alcance**:equipo 4D remoto

 Se conserva entre dos **sesiones**: no

 **Valores p** **osibles**: 0 (sin sincronización), 1 (auto sincronización) ó 2 (preguntar).

**Descripción**: modo de sincronización dinámico de la carpeta *Resources* del equipo cliente 4D que ejecuta el comando con el servidor. 

Cuando el contenido de la carpeta *Resources* en el servidor se ha modificado o un usuario ha solicitado la sincronización (por ejemplo vía el explorador de recursos o siguiendo la ejecución del comando [NOTIFY RESOURCES FOLDER MODIFICATION](notify-resources-folder-modification.md "NOTIFY RESOURCES FOLDER MODIFICATION")), el servidor notifica a los equipos cliente conectados. 

Tres modos de sincronización son posibles del lado del cliente. El selector Auto Synchro Resources Folder se utiliza para especificar el modo a utilizar por el equipo cliente para la sesión actual:

0 (valor por defecto): sin sincronización dinámica (la petición de sincronización se ignora) 1: sincronización dinámica automática2: visualización de una caja de diálogo en los equipos clientes, con la posibilidad de efectuar o rechazar la sincronización.El modo de sincronización también puede definirse globalmente en las Preferencias de la aplicación.



### Query by formula joins (49)

**Alcance**:Proceso actual

 Se conserva entre dos **sesiones**: no

 **Valores posibles**: 0 (utilizar configuración de la base), 1 (siempre utilizar relaciones automáticas) o 2 (utilizar las uniones SQL si es posible).

**Descripción**: modo de funcionamiento de los comandos [QUERY BY FORMULA](query-by-formula.md "QUERY BY FORMULA") y [QUERY SELECTION BY FORMULA](query-selection-by-formula.md "QUERY SELECTION BY FORMULA") relativos al uso de "uniones SQL."

En las bases de datos creadas a partir de la versión 11.2 de 4D v11 SQL, estos comandos efectúan uniones basados en el modelo de uniones SQL. Este mecanismo permite modificar la selección de una tabla en función de una búsqueda efectuada en otra tabla sin que las tablas estén conectadas por una relación automática (condición necesaria en las versiones anteriores de 4D).

El selector QUERY BY FORMULA Joins permite definir el modo de funcionamiento de los comandos de búsqueda por fórmula para el proceso actual:

0: Utilizar los parámetros actuales de la base (valor por defecto). En bases creadas a partir de la versión 11.2 de 4D v11 SQL, las "uniones SQL" siempre se activan para las búsquedas por fórmula. En bases de datos convertidas, este mecanismo no se activa por defecto por razones de compatibilidad pero puede implementarse vía una preferencia.1: Siempre utilizar relaciones automáticas (= funcionamiento de versiones anteriores de 4D). En este modo, una relación es necesaria para definir la selección de una tabla en función de búsquedas efectuadas en otra tabla. 4D no efectúa más "uniones SQL."2: Utilizar las uniones SQL si es posible (= funcionamiento o defecto de las bases creadas en versión 11.2 y superiores de 4D v11 SQL). En este modo, 4D establece "uniones SQL" para las búsquedas por fórmula cuando la fórmula se ajusta para ello (con dos excepciones, ver la descripción del comando [QUERY BY FORMULA](query-by-formula.md "QUERY BY FORMULA") o [QUERY SELECTION BY FORMULA](query-selection-by-formula.md "QUERY SELECTION BY FORMULA")).**Nota:** si quiere activar las uniones "tipo SQL" (consulte el selector QUERY BY FORMULA Joins selector), siempre debe ejecutar las fórmulas en el servidor de manera que tengan acceso a los registros. Atención, en este contexto, la fórmula no debe contener llamadas a un método, de lo contrario pasará automáticamente al equipo remoto.



### HTTP compression level (50)

**Alcance**: aplicación 4D 

Se conserva entre dos **sesiones**: no

**Descripción**: Constante obsoleta (se conserva por compatibilidad únicamente). Se recomienda utilizar los comandos [WEB SET OPTION](web-set-option.md) y [WEB GET OPTION](web-get-option.md) para la configuración del servidor HTTP.



### HTTP compression threshold (51)

**Alcance**: aplicación 4D 

Se conserva entre dos **sesiones**: no

Valores posibles: todo valor de tipo entero largo

**Descripción**: Constante obsoleta (se conserva por compatibilidad únicamente). Se recomienda utilizar los comandos [WEB SET OPTION](web-set-option.md) y [WEB GET OPTION](web-get-option.md) para la configuración del servidor HTTP.



### Server base process stack size (53)

**Alcance**: 4D Server

 Se conserva entre dos sesiones: no

 **Valores posibles**: entero largo positivo.

**Descripción**: tamaño de la pila asignada a cada proceso del sistema preferente en el servidor, expresado en bytes. El tamaño por defecto es determinado por el sistema.

Los procesos sistema preferente (procesos de tipo Proceso base 4D client) se cargan para controlar los procesos cliente 4D principales. El tamaño asignado por defecto a la pila de cada proceso preferente da facilidad de ejecución pero puede resultar consecuente cuando se crea un gran número de procesos (varios cientos). 

Por razones de optimización, este tamaño puede reducirse considerablemente si las operaciones efectuadas por la base lo permiten (por ejemplo si la base no efectúa ordenaciones de grandes cantidades de registros). Son posibles valores de 512 o incluso 256 KB. Sea cuidadoso, subdimensionar la pila es critico y puede afectar la operación de 4D Server. La definición de este parámetro debe hacerse con precaución y tener en cuenta las condiciones de uso de la base (número de registros, tipo de operaciones, etc.). 

Para que sea tenido en cuenta, este parámetro debe ejecutarse en el equipo servidor (por ejemplo en el *Método base On Server Startup*).





### Idle connections timeout (54)

**Alcance**: aplicación 4D a menos que valor sea negativo

**Se conserva entre dos sesiones:** no

**Valores posibles:** valor entero que expresa una duración en segundos. El valor puede ser positivo (nuevas conexiones) o negativo (conexiones existentes). Por defecto, el valor es 20.

**Descripción**: máximo periodo de inactividad (timeout) para conexiones al motor de la base 4D y al motor SQL, así como también en modo *ServerNet* (nueva capa de red), al servidor de la aplicación 4D. Cuando una conexión inactiva alcanza este límite, se pone en espera automáticamente, lo cual congela la sesión cliente/servidor y cierra el socket de red. En la ventana de administración del servidor, el estado del proceso del usuario se indica como "Postponed". Este funcionamiento es totalmente transparente para el usuario: tan pronto como hay una nueva actividad en la conexión que está en espera, el socket se reabre automáticamente y la sesión cliente/servidor se restaura.

Este parámetro permite, por una parte, economizar los recursos en el servidor: las conexiones en espera cierran el socket y liberan un proceso en el servidor. Por otra parte, esto le permite evitar pérdida de conexiones por el cierre de sockets por parte del firewall. Por esta razón, el valor del timeout para conexiones inactivas deber ser menor que el del firewall en este caso.

Si pasa un valor positivo en *valor*, se aplicará a todas las nuevas conexiones en todos los procesos. Si pasa un valor negativo, se aplicará a las conexiones que se abran en el proceso actual. Si pasa 0, las conexiones inactivas no serán sometidas a un timeout.

Este parámetro puede definirse del lado del cliente. Por lo general, no necesita cambiar este valor.



### PHP interpreter IP address (55)

**Alcance**: Aplicación 4D

Se conserva entre dos **sesiones**: no

**Valores**: cadena formateada del tipo "nnn.nnn.nnn.nnn" (por ejemplo "127.0.0.1"). 

**Descripción**: dirección IP utilizada localmente por 4D para comunicarse con el intérprete PHP vía FastCGI. Por defecto, el valor es "127.0.0.1". Esta dirección debe corresponder a la máquina donde en encuentra 4D. Este parámetro también puede definirse globalmente para todas las máquinas vía las Propiedades de la base.

Para mayor información sobre el intérprete PHP, por favor consulte el manual de *Diseño*.



### PHP interpreter port (56)

**Alcance**:Aplicación 4D

 **Se conserva entre dos sesiones**: No

**Valores**: valor de tipo entero largo positivo. Por defecto, el valor es 8002\. 

**Descripción**: número de puerto TCP utilizado o por el intérprete PHP de 4D. Este parámetro también puede modificarse globalmente para todos los equipos vía las Propiedades de la base. Para mayor información sobre el intérprete PHP, consulte el manual de *Diseño*.



### SSL cipher list (64)

**Alcance**: Aplicación 4D

Se conserva entre dos sesiones: No

**Valores posibles**: secuencia de cadenas separadas por dos puntos.

**Description:** **Descripción:** lista de cifrado (*cipher list*) utilizada por 4D para el protocolo seguro. Esta lista modifica la prioridad de los algoritmos de cifrado implementados por 4D. Por ejemplo, puede pasar la siguiente cadena en el parámetro *valor*: "HIGH:!aNULL:!MD5:!3DES:!CAMELLIA:!AES128:!RSA:!DH:!RC4". 

Para una descripción completa de la sintaxis para la lista cifrada, consulte la *página de cifrado del sitio OpenSSL*.

Esta configuración se aplica al servidor web principal (excluyendo los objetos del servidor web), al servidor SQL, a las conexiones cliente/servidor, así como al cliente HTTP y a todos los comandos 4D que hacen uso del protocolo seguro. Es temporal (no se mantiene entre sesiones). 

Cuando la lista de cifrado se modifica, debe reiniciar el servidor correspondiente para que los nuevos parámetros sean tenidos en cuenta. 

Para reinicializar la lista de cifrado a su valor por defecto (guardado permanentemente en el archivo SLI), llame al comando [SET DATABASE PARAMETER](set-database-parameter.md) y pase una cadena vacía ("") en el parámetro *valor*. 

**Nota:** con el comando [Get database parameter](get-database-parameter.md), la lista de cifrado se devuelve en el parámetro opcional *valorAlfa* y el parámetro de retorno es siempre 0.



### Cache unload minimum size (66)

**Alcance**: Aplicación 4D 

**Se conserva entre dos sesiones**: No

**Valores posibles**: Entero largo positivo > 1.

**Descripción**: tamaño mínimo de memoria a liberar del caché de la base de datos cuando el motor necesita hacer espacio para ubicar un objeto (valor en bytes). 

El propósito de este selector es reducir el número de liberaciones de datos de la caché con el fin de obtener un mejor rendimiento. Puede hacer variar este parámetro en función del tamaño de la caché y del de los bloques de datos manipulados en su base. 

Por defecto, si este selector no se utiliza, 4D descarga mínimo 10% de la caché en caso de que se necesite espacio.Alcance: Aplicación 4D 

Se conserva entre dos sesiones: No

Valores posibles: Entero largo positivo > 1.

Descripción: tamaño mínimo de memoria a liberar del caché de la base de datos cuando el motor necesita hacer espacio para ubicar un objeto (valor en bytes). 

El propósito de este selector es reducir el número de liberaciones de datos de la caché con el fin de obtener un mejor rendimiento. Puede hacer variar este parámetro en función del tamaño de la caché y del de los bloques de datos manipulados en su base. 

Por defecto, si este selector no se utiliza, 4D descarga mínimo 10% de la caché en caso de que se necesite espacio.



### Direct2D status (69)

**Alcance**: aplicación 4D

**Se conserva entre dos sesiones**: No

**Descripción**: modo de activación de Direct2D bajo Windows.

**Valores posibles**: una de las siguientes constantes (modo 3 por defecto):

Direct2D Disabled (0): el modo Direct2D no está habilitado y la base de datos funciona en el modo anterior (GDI/GDIPlus).

Direct2D Hardware (1): utilice Direct2D como contexto de hardware de gráficos para toda la aplicación 4D. Si este contexto no está disponible, use el contexto del software de gráficos Direct2D.

Direct2D Software (3) (modo predeterminado): a partir de Windows 7, utilice el contexto del software de gráficos Direct2D para toda la aplicación 4D.

***Advertencia* : este selector se proporciona solo para fines de depuración. Dado que varias funciones 4D se basan en Direct2D, no se debe desactivar en las aplicaciones implementadas. Solo el modo predeterminado (Direct2D Software)* **está aprobado para las aplicaciones desplegadas.*



### Direct2D get active status (74)

**Nota**: sólo puede utilizar este selector con el comando [Get database parameter](get-database-parameter.md "Get database parameter") y su valor no puede definirse.

**Descripción**: devuelve la implementación activa de Direct2D bajo Windows.

**Valores posibles**: 0, 1, 2, 3, 4 o 5 (ver los valores del selector 69). El valor devuelto depende de la disponibilidad de Direct2D, del hardware y de la calidad Direct2D soportado por el sistema operativo.

Por ejemplo, si ejecuta:

  SET DATABASE PARAMETER(Direct2D status;Direct2D Hardware)  $mode:=Get database parameter(Direct2D get active status)

- En Windows 7 y superiores, $mode vale 1 cuando el sistema detecta un hardware compatible con Direct2D; de lo contrario, $mode valdrá 3 (contexto software).

- En Windows Vista, $mode valdrá 1 si el sistema detecta un hardware compatible con Direct2D; de lo contrario, $mode toma el valor 0 (desactivando Direct2D).

- En Windows XP, $mode siempre valdrá 0 (no compatible con Direct2D).



### Diagnostic log recording (79)

**Thread-safe** : Yes

**Alcance**: Aplicación 4D

**Se conserva entre dos sesiones**: No

**Valores posibles**: 0 ó 1 (0 = no guardar,1 = guardar)

**Descripción**: inicio o detención del registro del archivo de diagnóstico de 4D. Por defecto, el valor es 0 (no guarda). 

4D permite guardar de manera continua en un archivo de diagnóstico un conjunto de eventos relativos al funcionamiento interno de la aplicación. La información contenida en este archivo está destinada a la actualización de las aplicaciones 4D y puede ser analizada con ayuda de los servicios técnicos de 4D. Cuando pasa 1 en este selector, el archivo de diagnóstico, llamado *NomBase.txt*, se crea automáticamente (o abre) en la carpeta **Logs** de la base. Una vez el archivo alcance un tamaño de 10 MB, se cierra y se genera un nuevo archivo *NomBase\_N.txt*, con un número secuencial N incrementado.

Note que es posible incluir la información personalizada en este archivo con ayuda del comando [LOG EVENT](log-event.md).



### Log command list (80)

**Alcance**: Aplicación 4D

**Se conserva entre dos sesiones**: No

**Valores posibles**: cadena que contiene la lista de números de los comandos 4D a guardar (separados por dos puntos), "all" para guardar todos los comandos o "" (cadena vacía) para no guardar ninguno.

**Descripción**: la lista de comandos 4D a guardar en el archivo de depuración (ver el selector 34, Debug Log Recording). Por defecto, se guardan todos los comandos 4D.

Este selector permite guardar la cantidad de información almacenada en el archivo de depuración limitando los comandos 4D donde quiera guardar la ejecución.



### Spellchecker (81)

**Alcance**: Aplicación 4D

 **Se conserva entre dos sesiones**: No

 **Valores posibles**: 0 (por defecto) = corrector macOS nativo (Hunspell desactivado), 1 = corrector Hunspell activo. 

**Descripción**: permite activar el corrector ortográfico Hunspell bajo macOS. Por defecto, en esta plataforma el corrector nativo está activo. Puede preferir utilizar el corrector Hunspell, por ejemplo, para unificar la interfaz de sus aplicaciones multiplataformas (bajo Windows, sólo el corrector Hunspell está disponible). Para mayor información, consulte *Corrección ortográfica*.



### Dates inside objects (85)

**Alcance**: Proceso actual

 **Se conserva entre dos sesiones:** No**

 Valores posibles**: String type without time zone (0), String type with time zone (1), Date type (2) (por defecto) 

**Descripción**: define la forma en que se almacenan las fechas dentro de los objetos, así como también cómo se importan / exportan en JSON.

Cuando el valor del selector es Date type (valor predeterminado para las bases creadas con 4D v17 y superior), las fechas 4D se almacenan con el tipo de fecha dentro de los objetos, con respecto a la configuración de fecha local. Cuando se convierte a formato JSON, los atributos de fecha se convertirán en cadenas que no incluyen un tiempo. (**Nota:** esta configuración se puede definir mediante la opción "Utilizar tipo de fecha en lugar del formato de fecha ISO en objetos" que se encuentra en *Página Compatibilidad* de la configuración de la base).

Si pasa String type with time zone en este selector, convertirá las fechas 4D en cadenas ISO y tendrá en cuenta la zona horaria local. Por ejemplo, la conversión de la fecha 23/08/2013 le da "2013-08-22T22: 00: 000Z" en formato JSON cuando la operación se realiza en Francia durante el horario de verano (GMT+ 2). Este principio se ajusta al funcionamiento estándar de JavaScript. Esto puede ser una fuente de errores cuando desea enviar valores de fecha JSON a alguien en un huso horario diferente. Por ejemplo, cuando exporta una tabla usando [Selection to JSON](selection-to-json.md) en Francia que se debe reimportar en los EE. UU. utilizando [JSON TO SELECTION](json-to-selection.md). Dado que las fechas se vuelven a interpretar en cada zona horaria, los valores almacenados en la base de datos serán diferentes. En este caso, puede modificar el modo de conversión de las fechas para que no tengan en cuenta la zona horaria pasando String type without time zone en este selector. La conversión de la fecha 23/08/2013 le dará "2013-08-23T00: 00: 00Z" en todos los casos.





### Diagnostic log level (86)

**Thread-safe** : Yes

**Alcance**: Aplicación 4D

**Se conserva entre dos sesiones**: No

**Descripción**: nivel(es) de los mensajes que se incluirán en el registro de diagnóstico cuando esté habilitado (ver selector Diagnostic log recording). Cada nivel designa una categoría de mensajes de diagnóstico e incluye automáticamente las categorías más importantes. Para una descripción de las categorías, consulte la sección *Niveles de registro de diagnóstico* en *developer.4d.com*. 

**Valores posibles**: una de las siguientes constantes (Log info por defecto): Log trace: activa ERROR, WARN, INFO, DEBUG, TRACE (nivel más detallado) Log debug: activa ERROR, WARN, INFO, DEBUG Log info: activa ERROR, WARN, INFO (por defecto) Log warn: activa ERROR, WARN Log error: activa ERROR (nivel menos detallado)



### Use legacy network layer (87)

**Alcance:** 4D en modo local, 4D Server**

Se conserva entre dos sesiones:** sí**

** **Descripción:** fija u obtiene el estado actual de la capa de red antigua para las conexiones cliente/servidor. 

La capa de red antigua es obsoleta a partir de 4D v14 R5 y debe ser reemplazada progresivamente en sus aplicaciones por la capa de red   *ServerNet*. *ServerNet* será requerida en próximas versiones 4D con el fin de beneficiarse de las futuras evoluciones de la red. Por razones de compatibilidad, la capa de red antigua aún se soporta para permitir una transición sin problemas para las aplicaciones existentes; (se usa por defecto en aplicaciones convertidas de una versión anterior a v14 R5). Pase 1 en este parámetro para utilizar la capa de red antigua (y desactivar *ServerNet*) para las conexiones cliente/servidor, y pase 0 para deshabilitar la red antigua (y utilizar *ServerNet*).

Esta propiedad también se puede definir mediante la opción "Usar capa de red antigua " que se encuentran en *Página Compatibilidad* de las Propiedades de la base (ver *Opciones red y cliente-servidor*). En esta sección, también puede encontrar una discusión sobre la estrategia de migración. Le recomendamos que active *ServerNet* tan pronto como sea posible.

Deberá reiniciar la aplicación para que este parámetro sea tenido en cuenta. No está disponible en 4D Server v14 R5 64-bit versión para macOS, que sólo soporta el *ServetNet*; (siempre devuelve 0).

**Valores posibles:** 0 o 1 (0 = no utilizan capa de red antigua, 1 = uso capa de red antigua)

**Valor por defecto:** 0 en bases de datos creadas con 4D v14 R5 o superior, 1 en bases de datos convertidas de 4D v14 R4 o anteriores.



### SQL Server Port ID (88)

**Alcance**: 4D modo local y 4D Server.

: Sí

**Descripción**: permite leer o definir el número del puerto TCP utilizado por el servidor SQL integrado de 4D en modo local o 4D Server. Por defecto, el valor es 19812\. Cuando se define este selector, la configuración de la base se actualiza. También puede definir el número del puerto TCP en la página "SQL" de la caja de diálogo de Propiedades de la base.

**Valores posibles:** 0 a 65535.

**Valor por defecto:** 19812



### Circular log limitation (90)

**Thread-safe** : Yes

**Alcance**: 4D local, 4D Server.

**Se conserva entre dos sesiones:** no

**Valores posibles**: todo valor entero, 0 = conservar todos los registros

**Descripción**: número máximo de archivos a conservar en rotación para cada tipo de registro. Por defecto, todos los archivos se conservan. Si pasa un valor *X*, solo los *X* archivos más recientes se conservan, el más antiguo se borra automáticamente cuando se crea uno nuevo. Esta parametrización se aplica a cada uno de los siguientes archivos de registro: registros de peticiones (selectores 28 y 45), registro de depuración (selector 34), registro de eventos (selector 79), así como el historial de peticiones web (selectores 29 y 84 del comando [WEB SET OPTION](web-set-option.md)), etc.



### Number of formulas in cache (92)

**Alcance**: aplicación 4D

**Se conserva entre dos sesiones:** no

**Valores posibles**: enteros largos positivos

**Valor por defecto**: 0 (sin caché) 

**Descripción**: establece u obtiene el número máximo de fórmulas a conservar en la memoria caché de fórmulas, que es utilizado por el comando [EXECUTE FORMULA](execute-formula.md). Este límite se aplica a todos los procesos, pero cada proceso tiene su propia caché de fórmulas. Ubicar las fórmulas en la caché acelera la ejecución del comando [EXECUTE FORMULA](execute-formula.md) en modo compilado, ya que cada fórmula en caché se tokeniza sólo una vez en este caso.Cuando se cambia el valor de la memoria caché, el contenido existente se restablecen incluso si el nuevo tamaño es más grande que el anterior. Una vez se alcanza el número máximo de fórmulas en la memoria caché, una nueva fórmula ejecutada borrará a la más antigua de la memoria caché (modo FIFO). Este parámetro sólo se tiene en cuenta en las bases o componentes compilados.



### OpenSSL version (94)

**Alcance**: todas las máquinas 4D

**Se conserva entre dos sesiones**: no

**Descripción**: devuelve el número de versión de la librería OpenSSL que se utiliza en la máquina. (Solo lectura)



### Cache flush periodicity (95)

**Thread-safe** : Yes


**Alcance**: 4D local, 4D Server

**Se conserva entre dos sesiones:** no

**Valores posibles:** entero largo > 1 (segundos)

**Descripción**: obtiene o establece la periodicidad del vaciado de la caché, expresado en segundos. La modificación de este valor prevalece sobre la opción **Vaciar caché cada X segundos** en [XML DECODE](xml-decode.md) de la configuración de la base para la sesión (que no se almacena en las Propiedades de la base).



### Remote connection sleep timeout (98)

**Alcance**: aplicación 4D Server

**Se mantiene entre dos sesiones**: no

**Valores posibles**: entero largo positivo

**Descripción**: tiempo de espera actual de la conexión remota en segundos. Por defecto, el valor es 172800 (48 horas). 

El tiempo de espera de la conexión remota se aplica después de que una máquina que ejecuta una aplicación remota 4D haya pasado al modo de reposo. En este caso, su sesión es mantenida por 4D Server (ver la descripción de la funcionalidad ). 4D Server verifica cada 5 minutos si algún 4D remoto en reposo ha superado el tiempo de espera de reposo, en cuyo caso se abandona. Por lo tanto, el máximo tiempo de espera permitido es *el tiempo de espera actual* \+ 300\. En algunos casos, es posible que desee modificar el tiempo de espera, por ejemplo para liberar los registros/licencias bloqueados más rápidamente. 





### Tips enabled (101)

**Alcance**: aplicación 4D

**Se conserva entre dos sesiones**: No

**Valores posibles**: 0 = consejos desactivados, 1 = consejos activados (predeterminado)

**Descripción**: define u obtiene el estado de visualización actual de los consejos para la aplicación 4D. De forma predeterminada, las sugerencias están activadas.

Tenga en cuenta que este parámetro define todos los consejos 4D, es decir, los mensajes de ayuda de formulario y las sugerencias del editor de modo Diseño.



### Tips delay (102)

**Alcance**: aplicación 4D

**Se conserva entre dos sesiones**: No

**Valores posibles**: entero largo >= 0 (tics)

**Descripción**: retraso antes de que se muestren las sugerencias una vez que el cursor del ratón se haya detenido en objetos con mensajes de ayuda adjuntos. El valor se expresa en tics (1/60 de segundo). El valor predeterminado es 45 tics (0.75 segundos).



### Tips duration (103)

**Alcance**: aplicación 4D

**Se conserva entre dos sesiones**: No

**Valores posibles**: entero largo >= 60 (tics)

**Descripción**: duración máxima de visualización de una sugerencia. El valor se expresa en tics (1/60 de segundo). El valor predeterminado es 720 tics (12 segundos).



### Min TLS version (105)

**Alcance**: 4D Server, 4D Web Server y 4D SQL Server

**Conservar entre dos sesiones**: No

**Descripción**: se utiliza para especificar el nivel TLS (Transport Layer Security), que ofrece cifrado y autenticación de datos entre aplicaciones y servidores. Se rechazarán los intentos de conexión de clientes que sólo soporten versiones inferiores a la mínima. La configuración se aplica globalmente a la capa de red. Una vez modificado, el servidor debe reiniciarse para utilizar el nuevo valor. 

**Valor por defecto**: TLSv1\_3 

**Valores posibles**: TLSv1\_2 (TLS 1.2, introducido en 2008) TLSv1\_3 (TLS 1.3, introducido en 2018) **NOTAS**: 

- El plugin 4D Internet Commands utiliza una capa de red diferente, por lo que este selector no tendrá ningún impacto en su versión TLS.

- Se ignorarán los intentos de aplicar TLS a la capa de red heredada. 







### User param value (108)

**Alcance**: 4D local, 4D Server

**Se conserva entre dos sesiones**: no

**Valores posibles**: toda cadena personalizada

**Descripción:** cadena personalizada pasada de una sesión a la siguiente cuando se reinicia la aplicación 4D. Este selector es útil en el contexto de pruebas unitarias automatizadas que requieren que las aplicaciones se reinicien con diferentes parámetros.

Cuando se utiliza con [SET DATABASE PARAMETER](set-database-parameter.md), define un nuevo valor que estará disponible en la próxima base de datos abierta después de que 4D se reinicie manualmente o utilizando los comandos [OPEN DATABASE](open-database.md)(\*), [OPEN DATA FILE](open-data-file.md), o [RESTART 4D](restart-4d.md). Cuando se utiliza con [Get database parameter](get-database-parameter.md), obtiene el valor del parámetro de usuario actualmente disponible, definido mediante una línea de comando (ver *Interfaz de línea de comando*), el archivo .4DLink (ver *Usar un archivo 4DLink*), o una llamada a [SET DATABASE PARAMETER](set-database-parameter.md) durante la sesión anterior. (\*) Si [SET DATABASE PARAMETER](set-database-parameter.md) define un User param value antes de una llamada a [OPEN DATABASE](open-database.md) con un archivo .4DLink que también contiene un atributo xml user-param, 4D 4D tiene en cuenta solo el parámetro ofrecido por [SET DATABASE PARAMETER](set-database-parameter.md).



### Times inside objects (109)

Alcance: 4D local, 4D Server (todos los procesos)

 Se conserva entre dos sesiones: No

 **Valores posibles**: Times in seconds (0) (predeterminado), Times in milliseconds (1) 

**Descripción**: define la forma en que los valores de tipo hora se convierten y almacenan dentro de las propiedades de los objetos y los elementos de la colección, así como la forma en que se importan/exportan en JSON y en las áreas web. Por defecto, a partir de 4D v17, las horas se convierten y almacenan en número de segundos en los objetos. 

En versiones anteriores, los valores de tiempo se convertían y almacenaban como cantidad de milisegundos en esos contextos. Usar este selector puede ayudarlo a migrar sus aplicaciones volviendo a la configuración anterior si es necesario.

**Nota**: los métodos ORDA y el motor SQL ignoran esta configuración, siempre suponen que los valores de tiempo son números de segundos.



### SMTP Log (110)

**Thread-safe** : Yes

**Alcance**: 4D local, 4D Server*

* **Se conserva entre dos sesiones**: No

 **Valores posibles**: 0 o de 1 a X (0 = no grabar, 1 a X = número secuencial, agregado al nombre del archivo). De forma predeterminada, el valor es 0 (intercambios SMTP no registrados).

**Descripción**: inicia o detiene la grabación de intercambios entre 4D y el servidor SMTP, cuando un objeto *transportador* se procesa a través de *transporter.send( )* o *SMTP\_transporter.checkConnection( )*. Por defecto, el valor es 0 (intercambios no registrados). Cuando este mecanismo está habilitado, se crea un archivo de registro en la carpeta Logs de la base. Se llama 4DSMTPLog\_X.txt, donde X es el número secuencial del registro. Una vez que el archivo 4DSMTPLog ha alcanzado un tamaño de 10 MB, se cierra y se genera uno nuevo, con un número secuencial incrementado. Si ya existe un archivo con el mismo nombre, se reemplaza directamente. Puede definir el número de inicio de la secuencia utilizando el parámetro *valor*. De forma predeterminada, todos los archivos se conservan, pero puede controlar la cantidad de archivos a seguir utilizando el parámetro Circular log limitation. 

Para obtener más información sobre los archivos 4DSMTPLog\_X.txt, consulte la sección *Descripción de archivos de historial*.



### Current process debug log recording (111)

**Alcance:** Aplicación 4D

**Se conserva entre dos sesiones:** No

**Descripción**: inicia o detiene el registro secuencial de eventos de programación **del proceso actual** en un archivo de historial separado. Este historial es similar al Debug log recording (selector 34) pero se enfoca solo en el proceso actual. El nombre del archivo de historial incluye la letra "p" y el número del proceso: 4DDebugLog\[\_p*N*_*n*].txt, donde N es el ID único del proceso. Para más información sobre este formato y sobre el uso del archivo *4DDebugLog*, consulte *Descripción de archivos de historial* en el Modo Diseño. **Notas:** Este selector se proporciona únicamente con el fin de depurar y debe utilizarse con cuidado. En particular, no debe ponerse en producción, ya que puede tener un impacto en el rendimiento de la aplicación. Puede utilizarar ambos selectores Debug log recording y Current process debug log recording simultáneamente, en cuyo caso las acciones del proceso actual no se registrarán en el archivo de historial principal.



### Is current database a project (112)

**Nota:** solo puede utilizar este selector con el comando [Get database parameter](get-database-parameter.md) y su valor no se puede definir.

**Alcance**: aplicación 4D

**Descripción**: devuelve 1 si la arquitectura de la base actual es un proyecto y 0 en caso contrario. Para más información, consulte la sección *Base proyecto vs base binaria*.



### Is host database a project (113)

**Nota:** solo puede utilizar este selector con el comando [Get database parameter](get-database-parameter.md) y su valor no se puede definir.

**Alcance**: aplicación 4D

**Descripción**: devuelve 1 si la arquitectura de la base local es un proyecto y 0 en caso contrario. Para más información, consulte la sección *Base proyecto vs base binaria*.



### Libldap version (114)

**Alcance**: máquina 4D actual 

**Se conserva entre dos sesiones**: no

**Descripción**: devuelve el número de versión de la librería LDAP en la aplicación 4D en la máquina actual. (Solo lectura)



### Libsasl version (115)

**Alcance**: máquina 4D actual 

**Se conserva entre dos sesiones**: no

**Descripción**: devuelve el número de versión de la librería SASL en la aplicación 4D en la máquina actual. (Solo lectura)



### POP3 Log (116)

**Thread-safe** : Yes

**Alcance:** 4D local, 4D Server

**Se conserva entre dos sesiones**: no

**Valores posibles:** 0 o de 1 a X (0 = no registrar, 1 a X = número secuencial, agregado al nombre del archivo). Por defecto, el valor es 0 (intercambios POP3 no registrados).

: iInicia o detiene la grabación de intercambios entre 4D y el servidor POP3, cuando un objeto transportador se procesa a través de *POP3\_transporter.getMail( )* o *POP3\_transporter.checkConnection( )*. Por defecto, el valor es 0 (intercambios no registrados). Cuando este mecanismo está habilitado, se crea un archivo de registro en la carpeta Logs de la base. Se llama 4DPOP3Log\_X.txt, donde X es el número secuencial del registro. Una vez que el archivo 4DPOP3Log ha alcanzado un tamaño de 10 MB, se cierra y se genera uno nuevo, con un número secuencial incrementado. Si ya existe un archivo con el mismo nombre, se reemplaza directamente. Puede establecer el número inicial de la secuencia utilizando el parámetro valor. De manera predeterminada, todos los archivos se mantienen, pero puede controlar la cantidad de archivos que se deben seguir utilizando el parámetro Circular log limitation. 

Para más información sobre los archivos 4DPOP3Log\_X.txt, consulte la sección *Descripción de archivos de historial*.



### Is host database writable (117)

**Nota**: solo puede utilizar este selector con el comando [Get database parameter](get-database-parameter.md) y su valor no se puede definir.

**Alcance**: aplicación 4D

**Descripción**: devuelve 1 si el archivo estructura/archivo proyecto local es editable y 0 si es de solo lectura.



### IMAP Log (119)

**Thread-safe** : Yes

**Alcance**: 4D local, 4D Server

**Se conserva entre dos sesiones**: No

**Valores posibles**: 0 o de 1 a X (0 = no grabar, 1 a X = número secuencial, añadido al nombre del archivo). Por defecto, el valor es 0 (los intercambios IMAP no se registran).

**Descripción**: inicia o detiene la grabación de los intercambios entre 4D y el servidor IMAP, cuando se procesa un objeto transportador a través de *IMAP\_transporter.getMail( )* o *IMAP\_transporter.checkConnection( )*. Por defecto, el valor es 0 (intercambios no registrados). Cuando se activa este mecanismo, se crea un archivo de registro en la carpeta Logs de la base. Se llama 4DIMAPLog\_X.txt, donde X es el número secuencial del registro. Una vez que el archivo 4DIMAPLog ha alcanzado un tamaño de 10 MB, se cierra y se genera uno nuevo, con un número secuencial incrementado. Si ya existe un archivo con el mismo nombre, se sustituye directamente. Se puede definir el número inicial de la secuencia mediante el parámetro valor. Por defecto, se conservan todos los archivos, pero puede controlar el número de archivos a conservar utilizando el parámetro Circular log limitation.

Para más información sobre los archivos 4DIMAPLog\_X.txt, consulte la sección *Descripción de archivos de historial*.



### Libzip version (120)

**Alcance**: máquina 4D actual

**Se conserva entre dos sesiones**: n/a

**Descripción**: devuelve el número de versión de la librería libzip en la aplicación 4D en la máquina actual. (Sólo lectura)



### Pause logging (121)

**Thread-safe** : Yes

**Alcance**: aplicación 4D

**Se mantiene entre dos sesiones**: no

**Valores posibles**: 0 (reanudar historial), 1 (pausar historial)

Este selector permite suspender/reanudar todas las operaciones de registro iniciadas en la aplicación (excepto los registros ORDA). Esta función puede ser útil para aligerar temporalmente las tareas de la aplicación 4D o programar las operaciones de registro.




  
  
**Nota**: el parámetro *tabla* sólo es utilizado por los selectores 31, 46 y 47\. En todos los demás casos, se ignora si se pasa. 

Si no se mantiene una configuración constante entre sesiones, pero desea asegurarse de que se aplique, debe ejecutarla en o [Método base On Server Startup](metodo-base-on-server-startup.md).

#### Selectores hilo seguro 

El comando **SET DATABASE PARAMETER** puede utilizarse en procesos apropiativos al llamar a los siguientes selectores:

* [4D Server log recording](#4d-server-log-recording-28)
* [Debug log recording](#debug-log-recording-34)
* [Diagnostic log recording](#diagnostic-log-recording-79)
* [Diagnostic log level](#diagnostic-log-level-86)
* [Circular log limitation](#circular-log-limitation-90)
* [Cache flush periodicity](#cache-flush-periodicity-95)
* [SMTP Log](#smtp-log-110)
* [POP3 Log](#pop3-log-116)
* [IMAP Log](#imap-log-119)
* [Pause logging](#pause-logging-121)


#### Ejemplo 1 

La siguiente instrucción evitará un posible problema de timeout:

```4d
  //Aumento del timeout a 3 horas para el proceso actual
 SET DATABASE PARAMETER(4D Server Timeout;-60*3)
  //Ejecución de una operación larga sin control de 4D
 ...
 WR PRINT MERGE(Area;3;0)
 ...
```

#### Ejemplo 2 

Este ejemplo forza temporalmente la ejecución de un comando búsqueda por fórmula en el equipo cliente:

```4d
 curVal:=Get database parameter([tabla1];Query By Formula On Server) //Almacena la configuración actual
 SET DATABASE PARAMETER([tabla1];Query By Formula On Server;1) //Fuerza la ejecución en el equipo cliente
```

#### Ejemplo 3 

Usted quiere exportar datos en JSON que contienen una fecha 4D convertida. Note que la conversión ocurre cuando la fecha se guarda en el objeto, debe llamar al comando [SET DATABASE PARAMETER](set-database-parameter.md) antes de llamar a [OB SET](ob-set.md): 

```4d
 var $o : Object
 SET DATABASE PARAMETER(Dates inside objects;0)
 OB SET($o ;"myDate";Current date) // conversión JSON
 $json:=JSON Stringify($o)
 SET DATABASE PARAMETER(Dates inside objects;1)
```

#### Ver también 

[Get database parameter](get-database-parameter.md)  
[LOG EVENT](log-event.md)  
[QUERY SELECTION](query-selection.md)  

#### Propiedades

|  |  |
| --- | --- |
| Número de comando | 642 |
| Hilo seguro | &cross; |


