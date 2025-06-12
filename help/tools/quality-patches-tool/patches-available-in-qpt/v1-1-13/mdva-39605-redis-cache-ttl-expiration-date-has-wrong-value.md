---
title: 'MDVA-39605 : la valeur de la TTL du cache Redis (date d’expiration) est incorrecte'
description: Le correctif MDVA-39605 résout le problème lorsque la TTL du cache Redis (date d’expiration) a une valeur incorrecte. Ce correctif est disponible lorsque l’outil [Outil de correctifs de la qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-39605. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605 : la valeur de la TTL du cache Redis (date d’expiration) est incorrecte

Le correctif MDVA-39605 résout le problème lorsque la TTL du cache Redis (date d’expiration) a une valeur incorrecte. Ce correctif est disponible lorsque l’[outil de correctifs de qualité (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13 est installé. L’ID du correctif est MDVA-39605. Notez que le problème est planifié pour être corrigé dans Adobe Commerce 2.4.5.

## Produits et versions concernés

**Le correctif est créé pour la version Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.4.2

**Compatible avec les versions d’Adobe Commerce :**

* Adobe Commerce (toutes les méthodes de déploiement) 2.3.4 - 2.4.4

>[!NOTE]
>
>Le correctif peut s’appliquer à d’autres versions avec de nouvelles versions de l’outil de correctifs de qualité. Pour vérifier si le correctif est compatible avec votre version d’Adobe Commerce, mettez à jour le package `magento/quality-patches` vers la dernière version et vérifiez la compatibilité sur la page [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilisez l’ID du correctif comme mot-clé de recherche pour localiser le correctif.

## Problème

La TTL du cache Redis (date d’expiration) a une valeur incorrecte.

<u>Procédure à suivre </u> :

Pour tester le correctif, videz le cache et ouvrez un produit configurable sur le storefront. Ouvrez ensuite un terminal (console) et procédez comme suit :

1. Exécutez la commande : `redis-cli`.
1. Exécutez `KEYS "*PRICE"` (il ne doit y avoir qu’une seule clé dans le résultat, par exemple `zc:ti:e54_PRICE`). Copiez la clé.
1. Exécutez `SMEMBERS` suivi de la clé de l’étape précédente (par exemple, `SMEMBERS zc:ti:e54_PRICE`). Copiez toute clé du résultat (par exemple, e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Exécutez `KEYS "*<key>"` avec le nom de clé de l’étape précédente pour obtenir le nom de clé complet (par exemple, `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Le résultat ne doit comporter qu’une seule clé (par exemple, `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Comme vous pouvez le constater, le nom complet de la clé est simplement le nom de la clé avec le préfixe « `zc:k:` ». Copiez maintenant le nom complet de la clé.
1. Exécutez `HGETALL` suivi du nom complet de la clé à partir de l’étape 4 pour vérifier la valeur. La valeur doit contenir des données sérialisées des produits associés d’un produit configurable associé.
1. Exécutez `TTL` suivi du nom complet de la clé à partir de l’étape 4 pour vérifier si la clé a une expiration. Le résultat doit être différent de **-1** et **-2** et doit être approximativement 2592000 (30 jours). Bien que le délai d’expiration défini dans le code soit d’un an, la bibliothèque Redis utilisée dans Adobe Commerce a une limite d’expiration maximale stricte de 2592000.

<u>Résultats attendus</u> :

La limite d’expiration est de 2592000

<u>Résultats réels</u> :

La limite d’expiration est définie sur **-1** ou **-2**.

## Application du correctif

Pour appliquer des correctifs individuels, utilisez les liens suivants en fonction de votre méthode de déploiement :

* Adobe Commerce ou Magento Open Source On-premise : [[!DNL Quality Patches Tool] > Utilisation](/help/tools/quality-patches-tool/usage.md) dans le guide de [!DNL Quality Patches Tool].
* Adobe Commerce sur les infrastructures cloud : [Mises à niveau et correctifs > Appliquer des correctifs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) dans le guide Commerce sur les infrastructures cloud .

## Lecture connexe

Pour en savoir plus sur l’outil de correctifs de la qualité, voir :

* Publication de l’outil [Correctifs de qualité](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) un nouvel outil permettant d’appliquer des correctifs de qualité en libre-service dans la base de connaissances du support.
* [Vérifiez si un correctif est disponible pour votre problème Adobe Commerce à l’aide de l’outil de correctifs de qualité](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) dans le guide de [!DNL Quality Patches Tool].

Pour plus d’informations sur les autres correctifs disponibles dans QPT, reportez-vous à [[!DNL Quality Patches Tool] : Rechercher des correctifs](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) dans le guide de [!DNL Quality Patches Tool].
