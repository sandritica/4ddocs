---
id: set-database-parameter
title: SET DATABASE PARAMETER
slug: /commands/set-database-parameter
displayed_sidebar: docs
---

<!--REF #_command_.SET DATABASE PARAMETER.Syntax-->**SET DATABASE PARAMETER** ( {*laTable* ;} *sélecteur* ; *valeur* )<!-- END REF-->
<!--REF #_command_.SET DATABASE PARAMETER.Params-->
| Paramètre | Type |  | Description |
| --- | --- | --- | --- |
| laTable | Table | &#8594;  | Table à paramétrer ou Table par défaut si ce paramètre est omis |
| sélecteur | Integer | &#8594;  | Code du paramètre de la base à modifier |
| valeur | Real, Text | &#8594;  | Valeur du paramètre |

<!-- END REF-->

## Description 

<!--REF #_command_.SET DATABASE PARAMETER.Summary-->La commande **SET DATABASE PARAMETER** permet de modifier divers paramètres internes de la base de données 4D.<!-- END REF-->

*sélecteur* désigne le paramètre à modifier. 4D vous propose des constantes prédéfinies, placées dans le thème *Paramètres de la base*. Le tableau suivant décrit chaque constante et indique sa portée et sa persistance entre deux sessions :

### 4D Server timeout (13)

**Portée** : Application 4D si *valeur* positive

**Conservé entre deux sessions** : Oui si *valeur* positive

**Valeurs possibles** : 0 -> 32 767

**Description** : Valeur du délai avant déconnexion (timeout) accordé par 4D Server aux postes clients. 

Par défaut, cette valeur est définie dans la page “Client-Serveur/Options réseau” des Propriétés de la base, sur le poste serveur. 

Le timeout serveur définit la période maximale de non-réponse du client "autorisée", par exemple s'il effectue une opération bloquante. A l'issue de cette période, 4D Server déconnecte le client. Le sélecteur 4D Server timeout vous permet de fixer un nouveau timeout, exprimé en minutes. Cette possibilité permet en particulier d’augmenter la valeur du timeout avant l’exécution sur le poste client d’une opération bloquante de longue durée, risquant d’entraîner une déconnexion ; par exemple, l’impression d’un grand nombre de pages. 

Vous disposez en outre de deux possibilités :

effectuer une modification globale et permanente : la nouvelle valeur s’applique à tous les process et est stockée dans les préférences de l’application (équivaut à une modification de la valeur dans la boîte de dialogue des Préférences). Pour cela, passez une valeur **positive** dans le paramètre *valeur*.effectuer une modification restreinte et temporaire : la nouvelle valeur ne s’applique qu’au process appelant (les autres process conservant la valeur d’origine), et est abandonnée dès que le serveur reçoit un signe d’activité du poste client — par exemple, dès que l’opération est terminée. Cette possibilité est utile pour gérer les opérations longues initiées par des plug-ins. Pour cela, passez une valeur **négative** dans le paramètre *valeur*. Pour définir une connexion “Ouverte en permanence”, passez 0 dans *valeur*. Reportez-vous à l’exemple 1.



### 4D Remote mode timeout (14)

**Portée** (ancienne couche réseau uniquement) : Application 4D si *valeur* positive 

**Conservé entre deux sessions** : Oui si *valeur* positive

**Description** : A utiliser dans des cas très spécifiques. Valeur du délai avant déconnexion (timeout) accordé par le poste 4D distant au poste 4D Server. Par défaut, cette valeur est définie dans la page “Client-Serveur/Options réseau” des Propriétés de la base, sur le poste distant. 

Le sélecteur 4D Remote mode timeout n'est pris en compte que si vous utilisez l'ancienne couche réseau. Avec la couche *ServerNet* activée, il est ignoré : ce paramétrage est entièrement géré par le sélecteur 4D Server timeout (13).



### Port ID (15)

**Portée** : 4D local, 4D Server

**Conservé entre deux sessions** : Non

**Description** : Numéro du port TCP utilisé par le serveur Web 4D avec 4D en mode local et 4D Server. Par défaut, la valeur est 80\. 

Le numéro de port TCP est défini dans la page “Web/Configuration” de la boîte de dialogue des Propriétés de la base. Vous pouvez utiliser les constantes du thème *Numéros de port TCP* pour le paramètre *valeur*. 

Le sélecteur Port ID est utile dans le cadre de serveurs Web 4D compilés et fusionnés avec 4D Desktop (pas d’accès au mode Développement). Pour plus d’informations sur le numéro de port TCP, reportez-vous à la section *Paramétrages du serveur Web*.



### Character set (17)

**Portée** : 4D local, 4D Server

**Conservé entre deux sessions** : Oui

**Description** : *Constante obsolète (conservée par compatibilité uniquement).* Il est désormais conseillé d'utiliser les commandes [WEB SET OPTION](web-set-option.md) et [WEB GET OPTION](web-get-option.md) pour le paramétrage du serveur HTTP.



### Max concurrent Web processes (18)

**Portée** : 4D local, 4D Server

**Conservé entre deux sessions** : Oui

**Description** : *Constante obsolète (conservée par compatibilité uniquement).* Il est désormais conseillé d'utiliser les commandes [WEB SET OPTION](web-set-option.md) et [WEB GET OPTION](web-get-option.md) pour le paramétrage du serveur HTTP.



### Client port ID (22)

**Portée** : Tous postes 4D distants

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : Voir sélecteur 15

**Description** : Permet de spécifier ce paramètre pour les postes 4D distants utilisés en tant que serveurs Web. La valeur définie via ce sélecteur est appliquée à tous les postes distants utilisés comme serveurs Web. Si vous souhaitez définir cette valeur pour certains postes distants uniquement, utilisez la boîte de dialogue des Préférences de 4D en mode distant.



### Client character set (24)

**Portée** : Tous postes 4D distants

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : Voir sélecteur 17

**Description** : Permet de spécifier ce paramètre pour les postes 4D distants utilisés en tant que serveurs Web. La valeur définie via ce sélecteur est appliquée à tous les postes distants utilisés comme serveurs Web. Si vous souhaitez définir cette valeur pour certains postes distants uniquement, utilisez la boîte de dialogue des Préférences de 4D en mode distant.



### Client max concurrent Web proc (25)

**Portée** : Tous postes 4D distants

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : Voir sélecteur 18

**Description** : Permet de spécifier ce paramètre pour les postes 4D distants utilisés en tant que serveurs Web. La valeur définie via ce sélecteur est appliquée à tous les postes distants utilisés comme serveurs Web. Si vous souhaitez définir cette valeur pour certains postes distants uniquement, utilisez la boîte de dialogue des Préférences de 4D en mode distant.



### Maximum Web requests size (27)

**Portée** : 4D local, 4D Server

 **Conservé** **entre deux sessions** : Oui

 **Description** : *Constante obsolète (conservée par compatibilité uniquement).* Il est désormais conseillé d'utiliser les commandes [WEB SET OPTION](web-set-option.md) et [WEB GET OPTION](web-get-option.md) pour le paramétrage du serveur HTTP.



### 4D Server log recording (28)

**Thread-safe** : Yes

**Portée** : 

 **Conservé** **entre deux sessions** : Non

**Valeurs possibles** : 0 ou de 1 à N (0 = ne pas enregistrer, 1 à N = numéro séquentiel, accolé au nom du fichier).

**Description** : Démarrage ou arrêt de l’enregistrement des requêtes standard reçues par 4D Server (hors requêtes Web). Par défaut, la valeur est 0 (pas d’enregistrement de requêtes). 

