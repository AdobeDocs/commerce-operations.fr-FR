---
title: "ACSD-42807 : symbole de devise personnalisée non affiché sur storefront"
description: Le correctif ACSD-42807 corrige le problème en raison duquel le symbole de devise personnalisé ne s’affiche pas sur le storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID de correctif est ACSD-42807. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.
feature: Storefront
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-42807 : le symbole de devise personnalisé ne s’affiche pas sur storefront

Le correctif ACSD-42807 corrige le problème en raison duquel le symbole de devise personnalisé ne s’affiche pas sur le storefront. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17 est installé. L’ID de correctif est ACSD-42807. Veuillez noter que le problème doit être corrigé dans Adobe Commerce 2.4.6.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.3

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.0 - 2.4.4

>[!NOTE]
>
>Le correctif peut devenir applicable à d’autres versions avec les nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la [[!DNL Quality Patches Tool] : recherchez des correctifs sur la page ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilisez l’ID de correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

Le symbole de devise personnalisé ne s’affiche pas sur le storefront.

<u>Étapes à reproduire</u> :

1. Accédez à **Magasin** > **Paramètres** > **Configurations** > **Général** > **Configuration de devise** et sélectionnez une devise personnalisée. Par exemple, **Peso Mexicain**.
1. Accédez à **Magasin** > **Paramètres** > **Configurations** > **Général** > **Options de paramètres régionaux** et sélectionnez **Espagnol (Mexique)**.
1. Accédez à **Magasin** > **Symboles de devise** et configurez le symbole de devise sur **MX$**.
1. Vérifiez le symbole de devise sur l’interface utilisateur frontale.

<u>Résultats attendus</u> :

Le symbole de devise par défaut est &quot;MX$&quot; avec une devise définie comme &quot;Mexique&quot; et un paramètre régional défini comme &quot;Espagnol (Mexique)&quot;.

<u>Résultats réels</u> :

Le symbole monétaire par défaut affiche &quot;$&quot;.

## Appliquer le correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source sur site : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide [!DNL Quality Patches Tool].
* Adobe Commerce sur l’infrastructure cloud : [mises à niveau et correctifs > Appliquer les correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=fr) dans le guide Commerce on Cloud Infrastructure.

## Lecture connexe

Pour en savoir plus sur l’outil Correctifs de qualité, consultez :

* [ L’outil de correctifs de qualité est sorti : un nouvel outil pour les correctifs de qualité en libre-service ](https://experienceleague.adobe.com/fr/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) dans la base de connaissances de support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide [!DNL Quality Patches Tool].

Pour plus d&#39;informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Recherche de correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=fr) dans le guide [!DNL Quality Patches Tool].
