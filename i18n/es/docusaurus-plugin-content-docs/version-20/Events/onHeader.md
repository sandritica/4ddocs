---
id: onHeader
title: On Header
---

| Code | Puede ser llamado por                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Definición                                                                    |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| 5    | [Área 4D Write Pro](FormObjects/writeProArea_overview.md) - [Botón ](FormObjects/button_overview.md) - [Rejilla de botones](FormObjects/buttonGrid_overview.md) - [Casilla de selección](FormObjects/checkbox_overview.md) - [Lista desplegable](FormObjects/dropdownList_Overview.md) - Formulario (formulario lista únicamente) - [Lista jerárquica](FormObjects/list_overview.md) - [Área de entrada](FormObjects/input_overview.md) - [Botón imagen](FormObjects/pictureButton_overview.md) - [Imagen del menu pop-up](FormObjects/picturePopupMenu_overview.md) - [Área de plug-in](FormObjects/pluginArea_overview.md) - [Indicador de progreso](FormObjects/progressIndicator.md) - [Botón rádio](FormObjects/radio_overview.md) - [Regla](FormObjects/ruler.md) - [Spinner](FormObjects/spinner.md) - [Splitter](FormObjects/splitters.md) - [Stepper](FormObjects/stepper.md) - [Control de tabulación](FormObjects/tabControl.md) | El área del encabezado del formulario está a punto de imprimirse o mostrarse. |


## Descripción

El evento `On Header` se llama cuando un registro está a punto de ser visualizado en un formulario de lista que se muestra vía `DISPLAY SELECTION` y `MODIFY SELECTION`.

> Este evento no se puede seleccionar para los formularios proyecto, sólo está disponible con los **formularios tabla**.

En este contexto, se desencadena la siguiente secuencia de llamadas a métodos y eventos de formulario:

- Para cada objeto en el área del encabezado:
    - Método objeto con el evento `On Header`
    - Método formulario con el evento `On Header`

> Los registros impresos se gestionan mediante el evento [`On Display Detail`](onDisplayDetail.md).

Llamar a un comando 4D que muestra una caja de diálogo desde el evento `On Header` no está permitido y provocará un error de sintaxis. Más concretamente, los comandos en cuestión son: `ALERT`, `DIALOG`, `CONFIRM`, `Request`, `ADD RECORD`, `MODIFY RECORD`, `DISPLAY SELECTION` y `MODIFY SELECTION`.