4D Server vous permet d’enregistrer dans un fichier d’historique chaque requête reçue par le poste serveur. Lorsque ce mécanisme est activé, deux fichiers sont créés dans le dossier Logs de la base. Sur le serveur, ils sont nommés *4DRequestsLogServer\_N.txt* et *4DRequestsLog\_ProcessInfoServer\_N.txt*. Sur le remote, ils sont nommés *4DRequestsLog\_N.txt* et *4DRequestsLog\_ProcessInfo\_N.txt*, où N est le numéro séquentiel de l'historique. Une fois qu'un fichier atteint une taille de 10 Mo, il est refermé et un nouveau fichier est généré, avec un numéro séquentiel incrémenté. Si un fichier du même nom existe déjà, il est directement remplacé. Vous pouvez définir le numéro de départ de la séquence à l'aide du paramètre *valeur*. Ces fichiers texte stockent dans un format tabulé simple diverses informations concernant chaque requête : heure, numéro de process, taille de la requête, durée de traitement, etc. Pour plus d'informations sur les fichiers texte 4DRequestsLog, veuillez vous reporter à la section *Description des fichiers d'historique*.



### Client Web log recording (30)

**Portée** :Tous postes 4D distants

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : 0 = Ne pas enregistrer (défaut), 1 = Enregistrer au format CLF, 2 = Enregistrer au format DLF, 3 = Enregistrer au format ELF, 4 = Enregistrer au format WLF.

**Description** : Démarrage ou arrêt de l’enregistrement des requêtes Web reçues par les serveurs Web de tous les postes clients. Par défaut, la valeur est 0 (pas d’enregistrement des requêtes). 

Le fonctionnement de ce sélecteur est identique à celui du sélecteur 29 ; il s’applique toutefois à tous les postes 4D clients utilisés en tant que serveurs Web. Le fichier “logweb.txt” est dans ce cas automatiquement placé dans le sous-dossier Logs du dossier base 4D client (dossier de cache). Si vous souhaitez définir des valeurs pour certains postes clients uniquement, utilisez la boîte de dialogue des Préférences de 4D en mode distant.



### Table sequence number (31)

**Portée** :Application 4D

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : Toute valeur de type entier long.

**Description** : Ce sélecteur permet de modifier ou de lire le numéro unique courant des enregistrements de la table passée en paramètre. “Numéro courant” signifie “dernier numéro utilisé” : si vous modifiez cette valeur à l’aide de [SET DATABASE PARAMETER](set-database-parameter.md), le prochain enregistrement sera créé avec comme numéro la valeur passée + 1\. Ce nouveau numéro est, lui, retourné par la commande [Sequence number](sequence-number.md) ainsi que dans tout champ de la table auquel la propriété "Incrémentation auto" a été affectée en Structure ou via le SQL. 

Par défaut, le numéro unique est défini par 4D et correspond à l’ordre de création des enregistrements. 

Pour des informations supplémentaires, reportez-vous à la documentation de la commande [Sequence number](sequence-number.md).



### Debug log recording (34)

**Thread-safe** : Yes

**Portée** : Application 4D

**Conservé** **entre deux sessions** : Non

**Description** : Démarrage ou arrêt de l’enregistrement séquentiel des événements de programmation de 4D dans le fichier *4DDebugLogServer* *\[\_pN\_n\].txt* (où \_n est le numéro de segment du fichier).

Deux modes sont possibles :

- Le mode standard propose une vue basique des événements et le fichier est automatiquement placé dans le sous-dossier Logs de la base, à côté du fichier de structure. Les durées d'exécution sont exprimées en millisecondes avec la valeur "< ms" qui s'affiche lorsqu'une opération dure moins d'une milliseconde.

- Le mode tabulé fournit des informations supplémentaires et utilise un format tabulé plus compact dans le fichier. Les durées d'exécution sont exprimées en millisecondes. **Valeurs possibles** : Entier long contenant un champ de bits (bit field) : valeur = bit1(1)+bit2(2)+bit3(4)+bit4(8)+…). 

- Le bit 0 (valeur 1) permet de demander à activer le fichier (à noter que toute autre valeur non nulle l’activera également)

- Le bit 1 (valeur 2) permet de demander les paramètres d’appel aux commandes et (mode interprété uniquement) aux méthodes.

- Le bit 2 (valeur 4) permet d’activer le format tabulé.

- Le bit 3 (valeur 8) permet de désactiver l’écriture immédiate de chaque opération sur disque (activée par défaut). L’écriture immédiate est moins rapide mais plus efficace par exemple pour rechercher les causes d’un plantage. Si vous désactivez ce mode, le fichier sera généré plus rapidement.

- Le bit 4 (valeur 16) permet de désactiver l’enregistrement des appels de plug-ins (activé par défaut).

- Le bit 5 (valeur 32) permet de désactiver l'enregistrement des fonctions membres.

Exemples :

FIXER PARAMETRE BASE(34;1) // active le mode standard sans les paramètres, avec les durées

FIXER PARAMETRE BASE(34;2) // active le mode standard avec les paramètres et les durées

FIXER PARAMETRE BASE(34;2+4) // active le mode tabulé avec les paramètres et les durées

FIXER PARAMETRE BASE(34;0) // désactive le fichier

Dans tout type d'application 4D (4D tous modes, 4D Server, 4D Volume Desktop), en interprété ou en compilé, vous pouvez éviter que le fichier n’enregistre une trop grande quantité d’informations :

- en restreignant les commandes 4D examinées à l'aide de Log command list (sélecteur 80), ou

- en le restreignant au process courant uniquement à l'aide de Current process debug log recording (sélecteur 111). Cela ajoutera la lettre "p" et le numéro de process au nom du fichier : *4DDebugLog* *\[\_pN\_n\].txt ou* *4DDebugLogServer\[\_pn\_n\].txt.* Pour plus d’informations sur le format et l’exploitation du fichier 4DDebugLog, veuillez consulter la *Description des fichiers d'historique* dans le Manuel Développement.

**Note :** Ce sélecteur est proposé uniquement à des fins de débogage et doit être utilisé avec précaution car il peut entraîner une dégradation des performances de l'application.



### Client Server port ID (35)

**Portée** :Base de données 

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : 0 à 65535

**Description** : Numéro de port TCP sur lequel 4D Server publie la base de données (à destination des postes 4D distants). Par défaut, la valeur est 19813\. 

La personnalisation de cette valeur permet d’utiliser plusieurs applications 4D client-serveur sur la même machine avec le protocole TCP ; dans ce cas, vous devez spécifier un numéro de port différent pour chaque application. 

La valeur est stockée dans le fichier de structure de la base. Elle peut être définie avec 4D en mode local mais n’est prise en compte qu’en configuration client-serveur. 

Lorsque vous modifiez cette valeur, il est nécessaire de redémarrer le poste serveur afin que la nouvelle valeur soit prise en compte.



### HTTPS Port ID (39)

**Portée** :4D local, 4D Server

 **Conservé** **entre deux sessions** : Oui

 **Description** : *Constante obsolète (conservée par compatibilité uniquement).* Il est désormais conseillé d'utiliser les commandes [WEB SET OPTION](web-set-option.md) et [WEB GET OPTION](web-get-option.md) pour le paramétrage du serveur HTTP.



### Client HTTPS port ID (40)

**Portée** :Tous postes 4D distants

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : 0 à 65535

**Description** : Numéro du port TCP utilisé par les serveurs Web des postes clients pour les connexions sécurisées via SSL (protocole HTTPS). Par défaut, la valeur est 443 (valeur standard).

Le fonctionnement de ce sélecteur est identique à celui du sélecteur 39 ; il s’applique toutefois à tous les postes 4D distants utilisés en tant que serveurs Web. Si vous souhaitez modifier la valeur de certains postes clients uniquement, utilisez la boîte de dialogue des Préférences de 4D distant.



### SQL Autocommit (43)

