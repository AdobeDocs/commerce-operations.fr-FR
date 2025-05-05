---
title: 'ACSD-60344 : duplication des emails de confirmation de commande lors de l''utilisation de [!UICONTROL Purchase Order] avec validation automatique'
description: Appliquez le correctif ACSD-60344 pour résoudre le problème Adobe Commerce en raison duquel des emails de confirmation de commande en double sont envoyés lors de l’utilisation d’un [!UICONTROL Purchase Order] avec approbation automatique.
feature: Purchase Orders
role: Admin, Developer
source-git-commit: afa03b31e4af0be1ebc0d12aabd4f9d8be17d1fe
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344 : duplication des emails de confirmation de commande lors de l&#39;utilisation de *[!UICONTROL Purchase Order]* avec validation automatique

Le correctif ACSD-60344 corrige le problème d’envoi d’emails de confirmation de commande en double lors de l’utilisation d’un *[!UICONTROL Purchase Order]* avec validation automatique. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 est installé. L’ID de correctif est ACSD-60344. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p4

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Des emails de confirmation de commande en double sont envoyés lors de l’utilisation d’un *[!UICONTROL Purchase Order]* avec validation automatique.

<u>Conditions préalables</u>

Activez les modules B2B et *[!UICONTROL Purchase Order]*.

<u>Étapes à reproduire</u> :

1. Créez un compte d’entreprise et activez-y un *[!UICONTROL Purchase Order]*.
1. Créez un compte d’utilisateur ordinaire et ajoutez-le au compte d’entreprise en tant qu’utilisateur d’entreprise.
1. Effectuez une commande à partir de ce compte.
1. Exécutez cron et vérifiez les emails.

<u>Résultats attendus</u> :

Un seul email de confirmation de commande est reçu par commande.

<u>Résultats réels</u> :

Deux emails de confirmation de commande sont reçus.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.


## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] : outil en libre-service pour les correctifs de qualité ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils.
