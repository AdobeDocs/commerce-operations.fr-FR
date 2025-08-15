---
title: 'MDVA-39163 : méthodes d’expédition non disponibles pour les utilisateurs nouvellement enregistrés avec des produits de la session d’invité'
description: Le correctif MDVA-39163 résout le problème où les méthodes d’expédition ne sont pas disponibles lorsqu’un nouvel utilisateur est enregistré et que les produits du panier sont issus de la session invité. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-39163. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: CMS, Marketing Tools, Orders, Products, Shipping/Delivery
role: Admin
exl-id: 781b466b-7d8f-4ad1-9fb4-5404cd02f7d8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# MDVA-39163 : méthodes d’expédition non disponibles pour les utilisateurs nouvellement enregistrés avec des produits de la session d’invité

Le correctif MDVA-39163 résout le problème où les méthodes d’expédition ne sont pas disponibles lorsqu’un nouvel utilisateur est enregistré et que les produits du panier sont issus de la session invité. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID du correctif est MDVA-39163. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les méthodes d’expédition ne sont pas disponibles lorsque le nouvel utilisateur est enregistré et les produits du panier sont issus de la session de l’invité.

<u>Procédure à suivre </u> :

1. Accédez à **Admin** > **Magasins** > **Configuration** > **Ventes** > **Méthodes de diffusion**. Activez uniquement la méthode d’expédition **Taux forfaitaire** et désactivez tout le reste.
1. Dans la méthode d&#39;expédition **Taux forfaitaire**, sélectionnez l&#39;option **Pays spécifique** disponible dans le paramètre **Expédier aux pays applicables** et sélectionnez un pays dans la liste (par exemple, États-Unis).
1. Accédez à **Admin** > **Magasins** > **Configuration** > **Client** > **Configuration client** et définissez **Exiger une confirmation par e-mail** sur _Yes_.
1. Créez un modèle d’e-mail dans **Admin** > **Marketing** > **Modèles d’e-mail** et chargez `Footer (magento/luma)` modèle, puis remplacez le contenu du modèle par un bloc CMS.

   ```CMS
   {{block class="Magento\Cms\Block\Block" block_id="footer_links_block"}}
   ```

1. Accédez à **Admin** > **Contenu** > **Conception** > **Configuration** et sélectionnez le thème associé à votre site web frontal. Définissez le « Modèle de pied de page » sur le nouveau modèle d’e-mail créé.
1. Accédez au serveur frontal et ajoutez un produit au panier.
1. Créez un client ou une cliente ; vous recevrez un e-mail pour confirmer l’adresse e-mail. Cliquez sur le lien de vérification. Vous serez connecté au site web.
1. Accédez à **Mon compte** et ajoutez une adresse. Définissez le pays de l’adresse sur le pays d’expédition que vous avez défini précédemment dans la configuration d’administration.
1. Accédez au passage en caisse.

<u>Résultats attendus</u> :

Le mode d’expédition est disponible, car le client dispose d’une adresse compatible avec le pays d’expédition.

<u>Résultats réels</u> :

Mode d’expédition non disponible.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/fr/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide de [!DNL Quality Patches Tool].
