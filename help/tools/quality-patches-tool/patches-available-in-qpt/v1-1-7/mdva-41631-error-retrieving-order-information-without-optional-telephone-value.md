---
title: 'MDVA-41631 : erreur lors de la récupération des informations de commande sans la valeur facultative « téléphone »'
description: Le correctif MDVA-41631 corrige le problème où les utilisateurs et utilisatrices obtiennent une erreur lors de la récupération des informations de commande sans valeur « téléphone » facultative via  [!DNL GraphQL]. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 est installé. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631 : erreur lors de la récupération des informations de commande sans la valeur facultative « téléphone »

Le correctif MDVA-41631 corrige le problème où les utilisateurs et utilisatrices obtiennent une erreur lors de la récupération des informations de commande sans valeur « téléphone » facultative via [!DNL GraphQL]. Ce correctif est disponible lorsque la version 1.1.7 de [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) est installée. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs obtiennent une erreur lors de la récupération des informations de commande sans valeur « téléphone » facultative via [!DNL GraphQL].

<u>Procédure à suivre </u> :

1. Accédez à **Boutique** > **Configuration** > **Clients** > **Configuration client** > **Options de nom et d’adresse** > **Afficher le numéro de téléphone** et définissez le numéro de téléphone comme facultatif.
1. Passez une commande en utilisant [!DNL GraphQL API] comme client connecté.
   * Ne définissez pas le numéro de téléphone lors de la définition des adresses de facturation et d’expédition. Suivez les instructions données dans le [[!DNL GraphQL] tutoriel de passage en caisse](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) de notre documentation destinée aux développeurs.
1. Récupérez la commande à l’aide de la requête [!DNL GraphQL] [`customerOrders`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/).

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Résultats attendus</u> :

Les utilisateurs obtiennent les informations sur la commande.

<u>Résultats réels</u> :

Les utilisateurs reçoivent l&#39;erreur suivante : *« message »: « Erreur de serveur interne »,*

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur le [!DNL Quality Patches Tool], voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
