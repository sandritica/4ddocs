---
id: security
title: Página seguridad
---

Esta página contiene opciones relacionadas con la protección del acceso y de los datos de sus aplicaciones de escritorio.

**Nota**: para una visión general de las funciones de seguridad de 4D, consulte la [guía de seguridad de 4D](https://blog.4d.com/4d-security-guide/).

## Acceso a datos / Acceso de usuarios remotos

> Estos parámetros no se aplican a las bases proyecto abiertas en modo monopuesto.

- **Acceso Diseño y al Explorador de ejecución**: da al grupo especificado la capacidad de entrar al modo Diseño de la base y mostrar el Explorador de ejecución.

    Note que:

    - La definición de un grupo de acceso en el entorno Diseño también permite desactivar la opción **Crear una tabla** de la caja de diálogo de importación de datos. Para más información sobre esta caja de diálogo, consulte [Importar los datos desde los archivos](https://doc.4d.com/4Dv20/4D/20.2/Importing-data-from-files.300-6750325.en.html).

    - El Diseñador y el Administrador siempre tienen acceso al entorno de diseño y al Explorador de ejecución, incluso si no son parte explícitamente del grupo de acceso específico. Para más información sobre usuarios y grupos de usuarios, consulta el capítulo [Usuarios y grupos](../Users/handling_users_groups.md).

- **Usuario por defecto**: cuando se ha definido un Usuario por defecto, todos los usuarios que abren o se conectan a la base tienen los mismos privilegios y restricciones de acceso definidos para este Usuario por defecto. Ya no es necesario ingresar un nombre de usuario. Además, si no ha asociado una contraseña al usuario por defecto, la caja de diálogo Contraseña ya no aparece y la base se abre directamente.
    Esta opción simplifica el acceso a la base de datos a la vez que mantiene un sistema completo de control de datos.

    - Si ha asociado una contraseña al usuario predeterminado, al abrir la base aparece una caja de diálogo en el que los usuarios deben introducir una contraseña.
    - Si no ha asociado una contraseña al Usuario Predeterminado, la caja de diálogo de Identificación de Usuario no aparecerá.**Nota:** puede "forzar" la visualización de la caja de diálogo Identificación de usuario cuando el modo "Usuario por defecto" está activo, por ejemplo para conectarse como Administrador o Diseñador. Para ello, presione la tecla **Mayús** mientras abre la base de datos o se conecta a ella.

- **Mostrar lista de usuarios en la caja de diálogo Contraseña**: si se marca esta opción, los usuarios deben elegir su nombre en la lista de usuarios e introducir su contraseña en la caja de diálogo de identificación de usuario. Si no está marcada, los usuarios deben introducir tanto su nombre como su contraseña. Para obtener más información sobre las dos versiones de la caja de diálogo de contraseña, consulte la sección "Acceso a las bases protegidas" en [Presentación del control de acceso](https://doc.4d.com/4Dv20/4D/20.2/Access-system-overview.300-6750353.en.html

    - **Ordenar la lista de los usuarios en orden alfabético** (sólo disponible si está marcada la opción anterior): cuando esta opción está seleccionada, la lista de los usuarios de la caja de diálogo de introducción de contraseña se ordena por orden alfabétic

- **Los usuarios pueden cambiar su contraseña**: cuando esta opción está marcada, aparece un botón **Cambiar** en la caja de diálogo Identificación del usuario. Este botón permite al usuario acceder a una caja de diálogo que puede utilizar para modificar su contraseña (para más información sobre esta caja de diálogo, consulte "Modificación de la contraseña por el usuario" en [Garantizar el mantenimiento del sistema](https://doc.4d.com/4Dv20/4D/20.2/Ensuring-system-maintenance.300-6750352.en.html)). Si lo desea, puede ocultar el botón **Cambiar** para que los usuarios no puedan modificar sus contraseñas. Para ello, desmarque esta opción.

## Opciones

- **Filtrado de comandos y métodos proyecto en el editor de fórmulas y en los documentos 4D View Pro y 4D Write Pro**:
    por razones de seguridad, por defecto 4D restringe el acceso a los comandos, funciones y métodos proyecto en el [Editor de fórmulas](https://doc.4d.com/4Dv20/4D/20.2/Formula-editor.200-6750079.en.html) en el modo Aplicación o añadido a áreas multiestilo (usando [`ST INSERT EXPRESSION`](../commands-legacy/st-insert-expression.md)), Documentos 4D Write Pro y 4D View Pro: sólo ciertas funciones 4D y métodos proyecto que han sido declarados explícitamente utilizando el comando [`SET ALLOWED METHODS`](../commands/set-allowed-methods.md) pueden ser utilizados. Puede eliminar total o parcialmente este filtrado mediante las siguientes opciones.
    - **Activado para todos** (opción por defecto): el acceso a los comandos, funciones y métodos proyecto está restringido para todos los usuarios, incluidos el Diseñador y el Administrador.
    - **Desactivado para el Diseñador y el Administrador**: esta opción concede acceso completo a los comandos 4D y a los métodos sólo al Diseñador y al Administrador. Permite definir un modo de acceso ilimitado a los comandos y métodos sin perder el control de las operaciones efectuadas. Durante la fase de desarrollo, este modo puede utilizarse para probar libremente todas las fórmulas, informes, etc. Durante el funcionamiento, puede utilizarse para definir soluciones seguras que permitan el acceso temporal a comandos y métodos. This consists in changing the user (via the [`CHANGE CURRENT USER`](../commands-legacy/change-current-user.md) command) before calling a dialog box or starting a printing process that requires full access to the commands, then returning to the original user when the specific operation is completed.
        **Nota:** si se ha activado el acceso completo mediante la opción anterior, esta opción no tendrá ningún efecto.
    - **Desactivado para todos**: esta opción desactiva el control en las fórmulas. Cuando esta opción está marcada, los usuarios tienen acceso a todos los comandos 4D, plug-ins y métodos proyecto (excepto los invisibles).
        **Nota:** esta opción tiene prioridad sobre el comando [`SET ALLOWED METHODS`](../commands/set-allowed-methods.md). Cuando se selecciona, este comando no hace nada.

- **Autorizar las propiedades usuario**: debe marcar esta opción para poder mostrar cajas de diálogo separadas para las propiedades usuario. Cuando esta opción está marcada, hay disponibles hasta tres cuadros de diálogo: **Propiedades estructura**, **Propiedades usuario**, y **Propiedades usuario para archivo de datos**. Para más información, consulte [Parámetros usuario](../Desktop/user-settings.md).

- **Ejecutar el método "On Host Database Event" de los componentes**: el [método base On Host Database Event](../commands-legacy/on-host-database-event-database-method.md) facilita las fases de inicialización y copia de seguridad de los componentes 4D. Por razones de seguridad, debe autorizar explícitamente la ejecución de este método en cada base de datos local. Para hacer esto, debe marcar esta opción. Por defecto, no está marcado.

    Cuando esta opción está seleccionada:

    - los componentes 4D están cargados,
    - cada método base [On Host Database Event](../commands-legacy/on-host-database-event-database-method.md) del componente (si lo hay) es llamado por la base local,
    - se ejecuta el código del método.

    Cuando no está marcada:

    - Los componentes 4D se cargan, pero tienen que gestionar ellos mismos sus fases de inicialización y copia de seguridad.
    - el desarrollador del componente tiene que publicar los métodos del componente que deben ser llamados por la base de datos anfitriona durante estas fases (inicio y cierre)
    - el desarrollador de la base local debe llamar a los métodos apropiados del componente en el momento adecuado (debe estar contemplado en la documentación del componente).