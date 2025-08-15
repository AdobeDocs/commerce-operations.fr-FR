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

## Tâches cron

Toutes les opérations asynchrones dans [!DNL Commerce] sont effectuées à l’aide de la commande Linux `cron`. Voir [Configurer et exécuter cron](../configuration/cli/configure-cron-jobs.md) pour le configurer correctement.

## Indexeurs

Un indexeur peut s’exécuter en mode **[!UICONTROL Update on Save]** ou **[!UICONTROL Update on Schedule]**. Le mode **[!UICONTROL Update on Save]** effectue immédiatement l’indexation à chaque modification de votre catalogue ou d’autres données. Ce mode suppose une faible intensité des opérations de mise à jour et de navigation dans votre boutique. Cela peut entraîner des retards importants et une indisponibilité des données lors de charges élevées. Nous vous recommandons d’utiliser l’option **Mise à jour selon le calendrier** à des fins de performances, car elle stocke des informations sur les mises à jour de données et effectue l’indexation par parties en arrière-plan via une tâche cron spécifique. Vous pouvez modifier le mode de chaque indexeur de [!DNL Commerce] séparément sur la page de configuration **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** . L’index [!UICONTROL Customer Grid] doit toujours être défini sur le mode **[!UICONTROL Update on Save]**.

>[!TIP]
>
>La réindexation sur MariaDB 10.4 et 10.6 prend plus de temps que les autres versions de MariaDB ou [!DNL MySQL]. Nous vous suggérons de modifier le paramètre de configuration MariaDB par défaut, qui est décrit dans la [conditions préalables à l’installation](../installation/prerequisites/database/mysql.md).

## Caches

Lorsque vous lancez votre boutique en production, activez tous les caches à partir de la page **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** . Nous vous recommandons vivement d’utiliser [!DNL Varnish], car il s’agit d’une solution efficace de mise en cache des pages de production.

## Notifications par e-mail asynchrones

