---
title: 'ACSD-64592 : Les liens de réclamation de carte cadeau de magasin non par défaut redirigent vers le site Web par défaut'
description: 'Appliquez le correctif ACSD-64592 pour résoudre le problème suivant : dans une configuration multi-sites, lorsqu’une carte cadeau virtuelle est achetée sur le site web secondaire (non par défaut), le lien Code de carte cadeau dans l’e-mail contient l’URL par défaut du site web.'
feature: Gift, Products
role: Admin, Developer
exl-id: 1cc026c0-7487-48e8-a092-3e72085ca38a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-64592 : Les liens de réclamation de carte cadeau de magasin non par défaut redirigent vers le site Web par défaut

Le correctif ACSD-64592 corrige un problème en raison duquel, dans un environnement multisite, si une carte-cadeau virtuelle est achetée à partir d&#39;un site Web secondaire (non principal), l&#39;e-mail contenant le lien du code de carte-cadeau dirige les utilisateurs vers l&#39;URL du site Web par défaut. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.9.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.6-p3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de [!DNL Quality Patches Tool]. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Dans une configuration multi-site, lorsqu’une carte cadeau virtuelle est achetée à partir d’un site secondaire (non par défaut), l’e-mail contenant le code de carte cadeau dirige les utilisateurs vers l’URL du site web par défaut.

<u>Procédure à suivre </u> :

1. Créez un site web secondaire, un magasin et une vue de magasin.
1. Configurez des URL de base différentes pour le site web de base et le site web secondaire.
1. Créez une carte cadeau virtuelle avec des options de montant.
1. Générez un nouveau pool de code sous **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**.
1. Passer une commande avec le produit Carte-cadeau sur le site Web secondaire.
1. Facturez la commande dans l’administration Commerce.
1. Vérifiez l’URL dans le lien Code de carte cadeau de l’e-mail *Vous avez reçu un cadeau de la part de Two*.

<u>Résultats attendus</u> :

Le lien Code de la carte-cadeau doit contenir le lien vers le deuxième site Web.

<u>Résultats réels</u> :

Le lien Code de carte cadeau contient l’URL par défaut du site web, même si la commande est passée sur le deuxième site web.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur [!DNL Quality Patches Tool], consultez :
* [[!DNL Quality Patches Tool] : un outil en libre-service pour les correctifs de qualité](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) dans le guide Outils .
