---
title: 'MDVA-43451 : erreur lors de la définition de la tarification et de la structure pour le catalogue partagé'
description: Le correctif MDVA-43451 résout le problème en raison duquel l’utilisateur ne peut pas définir la tarification et la structure d’un catalogue partagé. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43451. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management
role: Admin
exl-id: 2cddfca2-ee32-4e73-9ef6-78125fbaa13d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-43451 : erreur lors de la définition de la tarification et de la structure pour le catalogue partagé

Le correctif MDVA-43451 résout le problème en raison duquel l’utilisateur ne peut pas définir la tarification et la structure d’un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-43451. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur ne peut pas définir la tarification et la structure d’un catalogue partagé. Le message suivant s’affiche : *Le magasin demandé est introuvable. Vérifiez le magasin et réessayez.*

<u>Procédure à suivre </u> :

1. Créez un site web personnalisé. Les identifiants des sites web doivent être 0, 1 et 2.
1. Créez un magasin sous le site web ci-dessus. Les identifiants des magasins doivent être 0,1,2.
1. Créez trois vues de magasin pour le magasin ci-dessus. Les ID des vues de magasin doivent être 0,1, 2, 3 et 4.
1. Supprimez la vue de magasin avec l’ID 2. Désormais, le tableau du magasin doit ressembler au tableau ci-dessous.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Créez un catalogue partagé.
1. Lors de la configuration du prix et de la structure, sélectionnez le magasin créé à l’étape 2.
1. Enregistrez le catalogue partagé.

<u>Résultats attendus</u> :

Le catalogue partagé est enregistré sans problème.

<u>Résultats réels</u> :

Vous ne pouvez pas enregistrer le catalogue partagé. L’erreur suivante s’affiche :
*Le magasin demandé est introuvable. Vérifiez le magasin et réessayez.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
