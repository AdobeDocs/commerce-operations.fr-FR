---
title: 'ACSD-61969 : obligatoire pour saisir le code de bon tel que configuré en majuscules ou en minuscules.'
description: Appliquez le correctif ACSD-61969 pour résoudre le problème Adobe Commerce en raison duquel un utilisateur doit saisir le code de coupon exactement tel qu’il est configuré en majuscules ou en minuscules.
feature: Price Rules
role: Admin, Developer
source-git-commit: b2660e3ca0dedbe4c9d8fa441f2e49b2e096474b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969 : obligatoire pour saisir le code de bon tel que configuré en majuscules ou en minuscules.

Le correctif ACSD-61969 corrige le problème en raison duquel un utilisateur doit saisir le code de coupon exactement tel qu’il est configuré en majuscules ou en minuscules. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 est installé. L’ID de correctif est ACSD-61969. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lorsque vous les appliquez à partir du serveur principal, vous devez saisir le code du bon exactement tel que configuré en majuscules ou en minuscules. Elles sont sensibles à la casse lors de la création de l’ordre d’administration, mais pas à la casse sur le storefront.

<u>Étapes à reproduire</u> :

1. Créez un *[!UICONTROL Cart Price Rule]* avec un coupon spécifique *TEST*. Assurez-vous que le code de coupon est en majuscules.
1. Créez une commande dans l’Admin.
1. Ajoutez *test* au champ *[!UICONTROL Apply Coupon Code]* et cliquez sur la flèche près du champ pour appliquer le coupon.
1. Observez le résultat.

<u>Résultats attendus</u> :

Le coupon est appliqué avec succès. Le champ coupon n’est pas sensible à la casse.

<u>Résultats réels</u> :

Le coupon n&#39;est pas appliqué. L&#39;erreur suivante s&#39;affiche :

*Le code de coupon &quot;test&quot; n&#39;est pas valide. Vérifiez le code et réessayez.*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
