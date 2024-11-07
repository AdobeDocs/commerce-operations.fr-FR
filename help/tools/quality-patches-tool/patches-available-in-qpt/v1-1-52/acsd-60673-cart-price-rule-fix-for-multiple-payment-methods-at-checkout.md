---
title: "ACSD-60673 : [!UICONTROL Cart Price Rule] problème corrigé pour plusieurs méthodes de paiement lors du passage en caisse"
description: Appliquez le correctif ACSD-60673 pour résoudre le problème Adobe Commerce en raison duquel les remises d’un [!UICONTROL Cart Price Rule] qui utilise une condition de mode de paiement ne sont pas toujours répertoriées dans les totaux.
feature: Price Rules
role: Admin, Developer
source-git-commit: 9334b0bb7aa32cd14622c6dcef799dffe7e35fdc
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673 : [!UICONTROL Cart Price Rule] problème corrigé pour plusieurs méthodes de paiement lors du passage en caisse

Le correctif ACSD-60673 corrige le problème en raison duquel les remises d’un [!UICONTROL Cart Price Rule] qui utilise une condition de mode de paiement ne sont pas toujours répertoriées dans les totaux. Ce correctif est disponible lorsque [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 est installé. L’ID de correctif est ACSD-60673. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.8.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p6

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec de nouvelles versions [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

L’ [!UICONTROL Cart Price Rule] pour plusieurs méthodes de paiement au passage en caisse ne s’applique pas correctement au mode de paiement spécifique.

<u>Conditions préalables</u>

Assurez-vous que dans les **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** et **[!UICONTROL Bank Transfer]** est activé.

<u>Étapes à reproduire</u> :

1. Activez **[!UICONTROL Multiple Payment Methods]**.
1. Créez un *[!UICONTROL Cart Price Rule]*.
   * Définir **[!UICONTROL Conditions]** : Mode de paiement sur **[!UICONTROL Money Order]** (ou transfert bancaire)
   * Sélectionnez **[!UICONTROL Actions]** = *25 %* réduction sur tous les produits
1. Créez un produit virtuel.
1. Pour copier un nouveau devis et le client invité *[!UICONTROL Status]*, accédez au storefront et effacez les cookies.
1. Ajoutez le produit virtuel au panier.
1. Passez à *checkout*.
1. Cliquez sur le mode de paiement défini dans le *[!UICONTROL Cart Price Rule]*.
1. Mettez à jour votre *[!UICONTROL Billing Address]*.
1. Assurez-vous que la remise est visible dans le montant total.
1. Cochez la case pour modifier le mode de paiement.
1. Vérifiez que la remise est visible.

<u>Résultats attendus</u> :

La remise est visible dans *Totaux* après avoir coché la case pour passer à un mode de paiement applicable.

<u>Résultats réels</u> :

La remise n’est pas visible dans les *Totaux*.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], voir :

* [[!DNL Quality Patches Tool] publié : un nouvel outil pour les correctifs de qualité en libre-service](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!UICONTROL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
