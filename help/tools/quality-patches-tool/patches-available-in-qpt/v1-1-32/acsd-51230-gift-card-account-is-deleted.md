---
title: 'ACSD-51230 : le compte de carte cadeau est supprimé'
description: Appliquez le correctif ACSD-51230 pour résoudre le problème Adobe Commerce en raison duquel le compte de carte-cadeau est supprimé lorsque le remboursement partiel d’un produit simple est traité à partir d’une commande.
feature: Customer Service, Gift, Marketing Tools
role: Admin
exl-id: a4aed574-3908-42e0-ac32-911f61b44995
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-51230 : le compte de carte cadeau est supprimé

Le correctif ACSD-51230 corrige le problème de suppression du compte de carte-cadeau lorsque le remboursement partiel d’un produit simple est traité à partir d’une commande. Ce correctif est disponible lorsque [!DNL Quality Patches Tool (QPT)] 1.1.32 est installé. L’ID de correctif est ACSD-51230. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.7.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.7 - 2.4.6

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le compte de carte-cadeau est supprimé lorsque le remboursement partiel d’un produit simple est traité à partir d’une commande.

<u>Étapes à reproduire</u> :

1. Créez une commande avec une *Carte cadeau* et un *produit simple* (par exemple, *ajouter : SKU : GI000XX000XXX, SKU : PC046CP042076*) (tout mode de paiement et de livraison fonctionne).
1. Facturez la commande.
1. Accédez à **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Un compte est créé pour la carte-cadeau.
1. Accédez maintenant à **[!UICONTROL Order]** et créez un **[!UICONTROL Credit Memo]**.
1. Remplacez la quantité de la *carte-cadeau* par 0 et mettez-la à jour. Cela créera un remboursement partiel pour le *produit simple*.
1. Cliquez sur **[!UICONTROL Refund]**.
1. Actualisez maintenant le **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Le compte nouvellement créé est supprimé.

<u>Résultats attendus</u>

Le compte de carte-cadeau peut être utilisé, car le remboursement n’a pas été créé pour la carte-cadeau.

<u>Résultats réels</u>

Le compte de carte-cadeau est supprimé et la carte-cadeau n’est pas remboursée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].


Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
