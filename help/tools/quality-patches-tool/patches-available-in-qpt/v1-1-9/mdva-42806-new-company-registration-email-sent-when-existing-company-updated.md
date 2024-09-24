---
title: 'MDVA-42806 : un nouveau courrier électronique d’enregistrement de société est envoyé chaque fois qu’une société existante est mise à jour'
description: Le correctif MDVA-42806 résout le problème d’envoi d’un nouvel email d’enregistrement de société chaque fois qu’une société existante est mise à jour via l’API REST. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-42806. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.
feature: REST, B2B, Communications, Companies
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-42806 : un nouveau courrier électronique d’enregistrement de société est envoyé chaque fois que la société existante est mise à jour.

Le correctif MDVA-42806 résout le problème d’envoi d’un nouvel email d’enregistrement de société chaque fois qu’une société existante est mise à jour via l’API REST. Ce correctif est disponible lorsque l’ [outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 est installé. L’ID de correctif est MDVA-42806. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Un nouvel e-mail d’enregistrement de société est envoyé chaque fois qu’une société existante est mise à jour via l’API REST.

<u>Conditions préalables</u> :

Modules B2B installés.

<u>Étapes à reproduire</u> :

1. Créez un compte de société.
1. Utilisez le point d’entrée `/V1&#x200B;/company&#x200B;/<company_id>`. Pour mettre à jour la société créée, voir [mettre à jour la société](https://devdocs.magento.com/guides/v2.4/b2b/company-object.html#update-the-company) dans notre documentation destinée aux développeurs. Voici un exemple de payload :

```php
{
    "company": {
        "id": 2,
        "status": 1,
        "company_name": "Company",
        "company_email": "company@example.test",
        "street": [
            "Test"
        ],
        "city": "Test",
        "country_id": "US",
        "region_id": "1",
        "postcode": "12345",
        "telephone": "8009994301",
        "customer_group_id": 2,
        "sales_representative_id": 1,
        "super_user_id": 2
    }
}
```

<u>Résultats attendus</u> :

Aucun courrier électronique n’est envoyé indiquant &quot;Nouvelle demande d’enregistrement de la société&quot;, car l’API met à jour une société existante.

<u>Résultats réels</u> :

Un courrier électronique est envoyé, indiquant &quot;Nouvelle demande d’enregistrement de la société&quot; chaque fois que la demande d’API est envoyée.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide [!DNL Quality Patches Tool].
