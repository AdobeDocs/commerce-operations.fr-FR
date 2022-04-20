---
title: Bonnes pratiques de configuration
description: Optimisez le temps de réponse de votre déploiement Adobe Commerce ou Magento Open Source à l’aide de ces bonnes pratiques.
source-git-commit: 09c4d0e09354230c8779b930f085d8c7c131b85b
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Bonnes pratiques de configuration

Commerce fournit de nombreux paramètres et outils que vous pouvez utiliser pour améliorer le temps de réponse sur les pages et fournir un débit plus élevé.

## Tâches Cron

Toutes les opérations asynchrones dans [!DNL Commerce] sont effectuées sous Linux `cron` . Voir [Configuration et exécution de cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) pour le configurer correctement.

## Indexateurs

Un indexeur peut s’exécuter dans l’un des **[!UICONTROL Update on Save]** ou **[!UICONTROL Update on Schedule]** mode . Le **[!UICONTROL Update on Save]** Le mode indexe immédiatement chaque fois que votre catalogue ou d’autres données changent. Ce mode suppose une faible intensité des opérations de mise à jour et de navigation dans votre magasin. Cela peut entraîner des retards importants et une indisponibilité des données lors de charges élevées. Nous vous recommandons d’utiliser **Mise à jour de la planification** en production, car il stocke des informations sur les mises à jour des données et effectue l’indexation par parties en arrière-plan via une tâche cron spécifique. Vous pouvez modifier le mode de chaque [!DNL Commerce] indexeur séparément sur le  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** page de configuration.

La réindexation sur MariaDB 10.4 prend plus de temps que les autres MariaDB ou [!DNL MySQL] versions. Pour pallier ce problème, nous vous suggérons de modifier la configuration par défaut de MariaDB et de définir les paramètres suivants :

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Caches

Lorsque vous lancez votre magasin en production, activez tous les caches à partir du **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** page. Il est vivement recommandé d’utiliser [!DNL Varnish], car il s’agit d’une solution de cache de page de production efficace.

## Notifications électroniques asynchrones

L’activation du paramètre &quot;Notifications par e-mail asynchrones&quot; déplace les processus qui gèrent l’extraction et le traitement des notifications par e-mail en arrière-plan. Pour activer cette fonction, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Voir [Courriers électroniques de vente](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) dans le _Guide de l’utilisateur de Magento Open Source_ pour plus d’informations.

## Traitement asynchrone des données de commande

Il peut arriver que des ventes intensives sur un storefront se produisent en même temps que [!DNL Commerce] effectue un traitement intensif des commandes. Vous pouvez configurer [!DNL Commerce] pour distinguer ces deux schémas de trafic au niveau de la base de données afin d’éviter les conflits entre les opérations de lecture et d’écriture dans les tables correspondantes. Vous pouvez stocker et indexer les données d’ordre de manière asynchrone. Les commandes sont placées en stockage temporaire et déplacées en bloc vers la grille Gestion des commandes sans collision. Vous pouvez activer cette option à partir de **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Voir [Mises à jour de grille planifiées](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) dans le _Guide de l’utilisateur de Magento Open Source_ pour plus d’informations.

