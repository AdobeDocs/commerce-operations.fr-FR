---
title: Bonnes pratiques de configuration
description: Optimisez le temps de réponse de votre déploiement Adobe Commerce à l’aide de ces bonnes pratiques.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# Bonnes pratiques de configuration

Commerce fournit de nombreux paramètres et outils que vous pouvez utiliser pour améliorer le temps de réponse sur les pages et fournir un débit plus élevé.

## Tâches Cron

Toutes les opérations asynchrones dans [!DNL Commerce] sont effectuées à l’aide de la commande Linux `cron` . Voir [Configuration et exécution de cron](../configuration/cli/configure-cron-jobs.md) pour le configurer correctement.

## Indexateurs

Un indexeur peut s’exécuter en mode **[!UICONTROL Update on Save]** ou **[!UICONTROL Update on Schedule]**. Le mode **[!UICONTROL Update on Save]** est immédiatement indexe chaque fois que votre catalogue ou d’autres données changent. Ce mode suppose une faible intensité des opérations de mise à jour et de navigation dans votre magasin. Cela peut entraîner des retards importants et une indisponibilité des données lors de charges élevées. Nous vous recommandons d’utiliser **Mettre à jour sur la planification** à des fins de performances, car il stocke des informations sur les mises à jour des données et effectue l’indexation par des parties en arrière-plan par le biais d’une tâche cron spécifique. Vous pouvez modifier le mode de chaque indexeur [!DNL Commerce] séparément sur la page de configuration **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** . L’index [!UICONTROL Customer Grid] doit toujours être défini sur le mode **[!UICONTROL Update on Save]**.

