---
id: pluginAreaOverview
title: Zones de plug-in
---

## Vue d’ensemble

Une zone de plug-in est une zone du formulaire contrôlée par un plug-in. La capacité d’intégrer des plug-ins dans les formulaires permet d’accéder à des possibilités illimitées lorsque vous créez des applications personnalisées. Une zone de plug-in peut réaliser une tâche simple comme l’affichage d’une horloge numérique dans un formulaire, ou plus complexe comme proposer un environnement de traitement de textes, un tableur ou un éditeur graphique.

Lorsque vous ouvrez une base de données, 4D crée une liste interne des plug-ins [installés dans la base](#installing-plug-ins). Une fois que vous avez inséré une Zone de plug-in dans un formulaire, vous pouvez sélectionner le plug-in à lui affecter via la liste "Type" dans la fenêtre de propriétés de l’objet :

![](../assets/en/FormObjects/pluginArea.png)

> Certains plug-ins, comme 4D Internet Commands, ne peuvent pas être utilisés dans des formulaires ou des fenêtres externes. Dans ce cas, ils n’apparaissent pas dans la liste de propriétés.

Si vous dessinez une zone de plug-in trop petite, 4D l’affiche sous forme de bouton dont le libellé est le nom de la variable associée à la zone. En exécution, l’utilisateur peut cliquer sur ce bouton afin d’ouvrir une fenêtre spécifique affichant le plug-in.

### Propriétés avancées

Si les options avancées sont fournies par l'auteur du plug-in, un thème **Plug-in** contenant un bouton [**Propriétés avancées**](properties_Plugins.md) peut être activé dans la liste des propriétés. Dans ce cas, vous pouvez cliquer sur ce bouton pour définir ces options, généralement via une boîte de dialogue personnalisée.

## Installer un plug-in

Pour ajouter un plug-in dans votre environnement 4D, vous devez dans un premier temps quitter votre application 4D. Le chargement des plug-ins s’effectue au lancement de l’application 4D. Pour plus d’informations sur l’installation d’un plug-in, reportez-vous à la section [Installer des plugins ou des composants](https://doc.4d.com/4Dv17R6/4D/17-R6/Installing-plugins-or-components.300-4354866.en.html).

## Créer des plug-ins

Si vous souhaitez concevoir vos propres plug-ins, vous pouvez obtenir des informations détaillées sur l'écriture et la création de plug-ins. 4D fournit un [kit complet (sur github)](https://github.com/4d/4D-Plugin-SDK) pour vous aider à écrire des plug-ins personnalisés.

## Propriétés prises en charge

[Border Line Style](properties_BackgroundAndBorder.md#border-line-style) - [Bottom](properties_CoordinatesAndSizing.md#bottom) - [Advanced Properties](properties_Plugins.md) - [Class](properties_Object.md#css-class) - [Draggable](properties_Action.md#draggable) - [Droppable](properties_Action.md#droppable) - [Expression Type](properties_Object.md#expression-type) - [Focusable](properties_Entry.md#focusable) - [Height](properties_CoordinatesAndSizing.md#height) - [Horizontal Sizing](properties_ResizingOptions.md#horizontal-sizing) - [Left](properties_CoordinatesAndSizing.md#left) - [Method](properties_Action.md#method) - [Object Name](properties_Object.md#object-name) - [Plug-in Kind](properties_Object.md#plug-in-kind) - [Right](properties_CoordinatesAndSizing.md#right) - [Top](properties_CoordinatesAndSizing.md#top) - [Type](properties_Object.md#type) - [Variable or Expression](properties_Object.md#variable-or-expression) - [Vertical Sizing](properties_ResizingOptions.md#vertical-sizing) - [Visibilty](properties_Display.md#visibility) - [Width](properties_CoordinatesAndSizing.md#width)
