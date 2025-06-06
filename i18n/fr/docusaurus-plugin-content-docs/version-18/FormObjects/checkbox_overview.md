---
id: checkboxOverview
title: Case à cocher
---

## Vue d’ensemble

Une case à cocher est un type de bouton utilisée pour saisir ou afficher une donnée binaire (vrai-faux). Elle peut être soit sélectionnée soit désélectionnée, mais un troisième état peut également être défini (voir ci-dessous).

![](../assets/en/FormObjects/checkbox.png)

L’effet d’une case à cocher est contrôlé par une méthode. Comme tous les boutons, une case à cocher est initialisée à la valeur zéro lorsque le formulaire est ouvert pour la première fois. La méthode associée à une case à cocher est exécutée lorsqu’elle est cochée.

Une case à cocher affiche généralement du texte en face de la case. Ce texte est défini dans la zone [Titre](properties_Object.md#title) du thème “Objets” de la Liste des propriétés. Vous pouvez saisir dans cette zone un libellé sous forme de référence XLIFF (cf. [Annexe B : Architecture XLIFF](https://doc.4d.com/4Dv17R5/4D/17-R5/Appendix-B-XLIFF-architecture.300-4163748.en.html)).

## Utiliser une case à cocher

Une case à cocher peut être associée à une [variable ou expression](properties_Object.md#variable-or-expression) de type entier ou booléen.

- **entier :** si la case est cochée, la variable prend la valeur 1. Lorsqu'elle n'est pas cochée, elle porte la valeur 0. Si la case à cocher a un troisième état (voir ci-dessous), elle porte la valeur 2.
- **booléen :** si la case est cochée, la variable prend la valeur `Vrai`. Lorsqu'elle n'est pas cochée, elle prend la valeur `Faux`.

Une partie ou la totalité des cases à cocher contenues dans un formulaires peut être cochée ou non cochée. Plusieurs cases à cocher permettent à l'utilisateur de cocher plusieurs options.

### Cases à cocher à trois états

Les objets de type case à cocher de style [Classique](checkbox_overview.md#regular) et [A plat](checkbox_overview.md#flat) acceptent un troisième état. Ce troisième état représente un statut intermédiaire, généralement utilisé pour l’affichage. Il permet par exemple d’indiquer qu’une propriété est présente parmi une sélection d’objets mais pas dans chaque objet de la sélection.

![](../assets/en/FormObjects/checkbox_3states.png)

Pour qu’une case à cocher prenne en charge ce troisième état, vous devez lui attribuer la propriété [Trois états](properties_Display.md#three-states) dans la Liste des propriétés, thème “Affichage” .

Cette propriété n’est disponible que pour les cases à cocher classiques et à plat associées à des [variables ou expressions](properties_Object.md#variable-or-expression) numériques — les cases à cocher de représentation des expressions booléennes sont exclues de ce principe (une expression booléenne ne pouvant pas se trouver dans un état intermédiaire).

La variable associée à la case à cocher retourne la valeur 2 lorsque celle-ci se trouve dans le troisième état.
> En saisie, les cases à cocher à trois états affichent séquentiellement chaque état, dans l’ordre suivant : non coché / coché / intermédiaire / non coché, etc. L’état intermédiaire étant généralement inutile en saisie ; il vous suffit, dans le code, de “forcer” la valeur de la variable à 0 lorsqu’elle prend la valeur 2 afin de passer directement de l’état coché à l’état non coché.

## Utiliser une action standard

Vous pouvez affecter une [action standard](properties_Action.md#standard-action) à une case à cocher pour gérer les attributs des zones de texte. Par exemple, si vous sélectionnez l'action standard `fontBold`, à l'exécution la case à cocher permettra de gérer l'attribut "gras" du texte sélectionné dans la zone de texte courante.

Seules les actions qui peuvent représenter un statut vrai/faux (actions "à coche") sont prises en charge par cet objet :

| Actions prises en charge            | Conditions d'utilisation (le cas échéant) |
| ----------------------------------- | ----------------------------------------- |
| avoidPageBreakInsideEnabled         | Zones 4D Write Pro uniquement             |
| fontItalic                          |                                           |
| fontBold                            |                                           |
| fontLinethrough                     |                                           |
| fontSubscript                       | Zones 4D Write Pro uniquement             |
| fontSuperscript                     | Zones 4D Write Pro uniquement             |
| fontUnderline                       |                                           |
| font/showDialog                     | Mac uniquement                            |
| htmlWYSIWIGEnabled                  | Zones 4D Write Pro uniquement             |
| section/differentFirstPage          | Zones 4D Write Pro uniquement             |
| section/differentLeftRightPages     | Zones 4D Write Pro uniquement             |
| spell/autoCorrectionEnabled         |                                           |
| spell/autoDashSubstitutionsEnabled  | Mac uniquement                            |
| spell/autoLanguageEnabled           | Mac uniquement                            |
| spell/autoQuoteSubstitutionsEnabled | Mac uniquement                            |
| spell/autoSubstitutionsEnabled      |                                           |
| spell/enabled                       |                                           |
| spell/grammarEnabled                | Mac uniquement                            |
| spell/showDialog                    | Mac uniquement                            |
| spell/visibleSubstitutions          |                                           |
| visibleBackground                   | Zones 4D Write Pro uniquement             |
| visibleFooters                      | Zones 4D Write Pro uniquement             |
| visibleHeaders                      | Zones 4D Write Pro uniquement             |
| visibleHiddenChars                  | Zones 4D Write Pro uniquement             |
| visibleHorizontalRuler              | Zones 4D Write Pro uniquement             |
| visiblePageFrames                   | Zones 4D Write Pro uniquement             |
| visibleReferences                   |                                           |
| widowAndOrphanControlEnabled        | Zones 4D Write Pro uniquement             |

Pour plus d'informations sur ces actions, veuillez vous reporter à la section [Actions standard](https://doc.4d.com/4Dv17R5/4D/17-R5/Standard-actions.300-4163633.en.html).

## Styles des boutons "Case à cocher"

Les styles de bouton des cases à cocher contrôlent l'apparence générale d'une case à cocher ainsi que ses propriétés. Il est possible d'appliquer différents styles prédéfinis aux cases à cocher. Plusieurs variantes peuvent être obtenues en combinant ces propriétés/comportements.

À l'exception des [propriétés disponibles](#supported-properties), de nombreux objets case à cocher sont *structurellement* identiques. La différence réside dans le traitement de leurs variables associées.

4D propose des cases à cocher avec les styles prédéfinis suivants :

### Classique

Le style Classique de case à cocher correspond à un système de case à cocher standard (*i.e.*, un rectangle avec un titre descriptif) :

![](../assets/en/FormObjects/checkbox_regular.png)

#### Exemple JSON

```
 "myCheckBox": {
  "type": "checkbox",
  "style":"regular",
  "text": "Cancel",
  "action": "Cancel",  
  "left": 60,   
  "top": 160,  
  "width": 100,   
  "height": 20  
  "dataSourceTypeHint":"boolean"
  }
```

### A plat

Le style A plat a un design minimaliste. Le graphisme du style A plat est particulièrement utile pour les formulaires à imprimer.

![](../assets/en/FormObjects/checkbox_flat.png)

#### Exemple JSON

```
 "myCheckBox": {
   "type": "checkbox",
   "style":"flat",
   "text": "Cancel",
   "action": "cancel",
   "left": 60,  
    "top": 160,
    "width": 100,   
   "height": 20   
   }
```

### Toolbar button {#toolbar-button}

Le style du bouton Barre outils est initialement destiné à être intégré dans une barre d'outils.

Le style Barre outils possède un fond transparent et un titre. Il est généralement associé à une [image à 4 états](properties_TextAndPicture.md#number-of-states).

Exemples avec les états coché / non coché / surligné :

![](../assets/en/FormObjects/checkbox_toolbar.png)

#### Exemple JSON

```
 "myCheckBox": {
                "type": "checkbox",
                "style":"toolbar",
                "text": "Checkbox",
    "icon": "/RESOURCES/File.png",
    "iconFrames": 4
                "left": 60,
                "top": 160,
                "width": 100,     
                "height": 20     
                }
```

### Bevel

The Bevel check box style combines the appearance of the [Regular](#regular) (*i.e.*, a rectangle with a descriptive title) style with the [Toolbar](#toolbar-button) style's behavior.

Le style Bevel possède un fond gris clair et un titre. Il est généralement associé à une [image à 4 états](properties_TextAndPicture.md#number-of-states).

Exemples avec les états coché / non coché / surligné :

![](../assets/en/FormObjects/checkbox_bevel.png)

#### Exemple JSON

```
 "myCheckBox": {
                "type": "checkbox",
                "style":"bevel",
                "text": "Checkbox",  
     "icon": "/RESOURCES/File.png",
    "iconFrames": 4
               "left": 60,
                "top": 160,
                "width": 100,    
                "height": 20    
                }
```

### Bevel arrondi

Le style de case à cocher Bevel arrondi est presque identique au style [Bevel](#bevel), à l'exception des coins du bouton qui peuvent, selon le système d'exploitation, être arrondis. As with the Bevel style, the Rounded Bevel style combines the appearance of the [Regular](#regular) style with the [Toolbar](#toolbar-button) style's behavior.

Le style Bevel arrondi possède un fond gris clair et un titre. Il est généralement associé à une [image à 4 états](properties_TextAndPicture.md#number-of-states).

Exemple sous macOS :

  ![](../assets/en/FormObjects/checkbox_roundedbevel_mac.png)

> Sous Windows, le style Bevel arrondi est identique au style [Bevel](#bevel).

#### Exemple JSON

```4d
 "myCheckBox": {
                "type": "checkbox",
                "style":"roundedBevel",  
                "text": "Checkbox",
     "icon": "/RESOURCES/File.png",
    "iconFrames": 4
                "left": 60,
                "top": 160,
                "width": 100,   
                "height": 20   
                }
```

### OS X Gradient

Le style de case à cocher OS X Gradient est presque identique au style [Bevel](#bevel), à l'exception de son apparence qui peut, en fonction du système d'exploitation, avoir deux tons. As with the Bevel style, the OS X Gradient style combines the appearance of the [Regular](#regular) style with the [Toolbar](#toolbar-button) style's behavior.

Le style Gradient OS X a un arrière-plan gris clair et un titre et s'affiche sous la forme d'un bouton système bicolore sur macOS. Il est généralement associé à une [image à 4 états](properties_TextAndPicture.md#number-of-states).

  ![](../assets/en/FormObjects/checkbox_osxgradient_mac.png)

> Sous Windows, ce style est identique au style [Bevel](#bevel).

#### Exemple JSON

```
 "myCheckBox": {
   "type": "checkbox",
   "style":"gradientBevel",
   "text": "Checkbox",
   "icon": "/RESOURCES/File.png",
   "iconFrames": 4
   "left": 60,  
   "top": 160,  
   "width": 100,    
   "height": 20    
           }
```

### OS X Texture

Le style de case à cocher OS X Textured est presque identique au style [Bevel](#bevel), à l'exception de son apparence qui peut, en fonction du système d'exploitation, être différente. As with the Bevel style, the OS X Textured style combines the appearance of the [Regular](#regular) style with the [Toolbar](#toolbar-button) style's behavior.

Par défaut, le style OS X Textured apparaît comme :

- *Windows* - un bouton système standard avec un fond bleu clair et un libellé au centre.

  ![](../assets/en/FormObjects/checkbox_osxtextured.png)

- *Sous macOS* - un bouton système standard affichant un changement de couleur du gris clair au gris foncé. Sa hauteur est prédéfinie : il n'est pas possible de l'agrandir ou de la réduire.

  ![](../assets/en/FormObjects/checkbox_osxtextured_mac.png)

#### Exemple JSON

```
 "myCheckBox": {
   "type": "checkbox",
   "style":"texturedBevel",
   "text": "Checkbox",
   "left": 60,
   "top": 160,
   "width": 100,     
   "height": 20     
   }
```

### Office XP

The Office XP check box style combines the appearance of the [Regular](#regular) style with the [Toolbar](#toolbar-button) style's behavior.

Les couleurs (surbrillance et arrière-plan) d'un bouton au style Office XP sont basées sur les couleurs du système. En fonction du système d'exploitation, le design du bouton peut changer lorsque la souris le survole :

- *Sous Windows* - son arrière-plan n'apparaît que lorsque la souris le survole. Exemples avec les états coché / non coché / surligné :

  ![](../assets/en/FormObjects/checkbox_officexp.png)

- *Sous macOS* - son arrière-plan est toujours affiché. Exemples avec les états cochés / non cochés :

  ![](../assets/en/FormObjects/checkbox_officexp_mac.png)

#### Exemple JSON

```
 "myCheckBox": {
                "type": "checkbox",
                "style":"office",
                "text": "Checkbox",  
                "action": "fontBold",
     "icon": "/RESOURCES/File.png",
    "iconFrames": 4  
               "left": 60,
                "top": 160,  
                "width": 100,   
                "height": 20   
                }
```

### Contracter/Déployer

Ce style de case à cocher peut être utilisé pour ajouter une icône standard contracter/déployer. Ces boutons sont utilisés nativement dans les listes hiérarchiques.

- *Sous Windows* - le bouton est semblable à [+] ou à [-]

  ![](../assets/en/FormObjects/checkbox_collapse.png)

- *Sous macOS* - il ressemble à un triangle pointant sur vers la droite ou vers le bas.

  ![](../assets/en/FormObjects/checkbox_collapse_mac.png)

#### Exemple JSON

```
 "myCheckBox": {
                "type": "checkbox",
                "style":"disclosure",
    "method": "m_collapse",
    "left": 60,
                "top": 160,
                "width": 100,   
                "height": 20   
                }
```

### Bouton disclosure

Sous macOS et Windows, une case à cocher avec le style "Disclosure" apparaît comme un bouton disclosure standard, généralement utilisé pour afficher/masquer des informations supplémentaires. Lorsqu'il est utilisé comme bouton radio, le symbole du bouton pointe vers le bas avec la valeur 0 et vers le haut avec la valeur 1.

- *Windows*

 ![](../assets/en/FormObjects/checkbox_disclosure.png)

- *macOS*

 ![](../assets/en/FormObjects/checkbox_disclosure_mac.png)

#### Exemple JSON

```
 "myCheckBox": {
                "type": "checkbox",  
                "style":"roundedDisclosure",
    "method": "m_disclose",
                "left": 60,  
                "top": 160,
                "width": 100,   
                "height": 20   
                }
```

### Personnalisé

Le style de case à cocher personnalisé accepte une image d'arrière-plan personnalisée et permet de gérer des propriétés spécifiques:

- [Chemin d'accès arrière-plan](properties_TextAndPicture.md#background-pathname)
- [Décalage icône](properties_TextAndPicture.md#icon-offset)
- [Horizontal Margin](properties_TextAndPicture.md#horizontal-margin) and [Vertical Margin](properties_TextAndPicture.md#vertical-margin)

It is usually associated with a [4-state picture](properties_TextAndPicture.md#number-of-states), that can be used in conjunction with a [4-state](properties_TextAndPicture.md#number-of-states) [background picture](properties_TextAndPicture.md#background-pathname).

#### Exemple JSON

```
 "myCheckbox": {
  "type": "checkbox",
  "style":"custom",
  "text": "OK",
  "icon": "/RESOURCES/smiley.jpg",
  "iconFrame": 4,
  "customBackgroundPicture": "/RESOURCES/paper.jpg",
  "iconOffset": 5, //custom icon offset when clicked
  "left": 60,
  "top": 160,
  "width": 100,  
  "height": 20,
  "customBorderX": 20,
  "customBorderY": 5
  }
```

## Propriétés prises en charge

Toutes les cases à cocher partagent une même série de propriétés de base :

[Gras](properties_Text.md#bold) - [Bas](properties_CoordinatesAndSizing.md#bottom) - [Style de bouton](properties_TextAndPicture.md#button-style) - [Class](properties_Object.md#css-class) - [Focusable](properties_Entry.md#focusable) - [Police](properties_Text.md#font) - [Couleur de la police](properties_Text.md#font-color) - [Taille de la police](properties_Text.md#font-size) - [Hauteur](properties_CoordinatesAndSizing.md#height) - [Message d'aide](properties_Help.md#help-tip) - [Dim. horizontal](properties_ResizingOptions.md#horizontal-sizing) - [Italique](properties_Text.md#italic) - [Gauche](properties_CoordinatesAndSizing.md#left) - [Nom](properties_Object.md#object-name) - [Droite](properties_CoordinatesAndSizing.md#right) - [Raccourci](properties_Entry.md#shortcut) - [Action standard](properties_Action.md#standard-action) - [Titre](properties_Object.md#title) - [Haut](properties_CoordinatesAndSizing.md#top) - [Type](properties_Object.md#type) - [Souligné](properties_Text.md#underline) - [Variable ou expression](properties_Object.md#variable-or-expression) - [Dim. vertical](properties_ResizingOptions.md#vertical-sizing) - [Visibilité](properties_Display.md#visibility) - [Largeur](properties_CoordinatesAndSizing.md#width)

Additional specific properties are available, depending on the [button style](#check-box-button-styles):

- [Background pathname](properties_TextAndPicture.md#background-pathname) - [Horizontal Margin](properties_TextAndPicture.md#horizontal-margin) - [Icon Offset](properties_TextAndPicture.md#icon-offset) - [Vertical Margin](properties_TextAndPicture.md#vertical-margin) (Custom)
- [Trois états](properties_Display.md#three-states) (A plat, Classique)
- [Number of States](properties_TextAndPicture.md#number-of-states) - [Picture pathname](properties_TextAndPicture.md#picture-pathname) - [Title/Picture Position](properties_TextAndPicture.md#titlepicture-position) (Toolbar button, Bevel, Rounded Bevel, OS X Gradient, OS X Textured, Office XP, Custom)
