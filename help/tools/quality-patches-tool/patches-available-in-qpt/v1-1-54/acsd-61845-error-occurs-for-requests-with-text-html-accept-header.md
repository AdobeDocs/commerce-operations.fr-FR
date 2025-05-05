---
title: "ACSD-61845 : une erreur se produit pour les requêtes avec l’en-tête accept text/html"
description: Appliquez le correctif ACSD-61845 pour résoudre le problème Adobe Commerce en raison duquel l’envoi d’une requête HTTP avec uniquement un en-tête d’acceptation *text/html* provoque une erreur 500, avec les modules B2B installés.
feature: B2B
role: Admin, Developer
source-git-commit: 8dbf91806097281fb4f7c74e182f10b09b18e925
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845 : une erreur se produit pour les requêtes dont l’en-tête *text/html* accept

Le correctif ACSD-61845 corrige le problème en raison duquel une requête HTTP contenant uniquement un en-tête d’acceptation *text/html* provoquait une erreur 500 en raison de décalages de type de média dans la gestion des réponses. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 est installé. L’ID de correctif est ACSD-61845. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Lors de l’envoi d’une requête HTTP contenant uniquement *text/html* dans l’en-tête accept, une erreur 500 se produit en raison d’une incohérence dans la configuration du type de média.

<u>Conditions préalables</u> :

Les modules B2B sont installés et activés.

<u>Étapes à reproduire</u> :

1. Envoyez une requête avec uniquement *text/html* dans l’en-tête accept, comme suit :

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Résultats attendus</u> :

La page est renvoyée avec un *200 status code*.

<u>Résultats réels</u> :

Une erreur 500 est renvoyée, avec le message d’erreur suivant dans le `exception.log` :

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

[[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
