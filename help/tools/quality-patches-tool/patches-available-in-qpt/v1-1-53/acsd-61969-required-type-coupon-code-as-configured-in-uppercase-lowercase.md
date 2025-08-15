---
title: 'ACSD-61969 : requis pour saisir le code de coupon tel que configuré en majuscules ou en minuscules'
description: Appliquez le correctif ACSD-61969 pour résoudre le problème d’Adobe Commerce où un utilisateur doit saisir le code de coupon exactement tel qu’il est configuré en majuscules ou en minuscules.
feature: Price Rules
role: Admin, Developer
exl-id: 4bdf797b-2570-49f8-8e03-952b49ed1d18
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969 : requis pour saisir le code de coupon tel que configuré en majuscules ou en minuscules

Le correctif ACSD-61969 corrige le problème en raison duquel un utilisateur doit saisir le code de coupon exactement tel qu’il est configuré en majuscules ou en minuscules. Ce correctif est disponible lorsque la version 1.1.53 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-61969. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Vous devez saisir le code de coupon exactement comme configuré en majuscules ou en minuscules lors de son application à partir du serveur principal. Ils sont sensibles à la casse lors de la création de la commande d’administration, mais pas au storefront.

<u>Procédure à suivre </u> :

1. Créez un *[!UICONTROL Cart Price Rule]* avec un coupon spécifique *TEST*. Assurez-vous que le code du coupon est en majuscules.
1. Créez une commande dans l’Admin.
1. Ajoutez *test* au champ *[!UICONTROL Apply Coupon Code]* et cliquez sur la flèche près du champ pour appliquer le coupon.
1. Observez le résultat.

<u>Résultats attendus</u> :

Le coupon a été appliqué. Le champ de coupon n’est pas sensible à la casse.

<u>Résultats réels</u> :

Le coupon n’est pas appliqué. L’erreur suivante s’affiche :

*Le code de coupon « test » n’est pas valide. Vérifiez le code et réessayez.*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

[[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
