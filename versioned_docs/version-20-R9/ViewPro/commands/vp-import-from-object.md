---
id: vp-import-from-object
title: VP IMPORT FROM OBJECT
---

<details><summary>History</summary>

|Release|Changes|
|---|---|
|20 R9|Support of *paramObj* parameter|
</details>

<!-- REF #_method_.VP IMPORT FROM OBJECT.Syntax -->
**VP IMPORT FROM OBJECT** ( *vpAreaName* : Text  { ; *viewPro* : Object { ; *paramObj* : Object} } ) <!-- END REF -->

<!-- REF #_method_.VP IMPORT FROM OBJECT.Params -->

| Parameter    | Type   |  | Description |
|-------------|--------|---|-------------|
| vpAreaName  | Text   | -> | 4D View Pro area form object name |
| viewPro     | Object | -> | 4D View Pro object |
| paramObj    | Object | -> | (Optional) import options |

<!-- END REF -->

## Description

The `VP IMPORT FROM OBJECT` command <!-- REF #_method_.VP IMPORT FROM OBJECT.Summary -->imports and displays the *viewPro* 4D View Pro object in the *vpAreaName* 4D View Pro area<!-- END REF -->. The imported object contents replaces any data already inserted in the area.

In *vpAreaName*, pass the name of the 4D View Pro area. If you pass a name that does not exist, an error is returned.

In *viewPro*, pass a valid 4D View Pro object. This object can have been created using [VP Export to object](vp-export-to-object.md) or manually. For more information on 4D View Pro objects, please refer to the [4D View Pro object](../configuring.md#4d-view-pro-object) section.

An error is returned if the *viewPro* object is invalid.

In *paramObj*, you can pass the following property:

| Property | Type | Description |
|----------|------|-------------|
| formula  | 4D.Function | (Optional) Callback function to be executed when the object is loaded and all 4D custom functions have responded. See [Passing a callback method (formula)](vp-export-document.md#passing-a-callback-method-formula). |

The following parameters can be used in the callback method:

| Parameter |  | Type | Description |
|-----------|----|------|-------------|
| param1    |  | Text | The name of the 4D View Pro area object |
| param2    |  | Text | Reserved for compatibility, this parameter is always empty |
| param3    |  | Object | A reference to the command's *paramObj* parameter |
| param4    |  | Object | An object returned by the method with a status message |
|           | .success | Boolean | `True` if import was successful, `False` otherwise |
|           | .errorCode | Integer | Error code |
|           | .errorMessage | Text | Error message |

:::note

The callback function specified in the `formula` attribute is triggered after all [4D custom functions](../formulas.md#4d-functions) within the imported content have completed their calculations. This ensures that any dependent processes, such as document modifications or exports, are performed only after all formula-based computations are fully resolved.

:::

## Example

You want to import a spreadsheet that was previously saved in an object field, and trigger a callback function after all 4D custom functions have responded:

```4d
QUERY([VPWorkBooks];[VPWorkBooks]ID=10)

VP IMPORT FROM OBJECT("ViewProArea1"; [VPWorkBooks]SPBook; {formula: Formula(onImportComplete)})
```

```4d
// Method 'onImportComplete'
#DECLARE($name : Text; $path : Text; $paramObj : Object; $status : Object)
   ALERT("The document has been imported, and all custom functions have finished processing.")
```

## See also

[VP Export to object](vp-export-to-object.md)