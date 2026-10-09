---
title: 'ACP2E-3753 : e-mails d’alerte de stock n’utilisant pas de modèles de thème spécifiques au magasin dans la configuration multi-magasin'
description: Appliquez le correctif ACP2E-3753 pour résoudre le problème d’Adobe Commerce où les e-mails d’alerte de produit dans une configuration multi-magasin sont toujours envoyés à l’aide du thème par défaut, quelle que soit la configuration du magasin ou du thème.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%
---
# ACP2E-3753 : e-mails d’alerte de stock n’utilisant pas de modèles de thème spécifiques au magasin dans la configuration multi-magasin

Le correctif ACP2E-3753 corrige le problème où les e-mails d’alerte de produit dans une configuration multi-magasin étaient toujours envoyés à l’aide du thème par défaut, quelle que soit la configuration du magasin ou du thème. Ce correctif est disponible lorsque la version 1.1.65 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACP2E-3753. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.5-p11

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Dans une configuration multi-magasin, les e-mails d’alerte de produit sont toujours envoyés à l’aide du thème par défaut, quelle que soit la configuration du magasin ou du thème.

<u>Procédure à suivre </u> :

1. Créez deux sites web, magasins et vues de magasin.
1. Créez deux thèmes distincts et affectez-les à différents magasins.
1. Le paramètre d’alerte du produit est la portée par défaut qui s’exécute chaque minute.
1. Remplacez/ajoutez du contenu au fichier `stock.phtml` pour les deux thèmes. Exemple d&#39;emplacement du fichier :

   ```text
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Créez un utilisateur pour chaque boutique et abonnez-vous à l’alerte de stock de produits .
1. Déclenchez l’alerte de stock de produits pour envoyer les e-mails.

<u>Résultats attendus</u> :

L’e-mail doit inclure les modifications au niveau du thème.

<u>Résultats réels</u> :

Les e-mails n’incluent pas les modèles définis dans le site web/magasin correspondant.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
