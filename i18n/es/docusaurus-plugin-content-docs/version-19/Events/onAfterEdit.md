---
id: onAfterEdit
title: On After Edit
---

| Code | Puede ser llamado por                                                                                                                                                                                                                                                                                                                                                                               | Definición                                                                     |
| ---- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| 45   | [Área 4D View Pro](FormObjects/viewProArea_overview.md) - [Área 4D Write Pro](FormObjects/writeProArea_overview.md) - [Combo Box](FormObjects/comboBox_overview.md) - Formulario - [Entrada](FormObjects/input_overview.md) - [Lista Jerárquica](FormObjects/list_overview.md) - [List Box](FormObjects/listbox_overview.md) - [Columna List Box](FormObjects/listbox_overview.md#list-box-columns) | El contenido del objeto introducible que tiene el foco acaba de ser modificado |

## Descripción

### Caso general

Este evento se puede utilizar para filtrar la entrada de datos en los objetos editables por teclado en el nivel más bajo.

Cuando se utiliza, este evento se genera después de cada cambio realizado en el contenido de un objeto editable, independientemente de la acción que haya provocado la modificación, *es decir*:

- Acciones de edición estándar que modifican el contenido como pegar, cortar, borrar o cancelar;
- Soltar un valor (acción similar a pegar);
- Toda entrada de teclado realizada por el usuario; en este caso, el evento `On After Edit` se genera después de los eventos [`On Before Keystroke`](onBeforeKeystroke.md) y [`On After Keystroke`](onAfterKeystroke.md), si se utilizan.
- Cualquier modificación realizada mediante un comando del lenguaje que simule una acción del usuario (es decir, `POST KEY`).

En el evento `On After Edit`, los datos de texto introducidos son devueltos por el comando [`Get edited text`](https://doc.4d.com/4dv19/help/command/en/page655.html).

### 4D View Pro

El objeto devuelto por el comando `FORM Event` contiene:

| Propiedad   | Tipo         | Descripción                                                                                         |
| ----------- | ------------ | --------------------------------------------------------------------------------------------------- |
| code        | entero largo | On After Edit                                                                                       |
| description | text         | "On After Edit"                                                                                     |
| objectName  | text         | Nombre del área 4D View Pro                                                                         |
| sheetName   | text         | Nombre de la hoja del evento                                                                        |
| action      | text         | "editChange", "valueChanged", "DragDropBlock", "DragFillBlock", "formulaChanged", "clipboardPasted" |

En función del valor de la propiedad `action`, el [objeto evento](overview.md#event-object) contendrá propiedades adicionales.

#### action = editChange

| Propiedad   | Tipo    | Descripción                            |
| ----------- | ------- | -------------------------------------- |
| range       | object  | Rango de celdas                        |
| editingText | variant | El valor proveniente del editor actual |

#### action = valueChanged

| Propiedad | Tipo    | Descripción                                |
| --------- | ------- | ------------------------------------------ |
| range     | object  | Rango de celdas                            |
| oldValue  | variant | Valor de la celda antes de la modificación |
| newValue  | variant | Valor de la celda luego de la modificación |

#### action = DragDropBlock

| Propiedad | Tipo    | Descripción                                        |
| --------- | ------- | -------------------------------------------------- |
| fromRange | object  | Rango de celdas fuente (que se arrastra)           |
| toRange   | object  | Rango de la celda de destino (ubicación de soltar) |
| copy      | boolean | Indica si el rango fuente se copia o no            |
| insert    | boolean | Indica si el rango fuente se inserta o no          |

#### action = DragFillBlock

| Propiedad | Tipo   | Descripción                    |
| --------- | ------ | ------------------------------ |
| fillRange | object | Gama utilizada para el relleno |
 autoFillType|longint|Valor utilizado para el relleno.<li>0: las celdas se llenan con todos los datos (valores, formato y fórmulas)</li><li>1: las celdas se llenan con datos automáticamente secuenciales</li><li>2: Las celdas se llenan sólo con el formato</li><li>3: Las celdas se llenan de valores pero sin formato</li><li>4: Se eliminan los valores de las celdas</li><li>5: Las celdas se llenan automáticamente</li>| |fillDirection|longint|Direction of the fill.<li>0: Se llenan las celdas de la izquierda</li><li>1: Se llenan las celdas a la derecha</li><li>2: Las celdas de arriba se llenan</li><li>3: Las celdas de abajo se llenan</li>|

#### action = formulaChanged

| Propiedad | Tipo   | Descripción            |
| --------- | ------ | ---------------------- |
| range     | object | Rango de celdas        |
| formula   | text   | La fórmula introducida |

#### action = clipboardPasted

| Propiedad   | Tipo         | Descripción                                                                                                                                                                                              |
| ----------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| range       | object       | Rango de celdas                                                                                                                                                                                          |
| pasteOption | entero largo | Indica lo que se pega desde el portapapeles:<li>0: se pega todo (valores, formato y fórmulas)</li><li>1: solo se pegan los valores</li><li>2: sólo se pega el formato</li><li>3: solo se pegan las fórmulas</li><li>4: los valores y el formato se pegan (no las fórmulas)</li><li>5: las fórmulas y el formato se pegan (no los valores)</li> |
| pasteData   | object       | Los datos del portapapeles a pegar<li>"text" (texto): el texto del portapapeles</li><li>"html" (texto): el código HTML del portapapeles</li>                                                                                                                   |

#### Ejemplo

Aquí hay un ejemplo de manejo de un evento `On After Edit`:

```4d
 If(FORM Event.code=On After Edit)
    If(FORM Event.action="valueChanged")
       ALERT("WARNING: You are currently changing the value\  
       from "+String(FORM Event.oldValue)+\  
       " to "+String(FORM Event.newValue)+"!")
    End if
 End if
    End if
 End if
    End if
 End if
    End if
 End if
```

El ejemplo anterior podría generar un objeto evento como este:

```
{

"code":45;
"description":"On After Edit";
"objectName":"ViewProArea"
"sheetname":"Sheet1";
"action":"valueChanged";
"range": {area:ViewProArea,ranges:[{column:1,row:2,sheet:1}]};
"oldValue":"The quick brown fox";
"newValue":"jumped over the lazy dog";
}
```