**Portée** :Base de données

 **Conservé** **entre deux sessions** : Oui

 **Valeurs possibles** : 0 (désactivation) ou 1 (activation)

**Description** : Activation ou désactivation du mode SQL auto-commit. Par défaut, la valeur est 0 (mode désactivé)

Le mode auto-commit permet de renforcer l'intégrité référentielle de la base. Lorsque ce mode est actif, les requêtes *SELECT*, *INSERT*, *UPDATE*, *DELETE* (SIUD) sont automatiquement incluses dans des transactions lorsqu'elles sont exécutées en-dehors de toute transaction. Ce mode peut également être défini dans les préférences de la base.



### SQL Engine case sensitivity (44)

**Portée** : Base de données

**Conservé** **entre deux sessions** : Oui

**Valeurs possibles** : 0 (casse non prise en compte) ou 1 (casse prise en compte)

**Description** : Activation ou désactivation de la prise en compte de la casse des caractères pour les comparaisons de chaînes effectuées par le moteur SQL. 

Par défaut, la valeur est 1 (casse prise en compte) : le moteur SQL établit une différence entre les majuscules et les minuscules ainsi qu'entre les caractères accentués lors des comparaisons de chaînes (tris et recherches). Par exemple "ABC" = "ABC" mais "ABC" # "Abc" et "abc" # "âbc" . Dans certains cas, par exemple pour aligner le fonctionnement du moteur SQL sur celui du moteur 4D, vous pourrez souhaiter que les comparaisons de chaînes ne tiennent pas compte de la casse ("ABC"="Abc"="âbc").

**Attention :** *Étant donné que cette option modifie le fichier de structure de la base de données et tous les process, il est fortement recommandé,* *pour des raisons de performances,* *de la définir uniquement au démarrage de la base de données.* Cette option peut également être définie dans la [CALL SUBFORM CONTAINER](call-subform-container.md) des Propriétés de la base.



### Client log recording (45)

**Portée** : Poste 4D distant 

**Conservé** **entre deux sessions** : Non

**Valeurs possibles** : 0 ou de 1 à N (0 = ne pas enregistrer, 1 à N = numéro séquentiel, accolé au nom du fichier). 

**Description** : Démarrage ou arrêt de l'enregistrement des requêtes standard effectuées par le poste client 4D ayant exécuté la commande (hors requêtes Web). Par défaut, la valeur est 0 (pas d'enregistrement des requêtes). 

4D vous permet d'enregistrer l’historique des requêtes effectuées par le poste client. Lorsque ce mécanisme est activé, deux fichiers sont créés sur le poste client, dans le sous-dossier Logs du dossier local de la base. Il sont nommés 4DRequestsLog\_N.txt et 4DRequestsLog\_ProcessInfo\_N.txt où N est le numéro séquentiel de l'historique. Une fois que le fichier 4DRequestsLog atteint une taille de 10 Mo, il est refermé et un nouveau fichier est généré, avec un numéro séquentiel incrémenté. Si un fichier du même nom existe déjà, il est directement remplacé. Vous pouvez définir le numéro de départ de la séquence à l'aide du paramètre valeur.

Ces fichiers texte stockent dans un format tabulé simple diverses informations concernant chaque requête : heure, numéro de process, taille de la requête, durée de traitement, etc. Ces informations sont particulièrement utiles en phase de mise au point de l'application ou à des fins statistiques. Cf. *Description des fichiers d'historique*.



### Query by formula on server (46)

**Portée** :Table et process courants

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : 0 (utiliser le paramétrage de la base), 1 (exécuter sur le client) ou 2 (exécuter sur le serveur)

**Description** : Emplacement de l’exécution des commandes [QUERY BY FORMULA](query-by-formula.md) et [QUERY SELECTION BY FORMULA](query-selection-by-formula.md) pour la *table* passée en paramètre. 

Dans le cadre de l’exploitation d’une base en client-serveur, les commandes de recherche "par formule" peuvent exécutées soit sur le serveur soit sur le client :

dans les bases de données créées à partir de 4D v11 SQL, ces commandes sont exécutées sur le serveur. dans les bases de données converties, ces commandes sont exécutées sur le client, comme dans les versions précédentes de 4D.dans les bases de données converties, une préférence spécifique permet de modifier globalement le lieu d’exécution de ces commandes.Cette différence de lieu d’exécution influe sur les performances de l’application (l’exécution sur le serveur est généralement plus rapide) mais également sur la programmation. En effet, la valeur des composantes de la formule (notamment les variables appelées via une méthode) diffère suivant le contexte d’exécution. Vous pouvez utiliser ce sélecteur pour adapter ponctuellement le fonctionnement de votre application. 

Si vous passez 0 dans le paramètre *valeur*, l’emplacement d’exécution des commandes de recherche "par formule" dépendra de la configuration de la base : dans les bases créées avec 4D v11 SQL, les commandes seront exécutées sur le serveur. Dans les bases converties, elles seront exécutées sur le client ou le serveur en fonction des préférences de la base. Passez 1 ou 2 dans *valeur* pour "forcer" l’exécution des commandes respectivement sur le client ou sur le serveur. 

Reportez-vous à l'exemple 2.

**Note :** Si vous souhaitez pouvoir activer les jointures "type SQL" (cf. sélecteur Query by formula joins), vous devez toujours exécuter les formules sur le serveur afin qu'elle ait accès aux enregistrements. Attention, dans ce contexte, la formule ne doit pas contenir d'appel à une méthode, sinon elle est automatiquement basculée sur le poste distant.



### Order by formula on server (47)

**Portée** :Table et process courants

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : 0 (utiliser le paramétrage de la base), 1 (exécuter sur le client) ou 2 (exécuter sur le serveur)

**Description** : Emplacement de l’exécution de la commande [ORDER BY FORMULA](order-by-formula.md) pour la table passée en paramètre. 

Dans le cadre de l’exploitation d’une base en client-serveur, la commande [ORDER BY FORMULA](order-by-formula.md) peut être exécutée soit sur le serveur soit sur le client. Ce sélecteur permet de définir l’emplacement de l’exécution de cette commande (serveur ou client). Ce mode peut également être défini dans les préférences de la base. Pour plus d’informations, reportez-vous à la description du sélecteur 46, Query by formula on server.

**Note :** Si vous souhaitez pouvoir activer les jointures "type SQL" (cf. sélecteur Query by formula joins), vous devez toujours exécuter les formules sur le serveur afin qu'elle ait accès aux enregistrements. Attention, dans ce contexte, la formule ne doit pas contenir d'appel à une méthode, sinon elle est automatiquement basculée sur le poste distant.



### Auto synchro resources folder (48)

**Portée** :Poste 4D distant

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : 0 (pas de synchronisation), 1 (synchronisation auto) ou 2 (demander).

**Description** :  Mode de synchronisation dynamique du dossier *Resources* du poste client 4D ayant exécuté la commande avec celui du serveur. 

