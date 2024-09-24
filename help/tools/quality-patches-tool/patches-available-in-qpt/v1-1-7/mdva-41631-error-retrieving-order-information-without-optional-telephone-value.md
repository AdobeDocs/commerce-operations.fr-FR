---
title: '''MDVA-41631 : erreur lors de la récupération des informations de commande sans valeur "téléphonique" facultative'
description: Le correctif MDVA-41631 corrige le problème en raison duquel les utilisateurs obtenaient une erreur lors de la récupération des informations de commande sans valeur "téléphonique" facultative via GraphQL. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-41631 : erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative

Le correctif MDVA-41631 corrige le problème en raison duquel les utilisateurs obtenaient une erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative via GraphQL. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7 est installé. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.4.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.2-p1

**Compatible avec les versions d’Adobe Commerce :**

Adobe Commerce (toutes les méthodes de déploiement) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Les utilisateurs obtiennent une erreur lors de la récupération des informations de commande sans valeur &quot;téléphonique&quot; facultative via GraphQL.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasin** > **Configuration** > **Clients** > **Configuration client** > **Options de nom et d’adresse** > **Afficher le numéro de téléphone** et définissez le numéro de téléphone comme facultatif.
1. Passez une commande à l’aide de l’API GraphQL en tant que client connecté.
   * Ne définissez pas le numéro de téléphone lors de la définition des adresses de facturation et de livraison. Suivez les instructions du [tutoriel sur le passage en caisse de GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/tutorials/checkout/checkout-customer.html) dans notre documentation destinée aux développeurs.
1. Récupérez la commande à l’aide de la requête GraphQL [customerCommandes](https://devdocs.magento.com/guides/v2.4/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Résultats attendus</u> :

Les utilisateurs obtiennent des informations sur la commande.

<u>Résultats réels</u> :

Les utilisateurs reçoivent l’erreur suivante : *&quot;message&quot;: &quot;Erreur interne du serveur&quot;,*

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
