---
title: Bonnes pratiques de configuration
description: Optimisez le temps de réponse de votre déploiement Adobe Commerce à l’aide de ces bonnes pratiques.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# Bonnes pratiques de configuration

Commerce fournit de nombreux paramètres et outils que vous pouvez utiliser pour améliorer le temps de réponse sur les pages et fournir un débit plus élevé.

## Tâches Cron

Toutes les opérations asynchrones dans [!DNL Commerce] sont effectuées à l’aide de la commande Linux `cron` . Voir [Configuration et exécution de cron](../configuration/cli/configure-cron-jobs.md) pour le configurer correctement.

## Indexeurs

Un indexeur peut s’exécuter en mode **[!UICONTROL Update on Save]** ou **[!UICONTROL Update on Schedule]** . Le **[!UICONTROL Update on Save]** mode indexe immédiatement chaque fois que votre catalogue ou d’autres données changent. Ce mode suppose une faible intensité des opérations de mise à jour et de navigation dans votre magasin. Cela peut entraîner des retards importants et une indisponibilité des données lors de charges élevées. Nous vous recommandons d’utiliser **Mettre à jour sur la planification** à des fins de performances, car il stocke des informations sur les mises à jour des données et effectue l’indexation par des parties en arrière-plan par le biais d’une tâche cron spécifique. Vous pouvez modifier le mode de chaque indexeur [!DNL Commerce] séparément sur la page de configuration **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** . L’index [!UICONTROL Customer Grid] doit toujours être défini sur le mode **[!UICONTROL Update on Save]**.

