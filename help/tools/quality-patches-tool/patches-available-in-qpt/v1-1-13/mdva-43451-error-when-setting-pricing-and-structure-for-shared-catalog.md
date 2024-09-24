---
title: 'MDVA-43451 : erreur lors de la définition des tarifs et de la structure pour le catalogue partagé'
description: Le correctif MDVA-43451 résout le problème où l’utilisateur ne parvient pas à définir les tarifs et la structure d’un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-43451. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: Catalog Management
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-43451 : erreur lors de la définition des tarifs et de la structure pour le catalogue partagé

Le correctif MDVA-43451 résout le problème où l’utilisateur ne parvient pas à définir les tarifs et la structure d’un catalogue partagé. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID de correctif est MDVA-43451. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’utilisateur ne peut pas définir les tarifs et la structure pour un catalogue partagé. Le message suivant s’affiche : *Le magasin demandé est introuvable. Vérifiez le magasin et réessayez.*

<u>Étapes à reproduire</u> :

1. Créez un site web personnalisé. Les identifiants des sites web doivent être 0, 1, 2.
1. Créez un magasin sous le site web ci-dessus. Les identifiants des magasins doivent être 0,1,2.
1. Créez trois vues de magasin pour le magasin ci-dessus. Les identifiants des vues de magasin doivent être 0,1, 2, 3 et 4.
1. Supprimez la vue magasin avec l’identifiant 2. Le tableau du magasin doit maintenant ressembler au tableau ci-dessous.

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

Vous ne pouvez pas enregistrer le catalogue partagé. L&#39;erreur suivante s&#39;affiche :
*Le magasin demandé est introuvable. Vérifiez le magasin et réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
