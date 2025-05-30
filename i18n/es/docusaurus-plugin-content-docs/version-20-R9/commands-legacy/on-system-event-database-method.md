---
id: on-system-event-database-method
title: On System Event database method
slug: /commands/on-system-event-database-method
displayed_sidebar: docs
---

<!--REF #_command_.On System Event database method.Syntax-->$event -> Método base On System Event<!-- END REF-->
<!--REF #_command_.On System Event database method.Params-->
| Parámetro | Tipo |  | Descripción |
| --- | --- | --- | --- |
| $event | Entero largo | &#8592; | Código del evento |

<!-- END REF-->

## Descripción 

<!--REF #_command_.On System Event database method.Summary-->El **Método base On System Event** se llama cada vez que ocurre un evento sistema.<!-- END REF--> Esto concierne a todos los entornos 4D: 4D (todos los modos) y 4D Server, así como también las aplicaciones 4D compiladas y fusionadas con 4D Volume Desktop.

Para procesar un evento, debe probar el valor del parámetro $event al interior del método y compararlo con una de las siguientes constantes, del tema *Eventos de la base*:

| Constante                      | Tipo         | Valor | Comentario                            |
| ------------------------------ | ------------ | ----- | ------------------------------------- |
| On application background move | Entero largo | 1     | La aplicación 4D pasa al fondo        |
| On application foreground move | Entero largo | 2     | La aplicación 4D pasa al primer plano |

Estos eventos se generan cuando la aplicación 4D cambia de nivel, sin importar la acción del usuario que genera este cambio. Por ejemplo: 

* clic en la ventana de la aplicación o de otra aplicación,
* selección utilizando el atajo de teclado **Alt+Tab** (Windows) o **Comando+Tab** (macOS),
* selección del comando **Ocultar** en el dock (macOS),
* clic en el icono de la aplicación en el dock o la barra de tareas,
* clic en el botón de minimización de la ventana principal (Windows).

Es absolutamente necesario declarar el parámetro $event (entero largo) en el método base. La estructura del código del método base será entonces:

```4d
  // Método base On System Event
 
 #DECLARE($event : Integer)
 Case of
    :($event=On application background move)
  //Hacer algo
    :($event=On application foreground move)
  //Hacer otra cosa
 End case
```
