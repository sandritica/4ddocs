---
id: forms
title: Formulaires
---


Les formulaires fournissent l'interface par laquelle les informations sont saisies, modifiées et imprimées dans une application de bureau. A l'aide des formulaires, les utilisateurs peuvent interagir avec les données d'une base de données et imprimer des rapports. Les formulaires permettent de créer des boîtes de dialogue personnalisées, des palettes ou toute fenêtre personnalisée.

![](../assets/en/FormObjects/form1.png)

Les formulaires peuvent également contenir d'autres formulaires grâce aux fonctionnalités suivantes :

- [les objets sous-formulaires](FormObjects/subform_overview.md)
- [les formulaires hérités](./properties_FormProperties.md#inherited-form-name)

## Création de formulaires

Vous pouvez ajouter ou modifier des formulaires 4D à l'aide des éléments suivants :

- **L'interface 4D Developer :** Créez de nouveaux formulaires à partir du menu **Fichier** ou de la fenêtre de l' **Explorateur**.
- **L'éditeur de formulaires **: Modifiez vos formulaires à l'aide de l'</strong>[éditeur de formulaires](FormEditor/formEditor.md)</strong>.
- **Le code JSON :** Créez et concevez vos formulaires à l'aide de JSON et enregistrez les fichiers de formulaire à [l'emplacement approprié](Project/architecture#sources). Voici un exemple :

```
{
    "windowTitle": "Hello World",
    "windowMinWidth": 220,
    "windowMinHeight": 80,
    "method": "HWexample",
    "pages": [
        null,
        {
            "objects": {
                "text": {
                "type": "text",
                "text": "Hello World!",
                "textAlign": "center",
                "left": 50,
                "top": 120,
                "width": 120,
                "height": 80
                },
                "image": {
                "type": "picture",
                "pictureFormat": "scaled",
                "picture": "/RESOURCES/Images/HW.png",
                "alignment":"center", 
                "left": 70,
                "top": 20, 
                "width":75, 
                "height":75        
                },
                "button": {
                "type": "button",
                "text": "OK",
                "action": "Cancel",
                "left": 60,
                "top": 160,


                "width": 100,
                "height": 20
                }
            }
        }
    ]
}
```

## Formulaire projet et formulaire table

Il existe deux catégories de formulaires :

- **Les formulaires projet** - Formulaires indépendants qui ne sont rattachés à aucune table. Ils sont destinés plus particulièrement à la création de boîtes de dialogue d'interface et de composants. Les formulaires projet peuvent être utilisés pour créer des interfaces facilement conformes aux normes du système d'exploitation.

- **Les formulaires table** - Rattachés à des tables spécifiques et bénéficient ainsi de fonctions automatiques utiles pour développer des applications basées sur des bases de données. En règle générale, une table possède des formulaires d'entrée et de sortie séparés.

En règle générale, vous sélectionnez la catégorie de formulaire lorsque vous créez le formulaire, mais vous pouvez la modifier par la suite.

## Pages formulaire

Chaque formulaire est composé d'au moins deux pages :

- une page 1 : une page principale, affichée par défaut
- une page 0 : une page de fond, dont le contenu est affiché sur une page sur deux.

Vous pouvez créer plusieurs pages pour un formulaire d'entrée. Si le nombre de champs ou de variables est supérieur au nombre maximal supporté sur un écran, vous pouvez créer des pages supplémentaires pour les afficher. Plusieurs pages vous permettent d'effectuer les opérations suivantes :

- Placez les informations les plus importantes sur la première page et les informations les moins importantes sur les autres pages.
- Organisez chaque sujet sur sa propre page.
- Réduire ou éliminer le défilement pendant la saisie des données en définissant [l'ordre de saisie](formEditor.md#data-entry-order).
- Prévoyez de l'espace autour des éléments du formulaire pour un design d'écran attrayant.

Les pages multiples sont utiles uniquement pour les formulaires d'entrée. Elles ne sont pas destinées à être imprimées. Lorsqu'un formulaire de plusieurs pages est imprimé, seule la première page est imprimée.

Il n'y a aucune restriction sur le nombre de pages qu'un formulaire peut contenir. Le même champ peut apparaître en un nombre de fois illimité dans un formulaire et sur autant de pages que vous le souhaitez. Toutefois, plus vous aurez de pages dans un formulaire, plus il sera long à afficher.

Un formulaire multi-pages contient à la fois une page d'arrière-plan et plusieurs pages d'affichage. Les objets placés sur la page d'arrière-plan peuvent être visibles sur toutes les pages d'affichage, mais il ne peuvent être sélectionnés et modifiés que sur la page d'arrière-plan. Dans les formulaires multi-pages, vous devez placer votre palette de boutons sur la page d'arrière-plan. Vous devez également inclure un ou plusieurs objets sur la page d'arrière-plan qui fournissent à l'utilisateur des outils de navigation de page.

## Formulaires hérités

Les formulaires 4D peuvent utiliser et être utilisés comme «formulaires hérités», ce qui signifie que tous les objets du *Formulaire A* peuvent être utilisés dans le *Formulaire B*. Dans ce cas, *Formulaire B* "hérite" des objets du *Formulaire A*.

Les références à un formulaire hérité est toujours active : si un élément d'un formulaire hérité est modifié (par exemple le style des boutons), tous les formulaires qui l’utilisent seront automatiquement modifiés.

Tous les formulaires (formulaires table et formulaires projet) peuvent être désignés comme un formulaire hérité. Cependant, les éléments qu'ils contiennent doivent être compatibles avec une utilisation dans différentes tables de base de données.

A l’exécution du formulaire, les objets sont chargés et combinés dans l’ordre suivant :

1. Page zéro du formulaire hérité
2. Page 1 du formulaire hérité
3. Page zéro du formulaire ouvert
4. Page courante du formulaire ouvert.

Cet ordre détermine [l'ordre de saisie](formEditor.md#data-entry-order) par défaut des objets dans le formulaire.

> Seules les pages 0 et 1 du formulaire hérité peuvent apparaître dans les autres formulaires.

Les propriétés ainsi que la méthode d’un formulaire ne sont pas prises en compte lorsque celui-ci est utilisé comme formulaire hérité. En revanche, les méthodes des objets qu’il contient sont appelées.

Pour définir un formulaire hérité, les propriétés de [Inherited Form Name](properties_FormProperties.md#inherited-form-name) et [Inherited Form Table](properties_FormProperties.md#inherited-form-table) (pour les formulaires table) doivent être définies dans le formulaire qui héritera de quelque chose issue d'un autre formulaire.

Un formulaire peut hériter d'un formulaire projet, en définissant la propriété [Inherited Form Table](properties_FormProperties.md#inherited-form-table) sur `\&#060;None&#062;` dans la liste des propriétés (ou " " dans JSON).

Pour stopper l’héritage d’un formulaire, choisissez l’option **\<None>** dans la Liste des propriétés (ou " " dans JSON) pour la propriété [Inherited Form Name](properties_FormProperties.md#inherited-form-name).
> Il est possible de définir un formulaire hérité dans un formulaire qui servira à son tour de formulaire hérité pour un troisième formulaire. La combinaison des objets s’effectue alors de manière récursive. 4D détecte les boucles récursives (par exemple si le formulaire [table1]form1 est défini comme formulaire hérité de [table1]form1, c’est-à-dire de lui-même) et interrompt le chaînage des formulaires.

## Propriétés prises en charge

[Associated Menu Bar](properties_Menu.md#associated-menu-bar) - [Fixed Height](properties_WindowSize.md#fixed-height) - [Fixed Width](properties_WindowSize.md#fixed-width) - [Form Break](properties_Markers.md#form-break) - [Form Detail](properties_Markers.md#form-detail) - [Form Footer](properties_Markers.md#form-footer) - [Form Header](properties_Markers.md#form-header) - [Form Name](properties_FormProperties.md#form-name) - [Form Type](properties_FormProperties.md#form-type) - [Inherited Form Name](properties_FormProperties.md#inherited-form-name) - [Inherited Form Table](properties_FormProperties.md#inherited-form-table) - [Maximum Height](properties_WindowSize.md#maximum-height-minimum-height) - [Maximum Width](properties_WindowSize.md#maximum-width-minimum-width) - [Method](properties_Action.md#method) - [Minimum Height](properties_WindowSize.md#maximum-height-minimum-height) - [Minimum Width](properties_WindowSize.md#maximum-width-minimum-width) - [Pages](properties_FormProperties.md#pages) - [Print Settings](properties_Print.md#settings) - [Published as Subform](properties_FormProperties.md#published-as-subform) - [Save Geometry](properties_FormProperties.md#save-geometry) - [Window Title](properties_FormProperties.md#window-title)
