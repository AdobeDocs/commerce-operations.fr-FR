---
title: 'ACSD-60788 : scripts personnalisés pour  [!DNL Google Tag Manager]  non exécutés en raison d’erreurs CSP'
description: Appliquez le correctif ACSD-60788 pour résoudre le problème d’Adobe Commerce où les scripts personnalisés pour ne sont pas exécutés en raison  [!DNL Google Tag Manager] ’erreurs de la politique de sécurité du contenu (CSP).
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788 : les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de politique de sécurité du contenu

Le correctif ACSD-60788 corrige le problème où les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de politique de sécurité du contenu. Ce correctif est disponible lorsque la version 1.1.52 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. L’ID du correctif est ACSD-60788. Notez que ce problème doit être résolu dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les scripts personnalisés pour [!DNL Google Tag Manager] ne sont pas exécutés en raison d’erreurs de politique de sécurité du contenu (CSP).

<u>Procédure à suivre </u> :

1. Configurez la variable *[!DNL Google Tag Manager]* .
1. Configurez la *[!DNL Google Tag Manager]* balise HTML personnalisée .
1. Placez le code JavaScript suivant dans la première balise :

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Videz les caches après la configuration de *GTM*.
1. Ouvrez la Developer Console dans votre navigateur.
1. Ouvrez la page d’accueil.

<u>Résultats attendus</u> :

La console de développement du navigateur affiche *à usage unique à partir d’un JS simple (caractères aléatoires)*.

<u>Résultats réels</u> :

La console de développement du navigateur affiche *Nonce à partir du JS simple non défini*.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] sortie : un nouvel outil permettant de mettre en libre-service des correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce en utilisant [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!UICONTROL Quality Patches Tool].


Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
