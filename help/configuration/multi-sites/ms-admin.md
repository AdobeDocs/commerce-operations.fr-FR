---
title: Configurer plusieurs sites web, boutiques et vues de boutique dans l’Administration
description: Configurez d’autres sites web, boutiques et vues de boutique dans l’administration Commerce.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# Configurer plusieurs vues dans l’Admin

Cette tâche nécessite la création d’une catégorie racine (et de catégories supplémentaires, le cas échéant) pour chaque magasin. Les tâches décrites dans cette rubrique fournissent un moyen de configurer plusieurs magasins. Pour plus d’informations, consultez les ressources suivantes dans le Guide de l’utilisateur de Commerce :

- [Catégories](https://experienceleague.adobe.com/fr/docs/commerce-admin/catalog/categories/categories)
- [Ajout de sites web](https://experienceleague.adobe.com/fr/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [URL de magasin](https://experienceleague.adobe.com/fr/docs/commerce-admin/stores-sales/site-store/store-urls)
- [Contenu](https://experienceleague.adobe.com/fr/docs/commerce-admin/content-design/content-menu)

>[!INFO]
>
>À titre d’exemple uniquement, nous utilisons un site web français avec le code de site web `french` dans cette rubrique. Pour des tutoriels détaillés, voir [Tutoriel : configurer plusieurs sites web avec Apache](ms-apache.md) et [Tutoriel : configurer plusieurs sites web avec nginx](ms-nginx.md)

## Étape 1 : créer des catégories racine

La création d’une catégorie racine est facultative, mais nous montrons comment la créer dans ce tutoriel si vous souhaitez que chaque site web ait une catégorie racine unique. Vous pouvez créer des catégories supplémentaires si vous le souhaitez.

Pour créer une catégorie racine, procédez comme suit :

1. Connectez-vous à l’administrateur en tant qu’utilisateur autorisé à créer des catégories.
1. Cliquez sur **Catalogue** > **Catégories**.
1. Cliquez sur **Ajouter une catégorie racine**.
1. Dans le champ **Nom de la catégorie**, saisissez un nom unique pour identifier cette catégorie.
1. Assurez-vous que l’option Activer la catégorie est définie sur **Oui**.

   Pour plus d’informations sur les autres options de cette page, voir [Catégories racine](https://experienceleague.adobe.com/fr/docs/commerce-admin/catalog/categories/category-root).

   La figure suivante en est un exemple.

   ![Créer et activer une catégorie racine](../../assets/configuration/add-root-category.png)

1. Cliquez sur **Enregistrer**.
1. Répétez ces tâches autant de fois que nécessaire pour créer des catégories racine pour vos magasins.

## Étape 2 : créer des sites web

Pour créer un site web, procédez comme suit :

1. Connectez-vous à l’administrateur en tant qu’utilisateur autorisé à créer des sites web, des boutiques et des vues de boutique.
1. Cliquez sur **Magasins** > **Paramètres** > **Tous les magasins**.
1. Sur la page _Boutiques_, cliquez sur **Créer un site web**.

   - **Nom** : saisissez un nom pour identifier le site Web.
   - **Code**—Saisissez un code unique ; par exemple, si vous avez un magasin français, vous pouvez saisir `french`
   - **Ordre de tri** : entrez un ordre de tri numérique facultatif.

   La figure suivante en est un exemple.

   ![Ajouter un site web](../../assets/configuration/multi-site-website.png)

1. Cliquez sur **Enregistrer le site web**.
1. Répétez ces tâches autant de fois que nécessaire pour créer vos sites web.

## Étape 3 : créer des magasins

Pour créer un magasin :

1. Dans le panneau _Admin_, cliquez sur **Magasins** > **Paramètres** > **Tous les magasins**.
1. Sur la page _Magasins_, cliquez sur **Créer un magasin**.

   - **Site Web** : cliquez sur le nom du site Web auquel associer ce magasin.
   - **Nom** : saisissez un nom pour identifier le magasin.
   - **Code** : saisissez un code unique pour identifier le magasin.
   - **Catégorie racine** : cliquez sur le nom de la catégorie racine de ce magasin.

   La figure suivante en est un exemple.

   ![Ajouter un magasin](../../assets/configuration/multi-site-store.png)

1. Cliquez sur **Enregistrer la boutique**.
1. Répétez ces tâches autant de fois que nécessaire pour créer vos magasins.

## Étape 4 : Créer des vues de magasin

Pour créer une vue de magasin :

1. Dans le panneau _Admin_, cliquez sur **Magasins** > **Paramètres** > **Tous les magasins**.
1. Sur la page Boutiques, cliquez sur **Créer une vue de boutique**.

   - **Boutique** : cliquez sur le nom de la boutique à laquelle associer cette vue de boutique.
   - **Nom** : saisissez un nom pour identifier cette vue de magasin.
   - **Code** : saisissez un nom unique pour identifier cette vue de magasin.
   - **Statut**—Sélectionnez **Activé**.

   La figure suivante en est un exemple.

   ![Ajouter un magasin](../../assets/configuration/multi-site-storeview.png)

1. Cliquez sur **Enregistrer la vue de la boutique**.
1. Répétez ces tâches autant de fois que nécessaire pour créer les vues de votre boutique.

## Étape 5 : modifier l’URL de base du site web

Pour accéder à un site web à l’aide d’une URL unique telle que `http://french.magento.mg`, vous devez modifier l’URL de base de chaque site dans l’Administration.

Pour modifier l’URL de base du site web :

1. Dans le panneau _Admin_, cliquez sur **Magasins** > **Paramètres** > **Configuration** > **Général** > **Web**.
1. Dans la liste **Affichage de la boutique** située en haut de la page, cliquez sur le nom de l’un de vos sites web, comme le montre la figure suivante.

   ![Sélectionner une portée](../../assets/configuration/multi-site-scope.png)

1. Dans le volet de droite, développez **URL de base**.
1. Dans la section _URL de base_, désélectionnez **Utiliser la valeur du système**.
1. Saisissez l’URL de `http://french.magento.mg` dans les champs **URL de base** et **URL du lien de base**.

1. Répétez l’étape précédente dans la section _URL de base (sécurisées)_.

   >[!INFO]
   >
   >Si vous configurez une URL de base pour le déploiement d’Adobe Commerce sur une infrastructure cloud, vous devez remplacer le premier point par trois tirets. Par exemple, si votre URL de base est `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, saisissez `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Si vous configurez une URL de base pour les tests locaux, utilisez un point.

1. Cliquez sur **Enregistrer la configuration**.

1. Répétez ces tâches pour d’autres sites web.

## Étape 6 : ajouter le code du magasin à l’URL de base

Commerce vous offre la possibilité d’ajouter le code du magasin à l’URL de base du site, ce qui simplifie le processus de configuration de plusieurs magasins. Avec cette option, il n’est pas nécessaire de créer des répertoires sur le système de fichiers Commerce pour stocker les `index.php` et les `.htaccess`.

Cela empêche `index.php` et `.htaccess` de se désynchroniser de la base de code Commerce lors des futures mises à niveau.

Voir le [Guide de l’utilisateur de Commerce](https://experienceleague.adobe.com/fr/docs/commerce-admin/stores-sales/site-store/store-urls).

Pour ajouter le code de magasin à l’URL de base :

1. Dans le panneau _Admin_, cliquez sur **Magasins** > **Paramètres** > **Configuration** > **Général** > **Web**.
1. Dans la liste **Affichage de la boutique** en haut de la page, cliquez sur **Configuration par défaut** comme le montre l’image suivante.

   ![Sélectionnez la portée de configuration par défaut](../../assets/configuration/multi-site-default.png)

1. Dans le volet de droite, développez **Options d’URL**.
1. Désélectionnez la case **Utiliser la valeur système** située en regard de _Ajouter le code du magasin aux URL_.
1. Dans la liste _Ajouter le code de la boutique aux URL_, cliquez sur **Oui**.

   ![Ajoutez le code de magasin à l’URL de base du magasin](../../assets/configuration/multi-site-add-store-url.png)

1. Cliquez sur **Enregistrer la configuration**.
1. Si vous y êtes invité, videz le cache. (**Système** > **Gestion du cache**).

## Étape 7 : modifier l’URL de base de la vue de magasin par défaut

Vous devez effectuer cette étape en dernier, car vous perdrez l’accès à l’administrateur ; votre accès sera rétabli après la configuration des hôtes virtuels, comme indiqué dans les rubriques spécifiques au serveur web.

Pour modifier l’URL de base de la vue de magasin par défaut :

1. Dans le panneau _Admin_, cliquez sur **Magasins** > **Paramètres** > **Configuration** > **Général** > **Web**.

1. Dans la liste _Affichage de la boutique_ en haut de la page, cliquez sur **Configuration par défaut**.

   ![Sélectionnez la portée de configuration par défaut](../../assets/configuration/multi-site-default.png)

1. Dans le volet de droite, développez **URL de base**.
1. Dans la section _URL de base_, désélectionnez **Utiliser la valeur du système**.
1. Saisissez l’URL de `http://magento.mg` dans les champs **URL de base** et **URL du lien de base**.

1. Répétez l’étape précédente dans la section **URL de base (sécurisées)**.

   >[!INFO]
   >
   >Si vous configurez une URL de base pour Adobe Commerce sur une infrastructure cloud, vous devez remplacer le premier point par trois tirets. Par exemple, si votre URL de base est `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, saisissez `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Cliquez sur **Enregistrer la configuration**.

>[!INFO]
>
>Le site web, le magasin et le code d’affichage du magasin peuvent uniquement inclure des lettres (a-z ou A-Z), des chiffres (0-9) et des traits de soulignement (_). En outre, le premier caractère doit être une lettre. Si des majuscules ou des majuscules sont utilisées, en interne la correspondance est insensible à la casse pour permettre le remplacement des paramètres de configuration par le biais de variables d’environnement. Voir [&#x200B; Utilisation de variables d’environnement pour remplacer les paramètres de configuration](../reference/override-config-settings.md#environment-variables).