Lorsque le contenu du dossier *Resources* sur le serveur a été modifié ou qu’une demande de synchronisation a été émise (via l’explorateur de ressources ou suite à l'exécution de la commande [NOTIFY RESOURCES FOLDER MODIFICATION](notify-resources-folder-modification.md)), le serveur notifie les clients connectés. 

Trois modes de synchronisation sont alors possibles côté client. Le sélecteur Auto synchro resources folder vous permet de définir le mode à utiliser pour le poste client et la session courante :

0 (valeur par défaut) : pas de synchronisation dynamique (la demande de synchronisation est ignorée) 1 : synchronisation dynamique automatique2 : affichage d’une boîte de dialogue sur les postes clients, avec possibilité d’effectuer ou de refuser la synchronisation.Le mode de synchronisation peut également être défini globalement dans les Propriétés de la base.



### Query by formula joins (49)

**Portée** :Process courant

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : 0 (utiliser paramétrages de la base), 1 (toujours utiliser les liens auto) ou 2 (utiliser les jointures SQL si possible).

**Description** : Mode de fonctionnement des commandes [QUERY BY FORMULA](query-by-formula.md) et [QUERY SELECTION BY FORMULA](query-selection-by-formula.md) relatif à l’utilisation de "jointures SQL".

Dans les bases de données créées à compter de la version 11.2 de 4D v11 SQL, ces commandes effectuent des jointures sur le modèle des jointures SQL. Ce mécanisme permet de modifier la sélection d’une table en fonction d’une recherche effectuée sur une autre table sans que les tables soient reliées par un lien automatique (condition nécessaire dans les versions précédentes de 4D).

Le sélecteur Query by formula joins vous permet de définir le mode de fonctionnement des commandes de recherche par formule pour le process courant :

0 : utiliser les paramètres courants de la base (valeur par défaut). Dans les bases de données créées à compter de la version 11.2 de 4D v11 SQL, les "jointures SQL" sont toujours activées pour les recherches par formule. Dans les bases de données converties, ce mécanisme est inactivé par défaut pour des raisons des compatibilité mais peut être mis en oeuvre via une préférence.1 : toujours utiliser les liens auto (= fonctionnement des versions précédentes de 4D). Dans ce mode, un lien est nécessaire pour définir la sélection d’une table en fonction de recherches effectuées dans une autre table. 4D n’effectue pas de "jointures SQL".2 : utiliser les jointures SQL si possible (= fonctionnement par défaut des bases créées en version 11.2 et suivantes de 4D v11 SQL). Dans ce mode, 4D établit des "jointures SQL" pour les recherches par formule lorsque la formule s’y prête (à deux exceptions près, voir la description de la commande commandes [QUERY BY FORMULA](query-by-formula.md) ou [QUERY SELECTION BY FORMULA](query-selection-by-formula.md). **Note :** Avec 4D en mode distant, les "jointures SQL" ne peuvent être utilisées que si les formules sont exécutées sur le serveur (elles doivent avoir accès aux enregistrements). Pour configurer le lieu d'exécution des formules, reportez-vous aux sélecteurs 46 et 47.



### HTTP compression level (50)

**Portée** : Application 4D

 **Conservé** **entre deux sessions** : Non

 **Description** : *Constante obsolète (conservée par compatibilité uniquement).* Il est désormais conseillé d'utiliser les commandes [WEB SET OPTION](web-set-option.md) et [WEB GET OPTION](web-get-option.md) pour le paramétrage du serveur HTTP.



### HTTP compression threshold (51)

**Portée** : Application 4D

 **Conservé** **entre deux sessions** : Non

 **Description** : *Constante obsolète (conservée par compatibilité uniquement).* Il est désormais conseillé d'utiliser les commandes [WEB SET OPTION](web-set-option.md) et [WEB GET OPTION](web-get-option.md) pour le paramétrage du serveur HTTP.



### Server base process stack size (53)

**Portée** : 4D Server

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : Entier long positif.

**Description** : Taille de la pile allouée à chaque process système préemptif sur le serveur, exprimée en octets. La taille par défaut est déterminée par le système.

Les process système préemptifs (process de type Process base 4D client) sont chargés de contrôler les process clients 4D principaux. La taille allouée par défaut à la pile de chaque process préemptif permet un bon confort d’exécution mais peut s’avérer conséquente lorsque de très nombreux process (plusieurs centaines) sont créés. 

A des fins d’optimisation, cette taille peut être diminuée sensiblement si les opérations effectuées par la base s'y prêtent (par exemple si la base n’effectue pas de tris sur de grosses quantités d’enregistrements). Des valeurs de 512 voire de 256 Ko sont possibles. Attention, le sous-dimensionnement de la pile est critique et peut nuire au fonctionnement de 4D Server. Le réglage de ce paramètre est à effectuer avec précaution et doit tenir compte des conditions d’utilisation de la base (nombre d’enregistrements, types d’opérations, etc.). Pour être pris en compte, ce paramétrage doit être exécuté sur le poste serveur (par exemple dans la méthode base Sur démarrage serveur).



### Idle connections timeout (54)

**Portée** : Application 4D sauf si valeur négative

**Conservé** **entre deux sessions** : Non

**Valeurs possibles** : Valeur entière exprimant une durée en secondes. La valeur peut être positive (nouvelles connexions) ou négative (connexions existantes). Par défaut, la valeur est 20.

**Description** : Délai maximum d’inactivité (timeout) des connexions au moteur de base de données et au serveur SQL de 4D ainsi que, en mode *ServerNet* (nouvelle couche réseau), au serveur d'applications 4D. Lorsqu’une connexion inactive atteint ce délai, elle est automatiquement mise en veille, ce qui se traduit par le gel de la session client/serveur et la fermeture du socket réseau. Dans la fenêtre d'administration du serveur, le process utilisateur prend l'état "Postponed". Ce fonctionnement est entièrement transparent pour l’utilisateur : dès qu’il y a reprise d’activité sur la connexion mise en veille, le socket est automatiquement rouvert et la session client/serveur restaurée. 

Ce paramétrage permet, d’une part, d’économiser des ressources sur le serveur : les connexions mises en veille referment le socket et libèrent un processus sur le serveur. D’autre part, il permet d’éviter les pertes de connexions dues aux fermetures par les pare-feux des sockets inactifs. La valeur de timeout des connexions inactives doit pour cela être inférieure à celle du pare-feu. 

Si vous passez une valeur positive dans *valeur*, elle s'applique à toutes les nouvelles connexions dans tous les process. Si vous passez une valeur négative, elle s’applique aux connexions ouvertes dans le process courant. Si vous passez 0, les connexions inactives ne sont pas soumises à un timeout.

Ce paramètre doit être défini côté client. Généralement, vous n'aurez pas besoin de modifier cette valeur.



### PHP interpreter IP address (55)

**Portée** :Application 4D

 **Conservé** **entre deux sessions** : Non

**Valeurs** : Chaîne formatée en IPv4 (par exemple "127.0.0.1") ou en IPv6 (par exemple "2001:0db8:0000:0000:0000:ff00:0042:8329")

**Description** : Adresse IP utilisée localement par 4D pour communiquer avec l’interpéteur PHP via fastcgi. Par défaut, la valeur est "127.0.0.1" (les adresses au format IPv6 sont prises en charge à compter de 4D v16R4).. Cette adresse doit correspondre à la machine sur laquelle se trouve 4D. Ce paramètre peut également être défini globalement pour tous les postes via les Propriétés de la base.

Pour plus d’informations sur l’interpréteur PHP de 4D, reportez-vous au manuel *Mode Développement*.



### PHP interpreter port (56)

**Portée** :Application 4D

 **Conservé** **entre deux sessions** : Non

**Valeurs** : Valeur de type entier long positif. Par défaut, la valeur est 8002\. 

**Description** : Numéro du port TCP utilisé par l’interpréteur PHP de 4D. Ce paramètre peut également être défini globalement pour tous les postes via les Propriétés de la base. Pour plus d’informations sur l’interpréteur PHP de 4D, reportez-vous au manuel *Mode Développement*.



### SSL cipher list (64)

**Portée** : Application 4D

**Conservé entre deux sessions** : Non

**Valeurs possibles** : Suite de chaînes séparées par des deux-points.

**Description :** Liste de chiffrement (*cipher list*) utilisée par 4D pour le protocole sécurisé. Cette liste permet de modifier la priorité des algorithmes de chiffrement mis en oeuvre par 4D.

Par exemple, vous pouvez passer la chaîne suivante dans le paramètre *valeur* : "HIGH:!aNULL:!MD5:!3DES:!CAMELLIA:!AES128:!RSA:!DH:!RC4". Pour une description complète de la syntaxe de la liste de chiffrement, reportez-vous à la *page ciphers sur le site de OpenSSL*.

Ce paramétrage s'applique au principal serveur Web (à l'exclusion des objets Web server), au serveur SQL, aux connexions client/serveur ainsi qu'au client HTTP et aux commandes 4D faisant appel au protocole sécurisé. Ce paramétrage est temporaire (il n'est pas maintenu entre les sessions). 

