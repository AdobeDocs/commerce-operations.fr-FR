---
title: 'MDVA-43605 : les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API Rest'
description: Le correctif MDVA-43605 corrige le problème où les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API Rest. Ce correctif est disponible lorsque l’[Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43605. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605 : les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API Rest

Le correctif MDVA-43605 corrige le problème où les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API Rest. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 est installé. L’ID du correctif est MDVA-43605. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.1 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les données de commande renvoient des valeurs négatives pour les totaux des lignes lors de l’utilisation de l’API REST.

<u>Procédure à suivre </u> :

1. Activez la livraison gratuite.
1. Accédez à **Configuration** > **Catalogue** > **Prix** > et définissez Périmètre du prix du catalogue = Site Web.
1. Accédez à **Configuration** > **Ventes** > **Taxes** et mettez à jour :
   * Classe De Taxe Pour L&#39;Expédition = Marchandises Taxables
   * Paramètres de calcul :
      * Prix catalogue = Taxe incluse
      * Prix d’expédition = Prix inclus
      * Appliquer une remise sur les prix = Taxe incluse
   * Paramètres d’affichage des prix : Taxe incluse (tous les champs)
   * Paramètres d’affichage du panier : Taxe incluse (tous les champs)
   * Commandes, factures, avoirs :
      * Afficher le montant d&#39;expédition = Taxe incluse
1. Créer un taux d&#39;imposition pour les États-Unis (État = &#39;*&#39;), Taux en pourcentage = 24,00
1. Créez une règle de taxe avec le taux de taxe ci-dessus.
1. Créez une règle de prix de panier avec un coupon spécifique et une Remise = 50 $ du montant fixe pour l’ensemble du panier.
1. Créez quatre produits aux prix suivants : 8,90 $, 5,90 $, 6,90 $ et 5,95 $.
1. Créez une commande administrateur comprenant quatre de ces produits à l’aide du code de coupon créé à l’étape précédente. Utilisez la livraison gratuite.
1. Le paiement ne doit pas être requis, car le code de coupon couvre le total du panier.
1. Récupérez l’ordre qui vient d’être créé via le point d’entrée de l’API REST :

   ```json
   GET rest/V1/orders/1
   ```

<u>Résultats attendus</u> :

Les valeurs de `base_row_total` et `base_row_total_incl_tax` dans la réponse sont nulles.

<u>Résultats réels</u> :

Les champs `base_row_total` et `base_row_total_incl_tax` de la réponse ont des valeurs négatives.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
