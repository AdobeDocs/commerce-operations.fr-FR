---
title: 'ACSD-63406 : les guillemets persistants expirés ne sont pas effacés lors de l’exécution de la tâche cron persistent_clear_expired'
description: Appliquez le correctif ACSD-63406 pour résoudre le problème d’Adobe Commerce où les guillemets persistants expirés ne sont effacés par aucune tâche cron lors de l’exécution de la tâche cron « persistent_clear_expired ».
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406 : les guillemets persistants expirés ne sont pas effacés lors de `persistent_clear_expired`’exécution de la tâche cron

Le correctif ACSD-63406 corrige le problème où les guillemets persistants expirés ne sont effacés par aucune tâche cron lors de l’exécution de la tâche cron `persistent_clear_expired`. Ce correctif est disponible lorsque la version 1.1.62 de [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) est installée. L’ID du correctif est ACSD-63406. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.7-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les guillemets persistants expirés ne sont effacés par aucune tâche cron lors de l’exécution de la tâche cron `persistent_clear_expired`.

<u>Procédure à suivre </u> :

1. Créez une catégorie et un produit.
1. Accédez à **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**.
   1. Définissez toutes les options sur *Oui*.
   1. Définissez **[!UICONTROL Persistence Lifetime (seconds)]** sur *60*.
1. Créer un compte client sur le storefront et se connecter.
1. Ajoutez un produit au panier.
1. Déconnectez-vous, attendez 60 secondes et reconnectez-vous.

<u>Résultats attendus</u> :

La tâche cron `persistent_clear_expired` doit supprimer les guillemets persistants en fonction des paramètres de durée de vie de persistance dans la configuration.

<u>Résultats réels</u> :

La valeur `is_persistent` pour le devis client reste *1* dans le tableau des devis.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :

* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