L’activation du paramètre « Notifications par e-mail asynchrones » déplace les processus qui gèrent le passage en caisse et le traitement des notifications par e-mail vers l’arrière-plan. Pour activer cette fonctionnalité, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Voir [E-mails commerciaux](https://experienceleague.adobe.com/fr/docs/commerce-admin/config/sales/sales-emails) dans le _Guide d’utilisation destiné à l’administrateur_ pour plus d’informations.

## Traitement de données de commande asynchrone

Il peut arriver que des ventes intensives sur un storefront se produisent en même temps que [!DNL Commerce] effectue un traitement intensif des commandes. Vous pouvez configurer [!DNL Commerce] pour distinguer ces deux modèles de trafic au niveau de la base de données afin d’éviter les conflits entre les opérations de lecture et d’écriture dans les tables correspondantes. Vous pouvez stocker et indexer les données de commande de manière asynchrone. Les commandes sont placées en stockage temporaire et déplacées en bloc vers la grille Order Management sans aucun conflit. Vous pouvez activer cette option à partir de **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Voir [Mises à jour planifiées de la grille](https://experienceleague.adobe.com/fr/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) dans le _Guide d’utilisation de l’administrateur_ pour plus d’informations.

>[!WARNING]
>
>L’onglet **[!UICONTROL Developer]** et les options ne sont disponibles qu’en [mode Développeur](../configuration/cli/set-mode.md). [Adobe Commerce sur l’infrastructure cloud](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) ne prend pas en charge le mode `Developer`.

## Enregistrement asynchrone de la configuration

Pour les projets comportant un grand nombre de configurations au niveau du magasin, l’enregistrement d’une configuration de magasin peut prendre un temps excessif ou entraîner une expiration du délai. Le module _Configuration asynchrone_ permet des enregistrements de configuration asynchrones en exécutant une tâche cron qui utilise un client pour traiter l’enregistrement dans une file d’attente de messages. AsyncConfig est **désactivé** par défaut.

Vous pouvez activer AsyncConfig à l’aide de l’interface de ligne de commande :

```bash
bin/magento setup:config:set --config-async 1
```

La commande `set` écrit les éléments suivants dans le fichier `app/etc/env.php` :

```conf
...
   'config' => [
       'async' => 1
   ]
```

Démarrez le client suivant pour commencer à traiter les messages de la file d’attente selon le principe du premier entré, premier sorti :

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Mise à jour des stocks différée

En période de ventes intensives, [!DNL Commerce] pouvez différer les mises à jour des stocks liées aux commandes. Cela réduit le nombre d’opérations et accélère le processus de passation de commande. Cependant, cette option est risquée et ne peut être utilisée que lorsque les reliquats sont activés dans le magasin, car elle peut entraîner des quantités de stock négatives. Cette option peut améliorer considérablement les performances des flux de passage en caisse pour les magasins qui peuvent facilement remplir à nouveau leur stock à la demande. Pour activer les mises à jour de stock différées sur votre site, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Pour plus d’informations, consultez [Gestion des stocks](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) dans le _Guide de l’utilisateur d’Adobe Commerce_.

>[!INFO]
>
>Cette option n’est disponible que si **[!UICONTROL Backorder with any mode]** est activé.

>[!INFO]
>
>Cette option fonctionne également avec [placement asynchrone des commandes](high-throughput-order-processing.md#asynchronous-order-placement) en combinaison avec [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html?lang=fr).

## Paramètres d’optimisation côté client

Pour améliorer la réactivité du storefront de votre instance [!DNL Commerce], accédez à Admin en mode par défaut ou Développeur et modifiez les paramètres suivants :

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Groupe de paramètres | Paramètre | Valeur |
| ------------------- | -------------------------- | ------ |
| Paramètres de grille | Indexation asynchrone | Activer |
| Paramètres CSS | Minimiser les fichiers CSS | Oui |
| [!DNL JavaScript] Settings | Minimiser les fichiers [!DNL JavaScript] | Oui |
| [!DNL JavaScript] Settings | Activer le regroupement [!DNL JavaScript] | Oui |
| Paramètres de modèle | Minimisation d’HTML | Oui |

>[!INFO]
>
>L’onglet **[!UICONTROL Developer]** et les options ne sont disponibles qu’en [mode Développeur](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] sur l’infrastructure cloud](https://experienceleague.adobe.com/fr/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) ne prend pas en charge le mode `Developer`.

Lorsque vous activez l’option **[!UICONTROL Enable [!DNL JavaScript] Bundling]**, vous autorisez Commerce à fusionner toutes les ressources JS en un ou plusieurs lots chargés dans les pages de storefront. Le regroupement de JS entraîne une diminution des requêtes au serveur, ce qui améliore les performances de la page. Il permet également au navigateur de mettre en cache les ressources JS lors du premier appel et de les réutiliser pour toutes les recherches ultérieures. Cette option permet également une évaluation différée, car tout le code JS est chargé en tant que texte. Il ne lance l’analyse et l’évaluation du code qu’après le déclenchement d’actions spécifiques sur la page. Cependant, ce paramètre n’est pas recommandé pour les magasins où le temps de chargement de la première page est extrêmement critique, car tout le contenu JS sera chargé lors du premier appel.

>[!INFO]
>
>Voir [Optimisation des fichiers CSS et Javascript sur Adobe Commerce sur l’infrastructure cloud et Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) dans le Centre d’aide Adobe Commerce_ pour plus d’informations sur l’optimisation des fichiers CSS et Javascript.

### Conseils sur le regroupement

* Nous vous recommandons d’utiliser des outils tiers pour la minimisation et le regroupement (comme [r.js](https://requirejs.org/)). [!DNL Commerce] mécanismes intégrés ne sont pas optimaux et sont fournis en tant qu’alternatives de secours.
* L’activation du protocole HTTP/2 peut être une bonne alternative à l’utilisation du regroupement JS. Le protocole offre plusieurs des mêmes avantages. Elle est activée par défaut dans Adobe Commerce pour les projets d’infrastructure cloud.
* Nous vous déconseillons d’utiliser des paramètres obsolètes, tels que la fusion de fichiers JS et CSS, car ils ont été conçus uniquement pour le chargement synchrone de fichiers JS dans la section HEAD de la page. L’utilisation de cette technique peut entraîner un regroupement et un fonctionnement incorrect de la logique JS.

## Validation des segments client

Les commerçants qui ont un grand nombre de [segments de clients](https://experienceleague.adobe.com/fr/docs/commerce-admin/customers/segments/customer-segments) peuvent subir une dégradation significative des performances avec les actions des clients, telles que la connexion du client et l’ajout de produits au panier.

Les actions des clients déclenchent un processus de validation pour les segments de clientèle, ce qui peut entraîner une dégradation des performances. Par défaut, Adobe Commerce valide chaque segment en temps réel afin de définir les segments de clients qui correspondent et ceux qui ne correspondent pas.

Pour éviter une dégradation des performances, vous pouvez définir l’option de configuration du système de **[!UICONTROL Real-time Check if Customer is Matched by Segment]** sur **Non** afin de valider les segments clients à l’aide d’une seule requête SQL à condition combinée.

Pour activer cette optimisation, accédez à **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Ce paramètre améliore les performances de la validation des segments clients s’il y a de nombreux segments clients dans le système. Toutefois, il ne fonctionne pas avec les implémentations [base de données partagée](../configuration/storage/multi-master.md) ou lorsqu’il n’y a aucun client enregistré.

## Planning de maintenance de la base de données {#database}

Nous vous recommandons d’effectuer des sauvegardes périodiques des bases de données de vos instances d’évaluation et de production. En raison de la nature intensive en E/S des opérations de sauvegarde, vous pouvez rencontrer des sauvegardes plus lentes et des problèmes potentiels. L’exécution simultanée de processus de base de données pour plusieurs environnements peut être plus lente en raison de la contention des ressources disponibles.

Pour de meilleures performances, planifiez vos sauvegardes pour qu’elles s’exécutent successivement, une à la fois, aux heures creuses. Cette méthode évite les conflits d’E/S et réduit le temps d’exécution, en particulier pour les instances plus petites, les bases de données plus volumineuses, etc.

Par exemple, nous vous recommandons de planifier une sauvegarde de votre base de données de production suivie d’une sauvegarde de la base de données intermédiaire lorsque vos magasins rencontrent des visites inférieures.

## Limiter le nombre de produits dans la grille

Pour améliorer les performances de la grille de produits pour les catalogues volumineux, il est recommandé de limiter le nombre de produits dans la grille à l’aide du paramètre de configuration système **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]**.

Ce paramètre de configuration système est désactivé par défaut. En l’activant, vous pouvez limiter le nombre de produits dans la grille à une valeur spécifique. **[!UICONTROL Records Limit]** paramètre est personnalisable et sa valeur minimale par défaut est de `20000`.
Lorsque le paramètre **[!UICONTROL Limit Number of Products in Grid]** est activé et que le nombre de produits dans la grille est supérieur à la limite d’enregistrements, la collection limitée d’enregistrements est renvoyée. Lorsque la limite est atteinte, le nombre total d’enregistrements trouvés, le nombre d’enregistrements sélectionnés et les éléments de pagination sont masqués dans l’en-tête de grille.

Lorsque le nombre total de produits dans la grille est limité, les actions de masse de la grille de produits ne sont pas affectées. Cela affecte uniquement le calque de présentation de la grille de produits. Par exemple, si la grille contient un nombre limité de produits `20000`, l’utilisateur clique sur **[!UICONTROL Select All]**, sélectionne l’action de masse **[!UICONTROL Update attributes]** et met à jour un ou plusieurs attributs. Par conséquent, tous les produits sont mis à jour, et non la collection limitée d’enregistrements `20000`.

La limitation de la grille de produits affecte uniquement les collections de produits utilisées par les composants de l’interface utilisateur. Par conséquent, toutes les grilles de produits ne sont pas affectées par cette limitation. Uniquement ceux qui utilisent `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Vous pouvez limiter les collections de grille de produits aux pages suivantes uniquement :

* Grille de produits du catalogue
* Ajout D’Une Grille De Produits Associés/De Vente De Produits De Niveau Supérieur/De Vente Croisée
* Ajouter des produits à l’offre groupée
* Ajouter des produits au groupe de produits
* Page Créer une commande par l’administrateur

Si vous ne souhaitez pas que votre grille de produits soit limitée, nous vous encourageons à utiliser des filtres plus précisément pour que la collection de résultats contienne moins d’éléments que **[!UICONTROL Records Limit]**.