Lorsque la liste de chiffrement a été modifiée, vous devez redémarrer le serveur concerné pour que le nouveau paramétrage soit pris en compte.

Pour réinitialiser la liste de chiffrement à sa valeur par défaut (stockée en dur dans le fichier SLI), appelez la commande [SET DATABASE PARAMETER](set-database-parameter.md) et passez une chaîne vide ("") dans le paramètre *valeur*. 

**Note :** Avec la commande [Get database parameter](get-database-parameter.md), la liste de chiffrement est retournée dans le paramètre optionnel *valeurAlpha* et le paramètre de retour vaut toujours 0.



### Cache unload minimum size (66)

**Portée** : Application 4D 

**Conservé entre deux sessions** : Non

**Valeurs possibles** : Entier long positif > 1.

**Description** : Taille minimum de mémoire à libérer du cache de la base de données lorsque le moteur a besoin d’y faire de la place pour y allouer un objet (valeur en octets). 

Ce sélecteur a pour but de permettre de réduire le nombre de libérations de données du cache afin d’obtenir des gains de performances. Vous pouvez faire varier ce paramétrage en fonction de la taille du cache et de celle des blocs de données manipulées dans votre base. 

Par défaut, si ce sélecteur n’est pas utilisé, 4D décharge au minimum 10 % du cache en cas de besoin de place.



### Direct2D status (69)

**Portée**: Application 4D

**Conservé entre deux sessions** : Non

**Description** : Mode d’activation de l’implémentation de Direct2D sous Windows.

**Valeurs possibles** : Une des constantes suivantes (mode 3 par défaut) :

Direct2D disabled (0) : le mode Direct2D n’est pas activé, la base fonctionne dans le mode précédent (GDI/GDIPlus).

Direct2D hardware (1) : utilisation de Direct2D en contexte graphique matériel dans toute l’application 4D. Si ce contexte n’est pas disponible, utilisation du contexte graphique Direct2D logiciel.

Direct2D software (3) (Mode par défaut) : à partir de Windows 7, utilisation de Direct2D en contexte graphique logiciel dans toute l’application 4D.

**Attention :* Ce sélecteur est fourni uniquement à des fins de débogage. Etant donné que plusieurs fonctionnalités de 4D dépendent de Direct2D, il ne doit pas être désactivé dans les applications déployées. Seul le mode par défaut (Direct2D software) est approuvé pour les applications déployées.*



### Direct2D get active status (74)

**Note :** Ce sélecteur peut être utilisé uniquement avec la commande [Get database parameter](get-database-parameter.md), sa valeur ne peut pas être fixée.

**Description** : Retourne l’implémentation active de Direct2D sous Windows. 

**Valeurs possibles** : 0, 1, 2, 3, 4 ou 5 (cf. valeurs du sélecteur 69). La valeur retournée dépend de la disponibilité de Direct2D, du matériel et de la qualité de la prise en charge de Direct2D par le système d’exploitation.

Par exemple, si vous exécutez :

 SET DATABASE PARAMETER(;Direct2D Hardware)  $mode:=Get database parameter()

- sur Windows 7 et suivants, *$mode* vaudra 1 si le système détecte un matériel compatible Direct2D, sinon *$mode* vaudra 3 (contexte logiciel).

- sur Windows Vista, *$mode* vaudra 1 si le système détecte un matériel compatible Direct2D, sinon *$mode* vaudra 0 (désactivation de Direct2D).

- sur Windows XP, *$mode* vaudra toujours 0 (incompatibilité avec Direct2D).



### Diagnostic log recording (79)

**Thread-safe** : Yes

**Portée** : Application 4D

**Conservé** **entre deux sessions** : Non

**Valeurs possibles** : 0 ou 1 (0 = ne pas enregistrer, 1 = enregistrer)

**Description** : Démarrage ou arrêt de l’enregistrement du fichier de diagnostic de 4D. Par défaut, la valeur est 0 (pas d’enregistrement).