>[!TIP]
>
>La réindexation sur MariaDB 10.4 et 10.6 prend plus de temps que les autres versions de MariaDB ou de [!DNL MySQL]. Nous vous suggérons de modifier le paramètre de configuration MariaDB par défaut, décrit dans les conditions préalables[&#128279;](../installation/prerequisites/database/mysql.md) à l’installation.

## Caches

Lorsque vous lancez votre magasin en production, activez tous les caches à partir de la page **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** . Nous vous recommandons vivement d’utiliser [!DNL Varnish], car il s’agit d’une solution efficace de cache de page de production.

## Notifications électroniques asynchrones

L’activation du paramètre &quot;Notifications par e-mail asynchrones&quot; déplace les processus qui gèrent l’extraction et le traitement des notifications par e-mail en arrière-plan. Pour activer cette fonctionnalité, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Pour plus d’informations, voir [Courriers électroniques](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails) du service commercial dans le Guide _d’utilisation de l’administrateur_.

## Traitement asynchrone des données de commande

Il peut y avoir des moments où les ventes intensives sur une vitrine se produisent en même temps que [!DNL Commerce] le traitement intensif des commandes. Vous pouvez configurer [!DNL Commerce] pour distinguer ces deux modèles de trafic au niveau de la base de données afin d’éviter les conflits entre les opérations de lecture et d’écriture dans les tables correspondantes. Vous pouvez stocker et indexer les données de commande de manière asynchrone. Les commandes sont placées en stockage temporaire et déplacées en vrac vers la grille de gestion des commandes sans aucune collision. Vous pouvez activer cette option à partir de **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Pour plus d’informations, voir [Mises à jour](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) planifiées de la grille dans le Guide _d’utilisation de l’administrateur_.

>[!WARNING]
>
>L’onglet et les **[!UICONTROL Developer]** options ne sont disponibles qu’en [mode](../configuration/cli/set-mode.md) Développeur. [Adobe Commerce sur l’infrastructure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) cloud ne prend pas en charge `Developer` le mode.

## Enregistrement de configuration asynchrone

Pour les projets avec un grand nombre de configurations au niveau du magasin, l’enregistrement d’une configuration de magasin peut prendre un temps excessif ou entraîner un délai d’expiration. Le _module de configuration_ asynchrone active les sauvegardes de configuration asynchrone en exécutant une tâche cron qui utilise un consommateur pour traiter la sauvegarde dans une file d’attente de messages. AsyncConfig est **désactivé** par défaut.

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

En période de ventes intensives, [!DNL Commerce] peut différer les mises à jour de stock liées aux commandes. Cela réduit le nombre d’opérations et accélère le processus de placement des commandes. Cependant, cette option est risquée et ne peut être utilisée que lorsque les commandes en arrière-plan sont activées dans le magasin, car cette option peut entraîner des quantités de stock négatives. Cette option peut apporter une amélioration significative des performances sur les flux de paiement pour les magasins qui peuvent facilement remplir leur stock à la demande. Pour activer les mises à jour différées sur votre site, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Pour plus d’informations, consultez [Gestion des stocks](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) dans le Guide _de_ l’utilisateur de Adobe Commerce.

>[!INFO]
>
>Cette option n’est disponible que si **[!UICONTROL Backorder with any mode]** elle est activée.

>[!INFO]
>
>Cette option fonctionne également avec [le placement](high-throughput-order-processing.md#asynchronous-order-placement) de commande asynchrone en combinaison avec [la gestion des](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html) stocks.

## Paramètres d’optimisation côté client

Pour améliorer la réactivité de la vitrine de votre [!DNL Commerce] instance, accédez à l’administrateur en mode Par défaut ou Développeur et modifiez les paramètres suivants :

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Groupe de paramètres | Réglage | Valeur |
| ------------------- | -------------------------- | ------ |
| Paramètres de grille | Indexation asynchrone | Activer |
| Paramètres CSS | Minimisation des fichiers CSS | Oui |
| [!DNL JavaScript] Paramètres | Fichiers [!DNL JavaScript] de réduction | Oui |
| [!DNL JavaScript] Paramètres | Activer [!DNL JavaScript] le regroupement | Oui |
| Paramètres des modèles | Réduire HTML | Oui |

>[!INFO]
>
>L’onglet et les **[!UICONTROL Developer]** options ne sont disponibles qu’en [mode](../configuration/cli/set-mode.md) Développeur. [ [!DNL Commerce] Adobe sur l’infrastructure](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) cloud ne prend pas en charge `Developer` le mode.

Lorsque vous activez l’option **[!UICONTROL Enable [!DNL JavaScript] Bundling]** , vous autorisez Commerce à fusionner toutes les ressources JS en un ou un ensemble de bundles chargés dans les pages de vitrine. Le regroupement de JS réduit le nombre de demandes au serveur, ce qui améliore les performances des pages. Il aide également le navigateur à mettre en cache les ressources JS lors du premier appel et à les réutiliser pour toute navigation ultérieure. Cette option apporte également une évaluation différée, car tout le JS est chargé sous forme de texte. Elle n’effectue l’analyse et l’évaluation du code qu’après le déclenchement d’actions spécifiques sur la page. Cependant, ce paramètre n’est pas recommandé pour les magasins où le premier temps de chargement de page est extrêmement critique, car tout le contenu JS sera chargé lors du premier appel.

>[!INFO]
>
>Pour plus d’informations sur l’optimisation des fichiers CSS et Javascript sur Adobe Commerce sur l’infrastructure cloud et Adobe Commerce[&#128279;](https://support.magento.com/hc/en-us/articles/360044482152) dans le Centre d’aide Adobe Commerce_, voir Optimisation des fichiers CSS et Javascript.

### Conseils de regroupement

* Nous vous recommandons d’utiliser des outils tiers pour la minification et le regroupement (comme [r.js](https://requirejs.org/)). [!DNL Commerce] Les mécanismes natifs ne sont pas optimaux et sont fournis en tant qu’alternatives de secours.
* L’activation du protocole HTTP/2 peut être une bonne alternative à l’utilisation du regroupement JS. Le protocole offre bon nombre des mêmes avantages. Elle est activée par défaut dans Adobe Commerce sur les projets d’infrastructure cloud.
* Nous vous déconseillons d’utiliser des paramètres obsolètes tels que la fusion de fichiers JS et CSS, car ils ont été conçus uniquement pour le JS chargé de manière synchrone dans la section HEAD de la page. L’utilisation de cette technique peut entraîner le regroupement et entraîner un mauvais fonctionnement de la logique JS.

## Validation des segments client

Les commerçants qui ont un grand nombre de [segments de clients](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) peuvent rencontrer une dégradation significative des performances avec des actions de clients, comme la connexion client et l’ajout de produits au panier.

Les actions des clients déclenchent un processus de validation pour les segments de clients, ce qui peut entraîner une dégradation des performances. Par défaut, Adobe Commerce valide chaque segment en temps réel pour définir quels segments de clientèle correspondent et lesquels ne le sont pas.

Pour éviter une dégradation des performances, vous pouvez définir l’option de configuration du système sur **Non** pour valider les **[!UICONTROL Real-time Check if Customer is Matched by Segment]** segments de clients par une seule requête SQL de condition combinée.

Pour activer cette optimisation, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Ce paramètre améliore les performances de la validation des segments de clients s’il existe de nombreux segments de clients dans le système. Cependant, il ne fonctionne pas avec les implémentations [split database](../configuration/storage/multi-master.md) ou lorsqu’il n’y a aucun client enregistré.

## Planning de maintenance de la base de données {#database}

Nous vous recommandons d’effectuer des sauvegardes de base de données périodiques pour vos instances d’évaluation et de production. En raison de la nature gourmande en E/S des opérations de sauvegarde, vous pouvez rencontrer des sauvegardes plus lentes et des problèmes potentiels. L’exécution simultanée de processus de base de données pour plusieurs environnements peut s’exécuter plus lentement en raison de conflits pour les ressources disponibles.

Pour de meilleures performances, planifiez vos sauvegardes pour qu’elles s’exécutent successivement, une à la fois, aux heures creuses. Cette méthode évite les conflits d’E/S et réduit le temps d’exécution, en particulier pour les petites instances, les bases de données plus volumineuses, etc.

Par exemple, nous vous recommandons de planifier une sauvegarde de votre base de données de production suivie par la base de données d’évaluation lorsque vos magasins rencontrent moins de visites.

## Limiter le nombre de produits dans la grille

Pour améliorer les performances de la grille de produits pour les catalogues volumineux, nous vous recommandons de limiter le nombre de produits dans la grille avec le **[!UICONTROL Stores]paramètre > [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > > [!UICONTROL Admin Grids][!UICONTROL Limit Number of Products in Grid]** configuration du système.

Ce paramètre de configuration système est désactivé par défaut. En l’activant, vous pouvez limiter le nombre de produits dans la grille à une valeur spécifique. **[!UICONTROL Records Limit]** est un paramètre personnalisable dont la valeur minimale par défaut est de `20000`.
Lorsque le **[!UICONTROL Limit Number of Products in Grid]** paramètre est activé et que le nombre de produits dans la grille est supérieur à la limite d’enregistrement, la collection limitée d’enregistrements est renvoyée. Lorsque la limite est atteinte, le nombre total d’enregistrements trouvés, le nombre d’enregistrements sélectionnés et les éléments de pagination sont masqués dans l’en-tête de la grille.

Lorsque le nombre total de produits dans le réseau est limité, cela n’affecte pas les actions de masse de la grille de produits. Cela affecte uniquement la couche de présentation de la grille de produits. Par exemple, il y a un nombre limité de `20000` produits dans la grille, l’utilisateur clique sur **[!UICONTROL Select All]**, sélectionne l’action **[!UICONTROL Update attributes]** de masse et met à jour certains attributs. Par conséquent, tous les produits sont mis à jour, et non la collection limitée d’enregistrements `20000`.

La limitation de la grille de produits affecte uniquement les collections de produits utilisées par les composants de l’interface utilisateur. Par conséquent, toutes les grilles de produits ne sont pas concernées par cette limitation. Uniquement celles qui utilisent `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Vous pouvez limiter les collections de grille de produits aux pages suivantes uniquement :

* Grille de produits du catalogue
* Ajouter une grille de produits connexes/à vente croisée/à vente croisée
* Ajout de produits à un produit groupé
* Ajouter des produits au groupe Produit
* Admin Créer la page de commande

Si vous ne souhaitez pas que votre grille de produits soit limitée, nous vous encourageons à utiliser des filtres plus précisément pour que la collection de résultats ait moins d’articles que **[!UICONTROL Records Limit]**.
