---
title: 'ACSD-60788 : Scripts personnalisés pour  [!DNL Google Tag Manager] non exécutés en raison d’erreurs CSP'
description: Appliquez le correctif ACSD-60788 pour résoudre le problème Adobe Commerce en raison duquel les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs CSP (Content Security Policy, stratégie de sécurité du contenu).
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788 : les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de stratégie de sécurité du contenu.

Le correctif ACSD-60788 corrige le problème en raison duquel les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de stratégie de sécurité du contenu. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 est installé. L’ID de correctif est ACSD-60788. Veuillez noter que ce problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs CSP (Content Security Policy, stratégie de sécurité du contenu).

<u>Étapes à reproduire</u> :

1. Configurez la variable *[!DNL Google Tag Manager]*.
1. Configurez la balise d’HTML personnalisée *[!DNL Google Tag Manager]*.
1. Placez le code JavaScript suivant dans la première balise :

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Purge des caches après la configuration de *GTM*.
1. Ouvrez la console de développement dans votre navigateur.
1. Ouvrez la page d’accueil.

<u>Résultats attendus</u> :

La console de développement du navigateur affiche *Nonce de JS simple (caractères aléatoires)*.

<u>Résultats réels</u> :

La console de développement du navigateur affiche *Nonce de JS simple non défini*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