4D vous permet d’enregistrer de manière continue dans un fichier de diagnostic un ensemble d’événements relatifs au fonctionnement interne de l’application. Les informations contenues dans ce fichier sont destinées à la mise au point des applications 4D et pourront être analysées avec l’aide des services techniques de 4D (pour plus d'informations, reportez-vous à la section *Description des fichiers d'historique* sur *developer.4d.com*). Lorsque vous passez 1 dans ce sélecteur, un fichier de diagnostic est automatiquement créé (ou ouvert) dans le dossier **Logs** de la base. Le fichier est nommé *4DDiagnosticLog\_N*.txt (ou *4DDiagnosticLogServer\_N.*txt s'il est généré sur le serveur). Une fois que le fichier atteint une taille de 10 Mo, il est refermé et un nouveau fichier est généré, avec un numéro séquentiel N incrémenté.

A noter qu’il est possible d’inclure des informations personnalisées dans ce fichier à l’aide de la commande [LOG EVENT](log-event.md).



### Log command list (80)

**Portée** : Application 4D

**Conservé** **entre deux sessions** : Non

**Valeurs possibles** : Chaîne contenant la liste des numéros des commandes 4D à enregistrer (séparées par des points-virgules), ou "all" pour enregistrer toutes les commande, ou "" (chaîne vide) pour n’enregistrer aucune commande, ou le préfixe "-" pour exclure des commandes spécifiques.

**Description** : Liste des commandes 4D à enregistrer dans le fichier de débogage ou à exclure du fichier de débogage (cf. sélecteur 34, Debug log recording). Par défaut, toutes les commandes 4D sont enregistrées. Ce sélecteur vous permet de restreindre la quantité d’informations stockées dans le fichier de débogage en limitant les commandes 4D dont vous souhaitez enregistrer l’exécution ou bien que vous souhaitez exclure de l'enregistrement. Par exemple, vous pouvez écrire :  SET DATABASE PARAMETER(Log command list;"277;341") //enregistrer uniquement les commandes CHERCHER et CHERCHER DANS SELECTION  OU  SET DATABASE PARAMETER(Log command list;"-1666;-323") //exclure les commandes FIXER ALIAS UTILISATEUR et ENDORMIR PROCESS de l'enregistrement



### Spellchecker (81)

**Portée** : Application 4D

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : 0 (défaut) = correcteur macOS (Hunspell désactivé), 1 = correcteur Hunspell actif. 

**Description** : Permet d’activer le correcteur orthographique Hunspell sous macOS. Par défaut, sur cette plate-forme le correcteur natif est activé. Vous pouvez souhaiter utiliser le correcteur Hunspell par exemple pour unifier l’interface de vos applications multiplates-formes (sous Windows, seul le correcteur Hunspell est disponible). Pour plus d’informations, reportez-vous à la page *Correction orthographique*.



### Dates inside objects (85)

**Portée** : Process courant

 **Conservé** **entre deux sessions** : Non

 **Valeurs possibles** : String type without time zone (0), String type with time zone (1), Date type (2) (défaut)

**Description** : Définit la manière dont les dates sont stockées dans les objets, ainsi que leur traitement en cas d'importation/exportation en JSON. 

Lorsque ce sélecteur vaut Date type (valeur par défaut dans les bases créées à compter de 4D v17), les dates 4D sont stockées avec le type date dans les objets, en tenant compte des paramétrages de date locaux. Lorsqu'ils sont exportés au format JSON, les attributs date seront convertis en chaînes qui ne contiennent pas l'heure (**Note :** ce paramétrage peut être défini au niveau des paramètres de la base via l'option "Utiliser le type date au lieu du format date ISO dans les objets" dans la *Page Compatibilité*).

Si vous passez String type with time zone dans ce sélecteur, les dates 4D seront converties en chaînes ISO en tenant compte du fuseau horaire local. Par exemple, la conversion de la date !23/08/2013! donne "2013-08-22T22:00:00Z" au format JSON lorsque l’opération est effectuée en France en été (GMT+2). Ce principe est conforme au fonctionnement standard de JavaScript. Ce fonctionnement peut être source d’erreurs si vous souhaitez envoyer des valeurs de date en JSON à une personne qui se trouve dans un autre fuseau horaire. C’est le cas par exemple pour l’exportation d’une table avec [Selection to JSON](selection-to-json.md) en France destiné à être réimporté aux USA avec [JSON TO SELECTION](json-to-selection.md). Par défaut, les dates étant réinterprétées dans chaque fuseau horaire, les valeurs stockées dans la base seront différentes. Dans ce cas, vous pouvez modifier le mode de conversion des dates afin qu’il ne tienne pas compte du fuseau horaire en passant String type without time zone dans ce sélecteur. La conversion de la date !23/08/2013! donnera alors "2013-08-23T00:00:00Z" dans tous les cas.



### Diagnostic log level (86)

**Thread-safe** : Yes

**Portée :** Application 4D 

**Conservé entre deux sessions :** Non

**Description :** Niveau(x) de messages à inclure dans le journal de diagnostic lorsqu'il est activé (voir le sélecteur Diagnostic log recording). Chaque niveau désigne une catégorie de messages de diagnostic et inclut automatiquement la ou les catégories plus importantes. Pour une description des catégories, consultez la section *Log niveau diagnostic* sur le site *developer.4d.com*.

**Valeurs possibles** **:** L'une des constantes suivantes (Log info par défaut): Log trace: active ERROR, WARN, INFO, DEBUG, TRACE (niveau le plus détaillé) Log debug: active ERROR, WARN, INFO, DEBUG Log info: active ERROR, WARN, INFO (par défaut) Log warn: active ERROR, WARN Log error: active ERROR (niveau le moins détaillé)



### Use legacy network layer (87)

**Portée :** 4D local, 4D Server.

**Conservé entre deux sessions :** Oui

**Description :** Fixe ou lit le statut courant de l'ancienne couche réseau pour les connexions client/serveur. L'ancienne couche réseau est obsolète à compter de 4D v14 R5 et doit être progressivement remplacée dans vos applications par la couche réseau *ServerNet*. *ServerNet* sera nécessaire dans les prochaines versions de 4D afin de permettre aux applications 4D de tirer parti des futures évolutions réseau. Pour des raisons de compatibilité, l'ancienne couche réseau est toujours prise en charge afin de faciliter la transition des applications existantes (elle reste utilisée par défaut dans les applications converties depuis des versions antérieures à la v14 R5). Passez 1 dans ce paramètre pour utiliser l'ancienne couche réseau (et désactiver *ServerNet*), et passez 0 pour désactiver l'ancienne couche réseau (et utiliser *ServerNet*).

Cette propriété peut également être définie à l'aide de l'option "Utiliser l'ancienne couche réseau" présente dans la *Page Compatibilité* des Propriétés de la base (voir section *Options réseau et Client-serveur* ; dans cette section, vous trouverez aussi un paragraphe décrivant la stratégie de migration. Nous vous recommandons d'activer *ServerNet* dès que possible).

Il est nécessaire de redémarrer l'application pour que ce paramètre soit pris en compte.

**Valeurs possibles :** 0 ou 1 (0 = ne pas utiliser l'ancienne couche, 1 = utiliser l'ancienne couche)

**Valeur par défaut :** 0 dans les applications créées avec 4D v14 R5 ou suivantes, 1 dans les applications converties depuis 4D v14 R4 ou précédentes.



### SQL Server Port ID (88)

**Portée** : 4D mode local et 4D Server.

**Conservé entre deux sessions** : Oui

**Description** : Permet de lire ou de fixer le numéro du port TCP utilisé par le serveur SQL intégré de 4D en mode local ou de 4D Server. Par défaut, la valeur est 19812\. Le numéro de port TCP peut également être défini dans la page "SQL" de la boîte de dialogue des Propriétés de la base. Lorsque ce sélecteur est utilisé en écriture, la propriété de la base est mise à jour.

**Valeurs possibles** : 0 à 65535.

**Valeur par défaut** : 19812



### Circular log limitation (90)

**Thread-safe** : Yes

**Portée** : 4D local, 4D Server.

**Conservé entre deux sessions** : Non

**Valeurs possibles** : Toute valeur entière, 0 = conserver tous les journaux

**Description** : Nombre maximum de fichiers à conserver par roulement pour chaque type de journal. Par défaut, les 50 fichiers les plus récents sont conservés. Si vous passez une valeur N, seuls les N fichiers les plus récents seront conservés, le plus ancien étant automatiquement effacé à la création d'un nouveau. Ce paramétrage s'applique à tous les fichiers journaux, notamment le journal des requêtes (sélecteurs 28 et 45), le journal de débogage (sélecteur 34), le journal des événements (sélecteur 79), l'historique des requêtes Web (sélecteurs 29 et 84 de la commande [WEB SET OPTION](web-set-option.md)), etc.



### Number of formulas in cache (92)

**Portée** : Application 4D.

**Conservé entre deux sessions** : Non

**Valeurs possibles** : Entier long positif

**Valeur par défaut** : 0 (pas de cache) 

**Description** : Fixe ou lit le nombre maximum de formules à conserver dans le cache des formules, qui est utilisé par la commande [EXECUTE FORMULA](execute-formula.md). Cette limite est appliquée à tous les process, mais chaque process dispose de son propre cache de formules. Placer des formules dans le cache accélère l'exécution de la commande [EXECUTE FORMULA](execute-formula.md) en mode compilé puisque chaque formule en cache est tokenisée une seule fois dans ce cas. Lorsque vous modifiez la valeur du cache, son contenu est réinitialisé même si la nouvelle valeur est supérieure à la précédente. Une fois le nombre maximum de formules en cache atteint, toute nouvelle formule exécutée écrase la plus ancienne dans le cache (mode FIFO). Ce paramètre est pris en compte uniquement dans les bases ou les composants compilés.



### OpenSSL version (94)

**Portée** : Tous postes 4D 

 **Conservé entre deux sessions** : Non

**Description**: Retourne le numéro de version de la bibliothèque OpenSSL utilisée sur le poste. (Lecture seule)



### Cache flush periodicity (95)

**Thread-safe** : Yes


Portée : 4D local, 4D Server

**Conservé entre deux sessions** : Non

**Valeurs possibles** : entier long > 1 (secondes)

**Description** : Permet de lire ou de fixer la valeur courante de périodicité de l'écriture du cache de données sur le disque, exprimée en secondes. Si elle est modifiée, cette valeur remplace la valeur définie par l'option **Ecriture cache toutes les <n> secondes/minutes** dans la [XML DECODE](xml-decode.md) des Propriétés de la base durant la session courante (elle n'est pas stockée dans les Propriétés de la base).



### Remote connection sleep timeout (98)

**Portée** : Application 4D Server

**Conservé entre deux sessions** : Non

**Valeurs possibles** : Entier long positif

**Description** : Timeout de la connexion à distance en veille, exprimé en secondes. Par défaut, la valeur est 172800 (48 heures). Le délai de mise en veille est appliqué une fois qu'une machine exécutant une application distante 4D est passée en mode veille. Dans ce cas, sa session est maintenue par 4D Server (voir la description de la fonctionnalité ). 4D Server vérifie toutes les 5 minutes si un 4D distant en veille a dépassé le délai de veille, auquel cas il est abandonné. Ainsi, la durée de veille maximale autorisée est la *timeout mise en veille actuel + 300*. Dans certains cas, vous souhaiterez peut-être modifier le délai de mise en veille, pour libérer, par exemple, les enregistrements/licences verrouillés plus rapidement.



### Tips enabled (101)

**Portée :** Application 4D

**Conservé entre deux sessions :** Non

**Valeurs possibles :** 0 = message d'aide désactivés, 1 = messages d'aide activés (défaut)

**Description :** Définit ou récupère l'état d'affichage des messages d'aide dans l'application 4D. Par défaut, les messages d'aide sont activées.

 Notez que ce paramètre fixe tous les messages d'aides, c'est-à-dire les messages d'aide des formulaires et ceux de l'éditeur du mode Développement.



### Tips delay (102)

**Portée :** Application 4D

**Conservé entre deux sessions :** Non

**Valeurs possibles :** entier long >= 0 (ticks)

**Description :** délai avant que les messages d'aide soient affichés une fois que le curseur de la souris est arrêté sur les objets avec message d'aide. La valeur est exprimée en ticks (1/60e de seconde). La valeur par défaut est de 45 ticks (0,75 seconde).



### Tips duration (103)

**Portée :** Application 4D

**Conservé entre deux sessions :** Non

**Valeurs possibles :** entier long >= 60 (ticks)

**Description :** Durée maximum de l'affichage du message d'aide. La valeur est exprimée en ticks (1/60e de seconde). La valeur par défaut est de 720 ticks (12 secondes).



### Min TLS version (105)

**Portée** : 4D Server, 4D Web Server et 4D SQL Server

**Conservé entre deux sessions** : Non

**Description** : Permet de définir la version minimale de Transport Layer Security (TLS), chargé du cryptage et de l'authentification des données entre les applications et les serveurs. Les requêtes de connexion des clients prenant en charge uniquement des versions inférieures à cette version minimale seront rejetées. Ce paramétrage est appliqué globalement à l'ensemble de la couche réseau. S'il est modifié, le serveur doit être redémarré afin d'utiliser la nouvelle valeur. 

**Valeur par défaut** : TLSv1\_3 

**Valeurs possibles** : TLSv1\_2 (TLS 1.2, créé en 2008) TLSv1\_3 (TLS 1.3, introduit en 2018) **Notes** : 

- Le plug-in 4D Internet Commands utilise sa propre couche réseau, par conséquent ce sélecteur n'aura pas d'impact sur sa configuration TLS.

- Ce paramétrage est ignoré pour les connexions client-serveur si votre 4D Server utilise l'ancienne couche réseau.



### User param value (108)

**Portée :** 4D local, 4D Server

**Conservé entre deux sessions :** Non

**Valeurs possibles** : Toute chaîne personnalisée 

**Description :** Chaîne personnalisée passée d'une session à la suivante lorsque l'application 4D est redémarrée. Ce sélecteur est utile dans les cas où des tests unitaires automatisés nécessitent que les applications redémarrent avec des paramètres différents. 

Avec [SET DATABASE PARAMETER](set-database-parameter.md), définit une nouvelle valeur qui sera disponible dans la prochaine base de données ouverte après le redémarrage manuel de 4D or l'utilisation des commandes [OPEN DATABASE](open-database.md)(\*), [OPEN DATA FILE](open-data-file.md), ou [RESTART 4D](restart-4d.md). Avec [Get database parameter](get-database-parameter.md), retourne la valeur User param courante définie à l'aide d'une ligne de commande (voir *Interface ligne de commande*), un fichier .4DLink (voir *Utiliser un fichier 4DLink*), ou un appel à [SET DATABASE PARAMETER](set-database-parameter.md) durant la session précédente. (\*) Si [SET DATABASE PARAMETER](set-database-parameter.md) fixe une User param value avant d'appeler [OPEN DATABASE](open-database.md) à l'aide d'un fichier .4DLink contenant également un attribut xml user-param xml, 4D ne tient compte que du paramètre fourni par [SET DATABASE PARAMETER](set-database-parameter.md).



### Times inside objects (109)

Portée : 4D local, 4D Server (tous process)

**Conservé entre deux sessions** : Oui

 **Valeurs possibles** : Times in seconds (0) (défaut), Times in milliseconds (1) 

**Description** : Définit la manière dont les valeurs de type heure sont converties et stockées dans les propriétés d'objets et les éléments de collections, ainsi que lors des imports/exports JSON et via les zones Web. Par défaut, à compter de 4D v17, les heures sont converties et stockées en nombre de secondes. 

Dans les versions précédentes, les heures étaient converties et stockées en nombre de millisecondes dans ces contextes. L'utilisation de ce sélecteur peut vous aider lors de la migration de vos applications en rétablissant le fonctionnement précédent lorsque c'est nécessaire. 

**Note** : Les méthodes ORDA et le moteur SQL ne tiennent pas compte de ce paramétrage, ces deux environnements manipulent toujours les heures en nombre de secondes.



### SMTP Log (110)

**Thread-safe** : Yes

Portée : 4D local, 4D Server*

* **Conservé entre deux sessions** : Non

**Valeurs possibles** : 0 ou de 1 à N (0 = ne pas enregistrer, 1 à N = numéro séquentiel, accolé au nom du fichier). Par défaut, la valeur est 0 (pas d'enregistrement des échanges SMTP).

**Description** : Démarrage ou arrêt de l'enregistrement des échanges entre 4D et le serveur SMTP, lorsqu'un objet *transporteur* est traité par *transporteur.send( )* ou *SMTP\_transporteur.checkConnection( )*. Par défaut, la valeur est 0 (pas d'enregistrement des échanges SMTP). Lorsque ce mécanisme est activé, un fichier d'historique est créé dans le dossier Logs de la base. Il est nommé 4DSMTPLog\_X.txt, *où N* est le numéro séquentiel de l'historique. Une fois qu'un fichier atteint une taille de 10 Mo, il est refermé et un nouveau fichier est généré, avec un numéro séquentiel incrémenté. Si un fichier du même nom existe déjà, il est directement remplacé. Vous pouvez définir le numéro de départ de la séquence à l'aide du paramètre *valeur*. Par défaut, tous les fichiers sont conservés, mais vous pouvez gérer le nombre de fichier à conserver à l'aide du paramètre Circular log limitation. 

Pour plus d'informations sur les fichiers 4DSMTPLog\_X.txt, veuillez consulter la section *Description des fichiers d'historique*.



### Current process debug log recording (111)

**Portée :** Application 4D

**Conservé entre deux sessions :** Non

**Description** : Démarrage ou arrêt de l'enregistrement séquentiel des événements de programmation **du process courant** dans un fichier d'historique séparé. Cet historique est semblable à Debug log recording (sélecteur 34) mais il ne porte que sur le process courant. Le nom du fichier d'historique inclut la lettre "p" et le numéro du process : 4DDebugLog\[\_p*N*_*n*].txt, où N est l'ID unique du process. Pour plus d'informations sur ce format et sur l'utilisation du fichier *4DDebugLog*, veuillez consulter la *Description des fichiers d'historique* dans le Mode Développement. 

**Notes :** Ce sélecteur est fourni uniquement à des fins de débogage et doit être utilisé avec précaution. Plus particulièrement, il ne doit pas être utilisé en production, étant donné qu'il peut avoir une incidence sur les performances de l'application. Vous pouvez utiliser simultanément les sélecteurs Debug log recording et Current process debug log recording, auquel cas les actions liées au process courant ne seront pas enregistrées dans le fichier d'historique principal.



### Is current database a project (112)

**Note :**  Vous pouvez utiliser ce sélecteur uniquement à l'aide de la commande [Get database parameter](get-database-parameter.md) et ses valeurs ne peuvent pas être définies.

**Portée** : Application 4D

**Description** : Retourne 1 si l'architecture de la base courante est un projet, sinon elle retourne 0\. Pour plus d'informations, veuillez consulter la section *Base projet VS base binaire*.



### Is host database a project (113)

**Note :**  Vous pouvez utiliser ce sélecteur uniquement à l'aide de la commande [Get database parameter](get-database-parameter.md) et ses valeurs ne peuvent pas être définies.

**Portée** : Application 4D

**Description** : Retourne 1 si l'architecture de la base hôte est un projet, sinon elle retourne 0\. Pour plus d'informations, veuillez consulter la section *Base projet VS base binaire*.



### Libldap version (114)

**Portée** : Machine 4D courante

**Conservé entre deux sessions** : Non

**Description** : Retourne le numéro de version de la bibliothèque LDAP dans l'application 4D sur la machine locale. (Lecture seule)



### Libsasl version (115)

**Portée** : Machine 4D courante

**Conservé entre deux sessions** : Non

**Description** : Retourne le numéro de version de la bibliothèque SASL dans l'application 4D sur la machine locale. (Lecture seule)



### POP3 Log (116)

**Thread-safe** : Yes

Portée : 4D local, 4D Server

**Conservé entre deux sessions** : Non

**Valeurs possibles** : 0 ou de 1 à N (0 = ne pas enregistrer, 1 à N = numéro séquentiel, accolé au nom du fichier). Par défaut, la valeur est 0 (pas d'enregistrement des échanges POP3).

**Description** : Démarrage ou arrêt de l'enregistrement des échanges entre 4D et le serveur POP3, lorsqu'un objet *transporteur* est traité par *POP3\_transporteur.getMail( )* ou *POP3\_transporteur.checkConnection( )*. Par défaut, la valeur est 0 (pas d'enregistrement des échanges POP3). Lorsque ce mécanisme est activé, un fichier d'historique est créé dans le dossier Logs de la base. Il est nommé 4DPOP3Log\_X.txt, *où N* est le numéro séquentiel de l'historique. Une fois qu'un fichier atteint une taille de 10 Mo, il est refermé et un nouveau fichier est généré, avec un numéro séquentiel incrémenté. Si un fichier du même nom existe déjà, il est directement remplacé. Vous pouvez définir le numéro de départ de la séquence à l'aide du paramètre *valeur*. Par défaut, tous les fichiers sont conservés, mais vous pouvez gérer le nombre de fichier à conserver à l'aide du paramètre Circular log limitation. Pour plus d'informations sur les fichiers 4DPOP3Log\_X.txt, veuillez consulter la section *Description des fichiers d'historique*.



### Is host database writable (117)

**Note :** Vous pouvez utiliser ce sélecteur uniquement avec la commande [Get database parameter](get-database-parameter.md) et sa valeur ne peut pas être définie.

**Portée** : Application 4D 

**Description** : Retourne 1 si le fichier de structure ou le fichier de projet de l'hôte est en écriture, et retourne 0 s'il est en lecture seule.



### IMAP Log (119)

**Thread-safe** : Yes

**Portée** : 4D local, 4D Server

**Conservé entre deux sessions :** Non

**Valeurs possibles :** 0 ou de 1 à N (0 = ne pas enregistrer, 1 à N = numéro séquentiel, ajouté au nom du fichier). Par défaut, la valeur est 0 (échanges IMAP non enregistrés).

**Description :** Démarre ou stoppe l'enregistrement des échanges entre 4D et le serveur IMAP, lorsqu'un objet transporteur est traité via *IMAP\_transporteur.getMail( )* ou *IMAP\_transporteur.checkConnection( )*. Par défaut, la valeur est 0 (échanges non enregistrés). Lorsque ce mécanisme est activé, un fichier journal est créé dans le dossier Journaux de la base de données. Il est nommé 4DIMAPLog\_N.txt, où N est le numéro séquentiel du journal. Une fois que le fichier 4DIMAPLog a atteint une taille de 10 Mo, il est fermé et un nouveau est généré, avec un numéro séquentiel incrémenté. Si un fichier du même nom existe déjà, il est directement remplacé. Vous pouvez définir le numéro de départ de la séquence à l'aide du paramètre value. Par défaut, tous les fichiers sont conservés, mais vous pouvez contrôler le nombre de fichiers à conserver en utilisant le paramètre Circular log limitation.

Pour plus d'informations sur les fichiers 4DIMAPLog\_N.txt, reportez-vous à la section *Description des fichiers d'historique*.



### Libzip version (120)

**Portée :** Machine 4D courante

**Conservé entre deux sessions :** n/a

**Description :** Retourne le numéro de version de la bibliothèque libzip dans l'application 4D sur la machine courante. (Lecture seule)



### Pause logging (121)

**Thread-safe** : Yes

**Portée :** Application 4D

**Conservé entre deux sessions :** Non

**Valeurs possibles :** 0 (reprise des journaux), 1 (pause des journaux)

Ce sélecteur permet de suspendre/reprendre toutes les opérations de journalisation lancées sur l'application (à l'exception des journaux ORDA). Cette fonction peut être utile pour alléger temporairement les tâches de l'application 4D ou pour planifier les opérations des journaux.





**Notes :** 

* Le paramètre *laTable* est utilisé par les sélecteurs 31, 46 et 47 uniquement. Dans les autres cas, il est ignoré s'il est passé.
* Lorsqu'un paramétrage n'est pas conservé entre les sessions, vous pouvez le définir au démarrage via la ou la [On Server Startup database method](on-server-startup-database-method.md).

## Sélecteurs thread-safe 

La commande **SET DATABASE PARAMETER** peut être utilisée dans des processus préemptifs lors de l'appel des sélecteurs suivants :

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


## Exemple 1 

L’instruction suivante permet d'anticiper un éventuel problème de **timeout**

```4d
  //Augmentation du timeout à 3 heures pour le process courant
 SET DATABASE PARAMETER(4D Server Timeout;-60*3)
  //Exécution d’une opération longue hors du contrôle de 4D
 ...
 WR PRINT MERGE(LaZone;3;0)
 ...
```

## Exemple 2 

Cet exemple force temporairement l’exécution sur le client d’une commande de recherche par formule :

```4d
 valCourante:=Get database parameter([table1];Query By Formula On Server) //Stocker le paramétrage courant
 SET DATABASE PARAMETER([table1];Query By Formula On Server;1) //Forcer l’exécution sur le client
 QUERY BY FORMULA([table1];maformule)
 SET DATABASE PARAMETER([table1];Query By Formula On Server;valCourante) //Rétablir le paramétrage courant
```

## Exemple 3 

Vous souhaitez exporter des données en JSON contenant une date 4D convertie. A noter que la conversion a lieu au moment du stockage de la date dans l’objet, il faut donc appeler la commande [SET DATABASE PARAMETER](set-database-parameter.md) avant [OB SET](ob-set.md) : 

```4d
 var $o : Object
 SET DATABASE PARAMETER(Dates inside objects;0)
 OB SET($o ;"maDate";Current date) // conversion JSON
 $json:=JSON Stringify($o)
 SET DATABASE PARAMETER(Dates inside objects;1)
```

## Voir aussi 

[Get database parameter](get-database-parameter.md)  
[LOG EVENT](log-event.md)  
[QUERY SELECTION](query-selection.md)  

## Propriétés

|  |  |
| --- | --- |
| Numéro de commande | 642 |
| Thread safe | &cross; |