>[!WARNING]
>
>Le **[!UICONTROL Developer]** Les options et les onglets ne sont disponibles que dans [Mode Développeur](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe Commerce sur l’infrastructure cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ne prend pas en charge `Developer` mode .

## Mise à jour différée du stock

En période de ventes intensives, [!DNL Commerce] peut différer les mises à jour de stock liées aux commandes. Cela réduit le nombre d’opérations et accélère le processus de placement des commandes. Cependant, cette option est risquée et ne peut être utilisée que lorsque les commandes en arrière-plan sont activées dans le magasin, car cette option peut entraîner des quantités de stock négatives. Cette option peut améliorer considérablement les performances des flux de passage en caisse pour les magasins qui peuvent facilement reremplir leur stock à la demande. Pour activer les mises à jour différées de stock sur votre site, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Voir [Gestion du stock](https://docs.magento.com/user-guide/catalog/inventory.html) dans le _Guide de l’utilisateur d’Adobe Commerce_ pour plus d’informations.

>[!INFO]
>
>Cette option est disponible uniquement si **[!UICONTROL Backorder with any mode]** est activée.

## Paramètres d’optimisation côté client

Pour améliorer la réactivité du storefront [!DNL Commerce] Accédez à Admin en mode par défaut ou Développeur et modifiez les paramètres suivants :

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Groupe de paramètres | Paramètre | Valeur |
| ------------------- | -------------------------- | ------ |
| Paramètres de grille | Indexation asynchrone | Activer |
| Paramètres CSS | Minimisation des fichiers CSS | Oui |
| [!DNL JavaScript] Paramètres | Minify [!DNL JavaScript] Fichiers | Oui |
| [!DNL JavaScript] Paramètres | Activer [!DNL JavaScript] Regroupement | Oui |
| Paramètres des modèles | Minimiser le HTML | Oui |

>[!INFO]
>
>Le **[!UICONTROL Developer]** Les options et les onglets ne sont disponibles que dans [Mode Développeur](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe [!DNL Commerce] sur l’infrastructure cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ne prend pas en charge `Developer` mode .

Lorsque vous activez la variable **[!UICONTROL Enable [!DNL JavaScript] Bundling]** vous autorisez Commerce à fusionner toutes les ressources JS en un ou un ensemble de lots chargés dans les pages de storefront. Le regroupement de JS entraîne une diminution du nombre de requêtes envoyées au serveur, ce qui améliore les performances des pages. Cela permet également de mettre en cache les ressources JS du navigateur lors du premier appel et de les réutiliser pour toute autre navigation. Cette option apporte également une évaluation différée, car tous les JS sont chargés en tant que texte. Elle n’effectue l’analyse et l’évaluation du code qu’après le déclenchement d’actions spécifiques sur la page. Cependant, ce paramètre n’est pas recommandé pour les magasins où le premier temps de chargement de page est extrêmement critique, car tout le contenu JS sera chargé lors du premier appel.

>[!INFO]
>
>Voir [Optimisation des fichiers CSS et JavaScript sur Adobe Commerce sur l’infrastructure cloud et Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) dans le Centre d’aide Adobe Commerce_ pour plus d’informations sur l’optimisation de CSS et JavaScript.

### Conseils de regroupement

* Nous vous recommandons d’utiliser des outils tiers pour la minification et le regroupement (comme [r.js](http://requirejs.org/)). [!DNL Commerce] les mécanismes natifs ne sont pas optimaux et sont fournis en tant qu’alternatives de secours.
* L’activation du protocole HTTP2 peut être une bonne alternative à l’utilisation du regroupement JS. Le protocole offre à peu près les mêmes avantages.
* Il est déconseillé d’utiliser des paramètres obsolètes tels que la fusion de fichiers JS et CSS, car ils ont été conçus uniquement pour les fichiers JS chargés de manière synchrone dans la section HEAD de la page. L’utilisation de cette technique peut entraîner le regroupement et entraîner un mauvais fonctionnement de la logique JS.

## Planning de maintenance de la base de données {#database}

Nous vous recommandons d’effectuer des sauvegardes périodiques de la base de données pour vos instances d’évaluation et de production. En raison de la nature intensive des E/S des opérations de sauvegarde, vous pouvez rencontrer des sauvegardes plus lentes et des problèmes potentiels. L’exécution simultanée de processus de base de données pour plusieurs environnements peut s’exécuter plus lentement en raison d’une simultanéité des ressources disponibles.

Pour de meilleures performances, planifiez l’exécution de vos sauvegardes les unes après les autres, une par une, aux heures creuses. Cette méthode permet d’éviter les conflits d’E/S et de réduire le temps d’exécution, en particulier pour les petites instances, les bases de données volumineuses, etc.

Par exemple, nous vous recommandons de planifier une sauvegarde de votre base de données de production suivie de la base de données intermédiaire lorsque vos magasins rencontrent des visites inférieures.