>[!TIP]
>
>La réindexation sur MariaDB 10.4 et 10.6 prend plus de temps que les autres versions de MariaDB ou de [!DNL MySQL]. Nous vous suggérons de modifier le paramètre de configuration par défaut de MariaDB, qui est décrit dans les [conditions préalables à l&#39;installation](../installation/prerequisites/database/mysql.md).

## Caches

Lorsque vous lancez votre magasin en production, activez tous les caches à partir de la page **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** . Nous vous recommandons vivement d’utiliser [!DNL Varnish], car il s’agit d’une solution de cache de page de production efficace.

## Notifications électroniques asynchrones

L’activation du paramètre &quot;Notifications par e-mail asynchrones&quot; déplace les processus qui gèrent l’extraction et le traitement des notifications par e-mail en arrière-plan. Pour activer cette fonctionnalité, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Pour plus d’informations, voir [Courriers électroniques de vente](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) dans le _Guide de l’utilisateur d’administration_.

## Traitement asynchrone des données de commande

Il peut arriver que des ventes intensives sur un storefront se produisent en même temps que [!DNL Commerce] effectue un traitement intensif des commandes. Vous pouvez configurer [!DNL Commerce] pour distinguer ces deux modèles de trafic au niveau de la base de données afin d’éviter les conflits entre les opérations de lecture et d’écriture dans les tables correspondantes. Vous pouvez stocker et indexer les données d’ordre de manière asynchrone. Les commandes sont placées en stockage temporaire et déplacées en masse vers la grille Order Management sans collision. Vous pouvez activer cette option à partir de **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Pour plus d’informations, voir [Mises à jour de grille planifiées](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) dans le _Guide de l’utilisateur d’administration_.

>[!WARNING]
>
>L’onglet **[!UICONTROL Developer]** et les options ne sont disponibles que dans le [mode Développeur](../configuration/cli/set-mode.md). [Adobe Commerce sur l’infrastructure cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ne prend pas en charge le mode `Developer`.

## Enregistrement de la configuration asynchrone

Pour les projets avec un grand nombre de configurations au niveau du magasin, l’enregistrement d’une configuration de magasin peut prendre un temps démesuré ou entraîner un délai d’expiration. Le module _de configuration asynchrone_ active des enregistrements de configuration asynchrones en exécutant une tâche cron qui utilise un client pour traiter l’enregistrement dans une file d’attente de messages. AsyncConfig est **désactivé** par défaut.

Vous pouvez activer AsyncConfig à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --config-async 1
```

La commande `set` écrit ce qui suit dans le fichier `app/etc/env.php` :

```conf
...
   'config' => [
       'async' => 1
   ]
```

Démarrez le client suivant pour commencer à traiter les messages de la file d’attente en fonction du premier entré dans la file d’attente :

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Mise à jour différée du stock

En période de ventes intensives, [!DNL Commerce] peut différer les mises à jour de stock liées aux commandes. Cela réduit le nombre d’opérations et accélère le processus de placement des commandes. Cependant, cette option est risquée et ne peut être utilisée que lorsque les commandes en arrière-plan sont activées dans le magasin, car cette option peut entraîner des quantités de stock négatives. Cette option peut améliorer considérablement les performances des flux de passage en caisse pour les magasins qui peuvent facilement reremplir leur stock à la demande. Pour activer les mises à jour de stock différées sur votre site, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Pour plus d’informations, voir [Gestion de l’inventaire](https://docs.magento.com/user-guide/catalog/inventory.html) dans le _Guide de l’utilisateur d’Adobe Commerce_.

>[!INFO]
>
>Cette option est disponible uniquement si **[!UICONTROL Backorder with any mode]** est activé.

>[!INFO]
>
>Cette option fonctionne également avec [Placement de commande asynchrone](high-throughput-order-processing.md#asynchronous-order-placement) en combinaison avec [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Paramètres d’optimisation côté client

Pour améliorer la réactivité du storefront de votre instance [!DNL Commerce], accédez à Admin en mode par défaut ou Développeur et modifiez les paramètres suivants :

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer] :**

| Groupe de paramètres | Paramètre | Valeur |
| ------------------- | -------------------------- | ------ |
| Paramètres de grille | Indexation asynchrone | Activer |
| Paramètres CSS | Minimisation des fichiers CSS | Oui |
| [!DNL JavaScript] Paramètres | Minimiser les fichiers [!DNL JavaScript] | Oui |
| [!DNL JavaScript] Paramètres | Activer le regroupement [!DNL JavaScript] | Oui |
| Paramètres des modèles | Minimiser l’HTML | Oui |

>[!INFO]
>
>L’onglet **[!UICONTROL Developer]** et les options ne sont disponibles que dans le [mode Développeur](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce]  sur l’infrastructure cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ne prend pas en charge le mode `Developer`.

Lorsque vous activez l’option **[!UICONTROL Enable [!DNL JavaScript] Bundling]**, vous autorisez Commerce à fusionner toutes les ressources JS en un ou un ensemble de lots chargés dans les pages de storefront. Le regroupement de JS entraîne une diminution du nombre de requêtes envoyées au serveur, ce qui améliore les performances des pages. Cela permet également de mettre en cache les ressources JS du navigateur lors du premier appel et de les réutiliser pour toute autre navigation. Cette option apporte également une évaluation différée, car tous les JS sont chargés en tant que texte. Elle n’effectue l’analyse et l’évaluation du code qu’après le déclenchement d’actions spécifiques sur la page. Cependant, ce paramètre n’est pas recommandé pour les magasins où le premier temps de chargement de page est extrêmement critique, car tout le contenu JS sera chargé lors du premier appel.

>[!INFO]
>
>Pour plus d’informations sur l’optimisation des fichiers CSS et Javascript sur Adobe Commerce sur l’infrastructure cloud et Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) dans le Centre d’aide Adobe Commerce_, voir [Optimisation des fichiers CSS et Javascript.

### Conseils de regroupement

* Nous vous recommandons d’utiliser des outils tiers pour la minification et le regroupement (comme [r.js](https://requirejs.org/)). [!DNL Commerce] Les mécanismes natifs ne sont pas optimaux et sont fournis en tant qu’alternatives de secours.
* L’activation du protocole HTTP/2 peut être une bonne alternative à l’utilisation du regroupement JS. Le protocole offre plusieurs des mêmes avantages. Elle est activée par défaut dans Adobe Commerce sur les projets d’infrastructure cloud.
* Il est déconseillé d’utiliser des paramètres obsolètes tels que la fusion de fichiers JS et CSS, car ils ont été conçus uniquement pour les fichiers JS chargés de manière synchrone dans la section HEAD de la page. L’utilisation de cette technique peut entraîner le regroupement et entraîner un mauvais fonctionnement de la logique JS.

## Validation des segments client

Les commerçants qui ont un grand nombre de [segments de clients](https://docs.magento.com/user-guide/marketing/customer-segments.html) peuvent rencontrer une dégradation significative des performances avec des actions de clients, comme la connexion client et l’ajout de produits au panier.

Les actions des clients déclenchent un processus de validation pour les segments de clients, ce qui peut entraîner une dégradation des performances. Par défaut, Adobe Commerce valide chaque segment en temps réel afin de définir les segments clients qui correspondent et ceux qui ne le sont pas.

Pour éviter une dégradation des performances, vous pouvez définir l’option de configuration du système **[!UICONTROL Real-time Check if Customer is Matched by Segment]** sur **Non** pour valider les segments de clients par une seule requête SQL de condition combinée.

Pour activer cette optimisation, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Ce paramètre améliore les performances de la validation des segments de clients s’il existe de nombreux segments de clients dans le système. Cependant, il ne fonctionne pas avec les implémentations [split database](../configuration/storage/multi-master.md) ou lorsqu’il n’y a aucun client enregistré.

## Planning de maintenance de la base de données {#database}

Nous vous recommandons d’effectuer des sauvegardes périodiques de la base de données pour vos instances d’évaluation et de production. En raison de la nature intensive des E/S des opérations de sauvegarde, vous pouvez rencontrer des sauvegardes plus lentes et des problèmes potentiels. L’exécution simultanée de processus de base de données pour plusieurs environnements peut s’exécuter plus lentement en raison d’une simultanéité des ressources disponibles.

Pour de meilleures performances, planifiez l’exécution de vos sauvegardes les unes après les autres, une par une, aux heures creuses. Cette méthode permet d’éviter les conflits d’E/S et de réduire le temps d’exécution, en particulier pour les petites instances, les bases de données volumineuses, etc.

Par exemple, nous vous recommandons de planifier une sauvegarde de votre base de données de production suivie de la base de données intermédiaire lorsque vos magasins rencontrent des visites inférieures.

## Limiter le nombre de produits dans la grille

Pour améliorer les performances de la grille de produits pour les catalogues volumineux, nous vous recommandons de limiter le nombre de produits dans la grille avec le paramètre de configuration système **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** .

Ce paramètre de configuration du système est désactivé par défaut. En l’activant, vous pouvez limiter le nombre de produits dans la grille à une valeur spécifique. **[!UICONTROL Records Limit]** est un paramètre personnalisable dont la valeur minimale par défaut est `20000`.
Lorsque le paramètre **[!UICONTROL Limit Number of Products in Grid]** est activé et que le nombre de produits dans la grille est supérieur à la limite d’enregistrements, la collecte limitée d’enregistrements est renvoyée. Lorsque la limite est atteinte, le nombre total d’enregistrements trouvés, le nombre d’enregistrements sélectionnés et les éléments de pagination sont masqués dans l’en-tête de la grille.

Lorsque le nombre total de produits dans la grille est limité, cela n’affecte pas les actions de masse de la grille de produits. Elle affecte uniquement la couche de présentation de la grille de produit. Par exemple, il y a un nombre limité de produits `20000` dans la grille, l’utilisateur clique sur **[!UICONTROL Select All]**, sélectionne l’action de masse **[!UICONTROL Update attributes]** et met à jour certains attributs. Par conséquent, tous les produits sont mis à jour, et non la collection limitée d’enregistrements `20000`.

La limitation de la grille de produit affecte uniquement les collections de produits utilisées par les composants de l’interface utilisateur. Par conséquent, toutes les grilles de produits ne sont pas affectées par cette limitation. Uniquement celles qui utilisent `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Vous pouvez limiter les collections de grille de produits aux pages suivantes uniquement :

* Grille de produits du catalogue
* Ajouter une grille de produits connexes/à vente croisée/à vente croisée
* Ajout de produits à un produit groupé
* Ajout de produits au groupe
* Page de création de commande de l’administrateur

Si vous ne souhaitez pas que votre grille de produits soit limitée, nous vous encourageons à utiliser des filtres plus précis pour que la collection de résultats ait moins d’éléments que **[!UICONTROL Records Limit]**.
